               TRƯỜNG ĐẠI HỌC KHOA HỌC TỰ NHIÊN
                       KHOA CÔNG NGHỆ THÔNG TIN




        Báo cáo Bài tập HW03 - GUI & Usability
                              Môn: Kiểm thử phần mềm


Họ tên sinh viên: Lê Mạnh Phú
MSSV: 23120325
Gmail: lemanhphu2712@gmail.com
GitHub repo link: https://github.com/PhuLe2712/HW03-GUI-Usability.git


I. Task 1 — GUI Checklist
1. SUT và phạm vi
- Luồng chọn: FR-01 Đăng ký → FR-02 Đăng nhập → FR-05 Danh sách/tìm kiếm → FR-06 Chi
tiết → FR-07 Giỏ hàng.

- SUT là EShop, mã nguồn do môn học cung cấp tại `eshop-sut`. Phạm vi GUI tập trung vào FR-
01, FR-02, FR-05, FR-06 và FR-07; không đánh giá checkout, admin hoặc các luồng ngoài lựa
chọn.

- Luồng nhiệm vụ mục tiêu là người dùng mới tạo tài khoản, đăng nhập, tìm một sản phẩm, mở
chi tiết và kiểm tra sản phẩm trong giỏ. Các màn hình được xem: đăng ký, đăng nhập, danh sách
sản phẩm, chi tiết sản phẩm và giỏ hàng.

2. Task 1 - Thiết kế GUI checklist
- Checklist hoàn chỉnh trong file Excel Task1_GUI_Checklist.xlsx gồm 67 tiêu chí, phân bổ toàn
diện trên cả 4 khía cạnh giao diện (Interface Aspects - IA):



 Khía cạnh giao diện     Số lượng      Tỷ lệ (%)     Phạm vi bao phủ chính
 (Interface Aspect)      tiêu chí


 IA-01 - General                  18 26.9%          Ngôn ngữ tiếng Việt, cấu trúc Heading
 UI standards                                       H1, màu sắc nút CTA, đơn vị tiền tệ,
                                                    typography, tương phản màu sắc
 IA-02 - Forms                    18 26.9%          Nhãn trường nhập liệu, định dạng
                                                    email/mật khẩu, đánh dấu bắt buộc,
                                                    validation, kiểu bàn phím số lượng
 IA-03 - Navigation               12 17.9%          Phân trang, lọc danh mục, breadcrumb,
                                                    kích thước vùng chạm (touch targets),
                                                    luồng điều hướng nút
                                                    Back
 IA-04 - Feedback /               19 28.3%          Phản hồi thêm giỏ hàng, thông báo
 state                                              toast/badge, trạng thái rỗng (empty
                                                    state), xử lý lỗi tải, bảo lưu giỏ qua
                                                    reload
 Tổng cộng                        67 100%           Toàn diện 5 màn hình thuộc luồng
                                                    mua sắm cốt lõi



- Đóng góp giữa AI và Rà soát Thủ công (AI vs. Human Review)
+ Nguồn "AI ban đầu": 50 tiêu chí. AI cung cấp khung checklist tiêu chuẩn tốt về quy chuẩn giao
diện tổng quát (nhãn tiếng Việt, màu sắc, bố cục không tràn
ngang, các trường form cơ bản).
+ Nguồn "Bổ sung thủ công": 17 tiêu chí. Đây là các tiêu chí mang tính chuyên sâu mà AI ban
đầu đã bỏ sót do hạn chế của mô hình ngôn ngữ khi không trực tiếp tương tác thực tế với ứng
dụng. Cụ thể:
1. Khả năng tiếp cận & Phóng to (Accessibility & Zoom): Kiểm tra thẻ alt rỗng
của ảnh sản phẩm (GUI-12), khả năng co giãn bố cục khi zoom 200% (GUI-13), liên kết nhãn
với control for/id (GUI-15).



2. Hành vi biên và Ngoại lệ (Edge cases & Error Handling): Rủi ro lộ mật khẩu
plain-text khi chạy thực tế (GUI-25), kiểm tra lỗi mạng và fallback nội dung
(GUI-51), phản hồi bất thường khi nút không kích hoạt ở lần bấm đầu (GUI-54).



3. Tính liên tục trạng thái (State Continuity & Persistence): Kiểm tra dữ liệu giỏhàng có được lưu
trữ bền vững qua các lần reload/F5 hay không (GUI-62), thời gian hiển thị và sự tự biến mất của
thông báo toast (GUI-55).



4. Đặc thù Responsive thiết bị di động (Mobile Specifics): Vùng chạm tối thiểu trên màn hình
cảm ứng (GUI-41), bố cục bảng giỏ hàng bị co ép chữ trên màn hình hẹp (GUI-64), khả năng
hiển thị tương thích RTL (GUI-67).


+ Tất cả 17 tiêu chí bổ sung đều được ghi rõ lý do AI bỏ sót tại cột H ("Lý do AI bỏ sót") trong
file Excel để đáp ứng đầy đủ yêu cầu của đề bài.




3. Kết quả thực thi checklist:

                                                                                    Đã đánh
        Nền tảng                PASS        FAIL                N/A                    giá

                                                   3 (Mobile Only: GUI-41,
Chrome Desktop             28          36                                         64/67
                                                   GUI-63, GUI-64)
                                                   3 (Mobile Only: GUI-41,
Firefox Desktop            28          36                                         64/67
                                                   GUI-63, GUI-64)
