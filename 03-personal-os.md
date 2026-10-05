# 03 — Personal OS (sản phẩm chính)

> **2026-10-04:** không có commit mới từ `4657793` (29/09). Mọi quyết định chờ Founder vẫn mở (xem `04-cong-viec.md`). Dự án mới HowlsOS: `07-howlsos.md`.

## Sản phẩm
- Hệ điều hành cá nhân cho **một chủ sở hữu (Founder)**: personal CRM + công việc + AI + integrations.
- **API-first**, một Postgres làm nguồn sự thật, lộ ra qua REST `/api/v1` và lớp tool **MCP** để AI đọc/ghi có kiểm quyền và audit.
- Dịch vụ ngoài (Google Calendar, Gmail, Notion, GitHub, Resend) chỉ là adapter thay thế được.
- **Stack:** Next.js 16 (App Router, Route Handlers) · TypeScript strict · Tailwind v4 · Supabase (Postgres, Auth, RLS) · Zod · Vercel · MCP. Modular monolith (`src/modules/<domain>`), không microservice/queue/Redis.
- **Song ngữ VI/EN**, mặc định **VI**, lưu lựa chọn qua cookie; từ điển ở `src/lib/i18n` (`vi.ts`, `en.ts`, `client.tsx`, `server.ts`, `index.ts`).

## Mong muốn UI của Founder
- Tối giản, kiểu **app macOS / Apple-like**.
- Bố cục **CRM chuyên nghiệp**: sidebar nhóm theo domain (Planning, Projects, Finance, Relationships...) + dashboard.
- **Mobile-friendly**: mỗi màn hình chỉ vài thông tin chính.
- **KHÔNG** kiểu landing page.
- `DESIGN.md` trong repo là nguồn sự thật cho token/typography/component (bản sao: `docs/personal-os-repo/DESIGN.md`).

## Repo & deploy
- Repo: https://github.com/PNCTriet/personal-os — **PUBLIC** → tuyệt đối không commit secret.
- **Author commit bắt buộc:** `PNCTriet <147395796+PNCTriet@users.noreply.github.com>` (Vercel Hobby chặn deploy từ author khác).
- Live: https://personal-os-blond-eta.vercel.app — **auto-deploy khi push lên `main`**.
- Chạy local: `nvm use && npm ci && npm run dev` (demo mode, không cần setup). Kiểm tra: `npm run typecheck && npm run lint && npm run build`.
- Hai mode tự chọn: **Demo mode** (thiếu env Supabase → dữ liệu mẫu in-memory) và **Supabase mode** (đủ `NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY`, `OWNER_EMAIL`).

## Lịch sử `origin/main` (đã `git fetch` lại ngày 2026-10-04, không đổi; giờ quy đổi sang VN)
| Commit | Thời gian (VN) | Nội dung |
|---|---|---|
| `4657793` | 29/09 11:45 | Restyle app shell kiểu Notion ấm + trang login + avatar menu; **thêm `documents/UX_UI.md`** |
| `f6a37c3` | 29/09 03:07 | Commit rỗng để trigger deploy |
| `375f22a` | 29/09 02:56 | PR #3: mobile dashboard tối giản, fix scroll drawer, i18n vi/en (mặc định vi) |
| `c964f39` | 29/09 02:29 | PR #2: CRM app shell + dashboard command-center + preview các domain |
| `7766f77` | 29/09 02:09 | PR #1: MVP v0 (projects, tasks, today, activity) + demo mode |
| `4156fe8` | 29/09 01:57 | docs: ADR-017 thứ tự client Cursor → ChatGPT (OAuth ở 1.5b); accept ADR của TD |
| `88e5cc9` | 29/09 01:54 | docs: Phase 1 plan |
| `0a9f980` | 29/09 01:53 | docs: lock ADR-003/012/013/015/017 (Founder duyệt 2026-09-29) |
| `c71e3a8` | 29/09 01:26 | Phase 0: toàn bộ tài liệu kiến trúc |

**Vấn đề với `4657793`:**
- `documents/UX_UI.md` mô tả **một app khác ("DNY CRM"**, app văn phòng luật, Ant Design) chứ không phải Personal OS → câu hỏi mở: giữ hay xoá.
- Commit này được author bằng **email công việc** của Founder (không phải noreply) trên repo public → lộ email. (Không ghi lại địa chỉ ở đây.)
- Ghi chú: bản clone local trên box `/workspace/personal-os` đang **chậm 1 commit** (chưa có `4657793`); các bản sao trong folder này lấy từ `origin/main`.

## Hạ tầng & blocker
- **Supabase:** đang chạy **mock data** vì tài khoản Supabase `PNCTriet` đã đạt giới hạn **2 project free** (`DNY_DB`, `HOWLSLAB`). Lựa chọn (chờ Founder):
  1. Pause một project hiện có để tạo project mới (miễn phí).
  2. Nâng Pro ~ $25/tháng (ngoài quỹ).
  3. Tiếp tục mock data.
- **CI:** file workflow đang "đỗ" ở `ci/github-actions-ci.yml` (typecheck, lint, build, migration + RLS smoke test) vì push workflow cần GitHub scope `workflow`. Muốn bật: chuyển sang `.github/workflows/ci.yml` bằng tài khoản có scope đó.
- Migration thật duy nhất: `supabase/migrations/20260929000000_mvp_v0_work.sql` (profiles, companies, projects, tasks, audit_logs, RLS). Schema đầy đủ chỉ là proposal: `supabase/proposal/0000_proposed_schema.sql`.

