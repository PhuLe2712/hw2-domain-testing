# Báo cáo lỗi chi tiết — GitHub Issues


##  Tóm tắt lỗi

| Bug ID | Tiêu đề | Severity | Priority đề xuất | Test case liên quan | GitHub Issue |
|---|---|---:|---:|---|---|
| BUG-01 | Form đăng ký thiếu trường xác nhận mật khẩu | Cao | P2 | REG-D01, REG-D12, REG-D13 | [#1](https://github.com/PhuLe2712/hw2-domain-testing/issues/1) |
| BUG-02 | Đăng ký chấp nhận email đã tồn tại | Cao | P1 | REG-D05, REG-B10 | [#2](https://github.com/PhuLe2712/hw2-domain-testing/issues/2) |
| BUG-03 | API đăng ký không kiểm tra đầy đủ dữ liệu đầu vào | Cao | P1 | REG-D04; probe API ghi trong issue | [#3](https://github.com/PhuLe2712/hw2-domain-testing/issues/3) |
| BUG-04 | Thêm một sản phẩm nhiều lần tạo nhiều dòng giỏ hàng | Cao | P2 | CART-D04, CART-B08 | [#4](https://github.com/PhuLe2712/hw2-domain-testing/issues/4) |
| BUG-05 | Giỏ hàng không có nút tăng/giảm quantity | Cao | P2 | CART-D05, CART-D06, CART-D07, CART-B07 | [#5](https://github.com/PhuLe2712/hw2-domain-testing/issues/5) |
| BUG-06 | Xóa sản phẩm khỏi giỏ không có bước xác nhận | Cao | P2 | CART-D08, CART-D09, CART-B09, CART-B10 | [#6](https://github.com/PhuLe2712/hw2-domain-testing/issues/6) |
| BUG-07 | Nhãn tổng tiền trong giỏ không đúng yêu cầu | Thấp | P3 | CART-D12 | [#7](https://github.com/PhuLe2712/hw2-domain-testing/issues/7) |
| BUG-08 | User thường truy cập API admin và thay đổi dữ liệu | Nghiêm trọng | P1 | ACL-D04–ACL-D09, ACL-B06, ACL-B07 | [#8](https://github.com/PhuLe2712/hw2-domain-testing/issues/8) |
| BUG-09 | User thường tự nâng quyền qua API cập nhật hồ sơ | Nghiêm trọng | P1 | ACL-B10 | [#9](https://github.com/PhuLe2712/hw2-domain-testing/issues/9) |
| BUG-10 | Chi tiết sản phẩm mobile không hiển thị danh mục | Cao | P2 | MOB-D02 | [#10](https://github.com/PhuLe2712/hw2-domain-testing/issues/10) |
| BUG-11 | Sản phẩm thiếu ảnh không có ảnh thay thế/trạng thái lỗi | Cao | P2 | MOB-D03 (cần đồng bộ lại phạm vi bước tái hiện) | [#11](https://github.com/PhuLe2712/hw2-domain-testing/issues/11) |
| BUG-12 | Quantity mobile không hợp lệ bị đổi âm thầm thành 1 | Cao | P2 | MOB-B01, MOB-B04, MOB-B05, MOB-B06 | [#12](https://github.com/PhuLe2712/hw2-domain-testing/issues/12) |

> Ghi chú: Priority là đánh giá đề xuất để nhóm sắp xếp xử lý, không phải trường dữ liệu đã có trên các issue.

## Chi tiết bug report

### BUG-01 — Form đăng ký không yêu cầu xác nhận mật khẩu

- **Test phát hiện:** `REG-D01`, `REG-D12`, `REG-D13`.
- **Feature / kênh:** FR-01 Đăng ký tài khoản / Web UI.
- **Môi trường:** EShop chạy local, trang `/register`, Chromium headless (kết quả theo lần chạy báo cáo).
- **Severity:** Cao (theo Issue #1).
- **Priority đề xuất:** P2 — có nguy cơ người dùng nhập nhầm mật khẩu nhưng không thể xác nhận trước khi tạo tài khoản.
- **GitHub Issue:** [#1](https://github.com/PhuLe2712/hw2-domain-testing/issues/1).

**Mô tả:** Form chỉ có các trường `name`, `email`, `password`. Không có `Confirm Password`, nên người dùng không thể nhập lại mật khẩu để đối chiếu.

#### Bước tái hiện

1. Mở `http://localhost:5173/register`.
2. Kiểm tra các trường trong form đăng ký.
3. Nhập các giá trị hợp lệ vào tên, email và mật khẩu rồi gửi form.
4. Thử tìm trường xác nhận mật khẩu hoặc kiểm tra request `POST /api/register`.

#### Kết quả mong đợi (nguồn: README.md, FR-01)

Form có trường xác nhận mật khẩu; nếu hai mật khẩu không khớp thì từ chối đăng ký và không tạo tài khoản.

#### Kết quả thực tế

Không có trường xác nhận mật khẩu. Form chỉ gửi tên, email và một giá trị mật khẩu; đăng ký hợp lệ vẫn chuyển sang trang đăng nhập.

#### Bằng chứng

Ảnh form trong [GitHub Issue #1](https://github.com/PhuLe2712/hw2-domain-testing/issues/1); ảnh local [FR01-form-thieu-xac-nhan.png](evidence/FR01-form-thieu-xac-nhan.png).

---

### BUG-02 — Đăng ký chấp nhận email đã tồn tại

- **Test phát hiện:** `REG-D05`, `REG-B10`.
- **Feature / kênh:** FR-01 Đăng ký tài khoản / Web UI và API.
- **Môi trường:** EShop local (`http://localhost:5173/register`, API `http://localhost:3000/api/register`); dùng email kiểm thử và database test.
- **Severity:** Cao (theo Issue #2).
- **Priority đề xuất:** P1 — vi phạm tính duy nhất của tài khoản và có thể tạo nhiều tài khoản cùng địa chỉ email.
- **GitHub Issue:** [#2](https://github.com/PhuLe2712/hw2-domain-testing/issues/2).

**Mô tả:** Hệ thống không từ chối đăng ký lại địa chỉ email đã được dùng. Bộ test cũng ghi nhận email chỉ khác chữ hoa/thường vẫn có thể tạo tài khoản khác.

#### Bước tái hiện

1. Dùng database test và đăng ký tài khoản mới với email chưa tồn tại, ví dụ `test01@domain.com`.
2. Gửi lại form với cùng email, nhưng tên/mật khẩu hợp lệ.
3. Kiểm tra response hoặc danh sách user trong database test.
4. Lặp lại với cùng địa chỉ email nhưng đổi chữ hoa/thường để kiểm tra hành vi phân biệt hoa thường.

#### Kết quả mong đợi (nguồn: README.md, FR-01)

Email phải duy nhất. Lần đăng ký sau bị từ chối; số tài khoản với địa chỉ email đó không tăng.

#### Kết quả thực tế

Lần đăng ký thứ hai được chấp nhận và tạo user mới. Trong lần tái hiện API local ngày 18-10-2026, cùng một email kiểm thử nhận `HTTP 200` và thông báo `User registered successfully` ở cả hai request; response trả hai ID khác nhau.

#### Bằng chứng

Issue #2 hiện có 4 ảnh. 

---

### BUG-03 — API đăng ký không kiểm tra đầy đủ dữ liệu đầu vào

- **Test phát hiện:** `REG-D04` và probe API bổ sung có ghi trong Issue #3.
- **Feature / kênh:** FR-01 Đăng ký tài khoản / API.
- **Môi trường:** Backend local `http://localhost:3000`; request trực tiếp `POST /api/register`; database test.
- **Severity:** Cao (theo Issue #3).
- **Priority đề xuất:** P1 — API có thể lưu user với dữ liệu không hợp lệ nếu client bỏ qua validation ở giao diện.
- **GitHub Issue:** [#3](https://github.com/PhuLe2712/hw2-domain-testing/issues/3).

**Mô tả:** Validation ở giao diện không được áp dụng đầy đủ ở server. Gọi API trực tiếp với email sai định dạng hoặc trường bắt buộc rỗng vẫn có thể được xử lý như đăng ký thành công.

#### Bước tái hiện

1. Tạo request `POST http://localhost:3000/api/register`.
2. Đặt `Content-Type: application/json`.
3. Gửi body kiểm thử không hợp lệ, ví dụ:

```json
{
  "name": "",
  "email": "invalid-email",
  "password": ""
}
```

4. Kiểm tra HTTP status, response body và user mới trong database test.

#### Kết quả mong đợi (nguồn: README.md, FR-01)

Server từ chối tên/email/mật khẩu không hợp lệ bằng response validation phù hợp; không tạo user mới.

#### Kết quả thực tế

Trong lần tái hiện local, server trả `HTTP 200` với `{"message":"User registered successfully",...}` cho body trên. Test email `user@` cũng bị UI chặn nhưng API trực tiếp vẫn chấp nhận.

#### Bằng chứng

Issue #3 đã có 1 ảnh. 

---

### BUG-04 — Thêm cùng sản phẩm nhiều lần tạo nhiều dòng trong giỏ

- **Test phát hiện:** `CART-D04`, `CART-B08`.
- **Feature / kênh:** FR-07 Giỏ hàng / Web UI.
- **Môi trường:** EShop local, trang chi tiết sản phẩm và `/cart`, Chromium headless.
- **Severity:** Cao (theo Issue #4).
- **Priority đề xuất:** P2 — làm giỏ khó đọc và khiến cùng sản phẩm bị tách thành nhiều dòng.
- **GitHub Issue:** [#4](https://github.com/PhuLe2712/hw2-domain-testing/issues/4).

**Mô tả:** Thêm lại một sản phẩm đã có trong giỏ tạo thêm dòng mới, thay vì cộng quantity vào dòng hiện tại.

#### Bước tái hiện

1. Mở sản phẩm iPhone 15 Pro Max.
2. Bấm `Thêm vào giỏ` hai lần.
3. Mở trang `/cart` và đếm số dòng iPhone.

#### Kết quả mong đợi (nguồn: README.md, FR-07)

Cùng một sản phẩm chỉ có một dòng; quantity tăng từ 1 lên 2 và tổng tiền được tính theo quantity mới.

#### Kết quả thực tế

Giỏ hiển thị hai dòng iPhone riêng biệt, mỗi dòng quantity 1.

#### Bằng chứng

Ảnh giỏ hàng có trong Issue #4; ảnh local [FR07-hai-dong-cung-san-pham.png](evidence/FR07-hai-dong-cung-san-pham.png).

---

### BUG-05 — Giỏ hàng không có nút tăng/giảm quantity

- **Test phát hiện:** `CART-D05`, `CART-D06`, `CART-D07`, `CART-B07`.
- **Feature / kênh:** FR-07 Giỏ hàng / Web UI.
- **Môi trường:** EShop local, trang `/cart`, Chromium headless.
- **Severity:** Cao (theo Issue #5).
- **Priority đề xuất:** P2 — người dùng không thể sửa số lượng ngay trong giỏ.
- **GitHub Issue:** [#5](https://github.com/PhuLe2712/hw2-domain-testing/issues/5).

**Mô tả:** Quantity trong giỏ chỉ hiển thị dạng chữ; không có nút điều chỉnh tăng/giảm.

#### Bước tái hiện

1. Thêm một sản phẩm vào giỏ và mở `/cart`.
2. Quan sát cột quantity.
3. Thử tăng quantity; lặp lại với sản phẩm quantity 2 để thử giảm về 1.
4. Kiểm tra xem thành tiền và tổng giỏ có thể cập nhật theo thao tác hay không.

#### Kết quả mong đợi (nguồn: README.md, FR-07)

Có điều khiển tăng/giảm quantity; thành tiền dòng và tổng giỏ thay đổi tương ứng, không giảm quantity xuống giá trị không hợp lệ.

#### Kết quả thực tế

Quantity chỉ là văn bản. Không có điều khiển tăng/giảm nên các thao tác trong test case không thực hiện được.

#### Bằng chứng

Ảnh giao diện giỏ trong Issue #5.

---

### BUG-06 — Xóa sản phẩm khỏi giỏ không có bước xác nhận

- **Test phát hiện:** `CART-D08`, `CART-D09`, `CART-B09`, `CART-B10`.
- **Feature / kênh:** FR-07 Giỏ hàng / Web UI.
- **Môi trường:** EShop local, trang `/cart`, Chromium headless.
- **Severity:** Cao (theo Issue #6).
- **Priority đề xuất:** P2 — bấm nhầm sẽ xóa item ngay, không có cách hủy thao tác.
- **GitHub Issue:** [#6](https://github.com/PhuLe2712/hw2-domain-testing/issues/6).

**Mô tả:** Nút `Xóa` loại sản phẩm khỏi giỏ ngay lập tức, không hiển thị hộp thoại xác nhận.

#### Bước tái hiện

1. Thêm một sản phẩm vào giỏ.
2. Mở `/cart` và ghi nhận sản phẩm đang có trong giỏ.
3. Bấm `Xóa` ở dòng sản phẩm.
4. Quan sát xem có hộp thoại xác nhận/hủy hay sản phẩm biến mất ngay.

#### Kết quả mong đợi (nguồn: README.md, FR-07)

Hiện dialog xác nhận. Chọn hủy thì giữ nguyên sản phẩm; chỉ xóa sau khi người dùng xác nhận.

#### Kết quả thực tế

Sản phẩm bị xóa ngay sau khi bấm `Xóa`; không có dialog hoặc thao tác hủy.

#### Bằng chứng

Issue #6 hiện có 2 ảnh. Ảnh local trước khi xóa: [BUG-06-cart-before-remove.png](evidence/BUG-06-cart-before-remove.png); sau khi xóa: [BUG-06-cart-after-remove.png](evidence/BUG-06-cart-after-remove.png). Hai ảnh local chưa tải lên GitHub.

---

### BUG-07 — Nhãn tổng tiền trong giỏ không đúng yêu cầu

- **Test phát hiện:** `CART-D12`.
- **Feature / kênh:** FR-07 Giỏ hàng / Web UI.
- **Môi trường:** EShop local, trang `/cart`, Chromium headless.
- **Severity:** Thấp (theo Issue #7).
- **Priority đề xuất:** P3 — sai nhãn nhưng không làm sai phép tính tiền.
- **GitHub Issue:** [#7](https://github.com/PhuLe2712/hw2-domain-testing/issues/7).

**Mô tả:** Cụm từ mô tả tổng tiền ở cuối trang giỏ không khớp yêu cầu trong SRS.

#### Bước tái hiện

1. Thêm một sản phẩm bất kỳ vào giỏ.
2. Mở `/cart`.
3. Quan sát nhãn bên cạnh tổng tiền cuối trang.

#### Kết quả mong đợi (nguồn: README.md, FR-07)

Nhãn hiển thị `Tổng cộng`.

#### Kết quả thực tế

UI hiển thị `Tổng tạm tính`.

#### Bằng chứng

Ảnh giỏ hàng trong Issue #7.

---

### BUG-08 — User thường truy cập API admin và API thay đổi dữ liệu

- **Test phát hiện:** `ACL-D04`–`ACL-D09`, `ACL-B06`, `ACL-B07`.
- **Feature / kênh:** FR-12 Kiểm soát truy cập / API.
- **Môi trường:** Backend `http://localhost:3000`, Postman, JWT user thường, database SQLite test. Token chỉ dùng trong máy local; không ghi token thật vào báo cáo.
- **Severity:** Nghiêm trọng (theo Issue #8).
- **Priority đề xuất:** P1 — lộ dữ liệu người dùng và cho phép thay đổi/xóa dữ liệu mà không có vai trò admin.
- **GitHub Issue:** [#8](https://github.com/PhuLe2712/hw2-domain-testing/issues/8).

**Mô tả:** Các endpoint đặc quyền cho phép user thường thực hiện thao tác quản trị: một số route chỉ xác thực JWT nhưng không kiểm tra role admin; các route product được probe trong bộ test không có lớp bảo vệ phù hợp. Issue chính cùng các bình luận ghi nhận user thường có thể đọc danh sách user, đổi trạng thái đơn, xóa user, tạo/xóa sản phẩm, tạo danh mục và tạo coupon.

#### Bước tái hiện

1. Đăng nhập tài khoản user test qua `POST http://localhost:3000/api/login`; sao chép token từ response.
2. Tạo request `GET http://localhost:3000/api/admin/users`, chọn Authorization → Bearer Token và gắn token user.
3. Gửi các request đặc quyền bằng chính token user, mỗi thao tác trên DB test:
   - `PUT /api/admin/orders/{id}/status` với body `{"status":"confirmed"}`.
   - `DELETE /api/admin/users/{id-test}`.
   - `POST /api/products`, sau đó kiểm tra và xóa sản phẩm test.
   - `POST /api/categories` với body `{"name":"ACL test category"}`.
   - `POST /api/admin/coupons` với dữ liệu coupon test.
4. So sánh response và trạng thái dữ liệu trước/sau. Không đưa token vào ảnh công khai.

#### Kết quả mong đợi (nguồn: README.md, FR-12)

API đặc quyền chỉ cho phép token hợp lệ có `role = admin`. Với token user, server trả 401/403 và không đọc/thêm/sửa/xóa dữ liệu.

#### Kết quả thực tế

Các probe đã ghi HTTP 200 với token user: trả danh sách user; cập nhật trạng thái đơn; xóa user; tạo/xóa product; tạo category và coupon. Dữ liệu test bị thay đổi tương ứng.

#### Bằng chứng

Issue #8 có nhiều ảnh trong nội dung/bình luận cho ACL-D04–D09 và B06–B07. Rà lại từng ảnh trước khi nộp để che Authorization/JWT, email và thông tin cá nhân nếu xuất hiện.

---

### BUG-09 — User thường tự nâng quyền qua API cập nhật hồ sơ

- **Test phát hiện:** `ACL-B10`.
- **Feature / kênh:** FR-12 Kiểm soát truy cập / API.
- **Môi trường:** Backend local `http://localhost:3000`, Postman, tài khoản user test và DB SQLite test.
- **Severity:** Nghiêm trọng (theo Issue #9).
- **Priority đề xuất:** P1 — user có thể tự cấp role admin rồi gọi API đặc quyền.
- **GitHub Issue:** [#9](https://github.com/PhuLe2712/hw2-domain-testing/issues/9).

**Mô tả:** `PUT /api/users/me` nhận `role` từ request body và ghi giá trị đó vào hồ sơ user đang xác thực.

#### Bước tái hiện

1. Đăng nhập user thường và dùng token của chính user đó.
2. Ghi nhận role ban đầu bằng `GET /api/users/me`.
3. Gửi `PUT http://localhost:3000/api/users/me` với Authorization Bearer token user và body:

```json
{
  "name": "Test User",
  "shipping_address": "test-only",
  "phone": "0900000000",
  "role": "admin"
}
```

4. Gọi lại `GET /api/users/me` và kiểm tra role; không thử trên tài khoản/dữ liệu thật.

#### Kết quả mong đợi (nguồn: README.md, FR-12)

Server bỏ qua hoặc từ chối trường `role` do client gửi; role của user vẫn là `user` và tài khoản không được cấp quyền admin.

#### Kết quả thực tế

Probe ghi nhận `HTTP 200`; role trong DB đổi thành `admin`. User sau đó có thể thử gọi API admin.

#### Bằng chứng

Issue #9 có 2 ảnh. Body hiện đang ghi nhầm `BUG-10` thay vì `BUG-09` ở dòng tiêu đề; phần nhãn **Bằng chứng cần đính kèm** cũng thiếu dấu đóng Markdown.

---

### BUG-10 — Chi tiết sản phẩm mobile không hiển thị danh mục

- **Test phát hiện:** `MOB-D02`.
- **Feature / kênh:** Pool D · FR-06 Chi tiết sản phẩm mobile / compatibility harness.
- **Môi trường:** Chromium compatibility harness chạy `frontend-mobile/App.js` cùng adapter React Native giả; chưa xác minh native Android/iOS.
- **Severity:** Cao (theo Issue #10).
- **Priority đề xuất:** P2 — thiếu một trường thông tin trên màn hình chi tiết sản phẩm.
- **GitHub Issue:** [#10](https://github.com/PhuLe2712/hw2-domain-testing/issues/10).

**Mô tả:** Khi mở sản phẩm có `category_id` đã biết, màn hình chi tiết không hiển thị tên danh mục.

#### Bước tái hiện

1. Chạy compatibility harness cho app mobile.
2. Chọn sản phẩm có danh mục đã biết trong dữ liệu test.
3. Mở màn hình chi tiết sản phẩm.
4. Kiểm tra khu vực thông tin sản phẩm có tên danh mục hay không.

#### Kết quả mong đợi (nguồn: yêu cầu chi tiết sản phẩm FR-06/FR-20 trong SRS)

Chi tiết hiển thị danh mục cùng các thông tin sản phẩm theo yêu cầu.

#### Kết quả thực tế

Harness không render tên danh mục. Đây là kết quả harness, chưa phải xác minh trên Expo Go/điện thoại native.

#### Bằng chứng

Ảnh trong [GitHub Issue #10](https://github.com/PhuLe2712/hw2-domain-testing/issues/10); ảnh local hiện có trong báo cáo là `evidence/MDET-thieu-danh-muc-compat-harness.png`.

---

### BUG-11 — Sản phẩm thiếu ảnh không có ảnh thay thế hoặc trạng thái báo lỗi

- **Test phát hiện:** `MOB-D03` (test case báo cáo mở chi tiết sản phẩm; các bước trong Issue #11 lại mô tả sản phẩm ở trang chủ — cần thống nhất trước khi nộp).
- **Feature / kênh:** Pool D · FR-06 mobile / compatibility harness.
- **Môi trường:** Chromium compatibility harness; chưa xác minh native Android/iOS.
- **Severity:** Cao (theo Issue #11).
- **Priority đề xuất:** P2 — người dùng không thấy nội dung ảnh thay thế khi sản phẩm thiếu ảnh.
- **GitHub Issue:** [#11](https://github.com/PhuLe2712/hw2-domain-testing/issues/11).

**Mô tả:** Khi dữ liệu sản phẩm không có URL ảnh hoặc ảnh lỗi, giao diện không hiện ảnh thay thế hay trạng thái báo lỗi.

#### Bước tái hiện

1. Trong harness, dùng dữ liệu sản phẩm có URL ảnh rỗng hoặc không tải được.
2. Mở khu vực giao diện được nêu trong issue (hiện issue ghi trang chủ; test case `MOB-D03` ghi màn hình chi tiết).
3. Quan sát vùng ảnh.

#### Kết quả mong đợi (nguồn: tiêu chí ghi trong Issue #11)

Hiện ảnh mặc định hoặc một trạng thái lỗi ảnh rõ ràng, không để vùng ảnh trống mà không giải thích.

README.md, FR-06 yêu cầu hiển thị ảnh lớn nhưng không nêu rõ hành vi fallback; cần xác nhận tiêu chí fallback với đặc tả/nhóm trước khi coi đây là yêu cầu SRS.

#### Kết quả thực tế

Harness ghi nhận không có ảnh thay thế. Phạm vi giữa test case và bước tái hiện ở Issue #11 chưa trùng nhau hoàn toàn; cần chạy lại thống nhất trên cùng màn hình trước khi khẳng định traceability.

#### Bằng chứng

Ảnh hiện đính kèm trong [GitHub Issue #11](https://github.com/PhuLe2712/hw2-domain-testing/issues/11).

---

### BUG-12 — Quantity mobile không hợp lệ bị âm thầm đổi thành 1

- **Test phát hiện:** `MOB-B01`, `MOB-B04`, `MOB-B05`, `MOB-B06`.
- **Feature / kênh:** Pool D · FR-06 mobile / compatibility harness.
- **Môi trường:** Chromium compatibility harness chạy component `App.js` với adapter React Native giả; chưa xác minh native Android/iOS. Trường quantity native chỉ nhận số nên không dùng thử nhập chữ làm bằng chứng native.
- **Severity:** Cao (theo Issue #12).
- **Priority đề xuất:** P2 — người dùng không nhận biết dữ liệu nhập sai nhưng quantity khác với giá trị đã nhập.
- **GitHub Issue:** [#12](https://github.com/PhuLe2712/hw2-domain-testing/issues/12).

**Mô tả:** Giá trị quantity không hợp lệ bị chuẩn hóa thành 1 mà không hiện lỗi hoặc thông báo.

#### Bước tái hiện

1. Mở chi tiết sản phẩm trong compatibility harness.
2. Lần lượt nhập `0`, `-1`, `1.5` và để trống trường quantity.
3. Với mỗi giá trị, bấm thêm vào giỏ và kiểm tra quantity cuối cùng.

#### Kết quả mong đợi (nguồn: README.md, FR-06)

Chỉ nhận số nguyên dương. Giá trị không hợp lệ phải bị từ chối và có thông báo rõ ràng; không tự đổi thành giá trị khác.

#### Kết quả thực tế

Harness ghi nhận các giá trị `0`, số âm, thập phân và để trống bị đổi thành quantity 1 mà không báo lỗi. Issue cũng nêu trường hợp nhập chữ, nhưng trường hợp nhập chữ đã không còn trong bộ 87 test case cuối vì input native chỉ nhận số; không coi kết quả giả lập chữ trong harness là xác nhận native.

#### Bằng chứng

4 ảnh cho các giá trị đã thử nằm trong [GitHub Issue #12](https://github.com/PhuLe2712/hw2-domain-testing/issues/12). Kết quả chỉ được xác nhận trong harness.


