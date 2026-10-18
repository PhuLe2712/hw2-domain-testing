TRƯỜNG ĐẠI HỌC KHOA HỌC TỰ NHIÊN

KHOA CÔNG NGHỆ THÔNG TIN

![image1](MainReport_assets/image1.png)

# Báo cáo Bài tập HW2

Môn: Kiểm thử phần mềm

Họ tên sinh viên: Lê Mạnh Phú

MSSV: 23120325

Gmail: lemanhphu2712@gmail.com

Github repo: https://github.com/PhuLe2712/hw2-domain-testing.git
Github repo của nhóm: https://github.com/hoangphi117/HW02

## I. FR-01 Đăng ký tài khoản (Pool A)

- Mô hình miền:

Người dùng phải cung cấp: Họ Tên, Email, Mật khẩu.

Email phải có định dạng hợp lệ (user@domain.com) và là duy nhất trong hệ thống.

Yêu cầu mật khẩu mạnh: Tối thiểu 8 ký tự, có ít nhất 1 chữ hoa, 1 chữ thường, 1 chữ số và 1 ký tự đặc biệt (@, $, !, %, *, ?, &).

Phải có trường Xác nhận mật khẩu — hệ thống từ chối nếu hai trường không khớp.

Sau khi đăng ký thành công, người dùng được chuyển tới trang Đăng nhập.

- Test case Domain (13):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| REG - D01 | Tất cả trường hợp lệ; mật khẩu và xác nhận trùng nhau | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí<br>4. Tạo một tài khoản; chuyển tới đăng nhập | Tạo một tài khoản; chuyển tới đăng nhập | Form không có ô xác nhận; gửi 3 trường hợp lệ tạo tài khoản, chuyển trang login. | FAIL |


| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| REG - D02 | Họ tên rỗng | 1. Mở register trên EShop web<br>2. Để trống họ tên, điền email mới và mật khẩu hợp lệ<br>3. Nhấn đăng kí | Từ chối vì họ tên bắt buộc | Trình duyệt chặn gửi form đăng kí do trường họ tên bắt buộc; vẫn ở trang register. | PASS |
| REG - D03 | Họ tên chỉ có khoảng trắng | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Từ chối vì tên trống | Tên chỉ khoảng trắng được chấp nhận và chuyển trang login. | FAIL |
| REG - D04 | Email sai định dạng (`user@`) | 1. Mở register trên EShop web<br>2. Gửi `user@` qua form và API đăng ký.<br>3. Nhấn đăng kí | Từ chối, không tạo tài khoản. | Form chặn; API nhận email sai định dạng (HTTP 200) | FAIL<br>(API) |
| REG - D05 | Email đã tồn tại | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, nhưng dùng email đã đăng kí trước đó rồi.<br>3. Nhấn đăng kí | Từ chối email trùng; tài khoản cũ không đổi | Email đã đăng ký lần nữa vẫn tạo tài khoản, chuyển trang login.<br>Và tài khoản vừa đăng kí không đăng nhập được. | FAIL |
| REG - D06 | Mật khẩu thiếu chữ hoa | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, mật khẩu không có chữ in hoa<br>3. Nhấn đăng kí | Từ chối và hiển thị yêu cầu mật khẩu | Mật khẩu quá yếu! Phải dài tối thiểu 8 ký tự, gồm chữ hoa, chữ thường, số và KÝ TỰ ĐẶC BIỆT. | PASS |
| REG - D07 | Mật khẩu thiếu chữ thường | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới, mật khẩu không có chữ thường<br>3. Nhấn đăng kí | Từ chối và hiển thị yêu cầu mật khẩu | Mật khẩu quá yếu! Phải dài tối thiểu 8 ký tự, gồm chữ hoa, chữ thường, số và KÝ TỰ ĐẶC BIỆT. | PASS |
| REG - D08 | Mật khẩu thiếu chữ số | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới, mật khẩu không có chữ số<br>3. Nhấn đăng kí | Từ chối và hiển thị yêu cầu mật khẩu | Mật khẩu quá yếu! Phải dài tối thiểu 8 ký tự, gồm chữ hoa, chữ thường, số và KÝ TỰ ĐẶC BIỆT. | PASS |
| REG - D09 | Mật khẩu thiếu ký tự đặc biệt được phép | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới, mật khẩu không có kí tự đặc biệt cho phép<br>3. Nhấn đăng kí | Từ chối và hiển thị yêu cầu mật khẩu | Mật khẩu quá yếu! Phải dài tối thiểu 8 ký tự, gồm chữ hoa, chữ thường, số và KÝ TỰ ĐẶC BIỆT. | PASS |
| REG – D10 | Mật khẩu dùng ký tự đặc biệt không được phép (`#`) | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới, mật khẩu dùng kí tự đặc biệt không cho phép<br>3. Nhấn đăng kí | Từ chối và hiển thị yêu cầu mật khẩu | Mật khẩu quá yếu! Phải dài tối thiểu 8 ký tự, gồm chữ hoa, chữ thường, số và KÝ TỰ ĐẶC BIỆT. | PASS |
| REG - D11 | Mật khẩu có `?` được phép và thỏa điều kiện còn lại | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Chấp nhận | Mật khẩu có ? hợp lệ được chấp nhận, chuyển trang login. | PASS |
| REG - D12 | Xác nhận mật khẩu lệch một ký tự | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Xác nhận mật khẩu sai 1 kí tự<br>4. Nhấn đăng kí | Từ chối; không tạo tài khoản | Không có trường xác nhận để nhập lệch. | FAIL |
| REG - D13 | Thiếu trường xác nhận mật khẩu | 1. Mở register trên EShop web<br>2.  Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Không nhập xác nhận mật khẩu<br>4. Nhấn đăng kí | Từ chối; xác nhận mật khẩu là bắt buộc | Không có trường xác nhận; form vẫn chấp nhận và gửi. | FAIL |