Chrome Android                                     4 (Desktop Only: GUI-06,
                           32          31                                         63/67
emulation                                          GUI-07, GUI-13, GUI-40)



Tổng hợp và Phân nhóm 37 Lỗi Giao diện Phát hiện được
- Toàn bộ 37 tiêu chí FAIL duy nhất được tổng hợp, phân tích nguyên nhân và gom thành 30 bản
bug trên GitHub Issues kèm ảnh chụp bằng chứng




II. Task 2 — Báo cáo Đánh giá Khả dụng (Usability Evaluation)

1. Giai đoạn 1 — Lập kế hoạch và Chuẩn bị (Phase 1: Plan & Prepare)
1.1. Mục tiêu đánh giá (Objectives)
Đánh giá mức độ hiệu quả (Effectiveness), hiệu suất (Efficiency) và sự hài lòng (Satisfaction)
của người dùng cuối khi trải nghiệm luồng mua sắm cốt lõi trên ứng dụng EShop. Cụ thể:

1. Khả năng tự khám phá và định hướng (Discoverability & Learnability): Người dùng lần
đầu tiên truy cập có thể tự tạo tài khoản, đăng nhập và tìm kiếm sản phẩm mong muốn mà không
cần người hướng dẫn hay không?

 2. Nhận diện điểm nghẽn tương tác (Cognitive Bottlenecks): Xác định các bước người dùng
lúng túng, do dự hoặc thao tác sai do quy ước giao diện không nhất quán (nhãn nhập liệu, phản
hồi trạng thái, màu sắc CTA).

3. Phản hồi trạng thái hệ thống (Feedback & State Recovery): Kiểm tra phản ứng và khả
năng tự xử lý của người dùng trước các lỗi thực tế của SUT (nút “Thêm vào giỏ” không phản hồi
lần đầu, mật khẩu hiển thị plain-text, sản phẩm trùng lặp tạo nhiều dòng trong giỏ hàng).

 4. Mức độ tin cậy và an tâm (Trust & Confidence): Đánh giá tâm lý người dùng khi cung cấp
thông tin cá nhân và mật khẩu trên hệ thống.

1.2. Kịch bản nhiệm vụ (Task Scenario)
Kịch bản được thiết kế theo hướng mục tiêu thực hiện trên Website, tuyệt đối không chỉ dẫn thao
tác từng bước:


« Lời dẫn kịch bản gửi tới người tham gia trước khi trải nghiệm»
“Bạn là một khách hàng lần đầu tiên ghé thăm website thương mại điện tử EShop. Bạn đang
có nhu cầu tìm mua một thiết bị điện tử hoặc phụ kiện công nghệ phù hợp với nhu cầu hàng
ngày.
Hãy tạo một tài khoản mới, đăng nhập vào hệ thống, tìm sản phẩm bạn ưng ý, kiểm tra kỹ
thông tin chi tiết và thêm sản phẩm đó vào giỏ hàng với số lượng mong muốn để chuẩn bị
thanh toán.
Trong suốt quá trình thực hiện, bạn hãy vừa thao tác vừa suy nghĩ thành lời (Think-Aloud)
bất kỳ điều gì bạn đang nhìn thấy, dự định làm, cảm thấy hài lòng hoặc gặp khó khăn.”



1.3. Công cụ đo lường và Đánh giá (Evaluation Instruments)

A. Thang đo khả dụng chuẩn (System Usability Scale — SUS)

Thang đo SUS gồm 10 câu hỏi tiêu chuẩn quốc tế, đánh giá theo thang Likert 5 mức độ (1: Rất
không đồng ý ➔ 5: Rất đồng ý):

Q1 (+): Tôi nghĩ rằng tôi sẽ muốn sử dụng website này thường xuyên.
Q2 (-): Tôi thấy website này phức tạp không cần thiết.
Q3 (+): Tôi thấy website này dễ sử dụng.
Q4 (-): Tôi nghĩ rằng tôi cần sự hỗ trợ của một chuyên gia kỹ thuật để có thể sử dụng website
này.
Q5 (+): Tôi nhận thấy các chức năng trên website được tích hợp rất tốt.
Q6 (-): Tôi thấy có quá nhiều điều không nhất quán trên website này.
Q7 (+): Tôi nghĩ phần lớn mọi người sẽ học được cách sử dụng website này rất nhanh chóng.
Q8 (-): Tôi thấy website này rất cồng kềnh, rắc rối khi sử dụng.
Q9 (+): Tôi cảm thấy rất tự tin khi thao tác trên website này.
Q10 (-): Tôi phải học rất nhiều điều trước khi có thể làm quen và sử dụng website này.

Công thức tính điểm SUS chuẩn:

- Đối với câu hỏi lẻ (i∈{1,3,5,7,9}): Xi=Scorei−1

- Đối với câu hỏi chẵn (j∈{2,4,6,8,10}): Yj =5−Scorej

- Tổng điểm SUS của người tham gia: SUS Score=2.5×(∑Xi+∑Yj)

(Thang điểm từ 0 đến 100, chuẩn công nghiệp trung bình là 68.0 điểm).

