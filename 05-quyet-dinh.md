# 05 — Nhật ký quyết định

Giờ theo Asia/Saigon. "TD" = Technical Director (IVAN). Nguồn: brief bàn giao 2026-10-01, `docs/personal-os-repo/docs/decisions.md`, git log, và cập nhật tháng 10/2026 (`13-cap-nhat-2026-10-27.md`).

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
| 2026-10-05 | Quy tắc xưng hô bắt buộc: IVAN xưng `em`, gọi `anh`, luôn có `dạ/thưa`, không nói trống không | Founder | `11-ivan-voice-and-visit-ux-2026-10-05.md` |
| 2026-10-05 | Khởi chạy **Virtual Visit self-host (`vivis.howlslab.com`)** dùng Phaser 3 + Tiled + Supabase Realtime thay cho bản miễn phí ZEP bị lộ thương hiệu | Founder | `10-virtual-visit-2026-10-05.md` |
| 10/2026 | Quy tắc thương hiệu: `HOWLSTUDIO` là thương hiệu mẹ; `HOWLSLAB` cho sản phẩm công nghệ & R&D. Sản phẩm `HOWLSLAB` chưa public tuyệt đối không nhắc tới `HOWLSTUDIO`. Mọi bản demo song ngữ EN/VI (mặc định EN) | Founder | `13-cap-nhat-2026-10-27.md` |
| 10/2026 | Chuẩn hoá giao diện toàn bộ sản phẩm theo **Apple HIG** (minimalist, ít chữ, giữ tỉ lệ ảnh gốc, nhiều khoảng trắng) | Founder | `13-cap-nhat-2026-10-27.md` |
| 10/2026 | Ra mắt **ViCall (`vircall.howlslab.com`)** tích hợp Tavus (Lucy, Lee, Dr. Paws), `raven-1` vision và tính năng nạp `.md` instructions có mật khẩu bảo vệ Owner instructions | Founder | `13-cap-nhat-2026-10-27.md` |
| 10/2026 | Relaunch **EOI (`eoilinhtinh.com`)** trên Vercel `eoi-websiteofficial-ivtp` + Supabase `EOILINHTINH` (`yoqwyvhqsodvsowhxnum`), vá phân quyền admin (`app_metadata.role = "admin"`) và khóa bảng `custom_checkout_links` | Founder | `13-cap-nhat-2026-10-27.md` |
| 10/2026 | Khởi động **TAPTAP (`taptap-five.vercel.app`)** — nền tảng thu thập tem số NFC thí điểm tại Thảo Cầm Viên Sài Gòn; dùng thuần Google OAuth (`signInWithOAuth`) và tách riêng Supabase project **`TAPTAP`** (`dfvkhtheqcsjfbfihzrk`, org `TAPTAP`) | Founder | `13-cap-nhat-2026-10-27.md` |

## Đánh giá "Build, ship, earn" (2026-09-29 & cập nhật 10/2026)
- **Build & Ship:** Đã mở rộng mạnh trong tháng 10/2026 với hệ sinh thái sản phẩm live: **Virtual Visit (`vivis.howlslab.com`)**, **ViCall (`vircall.howlslab.com`)**, **Tryon (`tryon.howlslab.com`)**, **EOI (`eoilinhtinh.com`)**, **TAPTAP (`taptap-five.vercel.app`)**, cùng các giải pháp sự kiện thực tế (MB Life 10 năm — Photobooth, Lucky Draw, iPad Key Moment).
- **Earn:** Kết hợp thương mại điện tử (`eoilinhtinh.com`), giải pháp công nghệ sự kiện B2B và các sản phẩm R&D của HOWL LAB.

## Quyết định đang mở
Xem `04-cong-viec.md` → "Chờ Founder quyết" và `13-cap-nhat-2026-10-27.md`.
