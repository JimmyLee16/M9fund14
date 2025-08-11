# Proposal draft

**Project Name:** Anonymous DAO Voting dApp\
**Platform:** Midnight (ZK Layer on Cardano)\
**Goal:** Cung cấp một giải pháp bỏ phiếu DAO ẩn danh, không truy vết danh tính, hướng đến tiêu chuẩn thực tế có thể sử dụng trong hệ sinh thái DAO tương lai.\
**Type:** dApp Frontend Demo (không phát triển backend hay SDK – sử dụng SDK có sẵn từ Proposal 2)\
**Open Source:** Có – mã nguồn dApp sẽ được công khai trên GitHub theo giấy phép MIT

***

### 🔍 Problem Statement

Hầu hết các DAO hiện tại đều sử dụng hình thức biểu quyết công khai, dễ bị ảnh hưởng bởi áp lực cộng đồng, đe dọa và “vote theo sóng”.\
Ngoài ra, không có công cụ bỏ phiếu nào thực sự tích hợp được **ZK privacy** ở cấp người dùng cuối.

**Hiện trạng:**

* Các công cụ DAO hiện có chỉ phù hợp với các blockchain công khai (EVM, Cardano native)
* Không hỗ trợ tính ẩn danh thực sự (vì ví công khai, hành vi vote bị truy vết)
* Dữ liệu bỏ phiếu bị lộ có thể gây tác động tiêu cực đến các quyết định dài hạn
* Không có UI/UX tiêu chuẩn cho việc tương tác với vote ẩn danh

**Nhu cầu:**

* Một giải pháp bỏ phiếu **ẩn danh từ đầu đến cuối**
* UI rõ ràng, dễ dùng cho người không kỹ thuật
* Hỗ trợ các vai trò đặc trưng của DAO (proposal creators, voters, observers)

***

### 🧩 Solution Overview

Xây dựng một ứng dụng bỏ phiếu ẩn danh (frontend dApp) được thiết kế dành riêng cho DAO sử dụng ZK-privacy trên Midnight.

**Tính năng chính:**

* Giao diện người dùng thân thiện, hiện đại
* Tạo DAO và proposal mới
* Tham gia bỏ phiếu theo mô hình commit–reveal hoặc ZK-snark
* Hiển thị kết quả bỏ phiếu mà không tiết lộ hành vi cá nhân
* Xác thực người dùng mà không cần lộ danh tính ví

**Các vai trò chính:**

* **Project initiator:** Tạo DAO, mở vote
* **Proposal creator:** Gửi đề xuất vào DAO
* **Voter:** Tham gia vote ẩn danh
* **Observer:** Theo dõi và kiểm tra quá trình vote

***

### 🧠 Technical Scope

* Kết nối với SDK ZK Voting đã được phát triển (đã có sẵn từ Proposal 2)
* Không xây dựng backend – toàn bộ frontend gọi SDK và tương tác qua middleware
* UI/UX: TailwindCSS, animation tinh gọn, responsive
* Các trang chính:
  * Homepage
  * DAO Dashboard
  * Proposal View
  * Vote Page (Commit/Reveal)
  * Result Summary
  * Profile (ZK identity-based)

***

### 📆 Timeline & Milestones

#### **Milestone 1: Research & Wireframe (Month 1)**

* Nghiên cứu interaction SDK → frontend
* Vẽ mockup UI cho các chức năng
* Output:
  * Figma mockup các page
  * Research note integration SDK

#### **Milestone 2: Functional UI Development (Month 2–3)**

* Xây dựng component UI từng phần
* Kết nối interaction qua SDK (không viết backend)
* Output:
  * UI hoạt động cơ bản
  * Demo flow vote ẩn danh thành công

#### **Milestone 3: Integration & Feedback (Month 4–5)**

* Cải thiện animation, logic UX
* Mời cộng đồng test, nhận feedback và tối ưu
* Output:
  * Dashboard đầy đủ
  * 1 vòng test cộng đồng (10–20 người)
  * Log cải tiến từ feedback

#### **Milestone 4: Final Polish & Public Demo (Month 6)**

* Release bản public UI dApp
* Tối ưu cho performance
* Trình diễn trên video/demo site
* Output:
  * Public GitHub repo
  * Clip hướng dẫn demo
  * Báo cáo Catalyst & launch page

***

### 💰 Budget Breakdown (Total: **70,845 ADA**)

* **Design & Frontend Development:** 25,000 ADA
* **Midnight SDK integration (gọi hàm, xử lý ZK commit/reveal):** 10,000 ADA
* **Privacy R\&D, test ZK logic (UI test cases, sim case):** 12,000 ADA
* **UI polish & animation performance:** 6,000 ADA
* **Community feedback & test session iteration:** 5,000 ADA
* **Project management & Catalyst reporting:** 3,000 ADA
* **Marketing push + video demo:** 3,155 ADA
* **Total:** 70,845 ADA

***

### 👥 Team

* **PM / UI Architect:** 5+ năm làm blockchain, DAO system (Cardano & Ethereum)
* **Frontend Dev (Rust/WASM + React):** Có kinh nghiệm build dApp đa chain
* **ZK Research Support:** Hỗ trợ R\&D thiết kế test case, validate privacy logic
* **Design & Animation Lead:** Phụ trách Figma, Tailwind UI, animation chuẩn production