- Test case giá trị biên (12):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| REG - B01 | Họ tên dài 0 ký tự | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Từ chối | Tên rỗng bị required chặn. | PASS |
| REG - B02 | Họ tên dài 1 ký tự không phải khoảng trắng | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Chấp nhận | Tên một ký tự X được chấp nhận. Chuyển tới trang Login | PASS |
| REG - B03 | Họ tên có khoảng trắng đầu/cuối và nội dung thật | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới. Họ tên điền “    Lan   ’’<br>3. Nhấn đăng kí | Áp dụng nhất quán chính sách cắt/giữ khoảng trắng; không coi là rỗng | Được chấp nhận. Chuyển tới trang Login | PASS |
| REG - B04 | Mật khẩu dài 7 ký tự, có đủ các nhóm ký tự | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới. Mật khẩu chỉ có 7 kí tự nhưng đầy đủ yêu cầu.<br>3. Nhấn đăng kí | Từ chối | Mật khẩu quá yếu! Phải dài tối thiểu 8 ký tự, gồm chữ hoa, chữ thường, số và KÝ TỰ ĐẶC BIỆT. | PASS |
| REG - B05 | Mật khẩu dài 8 ký tự, có đủ các nhóm ký tự | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Chấp nhận | Tài khoản được tạo và chuyển sang trang Login | PASS |
| REG - B06 | Mật khẩu dài 9 ký tự, có đủ các nhóm ký tự | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Chấp nhận | Tài khoản được tạo và chuyển sang trang Login | PASS |
| REG - B07 | Email hợp lệ ngắn nhất theo định dạng | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới và email ví dụ “a@domain.com”<br>3. Nhấn đăng kí | Chấp nhận nếu chính sách định dạng cho phép | Tài khoản được tạo và chuyển sang trang Login | PASS |
| REG - B08 | Email thiếu ký tự trước “@” | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Từ chối | Bị chặn và yêu cầu phải bao gồm @ | PASS |
| REG - B09 | Email đã có nhưng khác chữ hoa/thường | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email đã có nhưng khác chữ hoa/thường<br>3. Nhấn đăng kí | Áp dụng chính sách phân biệt hoa thường nhất quán; từ chối nếu email không phân biệt hoa thường | Cùng email khác chữ hoa/thường vẫn được tạo tài khoản thứ hai. | FAIL |
| REG - B10 | Mật khẩu có đúng một ký tự đặc biệt được phép | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Chấp nhận | Mật khẩu có đúng một ký tự đặc biệt hợp lệ được chấp nhận. | PASS |
| REG - B11 | Tên miền email kết thúc bằng dấu chấm | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới và kết thúc email bằng dấu chấm<br>3. Nhấn đăng kí | Từ chối | Bị type=email chặn. | PASS |
| REG - B12 | Ký tự cuối của xác nhận mật khẩu khác mật khẩu | 1. Mở register trên EShop web<br>2. Trường khác dùng giá trị hợp lệ, dùng email mới.<br>3. Nhấn đăng kí | Từ chối | Không có ô xác nhận, không thể nhập ký tự lệch, form vẫn gửi. | FAIL |

