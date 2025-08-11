# Phase 1 - Chuẩn hóa kiến trúc SDK

### 📍 Milestone 1: Voting Logic Foundation (Tháng 1–2)

***

#### 🎯 Mục tiêu

Xây dựng lại từ đầu logic cốt lõi cho hệ thống bỏ phiếu DAO (voting prototype) theo kiến trúc có thể tái sử dụng và mở rộng trong SDK.\
Tạo nền tảng đủ vững chắc để phục vụ các milestone tiếp theo mà không phụ thuộc vào output của proposal khác.

***

#### 🧱 Kiến trúc dự kiến

**Module chính cần triển khai:**

* `vote-core`:
  * Quản lý lifecycle bỏ phiếu: tạo poll, submit vote, đếm phiếu
  * Các kiểu poll hỗ trợ: binary vote (`Yes/No`), multiple choice
  * Rule config: voting period, quorum, min stake
* `vote-types`:
  * Interface chung cho định nghĩa dữ liệu: `Vote`, `Poll`, `Result`, `VoterStake`
  * Cho phép mở rộng với adapter phía sau như ZK adapter (Midnight), non-ZK adapter
* `vote-storage` (Mock):
  * Lưu trạng thái poll/vote bằng file JSON hoặc in-memory (mock storage)
  * Tách biệt logic khỏi môi trường testnet (Midnight chưa ổn định)
* `vote-simulate`:
  * Chạy thử kịch bản: nhiều user vote, đếm phiếu, kiểm tra quorum, phân quyền admin
  * Cho phép config số lượng cử tri, phân phối token, test edge cases



<figure><img src="../../../.gitbook/assets/Milestone1 _ Mermaid Chart-2025-08-01-031413.png" alt=""><figcaption></figcaption></figure>

***

#### 🛠 Task cụ thể

**📦 1. Thiết kế cấu trúc codebase**

* Khởi tạo repo Git (private/public tùy chọn)
* Cài đặt base cấu trúc folder chuẩn: `core/`, `types/`, `mock/`, `cli/`
* Thiết lập CI basic (formatting, unit test chạy tự động)

**⚙️ 2. Phát triển logic vote-core**

* `PollManager`: hàm khởi tạo poll (với config)
* `VoteHandler`: hàm xử lý người dùng gửi vote, kiểm tra tính hợp lệ
* `TallyEngine`: tính kết quả cuối cùng, kiểm tra quorum, thắng/thua
* Thêm unit test cơ bản (Mocha/Jest hoặc test lib tương đương)

**🧪 3. Xây dựng hệ thống mô phỏng (simulate)**

* Viết module `vote-simulate.js/ts`:
  * Tạo danh sách cử tri giả lập
  * Tự động phân phối stake
  * Thực hiện hàng loạt lượt vote
  * In kết quả và log tracking
* Test các kịch bản:
  * Quorum đạt/không đạt
  * Vote late / vote duplicate
  * Poll expire

**🧾 4. Documentation kỹ thuật**

* Viết README cho từng module
* Phác thảo diagram kiến trúc module
* Giải thích các loại config hỗ trợ
* Document dạng Markdown và comment inline

***

#### 📤 Deliverables

| Output                       | Mô tả ngắn                                     |
| ---------------------------- | ---------------------------------------------- |
| `vote-core` source code      | Logic quản lý poll và vote cơ bản              |
| `vote-simulate` script       | Chạy thử mô phỏng bỏ phiếu với dữ liệu giả lập |
| `vote-types` interface       | Các type definitions để tái sử dụng trong SDK  |
| `README + ARCH.md`           | Tài liệu kỹ thuật kiến trúc hệ thống           |
| `Unit tests` (≥80% coverage) | Đảm bảo độ tin cậy và khả năng mở rộng         |

***

#### 🧑‍💻 Phân bổ nhân sự & effort

| Vai trò             | Ước tính giờ | Công việc chính                                 |
| ------------------- | ------------ | ----------------------------------------------- |
| Technical Architect | 40h          | Thiết kế kiến trúc module, định nghĩa interface |
| Blockchain Engineer | 80h          | Phát triển logic vote + simulate                |
| Tooling Dev         | 30h          | Xây dựng mock storage, test script              |
| QA + Test           | 20h          | Viết test case, test flow simulate              |
| Doc Writer          | 20h          | Viết tài liệu hướng dẫn và ghi chú nội bộ       |

**Tổng effort:** \~190 giờ làm việc (6 tuần, 1–2 dev chính)

***

#### 🔁 Kế hoạch review & kiểm thử

* Tuần 3: review kiến trúc + test logic bỏ phiếu
* Tuần 5: chạy thử full simulate 3 kịch bản khác nhau
* Tuần 6: tổng hợp tài liệu, chuẩn bị transition sang SDK hóa (milestone 2)
