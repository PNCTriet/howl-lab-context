# PROMPT SPECIFICATION FOR AI AGENT: HOWLSOS v0.1 (UI/UX Mockup & Prototype)

> **Mục tiêu:** Tạo bản Prototype Visual Live cho hệ thống **HOWLSOS v0.1** trên Next.js App Router, Tailwind CSS và Shadcn UI. 
> **Yêu cầu chính:** Chưa kết nối Database/Backend thật. Toàn bộ dữ liệu hiển thị bằng **Mock Data (TypeScript Constant)**, có tương tác UI/UX linh hoạt (React State / Local State) để kiểm chứng trải nghiệm người dùng trước khi triển khai DB thật.

---

## 1. TỔNG QUAN VỀ HỆ THỐNG & TECH STACK

* **Tên hệ thống:** HOWLSOS (HOWL Sales & Proposal Operating System)
* **Mô hình kiến trúc:** Đa thuê bao (Multi-Tenant) & Quản lý Phân quyền theo Dự án (Project-level RBAC).
* **Stack công nghệ FE:**
  * **Framework:** Next.js (App Router - TypeScript)
  * **Styling:** Tailwind CSS, Shadcn UI (Card, Dialog, Table, Tabs, Select, Badge, DropdownMenu, Form...)
  * **Icons:** Lucide React
  * **Drag & Drop (Kanban):** `@hello-pangea/dnd` hoặc `dnd-kit` (hoặc HTML5 DnD đơn giản)
  * **Charts:** Recharts / Tremor (để dựng Dashboard)

---

## 2. NGUYÊN TẮC THIẾT KẾ & DỮ LIỆU GIẢ (MOCK DATA)

### 2.1 File Dữ liệu Giả (`src/lib/mock-data.ts`)
Khởi tạo cấu trúc Mock Data đầy đủ trong 1 file tập trung để phục vụ hiển thị:

1. **Organizations:**
   * `id`: "org_howl", `name`: "HOWL Studio", `domain`: "howl.studio"
2. **Projects:**
   * `id`: "proj_1", `name`: "Virtual Try-On Retail", `code`: "VTO-01"
   * `id`: "proj_2", `name`: "Custom AI Automation", `code`: "AI-AUTO"
3. **Users & Roles:**
   * User 1: `Founder / Admin` (Role: `ORG_ADMIN`)
   * User 2: `Project Lead` (Role: `PROJECT_LEAD` - Proj 1)
   * User 3: `Sales Exec` (Role: `PROJECT_MEMBER` - Proj 1)
4. **Clients:** 3-5 khách hàng mẫu với thông tin công ty, contact person, email.
5. **Opportunities (Sales Pipeline):**
   * Các cột: `Lead`, `Discovery`, `Pitching`, `Proposal`, `Negotiation`, `Won`, `Lost`.
   * **Bắt buộc:** Mỗi Opportunity phải chứa `nextAction` (Ví dụ: "Gửi Proposal bổ sung gói B") và `nextActionDeadline` (Ví dụ: "2026-10-05").
6. **Proposals:** Danh sách Proposal đi kèm Scope, Timeline, Pricing (các mốc giá), trạng thái (`Draft`, `Sent`, `Accepted`, `Declined`).
7. **Contracts & Payment Milestones:** Hợp đồng liên kết với Opportunity (Won), chứa mốc thanh toán (Tạm ứng 30%, Bàn giao 70%).

---

## 3. CẤU TRÚC ĐỊNH TUYẾN & GIAO DIỆN MÀN HÌNH (ROUTING & UI SPECS)

### 3.1 Bố cục Chung (App Layout & Shell)
* **Header / Topbar:**
  * Dropdown Chọn **Organization** & **Project** (Cho phép đổi giữa các Project mock).
  * Badge hiển thị **Role của User hiện tại** trong Project đang chọn.
  * User Menu (Profile, Settings, Theme toggle).
* **Sidebar Navigation:**
  * Dashboard (`/dashboard`)
  * Quản lý Dự án & Team (`/projects`)
  * CRM Khách hàng (`/clients`)
  * Luồng Bán hàng (`/pipeline`)
  * Đề xuất / Proposals (`/proposals`)
  * Hợp đồng & Thanh toán (`/contracts`)
  * Email Logs & Analytics (`/emails`)
  * Cài đặt Cấu hình (`/settings`)

---

### 3.2 Chi tiết Tính năng theo Màn hình (Pages)

#### Màn hình 1: Tổng quan Doanh thu (`/dashboard`)
* **Chỉ số KPIs Top Cards:**
  * Tổng giá trị Sales Pipeline ($)
  * Doanh thu Thực thu ($)
  * Doanh thu Dự kiến ($)
  * Tỷ lệ Chốt thành công (Win Rate %)
* **Biểu đồ (Charts):**
  * Biểu đồ cột Doanh thu theo tháng (Bar Chart).
  * Biểu đồ hình quạt Tỷ lệ deal theo giai đoạn (Pie/Donut Chart).