## II. FR-07 Giỏ hàng (Pool B)

- Mô hình miền:

+ Trạng thái giỏ: rỗng so với có một/nhiều sản phẩm. Định danh sản phẩm: sản phẩm mới so với đã có trong giỏ. Số lượng: số nguyên dương; giảm không được thấp hơn 1 (cần xác nhận hành vi ở mức 1). Thao tác: tăng/giảm, xóa có xác nhận, tiếp tục mua sắm. Tổng tiền phải bằng tổng thành tiền từng dòng; nhãn tổng là “Tổng cộng”.

- Test case Domain (12):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| CART- D01 | Mở giỏ không có sản phẩm | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về rỗng | Hiện minh họa/thông báo giỏ trống và nút tiếp tục mua sắm | Trong giỏ hiển thị “Giỏ hàng của bạn đang trống” và tiếp tục mua sắm | PASS |
| CART- D02 | Một sản phẩm, số lượng 1 | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về rỗng<br>4. Ở trong danh sách sản phẩm thêm bất kì sản phẩm vào giỏ. | Đúng sản phẩm, đơn giá, số lượng, thành tiền và tổng tạm tính. | Sản phẩm: dòng iPhone: giá/số lượng/thành tiền/tổng tạm tính. Đúng và đầy đủ thông tin sản phẩm | PASS |
| CART- D03 | Nhiều sản phẩm khác nhau | 1. Đã đăng nhập thành công.<br>2. Ở trong danh sách sản phẩm thêm bất kì nhiều sản phẩm khác nhau vào giỏ. | Mỗi sản phẩm một dòng; tính đúng từng dòng và tổng | 2 sản phẩm khác nhau hiển thị 2 dòng. Tổng đúng và đầy đủ thông tin sản phẩm | PASS |
| CART- D04 | Thêm cùng một sản phẩm hai lần | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về rỗng<br>4. Ở trong danh sách sản phẩm thêm 2 sản phẩm giống nhau vào giỏ. | Một dòng; số lượng tăng | Thêm iPhone 2 lần tạo 2 dòng số lượng là 1 thay vì 1 dòng số lượng là 2. | FAIL |

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| CART- D05 | Tăng số lượng sản phẩm có trong giỏ hàng | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Ở trong danh sách sản phẩm thêm 1 sản phẩm bất kì vào giỏ.<br>4. Vào giỏ và tăng số lượng sản phẩm vừa thêm. | Số lượng, thành tiền và tổng tăng tương ứng | Không có nút tăng số lượng trong giỏ. | FAIL |
| CART- D06 | Giảm số lượng sản phẩm trong giỏ hàng khi đang lớn hơn 1 | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Ở trong danh sách sản phẩm thêm nhiều sản phẩm giống nhau vào giỏ.<br>4. Vào giỏ và giảm số lượng sản phẩm vừa thêm. | Số lượng, thành tiền và tổng giảm tương ứng | Không có nút giảm số lượng trong giỏ. | FAIL |
| CART- D07 | Giảm số lượng từ 1 | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 1 sản phẩm bất kì vào giỏ.<br>5. Vào giỏ và thử giảm số lượng sản phẩm vừa thêm. | Không giảm xuống 0; giữ quantity là 1 hoặc hỏi xác nhận xóa. | Không có nút giảm nên không thể thực hiện thao tác. | FAIL |
| CART- D08 | Xóa sản phẩm và xác nhận | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Ở trong danh sách sản phẩm thêm 1 sản phẩm bất kì vào giỏ.<br>4. Vào giỏ và thử xóa sản phẩm vừa thêm và xác nhận | Xóa đúng sản phẩm; tính lại tổng | Bấm Xóa xóa ngay; không hiện hộp thoại xác nhận | FAIL |
| CART- D09 | Xóa sản phẩm rồi hủy xác nhận | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 1 sản phẩm bất kì vào giỏ.<br>5. Vào giỏ và thử xóa sản phẩm vừa thêm và hủy xác nhận | Giữ nguyên sản phẩm và tổng | Bấm Xóa xóa ngay; không có lựa chọn hủy. | FAIL |
| CART- D10 | Tiếp tục mua sắm khi giỏ có hàng | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 1 sản phẩm bất kì vào giỏ. | Về trang chủ; giỏ vẫn còn dữ liệu | Tiếp tục mua sắm ở trang chủ; quay lại giỏ vẫn còn sản phẩm trước đó đã thêm. | PASS |
| CART- D11 | Nhiều giá và số lượng khác nhau | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm nhiều sản phẩm khác nhau vào giỏ. | Tổng bằng tổng thành tiền của mọi dòng | Tính đúng và đầy đủ thông tin các dòng sản phẩm | PASS |
| CART- D12 | Hiển thị tổng tiền | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm nhiều sản phẩm khác nhau vào giỏ. | Nhãn chính xác là “Tổng cộng” | Nhãn hiển thị “Tổng tạm tính”, không phải “Tổng cộng”. | FAIL |

