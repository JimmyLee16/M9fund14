# Roadmap

#### 🧩 **Milestone 1 – Project Setup & SDK Design**

* Thiết lập repo & cấu trúc codebase ban đầu.
* Xác định interface giữa `vote-core`, `vote-test-env`, `vote-cli`.
* Thiết kế JSON schema cho các thực thể chính: `poll`, `voterSet`, `vote`, `result`.
* Lập kế hoạch kỹ thuật và chia task theo module.

#### 🔧 **Milestone 2 – Develop vote-core & test-env**

* Xây dựng logic core: tạo poll, casting vote, tally, export kết quả.
* Tạo môi trường test giả lập (`vote-test-env`) dùng dữ liệu JSON và file voter list.
* Viết unit test cơ bản cho từng hàm chính trong core.

#### 💻 **Milestone 3 – Build CLI Tool & Draft Docs**

* Xây dựng `vote-cli` dùng Node.js CLI (hoặc Rust CLI): nhập poll, vote, xem kết quả.
* Tích hợp `vote-core` vào CLI & test-env.
* Viết tài liệu kỹ thuật: cấu trúc project, sơ đồ module, hướng dẫn sử dụng.

#### 🧪 **Milestone 4 – Internal Review & Finalization**

* Refactor codebase, kiểm thử edge cases.
* Tổng hợp toàn bộ tài liệu (`vote-docs`, `handover.md`, schema, lessons learned).
* Chuẩn bị đầu ra sạch để bàn giao cho nhóm Demo App.



