# Proposal draft

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



### 📘 Solution: Phát triển một SDK mô-đun chuẩn hóa cho commit–reveal voting trên Midnight

Giải pháp của chúng tôi là xây dựng một **Software Development Kit (SDK)** trung lập, có cấu trúc mô-đun, giúp các nhóm phát triển có thể dễ dàng tích hợp cơ chế bỏ phiếu commit–reveal sử dụng Midnight mà không phải tự xây lại logic từ đầu.

SDK này không phải là một sản phẩm ứng dụng hoàn chỉnh, mà đóng vai trò là lớp trung gian chuẩn hóa giữa:

* Các DAO/dApp có nhu cầu tích hợp voting riêng tư.
* Hệ thống Midnight (testnet hoặc mainnet) với nhiều thay đổi tiềm ẩn về kiến trúc.

#### 🎯 Mục tiêu chính của giải pháp:

* **Chuẩn hóa giao diện kỹ thuật** cho logic voting sử dụng commit–reveal.
* **Tách biệt rõ các mô-đun logic, test, CLI và tài liệu**, nhằm tăng khả năng mở rộng và bảo trì.
* **Tích hợp sẵn công cụ kiểm thử (test harness)**, mô phỏng hành vi testnet và hỗ trợ phát hiện lỗi sớm.
* **Đảm bảo khả năng kế thừa** từ các prototype trước, đồng thời hỗ trợ nhóm phát triển Demo App và các nhóm bên ngoài dễ dàng tiếp cận.

***

#### ⚙️ Thành phần chính của SDK:

1. **vote-core (Logic Voting)**
   * Cung cấp các hàm xử lý commit, reveal, kiểm tra trạng thái bỏ phiếu.
   * Thiết kế API trung lập, không phụ thuộc wallet cụ thể hay hệ thống lưu trữ.
   * Hỗ trợ thiết lập tham số thời gian (voting window, commit/reveal phase).
2. **vote-cli (Dòng lệnh & Automation)**
   * Công cụ CLI dùng để kiểm tra, tái tạo và chạy thử các chuỗi hành vi voting.
   * Cho phép thiết lập config (voter list, seed, tham số ZK) dễ dàng qua file YAML/JSON.
3. **vote-test-env (Môi trường kiểm thử mô phỏng)**
   * Mô phỏng epoch, block time và các tình huống fail/recover trong quá trình commit–reveal.
   * Cho phép chạy nhiều case song song, hỗ trợ kiểm thử khối lượng lớn (stress test).
4. **vote-docs (Tài liệu kỹ thuật & hướng dẫn tích hợp)**
   * Gồm: kiến trúc hệ thống, mô hình luồng dữ liệu, hướng dẫn tích hợp SDK vào dApp thực tế.
   * Phân tích rủi ro, fallback logic khi testnet không ổn định hoặc tính năng ZK chưa hỗ trợ.

***

#### 🛠️ Kỹ thuật tiếp cận và thiết kế:

* **Mô-đun hóa tối đa:**\
  Các thành phần SDK được đóng gói độc lập, có thể thay thế hoặc mở rộng theo nhu cầu thực tế. Ví dụ: logic commit/reveal có thể nâng cấp sang tích hợp Plonk hoặc Noir khi stack Midnight ổn định.
* **Tách biệt abstraction layer:**\
  SDK cung cấp abstraction interface, không phụ thuộc trực tiếp vào SDK chính thức của Midnight. Điều này giúp:
  * Dễ mock/test mà không



### 📅 Roadmap (4 Milestones)

#### ✅ Milestone 1: Chuẩn hóa kiến trúc SDK

**Mô tả:**\
Tách logic từ prototype thành module reusable, thiết kế theo chuẩn lib.

**Tasks:**

* Refactor vote-core thành thư viện
* Định nghĩa trait/interface rõ ràng
* Thiết kế API & error handling chuẩn Rust

**Deliverables:**

* SDK base structure
* API draft (Rustdoc)
* Tài liệu kiến trúc



***

#### ✅ Milestone 2: Phát triển tính năng SDK

**Mô tả:**\
Xây dựng các module con: commit, reveal, tally, epoch-sim.

**Tasks:**

* Viết `VoteSession`, `CommitProof`, `TallyEngine`
* Thiết lập mô phỏng epoch/slot/lock-time
* Viết unit test từng module

**Deliverables:**

* `src/lib.rs` hoàn chỉnh
* 90% test coverage
* Log sử dụng từng chức năng



***

#### ✅ Milestone 3: Tài liệu & bộ tích hợp mẫu

**Mô tả:**\
Viết tài liệu kỹ thuật, tạo ví dụ dùng SDK đơn giản (CLI/web mock).

**Tasks:**

* API doc + JSON schema input/output
* Code demo sample app dùng SDK
* Viết hướng dẫn tích hợp

**Deliverables:**

* API Doc HTML
* Sample App + hướng dẫn CLI/Web
* 1 case study



***

#### ✅ Milestone 4: Release bản public & đóng gói

**Mô tả:**\
Kiểm thử, đóng gói SDK, phát hành bản open-source.

**Tasks:**

* Check license, clean code
* Benchmark và tối ưu
* Release `v1.0.0` trên Github

**Deliverables:**

* SDK bản release (`crate`)
* Changelog + release note
* Báo cáo nộp Catalyst



### BUDGET

| Milestone | Nội dung chính                | Chi phí (ADA) |
| --------- | ----------------------------- | ------------- |
| M1        | Chuẩn hóa kiến trúc SDK       | 18,000        |
| M2        | Phát triển tính năng SDK      | 27,000        |
| M3        | Tài liệu & tích hợp mẫu       | 21,500        |
| M4        | Release bản public & đóng gói | 23,500        |
| **Tổng**  |                               | **90,000**    |



### **Value for money**



This SDK delivers a cost-effective, production-grade foundation for integrating anonymous voting into DAO infrastructures on Cardano, powered by the Midnight privacy stack. By modularizing complex components such as commit–reveal voting, time-locked sessions, and zero-knowledge proof handling, the SDK drastically reduces technical overhead for ecosystem builders.

The project is fully open-source and designed for reusability, ensuring that other teams can build upon it without reinventing the wheel. Based on typical market development rates, it is estimated to save **30–50%** of development cost and time for future DAO-related applications.

The team behind the SDK consists of experienced Rust developers and privacy researchers with a proven track record in blockchain R\&D. The deliverables follow best practices in software engineering: clean code, robust test coverage, formal documentation, and production-ready packaging. This ensures long-term maintainability and real-world applicability across multiple use cases within the Cardano ecosystem.