- Test case giá trị biên (10):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| CART-B01 | Giỏ rỗng (0 dòng) | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống | Hiện trạng thái trống; tổng bằng 0 hoặc ẩn nhất quán | 0 dòng hiển thị trạng thái rỗng; tổng được ẩn. | PASS |
| CART-B02 | Một dòng (giỏ có hàng nhỏ nhất) | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 1 sản phẩm vào giỏ. | Hiển thị đúng một dòng | 1 dòng được hiển thị đúng thông tin sản phẩm | PASS |
| CART-B03 | Hai dòng | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 2 sản phẩm khác nhau vào giỏ. | 2 dòng được hiển thị | 2 dòng được hiển thị đúng thông tin những sản phẩm vừa thêm | PASS |
| CART-B04 | Nhập số lượng 0 trong trang chi tiết sản phẩm và thêm vào giỏ | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4.  Ở trang chi tiết sản phẩm, nhập số lượng `0` rồi bấm “Thêm vào giỏ”. | Từ chối số lượng 0; không thêm sản phẩm vào giỏ. | Sản phẩm được thêm với quantity 0 và tổng tiền 0 ₫. | FAIL |
| CART-B05 | Nhập số lượng 1 trong trang chi tiết sản phẩm và thêm vào giỏ | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4.  Ở trang chi tiết sản phẩm, nhập số lượng `1` rồi bấm “Thêm vào giỏ”. | Chấp nhận mức tối thiểu | Số lượng 1 được thêm và hiển thị đúng thông tin sản phẩm vừa thêm. | PASS |
| CART-B06 | Nhập số lượng 2 trong trang chi tiết sản phẩm và thêm vào giỏ | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4.  Ở trang chi tiết sản phẩm, nhập số lượng `2` rồi bấm “Thêm vào giỏ”. | Chấp nhận; thành tiền đúng và sản phẩm số lượng hiển thị là 2 | Số lượng 2 được thêm; thông tin sản phẩm đúng, thành tiền và tổng tạm tính đúng. | PASS |
| CART-B07 | Giảm số lượng từ 2 về 1 | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4.  Ở trang chi tiết sản phẩm, nhập số lượng `2` rồi bấm “Thêm vào giỏ”.<br>5. Vào giỏ hàng và thử giảm số lượng sản phẩm vừa thêm từ 2 về 1 | Còn một; không xóa nhầm sản phẩm | Không có nút giảm nên không thể giảm 2 về 1 | FAIL |
| CART-B08 | Thêm sản phẩm đã có số lượng 1 | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4.  Ở trang chi tiết sản phẩm, nhập số lượng `1` rồi bấm “Thêm vào giỏ”.<br>5. Tiếp tục ra ngoài vào trang chi tiết đúng sản phẩm vừa thêm và nhập số lượng ‘1’ rồi bấm ‘‘ thêm vào giỏ ’’ lại 1 lần nữa | Một dòng với số lượng 2 | Thêm cùng sản phẩm lần hai tạo dòng thứ hai với số lượng là 1 thay vì 1 dòng số lượng 2. | FAIL |
| CART-B09 | Xóa dòng duy nhất và xác nhận | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 1 sản phẩm vào giỏ.<br>5. Vào giỏ và thử xóa dòng sản phẩm vừa thêm | Chuyển sang trạng thái giỏ trống | Xóa dòng duy nhất chuyển giỏ rỗng nhưng không có bước xác nhận. | FAIL |
| CART-B10 | Xóa dòng duy nhất rồi hủy xác nhận | 1. Đã đăng nhập thành công.<br>2. Nhấn vào giỏ hàng<br>3. Reset giỏ hàng về trống<br>4. Ở trong danh sách sản phẩm thêm 1 sản phẩm vào giỏ.<br>5. Vào giỏ và thử xóa dòng sản phẩm vừa thêm và hủy xác nhận | Dòng hàng còn nguyên; tổng không đổi | Xóa ngay; không có dialog để hủy, sản phẩm không được giữ lại. | FAIL |

