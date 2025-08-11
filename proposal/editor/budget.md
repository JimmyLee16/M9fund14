# Budget

### 💰 **Phân bổ ngân sách chi tiết theo thời gian & vai trò** (Tổng: **92,000 ADA**)

### ✅ **Cơ cấu tổng thể (theo từng vai trò)**

| Vai trò                 | Ngân sách (ADA) | Vai trò chính tại milestone     |
| ----------------------- | --------------- | ------------------------------- |
| Technical Architect     | 18,000          | M1 + M2                         |
| Blockchain Engineer     | 22,000          | M2 + M3                         |
| Tooling Developer       | 14,000          | M3                              |
| Technical Documentation | 12,000          | M4                              |
| QA & Internal Testing   | 8,000           | M2 + M4                         |
| Project Management      | 10,000          | M1 → M4                         |
| Contingency (10%)       | 8,000           | Dự phòng (SDK/testnet thay đổi) |
| **Tổng cộng**           | **92,000 ADA**  |                                 |

***

### 🔹 **Milestone 1: Hệ thống hóa kiến trúc & khởi tạo codebase**

**Mô tả:**\
Đặt nền tảng kiến trúc module `vote-core`, định nghĩa các interface chính, setup repo + CI/CD.

**Các task chính:**

* Thiết kế kiến trúc hệ thống & ranh giới module (`vote-core`, `vote-cli`, `vote-test-env`)
* Định nghĩa chuẩn interface & kiểu dữ liệu
* Khởi tạo codebase (repo, CI/CD, linter, auto-test)

**Phân bổ ngân sách:** `22,000 ADA`

* Technical Architect: 10,000
* Blockchain Engineer: 4,000
* Project Manager: 3,000
* QA (review logic sơ khởi): 2,000
* Contingency: 3,000

**Deliverable:**

* Kiến trúc hệ thống sơ bộ (PDF + schema)
* Repo GitHub khởi tạo + CI/CD
* Spec các module chính

***

### 🔹 **Milestone 2: Phát triển `vote-core` & mô phỏng bỏ phiếu**

**Mô tả:**\
Hoàn thiện logic commit–reveal, xử lý epoch, lock time, hash proof.

**Các task chính:**

* Phát triển `vote-core` (Rust)
* Mô phỏng chu kỳ bỏ phiếu (testnet giả lập)
* Unit test + test case xử lý sai lệch
* Review kiến trúc & code refactor

**Phân bổ ngân sách:** `28,000 ADA`

* Blockchain Engineer: 12,000
* Technical Architect: 6,000
* QA: 4,000
* Project Manager: 3,000
* Contingency: 3,000

**Deliverable:**

* Module `vote-core` chạy test được
* Test case & mô phỏng epoch
* Báo cáo tiến độ kỹ thuật nội bộ

***

### 🔹 **Milestone 3: Xây dựng CLI & môi trường test tương tác**

**Mô tả:**\
Cho phép test voting logic qua dòng lệnh, kết nối `vote-core` với môi trường test & kiểm thử hành vi thực tế.

**Các task chính:**

* Phát triển `vote-cli` với các command `init`, `commit`, `reveal`, `result`
* Hoàn thiện `vote-test-env` mô phỏng blockchain
* Viết test integration (giữa CLI ↔ test-env ↔ core)
* Chuẩn hóa interface gói SDK

**Phân bổ ngân sách:** `24,000 ADA`

* Tooling Dev: 10,000
* Blockchain Engineer: 6,000
* Project Manager: 3,000
* QA: 3,000
* Contingency: 2,000

**Deliverable:**

* CLI sử dụng được với nhiều config
* Output kết quả bỏ phiếu từ CLI
* Environment mock blockchain hoạt động ổn định

***

### 🔹 **Milestone 4: Viết tài liệu kỹ thuật & bàn giao**

**Mô tả:**\
Tổng hợp toàn bộ tài liệu kỹ thuật, hướng dẫn sử dụng CLI, phân tích kiến trúc, và chuẩn bị kế thừa SDK.

**Các task chính:**

* Soạn thảo tài liệu chi tiết (`vote-docs`)
* Tổng hợp lesson learned & guideline cho team SDK
* Đóng gói repo + tag release
* Viết báo cáo Catalyst & checklist deliverable

**Phân bổ ngân sách:** `18,000 ADA`

* Documentation: 12,000
* QA: 2,000
* Project Manager: 3,000
* Contingency: 1,000

**Deliverable:**

* `vote-docs` (PDF + markdown + hướng dẫn CLI)
* Báo cáo tổng kết milestone
* Checklist bàn giao cho SDK team

***

### 📦 **Tóm tắt phân bổ cuối cùng**

| Milestone                 | Ngân sách      | Tỉ lệ |
| ------------------------- | -------------- | ----- |
| M1: Kiến trúc + setup     | 22,000 ADA     | 24%   |
| M2: Logic core + mô phỏng | 28,000 ADA     | 30%   |
| M3: CLI + test env        | 24,000 ADA     | 26%   |
| M4: Docs + bàn giao       | 18,000 ADA     | 20%   |
| **Tổng cộng**             | **92,000 ADA** | 100%  |