* **Widget "Việc Cần Làm Ngay" (Next Action Tracker):**
  * Danh sách các Opportunity có `deadline` tới hạn trong 3 ngày tới, xếp theo thứ tự ưu tiên.

#### Màn hình 2: Quản lý Dự án & Phân quyền (`/projects`)
* **Danh sách Project:** Card view hiển thị thông tin từng dự án, mã dự án, số lượng thành viên.
* **Modal / Tab "Thành viên & Phân quyền":**
  * Bảng danh sách User thuộc Project.
  * Dropdown thay đổi Role (`Lead`, `Member`, `Viewer`).
  * Modal "Mời thành viên mới vào Project" (Form nhập Email & Chọn Role).

#### Màn hình 3: CRM Khách hàng (`/clients`)
* **Bảng danh sách Khách hàng:** Tên công ty, Ngành nghề, Người đại diện, Email, Số Deal đang chạy.
* **Màn hình Chi tiết Khách hàng (`/clients/[id]`):**
  * Tab Thông tin chung & Contacts.
  * Tab Lịch sử trao đổi / Activity Log.
  * Tab Các Proposal & Hợp đồng đã gửi cho khách hàng này.

#### Màn hình 4: Luồng Bán hàng Kanban (`/pipeline`)
* **Giao diện Kanban Board:**
  * 7 Cột tương ứng các giai đoạn: `Lead` ➔ `Discovery` ➔ `Pitching` ➔ `Proposal` ➔ `Negotiation` ➔ `Won` ➔ `Lost`.
  * **Card Opportunity:** Hiển thị Tên deal, Khách hàng, Giá trị ($), Badge `Next Action` + Deadline (tô đỏ nếu quá hạn).
  * Cho phép kéo thả Card giữa các cột (Cập nhật Local State).
* **Modal Chi tiết / Tạo Opportunity:**
  * Form nhập: Tên Deal, Chọn Client, Chọn Giá trị, Bắt buộc nhập `Next Action` và `Deadline`.

#### Màn hình 5: Proposal Builder & Preview (`/proposals`)
* **Danh sách Proposal:** Trạng thái (`Draft`, `Sent`, `Opened`, `Accepted`).
* **Trang Soạn thảo Proposal (`/proposals/new` hoặc `/proposals/[id]/edit`):**
  * Form 3 phần: Phạm vi công việc (Scope/Deliverables), Tiến độ (Timeline), Bảng giá (Pricing Packages).
  * Nút "Xem trước Web Proposal" & Nút "Xuất PDF (Mock)".
* **Trang Web Proposal công khai cho Khách (`/p/[id]`):**
  * Layout thiết kế đẹp mắt, hiện đại như một trang Landing Page dành riêng cho Proposal.
  * Khách hàng có nút "Chấp nhận Proposal" hoặc "Gửi Phản hồi".

#### Màn hình 6: Hợp đồng & Thanh toán (`/contracts`)
* **Danh sách Hợp đồng:** Gắn liền với các Opportunity `Won`.
* **Theo dõi Mốc thanh toán (Payment Milestones):**
  * Bảng hiển thị các đợt thanh toán (Ví dụ: Đợt 1 - Tạm ứng, Đợt 2 - Nghiệm thu).
  * Progress Bar tỷ lệ tiền đã thu về / Tổng giá trị hợp đồng.
  * Nút bấm giả lập "Đánh dấu Đã thanh toán" (Mark as Paid).

#### Màn hình 7: Log Email & Analytics (`/emails`)
* **Bảng Lịch sử Email:**
  * Tên Email, Khách hàng nhận, Thời gian gửi, Trạng thái Resend (`Sent`, `Delivered`, `Opened`, `Clicked`).
  * Nút "Thử nghiệm Gửi Email Proposal" (Trigger toast notification thành công).

---

## 4. BƯỚC THỰC THI CHO AGENT (STEP-BY-STEP INSTRUCTIONS)

1. **Khởi tạo Project & Layout Base:**
   * Set up Next.js App Router với Tailwind CSS và Shadcn UI Components.
   * Tạo file `src/lib/mock-data.ts` chứa toàn bộ dữ liệu giả nêu ở Phần 2.

2. **Dựng App Shell & Navigation:**
   * Tạo Sidebar, Header và Project Switcher Dropdown (Lưu selected project ID vào React Context hoặc Local Storage).

3. **Dựng các Màn hình (Page by Page):**
   * Lần lượt dựng từ `/dashboard` ➔ `/pipeline` (Kanban) ➔ `/proposals` ➔ `/clients` ➔ `/contracts` ➔ `/projects`.
   * Đảm bảo mọi nút bấm hành động (Tạo mới, Kéo thả, Đổi role) có tương tác giả lập bằng Local State / Toast notification.

4. **Kiểm tra UX & Polish Giao diện:**
   * Đảm bảo giao diện hiện đại, chuẩn Studio công nghệ (Clean, Dark/Light mode, Responsive).
   * Kiểm tra hiển thị dữ liệu cô lập theo Project đang chọn trên Topbar.