## III. FR-12 Kiểm soát truy cập Admin (Pool C):

- Mô hình miền:

Các thao tác được bảo vệ gồm `/api/admin/*` và API thay đổi sản phẩm, danh mục, mã giảm giá. Chia người gọi theo token: không có, sai định dạng, hết hạn/không hợp lệ, hợp lệ với vai trò user, và hợp lệ với vai trò admin. Kiểm tra thêm để trường trong request không thể đổi vai trò của người đã xác thực. API đặc quyền chỉ cho phép JWT hợp lệ có `role = admin`.

- Bước chuẩn bị token hết hạn:

+ Token user và admin còn hiệu lực: Trong Postman tạo POST http://localhost:3000/api/login . Chọn Body → raw → JSON, gửi lần lượt:

User: {"email":"test@eshop.com","password":"Test1234!"}

Admin: {"email":"admin@eshop.com","password":"Admin123!"}

+ Token hết hạn cho ACL-D03 và ACL-B05: Mở PowerShell tại thư mục gốc eshop-sut, chạy từng lệnh dưới đây rồi sao chép chuỗi JWT được in ra:

• node -e "const j=require('./backend/node_modules/jsonwebtoken'); console.log(j.sign({id:2,role:'user',exp:Math.floor(Date.now()/1000)-2},'super_secret_key_that_should_not_be_here'))"

• node -e "const j=require('./backend/node_modules/jsonwebtoken'); console.log(j.sign({id:1,role:'admin',exp:Math.floor(Date.now()/1000)-2},'super_secret_key_that_should_not_be_here'))"

Token hết hạn của user: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6Miwicm9sZSI6InVzZXIiLCJleHAiOjE3OTIwODAxMjYsImlhdCI6MTc5MjA4MDEyOH0.4Rkdzxg_THKteID5zDzSwWBZbf7izx2PiDVdGvPH2eE

Token hết hạn của admin: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwicm9sZSI6ImFkbWluIiwiZXhwIjoxNzkyMDgxNjk5LCJpYXQiOjE3OTIwODE3MDF9.DvvN6vOFGsRvcKXtdlO3lPePS5ZHttnzHzh6VEh-0k8