B. Bộ câu hỏi phỏng vấn sâu sau phiên
Clarity (Độ rõ ràng): Các thông tin về sản phẩm, nhãn form (VD: đăng kí/đăng nhập), nút bấm
và thông báo lỗi có dễ hiểu và rõ ràng đối với bạn không?
Error Recovery (Khả năng khôi phục lỗi): Khi bạn bấm nhầm hoặc gặp trục trặc (ví dụ bấm
nút mà không thấy phản hồi), bạn đã xử lý như thế nào để tiếp tục?
Speed & Efficiency (Tốc độ & Hiệu quả): Bạn cảm thấy tốc độ duyệt qua các bước từ tìm sản
phẩm đến khi thấy hàng trong giỏ như thế nào? Có bước nào gây mất thời gian không đáng có?
Trust (Độ tin cậy): Bạn có cảm thấy an tâm khi nhập mật khẩu và mua hàng trên trang web này
không? Có chi tiết nào làm bạn nghi ngờ về tính bảo mật?

1.4. Danh sách Người tham gia (Participant Demographics)
Toàn bộ người tham gia được tuyển chọn ngoài phạm vi lớp học HW03, đảm bảo
tính xác thực, đa dạng về độ tuổi (từ 22 đến 58 tuổi), ngành nghề và thói quen mua
sắm trực tuyến; ưu tiên người dùng không chuyên CNTT/kiểm thử để thu thập
phản hồi khách quan nhất:


 ID      Họ và tên      Độ tuổi /   Nghề nghiệp /     Thói quen mua sắm     Thông tin liên
                        Giới tính   Lĩnh vực          Online                lạc (Đã che 4
                                                                            số giữa)
 P00      Lê Mạnh       22 / Nam    Sinh viên IT      3–4 lần/tháng         033****657
         Phú                                          (Shopee, TikTok
                                                      Shop)
         (Pilot)
 P01     Ngô Phúc       22 / Nam    Sinh viên khoa    2–3 lần/tháng         078****921
         Lộc                        Hóa               (Shopee, TikTok
                                                      Shop)

 P02     Mai Huy        22/ Nam     Sinh viên khoa    5–6 lần/tháng         096****205
         Hoàng                      cơ khí            (Shopee, TikTok
                                                      Shop)

 P03     Phan Đặng      22 / Nam    Sinh viên khoa    Thỉnh thoảng mua      090****164
         Quốc Đạt                   điện tử viễn      hàng online
                                    thông
 P04     Lê Như Hảo      31/ Nữ     Chủ shop bán      3-4 lần / tuần        032****000
                                    hàng online
 P05     Đinh Lê        29/ Nam     Quản lí nhân sự   3-4 lần/ tháng        039****121
         Quốc Hải                   công ty nước
                                    ngoài
 P06     Lê Phước       58/ Nam     Viên Chức nhà     Thỉnh thoảng nhờ      091****192
         Hào                        nước              con cái đặt mua hộ
 P07     Đặng Thị        56/Nữ      Trưởng phòng      Thỉnh thoảng nhờ      091****414
         Thúy Hoàn                  kế toán ( Đã về   con cái đặt mua hộ
                                    hưu )



1.5. Phiên thử nghiệm sơ bộ (Pilot Session — P00)
Mục tiêu: Kiểm tra tính khả thi của kịch bản, độ trôi chảy của môi trường giả lập SUT, độ rõ
ràng của bộ câu hỏi SUS tiếng Việt và đo lường khung thời gian hợp lý
Diễn biến: P00 hoàn thành kịch bản trong 6 phút 15 giây.
Phát hiện từ Pilot:
Vấn đề hướng dẫn Think-Aloud: Người tham gia thường im lặng khi đọc thông tin hay trong lúc
thực hiện kịch bản; người điều phối cần nhắc nhở nhẹ nhàng trước khi thực hiện là: “Bạn cứ
thoải mái nói ra suy nghĩ khi gặp khó khăn hay thắc mắc. Đừng sợ gì cả trang web có vấn đề gì
hay thiếu sót gì bạn cứ việc đặt câu hỏi” mà không can thiệp vào hành động.
Công cụ SUS: P00 hiểu trọn vẹn 10 câu hỏi tiếng Việt, không bị khúc mắc thuật ngữ.



2. Giai đoạn 2 — Tiến hành các phiên thực nghiệm
2.1 Quy trình chuẩn hóa cho mỗi phiên:
• Thiết lập tâm lý (Set the Stage): Thông báo rõ với người tham gia rằng mục tiêu là kiểm tra
giao diện của phần mềm, người dùng không thể làm gì sai, mọi khó khăn họ gặp phải đều là lỗi
thiết kế của hệ thống.
• sát trung lập (Neutral Observation): Người điều phối chỉ can thiệp nếu người dùng rơi vào
bế tắc hoàn toàn (> 2 phút không tìm ra hướng đi).
• Đánh giá sau phiên (Debriefing): Người dùng điền phiếu SUS độc lập và trả lời phỏng vấn
sâu 4 câu hỏi định tính.


