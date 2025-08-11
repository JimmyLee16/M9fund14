# Solution

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