- Test case Domain (12):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| ACL - D01 | Không có token, gọi API liệt kê user admin | 1. Mở app Post man<br>2. gửi GET http://localhost:3000/api/admin/users<br>3. Ở tab Authorization, chọn No Auth.<br>4. Nhấn send. | 401; không trả dữ liệu bảo vệ | Không token: HTTP 401. | PASS |
| ACL - D02 | Token sai định dạng gọi API admin | 1. Tạo GET cùng URL `/api/admin/users`.<br>2. Authorization → Bearer Token; nhập `abc.def.ghi`.<br>3. Send. | Từ chối; không trả dữ liệu | HTTP 403. | PASS |
| ACL - D03 | Token hết hạn | 1. Tạo GET cùng URL `/api/admin/users`.<br>2. Authorization → Bearer Token; nhập token hết hạn của user đã làm sẵn ở trên<br>3. Send. | Từ chối; không trả dữ liệu. | HTTP 403 với JWT hết hạn. | PASS |
| ACL - D04 | Token hợp lệ của user thường | 1. Đăng nhập user thường qua `POST /api/login`, sao chép `token`<br>2. Tạo GET `/api/admin/users`.<br>3. Authorization → Bearer Token; dán token user.<br>4. Send. | HTTP 401/403; không trả danh sách user. | HTTP 200; trả 26 user. | FAIL |
| ACL - D05 | User thường sửa trạng thái đơn | 1. Lấy token user thường.<br>2. Tạo PUT `http://localhost:3000/api/admin/orders/id/status`. ( id đang pending )<br>3. Authorization → Bearer Token; dán token user.<br>4. Body → raw → JSON: `{"status":"confirmed"}`.<br>5. Send | Bị từ chối; trạng thái đơn không đổi. | HTTP 200; đơn 1 đổi từ `pending` sang `confirmed`. | FAIL |
| ACL - D06 | User thường xóa tài khoản khác | 1. Chọn một user test khác, ghi lại ID (lượt test trước dung tạo ID 26).<br>2. Tạo DELETE `http://localhost:3000/api/admin/users/26`.<br>3. Authorization → Bearer Token; dán token user.<br>4. Send | Từ chối dữ liệu không đổi | HTTP 200, user bị xóa | FAIL |
| ACL - D07 | User thường tạo và xóa sản phẩm | 1. Lấy token user thường<br>2. Gửi GET http://localhost:3000/api/products và ghi số sản phẩm hiện có.<br>3. Tạo POST `http://localhost:3000/api/products`.<br>4. Gửi JSON sản phẩm test (tên, giá, mô tả, ảnh, `category_id`).<br>5. Ghi ID trả về; gọi DELETE `/api/products/{id}` bằng cùng token.<br>6. Kiểm tra số sản phẩm trước/sau. | Cả hai thao tác bị từ chối; dữ liệu không đổi. | POST/DELETE đều HTTP 200; số sản phẩm đổi | FAIL |
| ACL - D08 | User thường tạo danh mục | 1. Lấy token user thường.<br>2. Tạo POST `http://localhost:3000/api/categories`.<br>3. Authorization → Bearer Token; dán token user.<br>4. Body JSON: `{"name":"ACL test category"}`.<br>5. Send. | Bị từ chối; danh mục mới không được tạo. | HTTP 200; tạo danh mục ID 5. | FAIL |
| ACL - D09 | User thường tạo mã giảm giá | 1. Lấy token user thường.<br>2. Tạo POST `http://localhost:3000/api/admin/coupons`.<br>3. Authorization → Bearer Token; dán token user.<br>4. Body JSON có `code`, `type`, `discount_value`, `min_order_amount`, `expired_at`.<br>5. Send. | Bị từ chối; mã giảm giá không được tạo. | HTTP 200; tạo mã giảm giá ID 7. | FAIL |
| ACL – D10 | - Token admin hợp lệ:<br>eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwicm9sZSI6ImFkbWluIiwiaWF0IjoxNzkyMDg2ODQyfQ.yPYDw9zPyoEEIXpJ2jH6XpG2EeNLcuNAgd-1D_pgj2w | 1. Đăng nhập admin qua `POST /api/login`, sao chép token.<br>2. Tạo GET `/api/admin/users`.<br>3. Authorization → Bearer Token; dán token admin.<br>4. Send. | HTTP 200; admin được xem danh sách. | HTTP 200 | PASS |
| ACL – D11 | User cập nhật hồ sơ, không gửi trường role | 1. Lấy token user thường.<br>2. Ghi lại role hiện tại bằng GET `/api/users/me`.<br>3. Tạo PUT `/api/users/me`, gửi thông tin hồ sơ nhưng bỏ trường `role`.<br>4. Gọi GET `/api/users/me` lần nữa. | Hồ sơ được cập nhật; role vẫn là `user`. | Role vẫn là `user`. | PASS |
| ACL – D12 | JWT giả mạo role admin | 1. Lấy token user thường.<br>2. Sửa payload token thành `role: admin` nhưng giữ chữ ký cũ/không hợp lệ.<br>3. Gửi GET `/api/admin/users` với token đã sửa trong Bearer Token. | Từ chối; token giả không được cấp quyền admin. | HTTP 403. | PASS |