2.2. Phương pháp thu thập và ghi nhận bằng chứng (Evidence Methodology)
• Phương pháp quan sát trực tiếp (Direct Observation): Người điều phối quan sát trực tiếp
người tham gia thao tác từ phía sau hoặc bên cạnh, không can thiệp, không giải thích thay giao
diện trừ khi người tham gia rơi vào bế tắc hoàn toàn (> 2 phút).
• Ghi chép có cấu trúc (Structured Observation Notes): Ghi nhận chi tiết: thời gian thực hiện
(Time-on-Task), trình tự click chuột, điểm do dự/lúng túng, câu nói bộc phát (think-aloud
verbalization) và lỗi thao tác.
• Thang đo chuẩn hoá System Usability Scale (SUS): Sau khi hoàn thành luồng mua sắm,
người tham gia tự mình điền 10 câu hỏi SUS chuẩn Likert 5 mức độ (từ 1: Rất không đồng ý đến
5: Rất đồng ý).
• Phỏng vấn sâu sau phiên (Post-Session Probe Questions): Phỏng vấn 4 câu hỏi định tính bao
quát: Độ rõ ràng (Clarity), Khả năng khôi phục lỗi (Error Recovery), Tốc độ & Hiệu quả (Speed
& Efficiency), Mức độ an tâm tin cậy (Trust).



2.3.1 Chi tiết Phiên 1 (Session 01 — P01: Ngô Phúc Lộc)
• Thời gian thực hiện: 7 phút 27 giây.
• Kết quả nhiệm vụ: Hoàn thành.
• Ghi chép hành vi & Think-aloud:
- Đăng ký/Đăng nhập: Khi điền form Đăng ký, Lộc thắc mắc:”Không có xác nhận lại mật khẩu
hả mày”. Khi chuyển sang Đăng nhập, bạn không biết username là gmail nên đã nhập Họ tên vào
phần username nhưng đã tự khắc phục được ngay khi nhận ra lỗi.
- Tìm kiếm & Xem chi tiết: Bạn hỏi: “sao không có hình ảnh gì hết trơn vậy”, Lộc nhấn vào
trang chi tiết Iphone và nói “rồi không có mô tả gì luôn sao lựa cha”, bạn nhấn vào logo Eshop
để thoát ra sau đó gõ từ khóa “Xiaomi” vào thanh tìm kiếm. Trang lọc ra sản phẩm không ra thứ
gì và bạn loay hoay không biết cách trở về trang chủ chính. Lúng túng 1 lúc thì bạn xóa tìm kiếm
rồi enter thì trở về được trang chính.
- Thêm vào giỏ & Kiểm tra: Lộc bấm “Thêm vào giỏ hàng” một lần, không thấy bất kỳ thông
báo toast hay popup nào, icon giỏ hàng trên header cũng không nhảy số badge. Lộc nói: “Ủa là
thêm được chưa? Sao giỏ hàng không hiện số” và bấm thêm 2 lần nữa. Sau đó, nhấn vào giỏ
hàng trên menu thì đã thêm vào thành công
Phỏng vấn sâu:
• Clarity: Không có hình ảnh minh họa và mô tả sản phẩm
• Error Recovery: Tự bấm lại nút thêm giỏ vì không thấy phản hồi.
• Speed: Tải trang nhanh, ổn định
• Trust: Không an tâm về bảo mật vì mật khẩu lộ khi gõ, nhãn đăng nhập nhập email mà ghi là
“Username”

• Điểm SUS cá nhân:
Q1: 3 | Q2: 3 | Q3: 3 | Q4: 2 | Q5: 3 | Q6: 4 | Q7: 4 | Q8: 3 | Q9: 2 | Q10: 2
Tính toán: Odd (2+2+2+3+1)=10; Even (2+3+1+2+3)=11
➔ Tổng =21×2.5= 52.5.


2.3.2 Chi tiết Phiên 2 (Session 02 — P02: Mai Huy Hoàng)
• Thời gian thực hiện: 7 phút 42 giây.


• Kết quả nhiệm vụ: Hoàn thành.
• Ghi chép hành vi & Think-aloud:
- Đăng nhập: Nhìn vào màn hình Login, thấy ô nhập ghi “Username”, Hoàng nhập họ tên lúc
đăng kí và bấm đăng nhập thì báo lỗi sai định dạng. Loay hoay 1 lúc thì bạn đã sửa lại thành
gmail.
- Tìm kiếm: Hoàng tìm màn hình máy tính. Không hiển thị sản phẩm nào thì bạn loay hoay
không biết cách quay trở lại trang chủ chính. Bạn nhấn logo Eshop cũng không được, sau đó bạn
nói “Rồi giờ sao quay lại trang chính”, sau đó bạn phải nhấn nút back lại trang trước thì mới
thành công trở về.
- Trang chi tiết: “Hoàng nói không có hình ảnh gì hết trơn luôn” và gặp lỗi nút “Thêm vào giỏ”
không phản hồi lần đầu. Bạn bấm liên tiếp nhiều lần. Sau đó,vào giỏ hàng thì bạn phát hiện sản
phẩm bị thêm 4 lần và có 4 hàng riêng biệt nhưng chỉ 1 sản phẩm.

Phỏng vấn sâu:
• Clarity: Form đăng nhập khó dùng, thông tin sản phẩm thiếu nhiều lắm
• Error Recovery: Bấm khi nào được thì thôi
• Speed: Bình thường
• Trust: Bình thường nhưng mà chỗ điền gmail mà ghi Username

• Điểm SUS cá nhân:
Q1: 2 | Q2: 4 | Q3: 2 | Q4: 4 | Q5: 2 | Q6: 3 | Q7: 3 | Q8: 4 | Q9: 3 | Q10: 3
Tính toán: Odd (1+1+1+2+2)=7; Even (1+1+2+1+2)=7
➔ Tổng =14×2.5= 35.


