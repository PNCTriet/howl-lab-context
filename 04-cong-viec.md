# 04 — Task board (trạng thái 2026-10-27)

> Xem chi tiết đầy đủ các dự án và quy tắc vận hành tháng 10/2026 tại **`13-cap-nhat-2026-10-27.md`**.
> Phân công chuẩn: giao việc code/infra cho **`@DEVIN`**, AI/MCP/RAG cho **`@KAI`**, research/growth cho **`@MEIL`**; mặc định không dùng Cloud Agent khi chưa cần.

## ✅ Done (Cập nhật tháng 10/2026)
- **TAPTAP (`PNCTriet/taptap` — `https://taptap-five.vercel.app`):**
  - Hoàn thiện ứng dụng thu thập tem số NFC thí điểm tại Thảo Cầm Viên Sài Gòn (4 trạm, bản đồ GPS `/map`, minh hoạ động vật đồng bộ, hiệu ứng mobile-first).
  - Chuyển sang thuần **Google OAuth (`signInWithOAuth`)**, bỏ modal đăng nhập 1-chạm.
  - Dựng Supabase project riêng **`TAPTAP`** (`dfvkhtheqcsjfbfihzrk`, region `ap-northeast-2`, org `TAPTAP`), chạy xong migration 12 bảng (`taptap_phase0_initial_schema`), RLS `TO authenticated` và dữ liệu seed Thảo Cầm Viên.
- **EOI (`PNCTriet/EOI_websiteofficial` — `https://eoilinhtinh.com`):**
  - Relaunch web thương mại điện tử đèn & mô hình in 3D `@eoilinhtinh` (Next.js 15, Supabase `EOILINHTINH` `yoqwyvhqsodvsowhxnum`, Resend).
  - Chuyển sang Vercel project mới `eoi-websiteofficial-ivtp` (team `howlstudios-projects`), gắn domain `eoilinhtinh.com` & `www.eoilinhtinh.com`.
  - Vá bảo mật admin (`app_metadata.role = "admin"`), khóa RLS bảng `custom_checkout_links`, tích hợp Google OAuth.
- **ViCall / Howls Lab Avatar (`PNCTriet/howlslab-avatar` — `https://vircall.howlslab.com`):**
  - Tích hợp Tavus video-call với 3 persona (Lucy `ped2a7d02db5`, Lee `p6d958e9a9f8`, Dr. Paws), bật `raven-1` vision + nút bật/tắt camera cho khách, hỗ trợ import file `.md` hướng dẫn (tối đa 100KB) theo từng cuộc gọi hoặc lưu làm Owner instructions có mật khẩu admin.
- **Virtual Visit / Vivis (`PNCTriet/virtual-visit-selfhost` — `https://vivis.howlslab.com`):**
  - Ship bản sửa lỗi di chuyển 4 hướng, cinema/shared TV, arcade games, gõ tiếng Việt, proximity chat, demo clip MacBook/iPhone (Supabase `HOWLSLAB` `jexjlaqblulgfjcssekb`).
- **Fitting Lab / Tryon (`PNCTriet/PER_Portfolio` — `https://tryon.howlslab.com` & `https://howlslab.com`):**
  - Đồng bộ thương hiệu sang Howls Lab (founded 2025, `howls.sslab@gmail.com`), giao diện light-mode chuẩn Apple HIG.
- **Danh mục dự án sự kiện & R&D:** Tổng hợp 10 dự án (Takico, MB Life Photobooth, MB Life Lucky Draw + iPad app "MB Life – Key Moment", Pendiasure, Jump Jump, Live Puzzle, Vivis, ViCall, Tryon, OCX) cùng TAPTAP và EOI.
- **HowlsOS (`https://howlsos.vercel.app`):**
  - Hoàn thiện charts admin chuẩn Apple HIG (`68596a9`), bezel Apple thật + VI/EN (`43c32be`), proposal mẫu `/p/pr_lumiere` (`aa83506`).
- **Personal OS (`https://personal-os-blond-eta.vercel.app`):**
  - Phase 0 docs + 21 ADR (`c71e3a8`, `0a9f980`, `4156fe8`), Phase 1 plan (`88e5cc9`), MVP v0 đến v4 (`4657793`), competitive brief của MEIL.

## 🔄 In progress / Chờ cấu hình
- **TAPTAP — Google OAuth:** Đang chờ dán Google Client ID / Client Secret vào Supabase project `TAPTAP` (`dfvkhtheqcsjfbfihzrk`) và cấu hình Redirect URL trên Google Cloud Console.
- **EOI — Báo giá đơn hàng:** Thực hiện xuất file báo giá Excel lưu về MacBook Air của anh Triết (`MacBook-Air-cua-Tina`) mỗi khi anh gửi tên khách, mã SP, số lượng, đơn giá.

## ⛔ Blocked / On hold (Personal OS & HowlsOS)
| Ai | Việc | Trạng thái / lý do |
|---|---|---|
| DEVIN | **T14** API keys, permissions, audit, idempotency (`personal-os`) | On hold từ 29/09. Brief lưu tại `docs/briefs/devin-t14-api-keys-brief.md`. |
| KAI | **1.5a** endpoint `/api/mcp` + task tools (`personal-os`) | On hold chờ mở lại Phase 1 Personal OS. |
| KAI | **1.5b** ChatGPT OAuth (`personal-os`) | Ngoài quỹ → cần Founder duyệt chi khi mở lại. |

## ❓ Chờ Founder quyết
1. **TAPTAP:** Hoàn tất dán Google OAuth Client ID/Secret để test luồng đăng nhập thật trên `taptap-five.vercel.app`.
2. **HowlsOS & Personal OS:** Chọn thời điểm mở lại các task backend/persistence tiếp theo.

## ⏭ Next
1. Hoàn tất cấu hình Google OAuth cho **TAPTAP** và kiểm thử end-to-end luồng quét NFC + lưu tem tại 4 trạm Thảo Cầm Viên.
2. Hỗ trợ vận hành **EOI (`eoilinhtinh.com`)**, xuất báo giá Excel khi có đơn khách lẻ/sỉ.
3. Tiếp tục nâng cấp **ViCall (`vircall.howlslab.com`)** và **Vivis (`vivis.howlslab.com`)** theo yêu cầu demo của anh Triết.
