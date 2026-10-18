# Báo cáo lỗi – Issues đã đăng trên GitHub

## Trạng thái

Cập nhật ngày 18-10-2026 sau khi đối chiếu repository nhóm [PhuLe2712/hw2-domain-testing](https://github.com/PhuLe2712/hw2-domain-testing): hiện có **12 GitHub Issues (#1–#12), đều đang mở**. Bảng dưới đây dùng mã BUG trong tiêu đề issue và liên kết trực tiếp đến issue tương ứng. Mức độ được giữ theo nội dung issue.

Kết quả thực thi và giới hạn bằng chứng vẫn cần đọc cùng [nhật ký thực thi thực tế](Thuc_thi_thuc_te.md) và [báo cáo Domain/BVA](HW02_Domain_BVA_Report.md). Việc issue đang mở chỉ phản ánh trạng thái trên GitHub, không tự xác nhận bug đã được tái hiện lại trên phiên bản hiện tại.

## Danh sách bug đã đăng

| Mã | GitHub Issue | Tính năng | Mức độ | Tóm tắt kết quả thực tế | Ghi chú bằng chứng |
|---|---|---|---|---|---|
| BUG-01 | [#1 – Form đăng ký không yêu cầu xác nhận mật khẩu](https://github.com/PhuLe2712/hw2-domain-testing/issues/1) | FR-01 | Cao | Form chỉ có `name`, `email`, `password`; không có trường xác nhận mật khẩu. | Issue có ảnh chụp form. |
| BUG-02 | [#2 – Đăng ký chấp nhận email đã tồn tại](https://github.com/PhuLe2712/hw2-domain-testing/issues/2) | FR-01 | Cao | Issue ghi nhận hệ thống vẫn tạo tài khoản với email đã đăng ký, kể cả trường hợp khác chữ hoa/thường. | Issue chưa đính kèm ảnh hoặc response/DB; nên thêm bằng chứng nếu còn lưu. |
| BUG-03 | [#3 – API đăng ký không kiểm tra dữ liệu đầu vào](https://github.com/PhuLe2712/hw2-domain-testing/issues/3) | FR-01 | Cao | Issue ghi API nhận input không hợp lệ và trả HTTP 200. | Nội dung issue còn placeholder `[Ghi chính xác response thực tế nếu có.]`; cần thay bằng response đã quan sát và bằng chứng tương ứng. |
| BUG-04 | [#4 – Thêm cùng sản phẩm tạo nhiều dòng trong giỏ](https://github.com/PhuLe2712/hw2-domain-testing/issues/4) | FR-07 | Cao | Cùng một sản phẩm được hiển thị thành hai dòng riêng trong giỏ. | Issue có ảnh giỏ hàng. |
| BUG-05 | [#5 – Giỏ hàng không có điều khiển tăng/giảm quantity](https://github.com/PhuLe2712/hw2-domain-testing/issues/5) | FR-07 | Cao | `Quantity` chỉ hiển thị dạng văn bản; không có nút `+`/`−` để chỉnh trực tiếp trong giỏ. | Issue có ảnh giỏ hàng. |
| BUG-06 | [#6 – Xóa sản phẩm khỏi giỏ không có xác nhận](https://github.com/PhuLe2712/hw2-domain-testing/issues/6) | FR-07 | Cao | Chọn `Xóa` thì sản phẩm bị xóa ngay, không hiện hộp thoại xác nhận. | Issue chưa có ảnh đính kèm. |
| BUG-07 | [#7 – Nhãn tổng tiền trong giỏ không khớp yêu cầu](https://github.com/PhuLe2712/hw2-domain-testing/issues/7) | FR-07 | Thấp | UI ghi `Tổng tạm tính`, trong khi mong đợi là `Tổng cộng`. | Issue có ảnh giỏ hàng. |
| BUG-08 | [#8 – User thường truy cập được API admin và API thay đổi dữ liệu](https://github.com/PhuLe2712/hw2-domain-testing/issues/8) | FR-12 | Nghiêm trọng | Issue ghi token user thường đọc được API admin và gọi được API thay đổi product/category/coupon, gồm trạng thái đơn. | Có 6 bình luận; cần bảo đảm ảnh/request che token và có trạng thái dữ liệu trước/sau nếu dùng làm bằng chứng. |
| BUG-09 | [#9 – User có thể tự nâng quyền qua API cập nhật hồ sơ](https://github.com/PhuLe2712/hw2-domain-testing/issues/9) | FR-12 | Nghiêm trọng | Issue ghi `PUT /api/users/me` nhận `role` từ body và user thường có thể tự đổi role thành admin. | Issue có hai ảnh. **Lưu ý:** tiêu đề ghi BUG-09 nhưng phần đầu nội dung lại ghi BUG-10; nên sửa nội dung issue để thống nhất mã. |
| BUG-10 | [#10 – Chi tiết sản phẩm mobile không hiển thị danh mục](https://github.com/PhuLe2712/hw2-domain-testing/issues/10) | Pool D · FR-06 mobile | Cao | Compatibility harness ghi danh mục không được render; issue nêu chưa xác nhận trên Expo/thiết bị Android/iOS thật. | Issue có ảnh; không ghi nhận đây là kết quả native đã xác minh. |
| BUG-11 | [#11 – Sản phẩm để trống ảnh không hiện ảnh thay thế hoặc trạng thái ảnh lỗi](https://github.com/PhuLe2712/hw2-domain-testing/issues/11) | Pool D · FR-06 mobile | Cao | Issue ghi sản phẩm không có ảnh thì không có ảnh thay thế. | Issue có ảnh; cách chạy/xác nhận native chưa được mô tả rõ trong issue. |
| BUG-12 | [#12 – Quantity mobile không hợp lệ bị âm thầm đổi thành 1](https://github.com/PhuLe2712/hw2-domain-testing/issues/12) | Pool D · FR-06 mobile | Cao | Compatibility harness ghi các giá trị 0, âm, thập phân và chữ bị chuyển thành 1 mà không báo lỗi. | Issue có bốn ảnh và ghi kết quả từ compatibility harness. Trường hợp nhập chữ đã bỏ khỏi bộ 87 ca vì trường quantity trên mobile native chỉ nhận số; không xem harness cho nhập chữ là bằng chứng native. |

## Đối chiếu với bản báo cáo trước

- Các mã từ BUG-04 trở đi đã được đánh lại để khớp mã trong tiêu đề GitHub Issue. Vì vậy bug giỏ hàng trước đây mang mã BUG-05…BUG-08 nay lần lượt là BUG-04…BUG-07; bug ACL trước đây BUG-09/10 nay là BUG-08/09.
- Phát hiện mobile “không có ảnh thay thế” được thêm thành BUG-11 theo GitHub Issue #11.
- Hai phát hiện trong bản báo cáo cũ **không nằm trong 12 issue hiện có**: lỗi regex mật khẩu chỉ trên baseline cũ và API trả `200 {}` khi ID sản phẩm không tồn tại. Chúng không được tính vào danh sách issue đã đăng ở trên.
- Pool D có kết quả harness được ghi trong issue #10 và #12; không nên mô tả các kết quả này là đã xác minh native trên điện thoại. Cập nhật báo cáo nếu sau này tái hiện riêng trên Expo/thiết bị thật.

## Việc nên hoàn thiện trên GitHub

- Bổ sung response thực tế và bỏ placeholder trong [Issue #3](https://github.com/PhuLe2712/hw2-domain-testing/issues/3).
- Sửa mã BUG trong phần nội dung [Issue #9](https://github.com/PhuLe2712/hw2-domain-testing/issues/9) cho khớp tiêu đề.
- Bổ sung ảnh hoặc request/response cho Issue #2 và #6 nếu có bằng chứng.
- Với Issue #8, chỉ đính kèm token đã che và dữ liệu kiểm thử không chứa thông tin thật.
