# Phase 3 - Tài liệu & tích hợp mẫu

#### Mục tiêu

Phát triển một công cụ dòng lệnh (`vote-cli`) để tương tác với hệ thống logic voting đã xây dựng, đồng thời kết nối trực tiếp với `vote-test-env`. Công cụ này giúp nhóm phát triển, kiểm thử và cả nhóm SDK kế thừa sử dụng dễ dàng hơn, ngay cả trong điều kiện chưa có testnet ổn định của Midnight.

***

#### 📌 Các đầu việc chính

* **Thiết kế CLI structure**
  * Xác định các nhóm lệnh chính: `create-poll`, `cast-vote`, `tally`, `export-result`
  * Định nghĩa schema input/output tương thích với `vote-core`
* **Phát triển vote-cli**
  * Viết tool bằng Rust hoặc TypeScript tùy context SDK của Midnight
  * Tích hợp trực tiếp `vote-core` thông qua các binding hoặc import nội bộ
  * Cho phép cấu hình mock voter, stake, voting params thông qua file JSON
* **Kết nối test environment**
  * Giao tiếp hai chiều giữa `vote-cli` và `vote-test-env`
  * Chạy các scenario mô phỏng vote đa dạng: vote hợp lệ, double-vote, vote quá hạn, tally sai stake…
* **Ghi log & export kết quả**
  * Xuất log toàn bộ quá trình vote vào file `.json`/`.csv`
  * Cho phép export result ở dạng `Merkle root` hoặc serialized object
* **Hướng dẫn sử dụng**
  * Viết tài liệu CLI: cú pháp, ví dụ sử dụng, troubleshooting cơ bản



<figure><img src="../../../.gitbook/assets/Milestone1 _ Mermaid Chart-2025-08-01-034709.png" alt=""><figcaption></figcaption></figure>

***

#### 📤 Deliverables

* Source code `vote-cli`, cấu trúc dễ mở rộng
* Một số file cấu hình mẫu: `poll.json`, `voterSet.json`
* Kết nối hoàn chỉnh với `vote-test-env`
* Hệ thống export log + kết quả vote (offline)
* Tài liệu hướng dẫn sử dụng CLI cho tester & developer

***

#### 🧩 Lưu ý kỹ thuật

* CLI này **không phụ thuộc** vào real Midnight testnet (có thể chạy local)
* Cho phép tích hợp dễ dàng về sau với SDK (đề xuất trong proposal #2)
* Cấu trúc CLI thiết kế module hóa, hỗ trợ dễ dàng wrap thành web UI nếu cần
