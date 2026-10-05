# 07 — HowlsOS (HOWL Sales & Proposal OS) — dự án MỚI

## Là gì
- Công cụ bán hàng & proposal cho **Howls Studio**: dashboard doanh thu, CRM khách hàng, pipeline Kanban, proposal builder + trang proposal public cho khách (`/p/[id]`), hợp đồng & thanh toán, log email.
- Trạng thái: **prototype bấm được, chỉ mock data** (`src/lib/mock-data.ts`), chưa backend.

## Repo & deploy
- Repo: https://github.com/PNCTriet/HowlsOS — **PRIVATE**. Vẫn giữ author commit `PNCTriet <147395796+PNCTriet@users.noreply.github.com>`.
- Live: https://howlsos.vercel.app (`/` → redirect `/dashboard`). Proposal mẫu: https://howlsos.vercel.app/p/pr_lumiere
- Vercel: project `howlsos`, team `howlstudios-projects`, **auto-deploy khi push lên `main`**.
- Stack: Next.js App Router · TypeScript · Tailwind · shadcn/ui · lucide-react · recharts · @hello-pangea/dnd · sonner.
- Spec: `docs/SPEC.md` (bản sao: `docs/howlsos-repo/SPEC.md`). Design: `docs/DESIGN.md` (phong cách Apple, nguồn getdesign) — **giống hệt** `docs/personal-os-repo/DESIGN.md`.
- Clone local trên Mac Founder: `~/Projects/HowlsOS`. Trên box IVAN cũ: `/workspace/HowlsOS` (không mang sang được).
- Chạy local: `npm install && npm run dev`.

## Route hiện có
`/dashboard`, `/clients`, `/clients/[id]`, `/pipeline`, `/proposals`, `/proposals/new`, `/projects`, `/contracts`, `/emails`, `/settings`, `/p/[id]` (public).

## Lịch sử `origin/main` (giờ VN)
| Commit | Thời gian | Nội dung |
|---|---|---|
| `43c32be` | 04/10 20:34 | DEVIN: iPhone mockup luôn hiện cạnh MacBook |
| `9033f30` | 04/10 20:26 | DEVIN: proposal v4 — bezel Apple Design Resources thật (MacBook Pro 14 M5 + iPhone 16 Pro) + toggle VI/EN |
| `bb75dd5` | 04/10 20:10 | Proposal v3 "playful": chữ viết tay, highlight, khung chọn kiểu Figma, mockup CSS |
| `c0aa23a` | 04/10 19:54 | Redesign `/p/[id]` kiểu Apple scroll storytelling |
| `4b54b4b` | 03/10 18:18 | v0.1 prototype (8 màn hình chính, mock data, UI Apple) |
| `2fb5e76` | 03/10 18:04 | Khởi tạo repo: README + docs/DESIGN.md |

## Giới hạn hiện tại
- Không lưu dữ liệu (mock, reload là mất).
- "Hôm nay" cố định **2026-10-03** trong mock data.
- Chưa có trang **sửa proposal**.
- Phân quyền chỉ là **badge**, chưa enforce.
- Bezel Apple: **phải đọc guideline sử dụng của Apple Design Resources trước khi dùng cho marketing.**

## Tham chiếu thiết kế: tryonenotch.com (Founder rất thích)
Founder thích: chữ viết tay, highlight, device mockup, vibe "Apple for Education". Phân tích kỹ thuật (2026-10-04):
- Next.js 15 App Router trên Vercel, **CSS Modules**.
- Font self-host: **SN Pro** + **Patrick Hand** + **Pecita** (viết tay).
- Icon: SF Symbols dạng PNG mask.
- **GSAP chỉ cho cursor pill** (không ScrollTrigger). Scroll: CSS `position: sticky` + rAF ghi biến `--p` + IntersectionObserver.
- Video mp4; SVG filter "liquid glass"; easing `cubic-bezier(.16,1,.3,1)`.
- Checkout: Lemon Squeezy.
- File phân tích thô trên box cũ: `/workspace/onenotch/` (không mang sang được).

## Ảnh
`assets/howlsos/`: dashboard desktop (v0.1), proposal v4 hero + mockup (1440px, 390px).

## Next (gợi ý, chờ Founder)
Persistence (Supabase hoặc tương tự), trang sửa proposal, "hôm nay" theo ngày thật, enforce phân quyền, kiểm tra license bezel Apple.
