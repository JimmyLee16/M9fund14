# Phase 2 - Phát triển tính năng

#### Mô tả ngắn gọn

Thiết kế và xây dựng abstraction layer của hệ thống voting – tách các phần logic độc lập, dễ bảo trì và hỗ trợ mở rộng trong các ứng dụng sử dụng SDK (như demo app, dApp khác trong tương lai).

***

#### 🛠 Các task chính

* Thiết kế sơ đồ module cho SDK theo chuẩn hóa:
  * `VoteCore`: logic vote
  * `VoteStore`: dữ liệu tạm & persistent
  * `VoteProof`: mô-đun giả lập proof logic (ZK optional)
  * `VoteClient`: các hàm tương tác từ app
* Refactor lại prototype logic (nếu có) thành cấu trúc module hóa.
* Xây dựng các interface SDK (`.ts`, `.rs`, hoặc `.json` schema tùy môi trường build).
* Đóng gói SDK thành gói thư viện (alpha), hỗ trợ import test nội bộ.
* Viết unit test cơ bản cho từng mô-đun.
* Đóng gói tài liệu auto-gen (nếu có) + draft hướng dẫn sử dụng.



<figure><img src="../../../.gitbook/assets/Milestone1 _ Mermaid Chart-2025-08-01-034344.png" alt=""><figcaption></figcaption></figure>

***

#### 📦 Deliverables

* Bộ mã nguồn `sdk-core` theo cấu trúc module hóa, với README hướng dẫn tích hợp.
* Gói thư viện SDK dưới dạng module hoặc CLI (alpha release).
* Sơ đồ kiến trúc các lớp (layer) trong SDK.
* Unit test sơ bộ các mô-đun.
* Tài liệu mô tả cách tích hợp SDK từ app bên ngoài.

***

#### ⏱ Ước lượng effort (tương ứng ngân sách milestone)

* **Blockchain Engineer**: \~40 giờ (refactor, logic, test) → \~10,000 ADA
* **Tooling Developer**: \~30 giờ (interface SDK + đóng gói CLI) → \~6,000 ADA
* **Technical Architect**: \~20 giờ (design interface, chuẩn hóa abstraction) → \~6,000 ADA
* **QA**: \~12 giờ (unit test, test case module) → \~2,500 ADA
* **Project Management**: \~8 giờ (review, điều phối tiến độ) → \~1,500 ADA
* **Dự phòng rủi ro SDK/thay đổi môi trường** → \~2,000 ADA
* **Tổng ngân sách Milestone 2**: \~28,000 ADA