## Bug UI đã biết (chưa sửa)
1. Mobile: ô tìm kiếm bị ép chỉ còn "Tì…".
2. Nhãn hiển thị "Hạn hôm …" thay vì "Hạn hôm nay".
3. Nút Approve bị mờ (faded).
4. Ô ngày hiển thị `mm/dd/yyyy` (không theo định dạng VN).

Chờ Founder: sửa ngay hay để sau khi duyệt MVP.

## Có gì trong MVP v0 (theo README repo)
- Module: companies (read), projects, tasks (status, priority, due, kind `task|follow_up|milestone`, mã `HOWL-POS-01-T07`, đổi mã khi move + `previous_codes`), today, activity (từ `audit_logs`).
- API `/api/v1/projects`, `/api/v1/tasks` (CRUD theo id hoặc code, Zod, envelope `{data, meta}`/`{error}`, cursor pagination), `/api/v1/health`.
- App shell: sidebar thu gọn nhóm theo domain (drawer trên mobile), ⌘K command palette, quick-add, theme sáng/tối; dashboard 8 KPI; Tasks table + kanban kéo thả; các domain khác chỉ là preview read-only từ dữ liệu mẫu.
- **Chưa có:** Supabase hosted + generated types, API keys + permission layer (T14/T11), idempotency, rate limit, logging/Sentry, MCP, e2e Playwright.

## Tóm tắt tài liệu Phase 0 (`docs/personal-os-repo/docs/`)
| File | Tóm tắt |
|---|---|
| `architecture.md` | Lớp hệ thống, layout repo, ranh giới module, vòng đời request ghi, môi trường, env vars |
| `domain-model.md` | Bounded contexts, entity, luật định danh (UUID + mã người đọc), phân loại dữ liệu |
| `schema.md` | Lý do từng bảng, cắt/gộp so với spec (ADR-015), RLS, soft delete, kế hoạch migration |
| `erd.md` | Sơ đồ ERD Mermaid theo domain |
| `api.md` | Contract `/api/v1`: quy ước, endpoint Phase 1 chi tiết, phase sau ở mức contract |
| `security.md` | Actors, scopes, operation registry (lớp quyền duy nhất), confirmation flow, API keys, RLS, token storage, audit, rate limit |
| `integrations.md` | Kiến trúc adapter, OAuth Google/Notion, webhooks, health |
| `ai-tools.md` | Tool registry, catalogue, quyền, `ai_actions` + audit, confirmations, grounding, MCP server |
| `roadmap.md` | Phase 0–8 + 1.5a (Cursor MCP, 3 ngày) + 1.5b (ChatGPT OAuth, 4.5 ngày) |
| `phase-1-plan.md` | 22 task `HOWL-POS-P1-T01…T22` (~22 ngày + 15% ≈ 5 tuần), DoD, rủi ro, những gì Founder phải cung cấp, checklist bảo mật, task Phase 1.5 |
| `risks.md` | 16 rủi ro kỹ thuật R-01…R-16 (cao nhất: scope creep, prompt injection, ràng buộc Google OAuth) |
| `decisions.md` | 21 ADR + status log (xem dưới) |

## ADR — trạng thái thực tế theo `docs/decisions.md` (origin/main)
> Lưu ý: brief giao việc gọi ADR-003/012/013/015 là "open", nhưng file `decisions.md` ghi chúng **đã Accepted bởi Founder ngày 2026-09-29**. Bảng dưới theo file.

| ADR | Nội dung | Trạng thái |
|---|---|---|
| ADR-003 | Data access: supabase-js + generated types + SQL functions (RPC), **không ORM** | Accepted (Founder) 29/09 |
| ADR-012 | Confirmation server-side cho actor không phải session; **ngoại lệ chi tiêu AI < 50.000 VND tự ghi** (có audit + Undo) | Accepted (Founder) 29/09. **Còn mở:** guardrail trần 24h (mặc định 500.000 VND hoặc 20 mục/actor) — chưa có hiệu lực nếu Founder chưa duyệt |
| ADR-013 | Auth integrations; Google = **@gmail.com cá nhân (không Workspace)** → app External ở Testing, refresh token hết hạn 7 ngày, reconnect hàng tuần | Accepted (Founder) 29/09. **Còn mở:** chọn Gmail scope ở kickoff Phase 4 (mặc định `gmail.readonly`+`gmail.compose`) |
| ADR-015 | Cắt/gộp bảng so với spec §10 (bỏ users/integrations/contacts/follow_ups; receivables → `debts(direction)`; thêm api_keys, idempotency_keys...) | Accepted (Founder) 29/09 |
| ADR-017 | MCP sớm: một endpoint `/api/mcp` stateless; client 1 = **Cursor** (API key, 1.5a), client 2 = **ChatGPT** (OAuth 2.1 qua Supabase Auth, 1.5b), Claude sau (Phase 7) | Accepted (Founder) 29/09, amended cùng ngày |
| ADR-001/002/006 | Vertical modules / single owner + API keys cho bot / UUID + mã người đọc | Accepted (Founder uỷ quyền TD) 29/09 |
| ADR-004/005/008/010/011/016/018–021 | Migrations SQL-first, API style, archive vs soft delete, external_references, audit, API key format, rate limit, timeline view, testing stack, không mirror Gmail | Accepted (TD) 29/09 |
| **ADR-007** | Money model (bigint minor units, VND base, không FX v1) | **Proposed — chờ Founder** (chặn Phase 3) |
| **ADR-009** | Mã hoá token integration ở app (AES-256-GCM) vs Supabase Vault | **Proposed — chờ Founder** (chặn Phase 2) |
| **ADR-014** | Calendar ownership & xung đột | **Proposed — chờ Founder** (chặn Phase 2) |
