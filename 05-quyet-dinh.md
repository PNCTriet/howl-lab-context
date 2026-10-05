# 05 — Nhật ký quyết định

Giờ theo Asia/Saigon. "TD" = Technical Director (IVAN). Nguồn: brief bàn giao 2026-10-01, `docs/personal-os-repo/docs/decisions.md`, git log.

| Ngày | Quyết định | Ai | Nguồn |
|---|---|---|---|
| 2026-09-29 | Phase 0 docs + 21 ADR đề xuất được đưa lên repo | TD | commit `c71e3a8` |
| 2026-09-29 | **Accept ADR-003** (supabase-js + generated types + RPC, không ORM) | Founder | decisions.md, `0a9f980` |
| 2026-09-29 | **Accept ADR-012** confirmation flow, ngưỡng tự ghi chi tiêu AI **< 50.000 VND** | Founder | decisions.md |
| 2026-09-29 | **Accept ADR-013**: Google = Gmail cá nhân (không Workspace), app Testing, reconnect 7 ngày | Founder | decisions.md |
| 2026-09-29 | **Accept ADR-015** cắt/gộp bảng | Founder | decisions.md |
| 2026-09-29 | **Accept ADR-017** MCP sớm; amended: client đầu **Cursor**, rồi **ChatGPT**, Claude sau; OAuth kéo lên Phase 1.5b | Founder (+ TD về timing OAuth) | decisions.md, `4156fe8` |
| 2026-09-29 | Accept ADR-001/002/006 (Founder uỷ quyền TD) và ADR-004/005/008/010/011/016/018–021 | TD | decisions.md |
| 2026-09-29 | Phase 1 plan 22 task, ~5 tuần | TD | `88e5cc9` |
| 2026-09-29 | Ship MVP v0 + app shell + mobile/i18n (VI mặc định) + restyle | Team | PR #1–#3, `4657793` |
| 2026-09-29 | Commit phải author `PNCTriet <147395796+PNCTriet@users.noreply.github.com>` (Vercel Hobby chặn author khác) | — (ràng buộc kỹ thuật) | brief bàn giao |
| 2026-09-29 02:44 | **Tạm dừng toàn team** đến khi Founder duyệt MVP; huỷ cloud agent DEVIN T14 | chưa xác minh người ra lệnh | brief bàn giao, transcript cloud agent |
| 2026-09-29 | Đánh giá "build, ship, earn" + đề xuất (xem dưới) | TD (đề xuất) | brief bàn giao |
| (đến 2026-09-30) | Quỹ 1tr/tháng chia DEVIN 300k / KAI 300k / MEIL 150k / IVAN 100k / dự phòng 150k; IVAN duyệt chi trong phần **chỉ sau khi Founder nói "đồng ý"** — **chưa có** | Đề xuất, chờ Founder | brief bàn giao |
| — | Cursor on-demand $5: một cloud agent một lúc, scope nhỏ, báo chi phí mỗi lượt | Luật vận hành | brief bàn giao |
| 2026-10-03 | Khởi động **HowlsOS** (HOWL Sales & Proposal OS), repo private, Vercel `howlsos`, mock data, design Apple | Founder | `2fb5e76`, `4b54b4b` |
| 2026-10-04 | Proposal public theo phong cách tryonenotch.com (viết tay, highlight, device mockup) | Founder | `bb75dd5`, `9033f30` |
| 2026-10-04 | IVAN được **giao task code cho DEVIN/KAI** dù team vẫn tạm dừng; task IVAN giao thì báo cáo/xin duyệt qua IVAN | Founder | chat với IVAN |
| 2026-10-04 | MEIL research xu hướng "bá khí" (Threads/Instagram), báo thẳng Founder | Founder | chat |
| 2026-10-04 | Mua domain `trietnguyenpham.tech` (Nhân Hòa) | Founder | email Nhân Hòa trong Gmail |

Ngày chính xác của các luật quỹ/Cursor: **chưa xác minh** (không có nguồn ghi ngày trên box).

## Đánh giá "Build, ship, earn" (2026-09-29)
- **Build: có. Ship: có** (MVP v0 live, auto-deploy).
- **Earn: chưa**, vì:
  - chưa có sản phẩm nào có người trả tiền;
  - không có vai trò bán hàng;
  - không có vòng phản hồi từ người dùng;
  - mọi hành động ra bên ngoài đều phải qua Founder.
- **Đề xuất (chưa được Founder chốt):**
  1. Founder đóng vai **người bán** vài giờ/tuần.
  2. **MEIL** chuyển sang **tìm nhu cầu trả tiền** và **soạn nháp outreach** (Founder duyệt trước khi gửi).
  3. **Ship sản phẩm nhỏ có thu phí mỗi 2–4 tuần**; sản phẩm nào không có người trả thì **khai tử**.
  4. **Personal OS = nền tảng nội bộ**; doanh thu đến từ **các tool AI/MCP nhỏ cho founder Việt Nam**.

## Quyết định đang mở
Xem `04-cong-viec.md` → "Chờ Founder quyết".