- Test case giá trị biên (10)

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| ACL -B01 | Không có header Authorization | 1. Tạo GET `http://localhost:3000/api/admin/users`.<br>2. Đảm bảo không có header Authorization (Authorization → No Auth).<br>3. Send. | HTTP 401; không trả dữ liệu. | HTTP 401. | PASS |
| ACL -B02 | Header Bearer có token rỗng | 1. Tạo GET `/api/admin/users`.<br>2. Authorization → Bearer Token; để trống token.<br>3. Send. | HTTP 401/403; tuyệt đối không trả danh sách. | HTTP 401. | PASS |
| ACL -B03 | Token hợp lệ bị sửa 1 ký tự | 1. Đăng nhập để lấy token user hợp lệ.<br>2. Sao chép token và đổi ký tự cuối.<br>3. Gửi GET `/api/admin/users` với token đã sửa | HTTP 401/403; không trả danh sách. | HTTP 403. | PASS |
| ACL -B04 | Token admin còn hạn | 1. Dùng token admin test có thời hạn còn khoảng 90 giây.<br>2. Gửi GET `/api/admin/users` với Bearer Token trước khi token hết hạn. | Token hợp lệ còn hạn được chấp nhận. | HTTP 200 | PASS |
| ACL -B05 | Token admin đã hết hạn | 1. Lấy token admin hết hạn theo lệnh ở phần chuẩn bị.<br>2. Tạo GET `http://localhost:3000/api/admin/users`.<br>3. Authorization → Bearer Token; dán JWT vừa tạo.<br>4. Send. | HTTP 401/403; không trả danh sách. | HTTP 403. | PASS |
| ACL -B06 | Token user thường đọc API admin | 1. Đăng nhập bằng user thường, sao chép token.<br>2. Gửi GET `/api/admin/users` với Bearer Token user.<br>3. Kiểm tra response có danh sách user không. | Bị từ chối; không trả dữ liệu admin. | HTTP 200; trả đầy đủ user. | FAIL |
| ACL -B07 | Token user thường tạo dữ liệu admin | 1. Lấy token user thường.<br>2. Tạo POST `http://localhost:3000/api/admin/coupons`.<br>3. Authorization → Bearer Token; dán token user.<br>4. Body JSON có `code`, `type`, `discount_value`, `min_order_amount`, `expired_at`.<br>5. Send.<br>. | Bị từ chối; coupon không được tạo. | HTTP 200; coupon được tạo. | FAIL |
| ACL -B08 | Token admin gọi API admin | 1. Đăng nhập admin, sao chép token.<br>2. Gửi GET `/api/admin/users` với Bearer Token admin.<br>3. Send | HTTP 200; được phép xem danh sách. | HTTP 200. | PASS |
| ACL -B09 | Cập nhật hồ sơ không có trường role | 1. Đăng nhập user thường; ghi role hiện tại.<br>2. Gửi PUT `/api/users/me` với thông tin hồ sơ, không có trường `role`.<br>3. Đọc lại hồ sơ. | Role không đổi. | Role vẫn là `user` | PASS |
| ACL -B10 | User thường tự gửi `role: admin` | 1. Đăng nhập user thường, sao chép token.<br>2. Gửi PUT `/api/users/me` với Bearer Token user và JSON có `role: "admin"`.<br>3. Gọi GET `/api/users/me`; sau đó thử GET `/api/admin/users`. | Server bỏ qua/từ chối role; user vẫn là user và không vào được API admin | HTTP 200; role DB đổi thành `admin`. | FAIL |

## IV. FR-06 Chi tiết sản phẩm trên Mobile (Pool D)

- Mô hình miền

Kiểm tra sản phẩm có dữ liệu hoặc thiếu dữ liệu; API trả sản phẩm, không tìm thấy hoặc lỗi mạng; mô tả ngắn/dài/rỗng; số lượng hợp lệ hoặc không hợp lệ. Màn hình chi tiết cần hiển thị ảnh, tên, giá, mô tả, danh mục; chỉ nhận số lượng nguyên dương và phản hồi khi thêm vào giỏ.

- Test case Domain (10):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| MOB-D01 | Sản phẩm có đủ dữ liệu | Mở một sản phẩm bất kì có ảnh, tên, giá và mô tả trong harness | Hiển thị đúng ảnh, tên, giá, mô tả. | Các trường dữ liệu được hiển thị. | PASS |
| MOB-D02 | Sản phẩm có danh mục | Mở sản phẩm có `category_id` đã biết. | Chi tiết hiển thị tên danh mục | Không render tên danh mục. | FAIL |
| MOB-D03 | Sản phẩm không có ảnh | Mở chi tiết với URL ảnh rỗng/sai. | Hiện ảnh thay thế hoặc trạng thái ảnh lỗi. | Không có ảnh thay thế. | FAIL |
| MOB-D04 | Mô tả sản phẩm rỗng | 1. Tạo một sản phẩm có mô tả rỗng<br>2. Mở sản phẩm có mô tả rỗng đó. | Màn hình không crash; phần mô tả để trống phù hợp. | Màn hình không crash. | PASS |
| MOB-D05 | Mô tả dài 1.500 ký tự | 1. Tạo 1 sản phẩm có mô tả dài 1500 ký tự<br>2.Mở sản phẩm có mô tả 1.500 ký tự; thử cuộn nội dung trong harness. | Toàn bộ mô tả đọc được bằng cách cuộn. | Nội dung 1.500 ký tự được tạo và đọc được bằng cách cuộn | PASS |
| MOB-D06 | Số lượng ban đầu là 1 | Mở một trang chi tiết sản phẩm bất kì | Quantity ban đầu là 1. | Quantity ban đầu là 1. | PASS |
| MOB-D07 | Thêm sản phẩm với qty 1 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Giữ số lượng 1<br>3. Bấm thêm vào giỏ. | Thêm đúng một sản phẩm, số lượng 1 | Thêm đúng số lượng 1 | PASS |
| MOB-D08 | Thêm sản phẩm với qty 3 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Nhập số lượng 3<br>3. Bấm thêm vào giỏ. | Giỏ có sản phẩm với số lượng 3 | Thêm đúng số lượng 3. | PASS |
| MOB-D09 | Phản hồi sau khi thêm | 1.Mở một trang chi tiết sản phẩm bất kì<br>2.Thêm sản phẩm hợp lệ vào giỏ. | Hiện thông báo/Alert xác nhận đã thêm. | Alert được gọi sau khi thêm. | PASS |
| MOB-D10 | Chuyển sang sản phẩm khác | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Nhập số lượng 3.<br>3. Sau đó đổi sang sản phẩm khác<br>4.Quay trở về sản phẩm vừa sửa | Quantity được đặt lại về giá trị mặc định 1 | Quantity được reset. | PASS |

