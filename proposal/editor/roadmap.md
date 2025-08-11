# Roadmap

### 📆 **Lộ trình thực hiện (6 tháng)**

| **Tháng**   | **Công việc chính**                                   | **Mô tả chi tiết**                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ----------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tháng 1** | **Khởi tạo hệ thống – vote-prototype repo**           | <p>- Thiết lập cấu trúc repo mã nguồn.<br>- Phân tích và xác định rõ ràng các interface giữa các module: <code>vote-core</code>, <code>vote-cli</code>, <code>vote-test-env</code>, <code>vote-docs</code>.<br>- Lập sơ đồ kiến trúc hệ thống, mô hình hóa luồng dữ liệu theo hướng tách biệt (modular).<br>- Xác định các tham số bỏ phiếu: token input, thời gian, random seed (nếu có), logic commit–reveal thuần (không dùng ZK).</p> |
| **Tháng 2** | **Phát triển module `vote-core`**                     | <p>- Xây dựng logic bỏ phiếu cơ bản: commit → reveal → verify.<br>- Thiết kế các cấu trúc dữ liệu: vote payload, hashed commitment, proof (giả lập).<br>- Viết các unit test để kiểm chứng logic hoạt động độc lập.<br>- Đảm bảo vote-core có thể được gọi như 1 SDK nhỏ (dùng lại sau này).</p>                                                                                                                                          |
| **Tháng 3** | **Phát triển `vote-test-env`**                        | <p>- Tạo môi trường mô phỏng testnet: trình giả lập block, thời gian epoch, địa chỉ người dùng.<br>- Cho phép chạy thử commit–reveal nhiều vòng với dữ liệu giả lập (mock voters).<br>- Tạo script để dễ dàng chạy lại test case nhiều lần.</p>                                                                                                                                                                                           |
| **Tháng 4** | **Phát triển `vote-cli` và tích hợp môi trường test** | <p>- Viết công cụ CLI để chạy quy trình bỏ phiếu: commit → reveal → kết quả.<br>- CLI sẽ tích hợp với <code>vote-core</code> và <code>vote-test-env</code> để tạo trải nghiệm tương tự dApp.<br>- Tạo lệnh giả lập test: <code>vote commit</code>, <code>vote reveal</code>, <code>vote verify</code>, <code>vote result</code>.<br>- Viết logics để in kết quả, xuất file JSON test.</p>                                                 |
| **Tháng 5** | **Soạn thảo tài liệu kỹ thuật – `vote-docs`**         | <p>- Ghi lại toàn bộ kiến trúc hệ thống, hướng dẫn sử dụng CLI.<br>- So sánh các phương pháp commit–reveal truyền thống vs zk–based (nêu lý do chọn design hiện tại).<br>- Mô tả cách hệ thống này có thể kết nối sang SDK giai đoạn tiếp theo (proposal #2).<br>- Cung cấp tài liệu dành cho developer (API, file cấu hình, test instructions).</p>                                                                                      |
| **Tháng 6** | **Rà soát nội bộ & tổng hợp kết quả**                 | <p>- Tổ chức các buổi review nội bộ để kiểm thử, phản biện kỹ thuật.<br>- Hoàn thiện hệ thống tài liệu và chuẩn bị bàn giao cho nhóm kế thừa (proposal SDK + Demo app).<br>- Tổng hợp toàn bộ kết quả, lessons learned, vấn đề còn mở để công bố minh bạch.<br>- (Tùy chọn) Chuẩn bị slide trình bày kết quả, để báo cáo cộng đồng Cardano.</p>                                                                                           |

\
Hoặc lộ trình theo milestone catalyst
-------------------------------------



#### ✅ **Milestone 1: Khởi tạo kiến trúc & chuẩn hóa module (Tháng 1)**

**Mô tả:** Thiết lập nền tảng hệ thống, xác định ranh giới giữa các module và chuẩn hóa cấu trúc repo.\
**Các task chính:**

* Tạo kho mã nguồn cho `vote-core`, `vote-cli`, `vote-test-env`, và `vote-docs`.
* Thiết kế kiến trúc tổng thể và interface giao tiếp giữa các thành phần.
* Xác định tiêu chuẩn dữ liệu (commit hash, timestamp, vote payload...).
* Lên kế hoạch chi tiết cho từng module (spec, deadline, ưu tiên).

**Success Criteria:**

* ✅ Tài liệu kiến trúc tổng thể (system overview) được hoàn thiện và review nội bộ.
* ✅ Repo khởi tạo với cấu trúc thư mục rõ ràng, CI đơn giản hoạt động.
* ✅ Giao diện giữa các module (API schema / data interface) được thống nhất.

**Deliverables:**

* 🔹 1 sơ đồ kiến trúc hệ thống (`architecture.md + diagram`)
* 🔹 Repo chứa 4 thư mục module chính với cấu trúc ban đầu (`vote-core/`, `vote-cli/`, v.v.)
* 🔹 Tài liệu spec module và interface dạng Markdown (`/docs/interfaces/`)

***

#### ✅ **Milestone 2: Phát triển vote-core & logic bỏ phiếu (Tháng 2–3)**

**Mô tả:** Xây dựng thành phần lõi điều phối quy trình bỏ phiếu theo commit–reveal.\
**Các task chính:**

* Xây dựng thư viện xử lý commit, reveal, verify.
* Mô phỏng bộ xác minh dữ liệu phiếu và trạng thái bỏ phiếu.
* Thiết lập test unit để đảm bảo logic hoạt động ổn định.
* Tối ưu vote-core để sẵn sàng tích hợp CLI và test-env.

**Success Criteria:**

* ✅ `vote-core` chạy độc lập với đầy đủ unit tests (>85% coverage).
* ✅ Mỗi bước trong quy trình commit → reveal → verify đều được test.
* ✅ Đảm bảo khả năng xử lý lỗi (e.g. commit sai format, reveal trễ...).

**Deliverables:**

* 🔹 Thư viện `vote-core` (code hoàn chỉnh)
* 🔹 Bộ test cases + coverage report (trên GitHub Actions hoặc tương đương)
* 🔹 Tài liệu mô tả chi tiết quy trình bỏ phiếu (`docs/vote-flow.md`)

***

#### ✅ **Milestone 3: Môi trường giả lập + công cụ CLI (Tháng 4)**

**Mô tả:** Tạo môi trường mô phỏng bỏ phiếu thực tế và phát triển CLI tương tác dòng lệnh.\
**Các task chính:**

* Thiết lập `vote-test-env`: block mock, epoch giả lập, tài khoản giả.
* Phát triển `vote-cli` với các lệnh: `commit`, `reveal`, `verify`, `result`.
* Kết nối CLI với `vote-core` và test nhiều kịch bản bỏ phiếu.
* Đánh giá tính nhất quán đầu–cuối của toàn hệ thống.

**Success Criteria:**

* ✅ CLI hoạt động hoàn chỉnh trên local (không cần SDK Midnight).
* ✅ Có demo đầu–cuối commit–reveal voting hoàn chỉnh trong test-env.
* ✅ 3+ kịch bản bỏ phiếu mô phỏng được xử lý thành công.

**Deliverables:**

* 🔹 Gói CLI (`vote-cli`) có thể cài bằng `cargo install` hoặc tương đương
* 🔹 Bộ mô phỏng `vote-test-env` chạy được trên local
* 🔹 Demo script + README hướng dẫn test end-to-end

***

#### ✅ **Milestone 4: Tài liệu kỹ thuật & tổng hợp đầu ra (Tháng 5–6)**

**Mô tả:** Soạn tài liệu kỹ thuật chi tiết và hoàn tất kiểm thử nội bộ.\
**Các task chính:**

* Viết bộ tài liệu `vote-docs`: hướng dẫn CLI, mô tả hệ thống, giải thích kỹ thuật.
* Tổng hợp kết quả test, đóng gói output có thể bàn giao cho nhóm SDK.
* Rà soát lại toàn bộ repo, checklist chất lượng kỹ thuật.
* Chuẩn bị báo cáo tổng kết để công bố minh bạch kết quả dự án.

**Success Criteria:**

* ✅ Tài liệu `vote-docs` được publish công khai, cấu trúc dễ đọc.
* ✅ Checklist đầu ra được hoàn thiện: code, test, hướng dẫn sử dụng.
* ✅ Báo cáo kết quả + roadmap kế thừa được gửi lại Catalyst.

**Deliverables:**

* 🔹 Bộ tài liệu kỹ thuật (`vote-docs/`) gồm:
  * Hướng dẫn cài đặt & sử dụng CLI
  * Mô tả chi tiết hệ thống & logic bỏ phiếu
  * Hướng dẫn tích hợp SDK
* 🔹 Báo cáo tổng kết + repo ở trạng thái ổn định sẵn sàng kế thừa
