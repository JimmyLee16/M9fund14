# Problem

### 🔎 Problem: Thiếu SDK chuẩn hóa để triển khai commit–reveal voting trên Midnight

Việc xây dựng các ứng dụng DAO với tính riêng tư cao là mục tiêu cốt lõi của hệ sinh thái Midnight. Một trong những thành phần quan trọng nhất của các hệ thống DAO này là **cơ chế bỏ phiếu ẩn danh**, thường được triển khai theo mô hình **commit–reveal voting**.

Mặc dù nhóm chúng tôi đã phát triển một **prototype khả thi**, mô phỏng logic voting và kiểm thử các tình huống với testnet của Midnight, hiện vẫn tồn tại một khoảng trống nghiêm trọng:

* ❌ **Không có thư viện SDK nào được chuẩn hóa** để tái sử dụng trong các dự án khác.
* ❌ **Không có chuẩn module hoặc giao diện API rõ ràng**, khiến việc tích hợp vào các dApp trở nên phức tạp, không nhất quán.
* ❌ **Không có bộ công cụ kiểm thử chính thức (test harness)** giúp xác minh tính đúng đắn và khả năng tương thích với những thay đổi từ stack Midnight (ví dụ: thay đổi epoch model, cơ chế ZK).

Điều này khiến cho mỗi nhóm phát triển đều phải "bắt đầu lại từ đầu", tự viết lại logic voting, mô phỏng môi trường riêng, và chịu rủi ro cao khi testnet Midnight thay đổi. Vấn đề không chỉ làm chậm tiến trình phát triển sản phẩm, mà còn cản trở việc áp dụng rộng rãi cơ chế voting riêng tư trong Cardano & Midnight ecosystem.

***

#### 📌 Tóm tắt các vấn đề chính:

* Không có SDK mô-đun chuẩn hóa cho commit–reveal voting sử dụng Midnight.
* Thiếu abstraction layer và interface rõ ràng giữa voting logic và môi trường dApp.
* Khó tái sử dụng code từ các prototype hoặc dApp hiện tại.
* Không có hướng dẫn hoặc tiêu chuẩn kỹ thuật chung cho những nhóm phát triển mới tham gia hệ sinh thái.