- Test case giá trị biên (8):

| ID | Miền đại diện | Thao tác | Kết quả mong đợi | Kết quả thực tế | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| MOB-B01 | Quantity 0 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Nhập số lượng 0.<br>3. Nhấn thêm vào giỏ | Từ chối; không thêm sản phẩm. | Âm thầm chuẩn hóa thành số lượng 1 | FAIL |
| MOB-B02 | Quantity nhỏ nhất hợp lệ: 1 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Giữ số lượng 1<br>3. Bấm thêm vào giỏ. | Chấp nhận qty 1. | Thêm qty 1. | PASS |
| MOB-B03 | Quantity hợp lệ: 3 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Nhập số lượng 3.<br>3. Bấm thêm vào giỏ. | Chấp nhận qty 3. | Thêm qty 3 | PASS |
| MOB-B04 | Quantity âm: -1 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Nhập số lượng -1.<br>3. Bấm thêm vào giỏ. | Từ chối; không thêm sản phẩm. | Âm thầm chuẩn hóa thành số lượng 1 | FAIL |
| MOB-B05 | Quantity thập phân: 1.5 | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Nhập số lượng 1.5<br>3. Bấm thêm vào giỏ. | Từ chối vì không phải số nguyên.<br>. | Âm thầm chuẩn hóa thành qty 1. | FAIL |
| MOB-B06 | Quantity để trống | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Để trống số lượng<br>3. Bấm thêm vào giỏ. | Yêu cầu nhập số nguyên dương | Giá trị không hợp lệ bị chuẩn hóa thành qty 1. | FAIL |
| MOB-B07 | Thêm cùng sản phẩm hai lần | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Thêm cùng 1 sản phẩm 2 lần<br>3. Bấm xem giỏ hàng. | Một dòng sản phẩm, quantity cộng dồn. | Hai lần thêm được gộp thành một dòng. | PASS |
| MOB-B08 | Đổi sản phẩm sau khi nhập quantity | 1.Mở một trang chi tiết sản phẩm bất kì<br>2. Đổi số lượng sản phẩm A<br>3. Mở sản phẩm B/<br>4. Quay lại sản phẩm A. | Quantity được reset về 1. | Quantity được reset về 1. | PASS |

## V. AI gap analysis.

Sau khi kiểm tra và thực hiện kiểm thử tất cả TC cũng như nội dung AI đưa ra trong bài HW02. Tôi nhận ra AI đã bỏ sót một vài trường hợp.

+ Đầu tiên, AI đã đưa ra TC của pool và thực hiện luôn phần kiểm thử. Tuy nhiên, AI đã không thực hiện chụp hình bất kì dẫn chứng nào về những lỗi mà AI đã test FAIL  Do tôi không prompt yêu cầu, nhưng AI đã đọc đề bài và có tóm tắt lúc trước rằng phải chụp screenshort màn hình bug nhưng AI sẽ không thực hiện khi prompt không yêu cầu AI làm

+ Thứ hai, AI đã bỏ sót một bug ở pool C ( ACL – D08 ) khi tôi prompt yêu cầu, AI đã bỏ sót qua bug đó khiến tôi phải tự báo cáo bug đó  Do sai sót của AI.

+ Cuối cùng, AI đã thực hiện kiểm thử chưa chính xác về App trên mobile. AI đã đưa ra TC rằng số lượng ( Quantity) có thể nhập bằng chữ. Tuy nhiên, khi tôi test phần nội dung của TC đó thì chỉ có thể nhập được số không thể nhập chữ  TC đó tôi đã loại bỏ ngay vì đây là hạn chế của AI.
