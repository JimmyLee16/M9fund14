# Proposal draft

### ❓ Vấn đề đặt ra

Trong các hệ thống DAO hiện nay, việc triển khai quy trình bỏ phiếu một cách **minh bạch, an toàn và đảm bảo quyền riêng tư** vẫn là một thách thức lớn. Với Midnight – blockchain bảo mật mới trên Cardano – cơ hội mở ra để thiết kế một cơ chế bỏ phiếu bảo mật hơn, tuy nhiên:

* Midnight vẫn đang trong giai đoạn testnet, SDK còn thiếu tài liệu và tính năng.
* Các công cụ xây dựng DAO hiện chưa tương thích hoặc chưa sẵn sàng với mô hình ZK và contract của Midnight.
* Việc phát triển trực tiếp một sản phẩm hoàn chỉnh (ví dụ một dApp) trên nền tảng chưa ổn định dễ dẫn tới rủi ro kỹ thuật cao và lãng phí tài nguyên.

Vì vậy, cần có một giai đoạn **nghiên cứu & thử nghiệm kiến trúc** trước khi bước sang giai đoạn triển khai thực tế.

***

### ✅ Mục tiêu của Proposal

Mục tiêu chính của proposal này là xây dựng một **prototype kỹ thuật** cho hệ thống bỏ phiếu DAO trên Midnight, theo mô hình commit–reveal, với kiến trúc mở, module hóa, và đủ độ chi tiết để làm cơ sở kỹ thuật cho SDK hoặc demo app trong tương lai.

***

### 💡 Giải pháp đề xuất

Chúng tôi đề xuất triển khai một prototype kỹ thuật, bao gồm:

#### 1. **Thiết kế kiến trúc mô-đun**

* Xây dựng các thành phần riêng biệt như `vote-core` (logic), `vote-test-env` (mô phỏng mạng), và `vote-cli` (công cụ dòng lệnh).
* Mỗi module có thể được tái sử dụng trong SDK hoặc tích hợp vào ứng dụng thực tế.

#### 2. **Mô phỏng môi trường bỏ phiếu**

* Do hạn chế của testnet và SDK Midnight hiện tại, nhóm sẽ xây dựng một lớp mô phỏng (mock layer) cho phép thử nghiệm quy trình vote commit–reveal một cách độc lập.

#### 3. **Tài liệu hóa toàn bộ kiến trúc**

* Soạn thảo tài liệu kỹ thuật chi tiết, bao gồm flow logic, data structure, và đánh giá các hướng triển khai bảo mật khác nhau.
* Tài liệu này sẽ là nền tảng để nhóm SDK & demo app tiếp tục phát triển.

***

### 🔧 Các thành phần chính

| Thành phần      | Mô tả ngắn                                                            |
| --------------- | --------------------------------------------------------------------- |
| `vote-core`     | Thư viện xử lý logic commit, reveal, kiểm tra tính hợp lệ của phiếu   |
| `vote-test-env` | Mô phỏng môi trường voting, bao gồm voter, signer, mạng giả lập       |
| `vote-cli`      | Công cụ dòng lệnh cho dev/test, nhập voter, chạy vote round mô phỏng  |
| `vote-docs`     | Tài liệu mô tả kiến trúc hệ thống, đánh giá kỹ thuật và hướng mở rộng |

***

### 📆 Lộ trình thực hiện (6 tháng)

| Tháng | Công việc chính                                   |
| ----- | ------------------------------------------------- |
| 1     | Khởi tạo repo, xác định interface giữa các module |
| 2     | Phát triển `vote-core` logic                      |
| 3     | Phát triển `vote-test-env`                        |
| 4     | Xây dựng `vote-cli` và kết nối với test env       |
| 5     | Soạn thảo tài liệu kỹ thuật (`vote-docs`)         |
| 6     | Review nội bộ, tổng hợp output, chuẩn bị kế thừa  |

***

### 💰 Phân bổ ngân sách đề xuất (Tổng: **92,000 ADA**)

| Hạng mục                | Ngân sách (ADA) | Mô tả chi tiết                                              |
| ----------------------- | --------------- | ----------------------------------------------------------- |
| Technical Architect     | 18,000          | Thiết kế kiến trúc, xác định ranh giới module               |
| Blockchain Engineer     | 22,000          | Phát triển logic voting và mô phỏng testnet                 |
| Tooling Developer       | 14,000          | Xây dựng CLI + test environment                             |
| Technical Documentation | 12,000          | Viết tài liệu hệ thống và phân tích kỹ thuật                |
| QA & Internal Testing   | 8,000           | Thiết kế test case, kiểm thử tính đúng đắn và mô phỏng      |
| Project Management      | 10,000          | Điều phối tiến độ, kết nối nhóm SDK và Demo App             |
| Contingency (10%)       | 8,000           | Phòng rủi ro từ SDK/testnet Midnight thay đổi hoặc lỗi mạng |
| **Tổng cộng**           | **92,000 ADA**  |                                                             |

***

### ⚠️ Các rủi ro & giải pháp

| Rủi ro                               | Giải pháp tương ứng                                                |
| ------------------------------------ | ------------------------------------------------------------------ |
| SDK Midnight thay đổi                | Tách module, giảm phụ thuộc, sử dụng test-mock layer khi cần thiết |
| Noir chưa hỗ trợ tính năng cần thiết | Ưu tiên commit–reveal đơn giản, không dùng zk-circuit phức tạp     |
| Testnet không ổn định                | Tạo mock network layer và cơ chế fallback để test offline          |

***

### 📦 Kết quả đầu ra

* Một bộ thư viện mô phỏng quy trình DAO voting trên Midnight.
* Một CLI công cụ dùng được trong nội bộ và giai đoạn SDK kế tiếp.
* Một bộ tài liệu kỹ thuật chuẩn hóa.
* Bộ test environment dùng cho lập trình viên không cần truy cập trực tiếp vào testnet.