2.3.3 Chi tiết Phiên 3 (Session 03 — P03: Phan Đặng Quốc Đạt)
• Thời gian thực hiện: 8 phút 09 giây.
• Kết quả nhiệm vụ: Hoàn thành.
• Ghi chép hành vi & Think-aloud:
- Đăng ký/Đăng nhập: Ở form đăng kí, Đạt không thấy trường xác nhận mật khẩu nên đã hỏi:
“Không có xác nhận mật khẩu hả ?”. Form đăng nhập, bạn nhập họ tên ở ô username. Thông báo
hiện lỗi, bạn nhập lại mật khẩu 3 lần nhưng vẫn bị lỗi thì bạn nói: “Username ở đây điền Gmail
mà đúng không ?”. Một lúc bối rối thì bạn điền lại gmail và đăng nhập thành công.
- Thêm giỏ: Bạn vào trang chi tiết sản phẩm và bấm thêm vào giỏ lần đầu không được thì nhấn
lại ngay lập tức hiện thông báo đã thêm. Sau đó, bạn hỏi: “Ủa thêm rồi mà sao giỏ hàng không
hiện số vậy?”. Bạn Đạt nhấn vào logo trang chủ chính rồi mới vào giỏ hàng thì đã có sản phẩm
vừa thêm.

Phỏng vấn sâu:
• Clarity: Giỏ hàng không có thông báo số rõ ràng nha, nhập gmail mà để username khó hiểu
• Error Recovery: Bấm lại lần nữa
• Speed: Bình thường
• Trust: Có thể tin tưởng được. Không

Điểm SUS cá nhân:
Q1: 3 | Q2: 3 | Q3: 3 | Q4: 3 | Q5: 4 | Q6: 2 | Q7: 3 | Q8: 3 | Q9: 3 | Q10: 3
Tính toán: Odd (2+2+3+2+2)=11; Even (2+2+3+2+2)=11
➔ Tổng =22×2.5= 55.0.

2.3.4. Chi tiết Phiên 4 (Session 04 — P04: Lê Như Hảo)


• Thời gian thực hiện: 8 phút 11 giây.
• Kết quả nhiệm vụ: Hoàn thành.
• Ghi chép hành vi & Think-aloud:
- Đăng kí/Đăng nhập: Form đăng kí, chị Hảo nói: “Sao cái yêu cầu mật khẩu bé xíu với mờ tịt
vậy má ?”, “rồi không có xác nhận mật khẩu luôn lỡ gõ sai thì sao”, nên là chị gõ rất chậm và từ
tốn. Form đăng nhập, chị Hảo gõ gmail ở username và nhập mật khẩu và đã đăng nhập thành
công.
- Trang chi tiết sản phẩm: Chị cuộn xuống và hỏi: “ Sao ít sản phẩm thế còn không có hình ảnh
minh họa gì cơ trời ơi”, sau đó nhấn vào trang chi tiết sản phẩm và chị nhấn thêm thành công vào
giỏ,
- Giỏ hàng: chị hỏi: “Ủa sao giỏ hàng không update gì hết vậy”. Chị Hảo nhấn vào giỏ thì đã
thấy thêm thành công. Chị tiếp tục thêm 1 sản phẩm khác thì vẫn thấy giỏ hàng không hiện thị
số.

Phỏng vấn sâu:
• Clarity: Chữ hướng dẫn mật khẩu mờ quá còn nhỏ nữa, giỏ hàng không update gì khi thêm vào
gì cả, ảnh minh họa không có
• Speed: Ok không có vấn đề gì
• Trust: Không, chưa tin tưởng được trang web này
• Điểm SUS cá nhân:
Q1: 2 | Q2: 2 | Q3: 3 | Q4: 2 | Q5: 2 | Q6: 2 | Q7: 3 | Q8: 2 | Q9: 2 | Q10: 2
Tính toán: Odd (1+2+1+2+1)=7; Even (3+3+3+3+3)=15
➔ Tổng =22×2.5= 55.


2.3.5. Chi tiết Phiên 5 (Session 05 — P05: Đinh Lê Quốc Hải)
• Thời gian thực hiện: 6 phút 33 giây.
• Kết quả nhiệm vụ: Hoàn thành.
• Ghi chép hành vi & Think-aloud:
- Đăng kí/Đăng nhập:Ở form đăng kí, anh Hải phát hiện không có trường xác nhận mật khẩu nên
đã copy mật khẩu mình vừa nhập. Form đăng nhập, anh nhập họ tên ở username và paste mật
khẩu đã copy từ trước. Sau đó nhận thông báo lỗi, anh lập tức điền lại thành gmail ở username.
- Tìm kiếm: Thanh tìm kiếm, anh Hải gõ tìm “bàn phím” nhưng không ra gì, sau đó anh nhấn
logo nhưng không quay về được anh đã back lại trang trước.
Trang chi tiết: anh bảo: “Web này làm sơ sài quá ta không có gì hết trơn”, sau đó anh thêm vào
giỏ hàng. Anh nhận ra giỏ hàng không thay đổi nên hỏi: “Đã thêm rồi sao trên giỏ hàng không
thấy gì vậy?”
- Giỏ hàng: Anh vào giỏ hàng thì thấy đã thêm thành công.

