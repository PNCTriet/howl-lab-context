# 04 — Task board (trạng thái 2026-10-04 20:40)

> **Team nhìn chung TẠM DỪNG** từ **2026-09-29 02:44** (giờ VN) cho đến khi Founder **duyệt MVP**. Không launch agent / tiêu tiền khi chưa có lệnh.
> **Ngoại lệ (04/10):** IVAN được giao task code cho DEVIN/KAI; họ báo cáo/xin duyệt qua IVAN. MEIL research "bá khí", báo thẳng Founder.

## ✅ Done
- Phase 0: bộ tài liệu kiến trúc (docs/), schema proposal đã validate, 21 ADR — commit `c71e3a8`.
- Lock ADR-003/012/013/015/017 (Founder duyệt 2026-09-29); ADR còn lại TD accept — `0a9f980`, `4156fe8`.
- Phase 1 plan (22 task) — `88e5cc9`.
- MVP v0 PR #1 (`7766f77`), CRM app shell PR #2 (`c964f39`), mobile + i18n PR #3 (`375f22a`), restyle Notion-like + login + avatar menu (`4657793`). Live tại https://personal-os-blond-eta.vercel.app (mock data).
- Ảnh mockup MVP v4 (MacBook/iPhone) — `assets/mvp-shots-v4/`.
- **HowlsOS** (03–04/10): v0.1 prototype `4b54b4b` → proposal Apple-style `c0aa23a` → playful v3 `bb75dd5` → DEVIN v4 bezel Apple thật + VI/EN `9033f30`, `43c32be`. Live https://howlsos.vercel.app. Chi tiết `07-howlsos.md`.
- Phân tích thiết kế tryonenotch.com (04/10) — tóm tắt ở `07-howlsos.md`.
- Mua domain `trietnguyenpham.tech` qua Nhân Hòa (04/10) — còn thủ tục, xem `08-viec-khac.md`.
- **MEIL:** competitive + UX brief — `docs/briefs/personal-os-competitive-brief.md` (gốc: `/workspace/research/personal-os-competitive-brief.md`).

## 🔄 In progress
- **MEIL:** research xu hướng "bá khí" trên Threads/Instagram → báo thẳng Founder (kết quả: chưa xác minh).
- **HowlsOS:** chờ Founder xem v4 và chọn bước tiếp (xem Next trong `07-howlsos.md`).
- **Domain** `trietnguyenpham.tech`: **nộp hồ sơ trước 07/10/2026**, xác nhận chủ sở hữu trong 15 ngày (thongbaotenmien.vn).

## ⛔ Blocked
| Ai | Việc | Trạng thái / lý do |
|---|---|---|
| DEVIN | **T14** API keys, permissions, audit, idempotency trên branch `feat/core-api` | Cloud agent chạy ~4 phút (transcript: hoạt động 02:42–02:44 ngày 29/09 giờ VN) rồi **bị huỷ**; **không có branch/PR**. Brief để relaunch: `docs/briefs/devin-t14-api-keys-brief.md`. Chờ Founder duyệt MVP. |
| KAI | **1.5a** = endpoint `/api/mcp` + 2–3 task tools, dùng `ApiKeyResolver` stub | **Chưa từng launch.** Chờ MVP. (Theo phase-1-plan §8, bản đầy đủ 1.5a có 6 tool: get_today, get_tasks, create_task, update_task, complete_task, get_action_status.) |
| KAI | **1.5b** ChatGPT OAuth | **Ngoài quỹ** → cần Founder duyệt chi. |
| MEIL | Follow-up sau competitive brief | **On hold.** |
| Hạ tầng | Supabase hosted | Hết 2 project free (`DNY_DB`, `HOWLSLAB`) → chờ Founder chọn. |
| Hạ tầng | Bật CI | Thiếu GitHub scope `workflow`; file chờ ở `ci/github-actions-ci.yml`. |

## ❓ Chờ Founder quyết
1. **Duyệt MVP** (mở khoá cả team).
2. Nói **"đồng ý"** trong group Howlslab để IVAN được duyệt chi trong phần quỹ (chưa có tính đến 2026-09-30).
3. **Supabase:** pause một project / Pro ~ $25/tháng / giữ mock.
4. **Bug UI** (4 bug ở `03-personal-os.md`): sửa ngay hay sau MVP.
5. **`documents/UX_UI.md`** (mô tả app DNY CRM, lọt vào repo public): giữ hay xoá. Kèm vấn đề email công việc trong commit `4657793`.
6. MEIL có nên quét **~3 ý tưởng sản phẩm trả phí** không.
7. (Từ docs) ADR-007, ADR-009, ADR-014 còn Proposed; guardrail 24h của ADR-012.
8. **HowlsOS:** bước tiếp (persistence, trang sửa proposal, enforce phân quyền); kiểm tra guideline bezel Apple trước khi dùng marketing.
9. **Zalo:** nháp trả lời Uyển Nhi (group "HỆ THỐNG PHẦN MỀM") — Founder quyết sau. Xem `08-viec-khac.md`.

## ⏭ Next (đề xuất thứ tự sau khi Founder mở khoá — IVAN chốt lại)
1. Supabase quyết xong → DEVIN relaunch T14 bằng brief có sẵn (một cloud agent, scope nhỏ, báo chi phí).
2. KAI 1.5a (`/api/mcp` + 2–3 task tools, ApiKeyResolver stub) — sau hoặc song song T14 tuỳ quỹ (luật: một cloud agent một lúc).
3. Sửa 4 bug UI nếu Founder muốn làm ngay.
4. Theo đề xuất "earn" (`05-quyet-dinh.md`): MEIL chuyển sang tìm nhu cầu trả tiền + soạn nháp outreach (chờ Founder duyệt).