Phỏng vấn sâu:
• Clarity: Giỏ hàng không hiện gì sau khi thêm, phần đăng nhập không rõ ràng phần username,
tìm kiếm xong cũng không có cách nào back về trang trước được nên người lớn tuổi sẽ khó sử
dụng khi không có hướng dẫn.
• Error Recovery: không để ý bấm đúp lần nữa
• Speed: Tạm ổn
• Trust: Chưa tin tưởng được, cảm giác như trang web của dự án sinh viên chưa hoàn thiện hay
sao vậy.

Điểm SUS cá nhân:
Q1: 2 | Q2: 3 | Q3: 2 | Q4: 3 | Q5: 3 | Q6: 2 | Q7: 3 | Q8: 3 | Q9: 2 | Q10: 3
Tính toán: Odd (1+1+2+2+1)=7; Even (2+2+3+2+2)=11


➔ Tổng =18×2.5= 45.0.


2.3.6. Chi tiết Phiên 6 (Session 06 — P06: Lê Phước Hào)
• Thời gian thực hiện: 11 phút 56 giây.
• Kết quả nhiệm vụ: Hoàn thành có sự trợ giúp.
• Ghi chép hành vi & Think-aloud:
- Đăng kí/ Đăng nhập: Form đăng kí, do hướng dẫn mật khẩu hợp lệ quá khó nhìn nên bác đã
phải lấy kính đeo mới có thể thực hiện tiếp, thực hiện chậm rãi từ tốn phần đăng kí. Form đăng
nhập, bác nhập họ tên vào phần username, sau đó nhập mật khẩu. Thông báo đăng nhập lỗi, bác
nhập lại mật khẩu 3-4 lần vẫn hiện lỗi đăng nhập. Bác nói: “Sao nhập mật khẩu nãy giờ đúng rồi
mà vẫn chưa đăng nhập được vậy. Sao ngộ vậy!”. Người hướng dẫn thực hiện chỉ dẫn bác nhập
gmail ở phần username. Và đã đăng nhập thành công
- Thêm giỏ hàng: Thao tác click lần đầu không có phản ứng. Bác chờ một lúc tưởng máy bị lag,
bác hỏi: “Là xong chưa thêm được chưa”, sau đó bác nhấn thêm lần nữa và hiện đã thêm.
- Giỏ hàng: Sau đó bác loay hoay 1 lúc ở trang chi tiết rồi mới tìm thấy phần giỏ hàng và kiểm
tra đã thêm thành công.

Phỏng vấn sâu:
• Clarity: Chỗ đăng kí chữ nhỏ quá không nhìn thấy chữ, phần điền tên mà đi điền gmail.
• Error Recovery: nhấn lần không ăn tưởng bị đơ, nhấn thêm lần nữa mới được
• Speed: Nhanh
• Trust: Chưa tin tưởng được mới dùng có lần đầu à.

Điểm SUS cá nhân:
Q1: 2 | Q2: 4 | Q3: 2 | Q4: 4 | Q5: 3 | Q6: 3 | Q7: 3 | Q8: 4 | Q9: 2 | Q10: 4
Tính toán: Odd (1+1+2+2+1)=7; Even (1+1+2+1+1)=6
➔ Tổng =13×2.5= 32.5.

2.3.7. Chi tiết Phiên 7 (Session 07 — P07: Đặng Thị Thúy Hoàn)
• Thời gian thực hiện: 9 phút 18 giây.
• Kết quả nhiệm vụ: Hoàn thành.
• Ghi chép hành vi & Think-aloud:
- Đăng nhập & Đăng ký: Cô Hoàn đăng kí thành công. Ở form đăng nhập, cô điền gmail ở user
nhưng lại nhập sai mật khẩu. Sau đó, nhập lại thì cô đã đăng nhập thành công.
Tìm kiếm sản phẩm: Cô vào thanh tìm kiếm và nhập chuột máy tính và không tìm được sản
phẩm nào. Sau đó, cô nhấn logo nhưng không trở về trang chính được. Cô lúng túng được rất lâu
thì cô reload lại trang thì đã trở về được trang chính.
- Giỏ hàng: Khi bấm Thêm giỏ không thấy gì, cô không thấy thông báo gì hết nên cô ấn thêm lần
nữa thì hiện đã thêm. Cô bảo: “ Sao đã thêm mà nó không vào giỏ hàng vậy”. Sau đó, cô nhấn
vào giỏ hàng kiểm tra thì đã vào giỏ.
Phỏng vấn sâu:
• Clarity: Tìm kiếm xong không biết về trang chủ đường nào luôn, thêm rồi mà giỏ hàng không
hiện gì nên không biết thêm được chưa
• Error Recovery: Nhấn lần đầu tưởng bị đơ, phải nhấn lần nữa mới thêm được
• Speed: Nhanh
• Trust: Bình thường, không vấn đề gì
Điểm SUS cá nhân:
Q1: 2 | Q2: 3 | Q3: 2 | Q4: 4 | Q5: 3 | Q6: 2 | Q7: 3 | Q8: 4 | Q9: 3 | Q10: 4
Tính toán: Odd (1+1+2+2+2)=8; Even (2+1+3+1+1)=8
➔ Tổng =16×2.5= 40.


       III. Giai đoạn 3 — Phân tích, Tổng hợp và Báo cáo (Phase 3: Analyse &
       Report)

       1. Bảng ma trận Điểm số SUS và Thống kê tổng hợp
       Sau khi kết thúc từng phiên thực nghiệm, cả 07 người tham gia (P01 đến P07) đều hoàn thành
       độc lập phiếu khảo sát System Usability Scale (SUS) 10 câu hỏi chuẩn Likert. Dữ liệu điểm từng
       câu và tổng điểm SUS quy đổi theo công thức chuẩn (Brooke, 1996) được tổng hợp chi tiết trong
       bảng dưới đây:




Người tham gia    Q1     Q2   Q3     Q4    Q5    Q6      Q7      Q8   Q9   Q10 Điểm Xếp loại Mức chấp
                                                                               SUS           nhận
P01 (Ngô Phúc     3      3    3      2     3     4       4       3    2    2   52.5    D       Marginal
Lộc)                                                                                           Low
P02 (Mai Huy      2      4    2      4     2     3       3       4    3    3   35.0    F       Not
Hoàng)                                                                                         Acceptable
P03 (Phan Đặng    3      3    3      3     4     2       3       3    3    3   55.0    D       Marginal
Quốc Đạt)                                                                                      Low
P04 (Lê Như       2      2    3      2     2     2       3       2    2    2   55.0    D       Marginal
Hảo)                                                                                           Low
P05 (Đinh Lê      2      3    2      3     3     2       3       3    2    3   45.0    F       Not
Quốc Hải)                                                                                      Acceptable
P06 (Lê Phước     2      4    2      4     3     3       3       4    2    4   32.5    F       Not
Hào)                                                                                           Acceptable
P07 (Đặng Thị     2      3    2      4     3     2       3       4    3    4   40.0    F       Not
Thúy Hoàn)                                                                                     Acceptable
TRUNG BÌNH        2.29   3.14 2.43 3.14 2.86 2.57        3.14 3.14 2.43 3.00   45.00   F      Not
(Mean)                                                                                 (POOR) Acceptable



       Phân tích định lượng kết quả SUS theo chuẩn công nghiệp (Sauro & Lewis, 2016):
       • Điểm SUS trung bình tổng thể: Đạt 45.00 / 100 điểm với độ lệch chuẩn SD = 9.46. Điểm số
       cao nhất là 55.0 (P03, P04) và thấp nhất là 32.5 (P06).
       • Đối chuẩn công nghiệp (Industry Benchmark): Mức điểm chuẩn trung bình của các ứng
       dụng phần mềm toàn cầu là 68.0 điểm. Mức điểm 45.00 của EShop rơi vào phân vị thứ 12%
       (12th Percentile), thuộc mức xếp loại Hạng F (Grade F - POOR), nằm trong vùng Không thể
       chấp nhận được (Not Acceptable).
       • Chỉ số Net Promoter Score (NPS): 100% người tham gia (7/7 người) đều rơi vào nhóm
       Detractor (người phản đối, điểm câu hỏi sẵn sàng khuyến nghị <= 6). Khách hàng không an tâm
       để giới thiệu website cho người thân sử dụng.

       2. Phân tích chỉ số hiệu năng thực thi
       Bên cạnh chỉ số đánh giá cảm nhận SUS, các thông số hiệu năng thao tác khách quan thu thập
       trực tiếp trong 07 phiên được tổng hợp như sau:


     Chỉ số hiệu năng (Metric)   Kết quả đo lường thực tế (N      Đánh giá & Ngưỡng kỳ vọng
                                             = 7)                            UX
 Tỷ lệ hoàn thành nhiệm vụ       100% (7/7 người hoàn thành)      Cả 7 người đều đưa được sản
 (TCR)                                                            phẩm vào giỏ hàng thành công.
 Tỷ lệ tự hoàn thành độc lập       85.7% (6/7 người độc lập)      Bác Lê Phước Hào (P06) cần
                                                                  người điều phối gợi ý do kẹt ở
                                                                  ô Username.
 Thời gian trung bình (Mean         8 phút 28 giây (508 giây)     Rất cao so với luồng mua sắm
 TOT)                                                             cơ bản (ngưỡng kỳ vọng thông
                                                                  thường < 3 phút).
 Thời gian nhanh nhất / lâu      6m33s (P05) / 11m56s (P06)       Người trẻ quen công nghệ nên
 nhất                                                             thao tác nhanh hơn; người lớn
                                                                  tuổi mất thời gian dò lỗi.
 Tỷ lệ cần trợ giúp (Assist      14.3% (1/7 người cần trợ giúp)   Người lớn tuổi gặp trở ngại lớn
 Rate)                                                            với nhãn form và thông báo lỗi
                                                                  kỹ thuật.
 Tần suất thao tác lỗi (Error            2.6 lỗi / phiên          Tập trung ở: nhập họ tên vào
 Rate)                                                            Username, click dư thừa nút
                                                                  Thêm giỏ, kẹt logo EShop.



3. Tổng hợp Bức xúc & Phân loại Khiếm khuyết Khả dụng (Thematic UX
Synthesis)
Dựa trên biên bản quan sát thao tác và trích dẫn suy nghĩ thành lời (Think-Aloud) của 7 người
tham gia, các vấn đề khả dụng được phân loại rõ ràng thành 2 nhóm:

A. Nhóm Khiếm khuyết Thiết kế Hệ thống (Systemic UX Flaws):
1. Quy ước nhãn nhập liệu đánh đố người dùng (Username vs. Email): Trường nhập liệu
đăng nhập hiển thị nhãn "Username" nhưng hệ thống lại yêu cầu định dạng Email. 6/7 người
tham gia (P01, P02, P03, P05, P06, P07) đều gõ họ tên theo phản xạ tự nhiên và nhận thông
báo lỗi đăng nhập. Người tham gia P06 phải thử lại 3-4 lần và bế tắc hoàn toàn nếu không có gợi
ý.
2. Đứt gãy phản hồi thao tác Thêm vào giỏ hàng (System Feedback Failure): Nút "Thêm vào
giỏ hàng" không phản hồi ở lần bấm đầu tiên, không có thông báo toast thành công và icon giỏ
hàng trên thanh header không cập nhật số badge. 100% người tham gia (7/7 người) đều tưởng
website bị lag hoặc chưa nhận lệnh nên đã bấm liên tiếp từ 2 đến 4 lần.
3. Đứt gãy luồng điều hướng quay lại trang chủ (Navigation Bottleneck): Sau khi tìm kiếm
không ra sản phẩm, người dùng nhấn vào Logo EShop để quay về trang chủ nhưng logo không
hoạt động. 4/7 người tham gia (P01, P02, P05, P07) bị lúng túng mất phương hướng, phải dùng
nút Back của trình duyệt hoặc xóa thanh tìm kiếm rồi Enter để quay lại.
4. Thiếu hoàn toàn hình ảnh và mô tả sản phẩm (Catalog / Content Defect): Trang chi tiết
sản phẩm không có ảnh minh họa và không có mô tả tính năng. Người tham gia (P01, P02, P04,
P05) đều bày tỏ sự thất vọng: "Sao không có hình ảnh gì hết trơn vậy", "Không có mô tả gì sao
lựa", làm giảm sút nghiêm trọng tính thuyết phục mua hàng.
5. Khả năng tiếp cận kém và thiếu xác nhận mật khẩu (Accessibility & Form Validation):
Dòng chữ hướng dẫn quy cách mật khẩu quá nhỏ và mờ (P04, P06 phải lấy kính đeo mới đọc


được). Form đăng ký thiếu trường "Xác nhận mật khẩu" (Confirm Password) khiến 4 người
(P01, P03, P04, P05) lo sợ gõ sai ký tự mà không biết.

B. Nhóm Lỗi Kỹ thuật Cô lập (Isolated Functional Bugs):
1. Nhân bản dòng sản phẩm trong giỏ hàng (Cart Duplication): Khi người dùng bấm thêm
nhiều lần do thiếu phản hồi, hệ thống không cộng dồn số lượng (Quantity) mà tạo thành các dòng
riêng biệt cho cùng một sản phẩm (P02 bị nhân bản thành 4 dòng riêng biệt).
2. Lộ mật khẩu đăng nhập dạng văn bản (Plain-text Password Input): Trường mật khẩu
form đăng nhập dùng type="text" làm hiển thị rõ toàn bộ ký tự khi gõ, gây lo ngại sâu sắc về rủi
ro bảo mật thông tin (P01 phàn nàn).
3. Màu sắc nút Đăng ký vi phạm quy chuẩn (Inconsistent CTA Color): Nút "Đăng ký" mang
màu đỏ cảnh báo nguy hiểm (btn-danger) gây cảm giác hoang mang như nút Hủy hoặc Xóa.

4. Bảng xếp hạng Mức độ Nghiêm trọng (Severity Ranking — Chuẩn Nielsen
Norman Group)
Toàn bộ khiếm khuyết được xếp hạng theo 4 mức độ nghiêm trọng chuẩn quốc tế (Nielsen,
1994):

  Mức độ nghiêm         Mô tả tác động UX          Số        Vấn đề phát hiện thực tế trên
      trọng                                      lượng                 EShop
 Severity 4          Chặn đứng luồng thao tác      2      1. Nút Thêm vào giỏ không phản hồi
 (Catastrophe /      hoặc phá vỡ hoàn toàn                lần đầu kết hợp không có
 Blocker)            niềm tin bảo mật của                 toast/badge.
                     người dùng.                          2. Mật khẩu đăng nhập hiển thị dạng
                                                          văn bản thuần (type="text").
 Severity 3 (Major   Gây trì hoãn nặng nề,         4      1. Nhãn form đăng nhập ghi
 Usability           khiến người dùng lúng                "Username" nhưng bắt buộc nhập
 Problem)            túng hoặc thao tác sai               Gmail.
                     hàng loạt.                           2. Logo EShop không điều hướng về
                                                          trang chủ sau khi tìm kiếm.
                                                          3. Sản phẩm trùng nhân bản thành
                                                          nhiều dòng trong giỏ hàng.
                                                          4. Trang chi tiết thiếu hoàn toàn hình
                                                          ảnh và mô tả sản phẩm.
 Severity 2 (Minor   Gây khó chịu nhưng người      3      1. Form đăng ký thiếu trường xác
 Usability           dùng vẫn có thể tự tìm               nhận mật khẩu (Confirm Password).
 Problem)            cách khắc phục được.                 2. Dòng hướng dẫn mật khẩu chữ quá
                                                          nhỏ và tương phản mờ.
                                                          3. Nút Đăng ký mang màu đỏ cảnh
                                                          báo (btn-danger).
 Severity 1          Khuyết điểm thị giác          1      1. Đơn vị tiền tệ hiển thị không
 (Cosmetic /         nhỏ, không ảnh hưởng                 đồng nhất (lúc "VND", lúc ký hiệu
 Visual Issue)       đến việc hoàn thành                  "₫").
                     nhiệm vụ.
