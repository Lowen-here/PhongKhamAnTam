# MINI-SRS: HỆ THỐNG QUẢN LÝ LỊCH KHÁM PHÒNG KHÁM AN TÂM

## Thông tin sinh viên

| MSSV | Họ và tên |
|---|---|
| 24120164 | Nguyễn Thế Anh |
| 24120172 | Bùi Quốc Đạt |
| 24120469 | Chế Nguyễn Thùy Trang |
| 24120370 | Trần Thị Lợi |

## 1. Giới thiệu

### 1.1 Hiện trạng và vấn đề

Phòng khám An Tâm có 6 bác sĩ thuộc nhiều chuyên khoa, phục vụ khoảng 80-120 lượt bệnh nhân mỗi ngày và 2 nhân viên tiếp nhận mỗi ca. Lịch hiện được ghi bằng sổ và xác nhận qua điện thoại; thông tin không được cập nhật đồng bộ, việc xác nhận/hủy tốn thời gian, bác sĩ chỉ nhận danh sách đầu ca, và khi bác sĩ nghỉ đột xuất nhân viên phải gọi từng bệnh nhân.

### 1.2 Mục tiêu hệ thống

- Tập trung hóa việc đặt, đổi, hủy và theo dõi lịch khám.
- Cung cấp lịch trong ngày và trạng thái tiếp nhận cho nhân viên, bác sĩ có quyền.
- Giảm thao tác thủ công và thông báo kịp thời khi lịch thay đổi.
- [CR-01] Hỗ trợ khám trực tuyến trả trước, có quản lý thanh toán, link khám và hoàn tiền khi bác sĩ hủy.

## 2. Phạm vi

### 2.1 Trong phạm vi

- Bệnh nhân xem slot trống, đặt / đổi / hủy lịch theo quy định được phòng khám xác nhận.
- Bác sĩ xem danh sách bệnh nhân trong ngày; nhân viên tiếp nhận quản lý hồ sơ, trạng thái đến/vắng mặt và các tình huống lịch ngoại lệ.
- Quản lý cập nhật lịch nghỉ, xuất báo cáo lịch hẹn / lượt khám / tỷ lệ vắng mặt.
- Gửi thông báo thay đổi lịch qua kênh được phòng khám lựa chọn và cấu hình.
- [CR-01]: đặt khám trực tuyến có thanh toán trước, cấp link gọi video và hoàn tiền khi bác sĩ hủy.

### 2.2 Ngoài phạm vi

- Kế toán, tính lương nhân viên.
- Quản lý kho thuốc và vật tư y tế.
- Kết nối trực tiếp với thiết bị y tế như siêu âm hoặc X-quang.

### 2.3 Môi trường và phụ thuộc

Hệ thống dự kiến được sử dụng qua trình duyệt máy tính và di động. Công nghệ triển khai, trình duyệt / phiên bản hỗ trợ, hạ tầng lưu trữ và chính sách sao lưu chưa được cung cấp, cần xác nhận. Các chức năng thông báo, thanh toán và gọi video phụ thuộc dịch vụ bên ngoài tương ứng; nhà cung cấp, SLA, cơ chế lỗi và môi trường tích hợp cần được lựa chọn trước khi nghiệm thu.

## 3. Stakeholder 

### 3.1 Stakeholder

| ID | Stakeholder | Vai trò | Nhu cầu | Ảnh hưởng |
|---|---|---|---|---|
| STK-MGR (Manager) | Quản lý phòng khám | Client, người phê duyệt | Bệnh nhân đặt lịch nhanh; giảm tải thao tác cho nhân sự. | Quyết định phê duyệt hệ thống và ngân sách. |
| STK-DOC (Doctor) | Bác sĩ (6 người) | User | Nắm được danh sách lịch khám và hồ sơ bệnh nhân từ đầu ca. | Trực tiếp sử dụng thông tin đầu ra để phục vụ công tác chuyên môn. |
| STK-REC (Receptionist) | Nhân viên tiếp nhận (2 người/ca) | User | Cập nhật lịch hẹn theo thời gian thực, dễ dàng quản lý ca khám và thông báo nhanh cho bệnh nhân khi có thay đổi đột xuất. | Trực tiếp vận hành luồng tiếp nhận. |
| STK-PAT (Patient) | Bệnh nhân | User | Chủ động đặt, đổi, hủy lịch trực tuyến không cần đến phòng khám; sử dụng được dịch vụ khám từ xa. | Là người dùng cuối, quyết định mức độ thành công của dịch vụ phần mềm. |

### 3.2 Thuật ngữ

| Thuật ngữ | Giải thích |
|---|---|
| No-show | Bệnh nhân không đến khám và không báo trước. |
| Booking ID | Mã định danh lịch hẹn do hệ thống cấp. |
| STK | Stakeholder - bên liên quan. |
| FR / NFR | Functional Requirement / Non-functional Requirement - yêu cầu chức năng / yêu cầu phi chức năng. |
| SC / TC | Scenario / Test Case - tình huống sử dụng / trường hợp kiểm thử. |
| CR | Change Request - yêu cầu thay đổi. |
| TBD | To Be Determined - nội dung chưa được xác định hoặc stakeholder chưa xác nhận. |

## 4. Thu thập yêu cầu

### 4.1 Kế hoạch

Nhóm lựa chọn **02 kỹ thuật chính** để thu thập thông tin một cách toàn diện và chính xác:
+ Phỏng vấn bán cấu trúc: Là phương pháp phỏng vấn kết hợp giữa sự linh hoạt và tính định hướng. Người phỏng vấn chuẩn bị trước một bộ câu hỏi mở hoặc danh sách các chủ đề chính, nhưng không bắt buộc phải tuân theo thứ tự hay kịch bản cứng nhắc.
+ Phân tích tình huống & qui trình: Là phương pháp làm việc nhóm hoặc quan sát để mổ xẻ, vẽ lại và đánh giá các bước thực hiện một công việc thực tế, bao gồm cả luồng xử lý chuẩn và các trường hợp ngoại lệ.

| Kỹ thuật | Đối tượng | Thời lượng | Vai trò | Ghi nhận |
|---|---|---|---|---|
| Phỏng vấn bán cấu trúc | Quản lý (1 người), bác sĩ đại diện (2 người), nhân viên tiếp nhận (2 người) | 30-45 phút / buổi | 1 thành viên phỏng vấn; 1 thành viên ghi biên bản | Biên bản phỏng vấn (Ghi âm nếu được phép) tổng hợp các câu trả lời và được gửi lại cho người được phỏng vấn xác nhận trong vòng 24 giờ |
| Phân tích tình huống / quy trình | Nhóm, nhân viên tiếp nhận và quản lý phòng khám | 2 buổi, 60 phút/buổi | 1 thành viên chủ trì rà soát ngoại lệ; 1 thành viên mô hình hóa | Bảng ma trận luồng công việc và tài liệu mô tả hiện trạng |

### 4.2 Bộ câu hỏi

**Câu hỏi mở:**

1. Q-OPEN-01: Anh/Chị hãy mô tả chi tiết quy trình từng bước từ lúc bệnh nhân gọi điện đến phòng khám cho đến khi lịch hẹn được ghi nhận thành công vào sổ?
2. Q-OPEN-02:  Phòng khám hiện đang xử lý việc phân chia khung giờ  khám cho các bác sĩ thuộc các chuyên khoa khác nhau như thế nào?
3. Q-OPEN-03: Khi một bệnh nhân đến trễ so với giờ hẹn hoặc no-show, nhân viên tiếp nhận đang xử lý tình huống này theo quy trình nào?
4. Q-OPEN-04: Trong trường hợp có bệnh nhân cấp cứu hoặc cần khám gấp, phòng khám sắp xếp chen ngang lịch khám đã đặt trước như thế nào?
5. Q-OPEN-05: Khi bác sĩ xin nghỉ đột xuất hoặc có lịch tác chiến khẩn cấp, quy trình thông báo và điều chuyển lịch khám của các bệnh nhân trong ngày hôm đó diễn ra như thế nào?
6. Q-OPEN-06: Bác sĩ muốn xem danh sách bệnh nhân đăng ký trong ca dưới dạng nào (xem danh sách tĩnh đầu ca hay cập nhật thời gian thực trên ứng dụng)?
7. Q-OPEN-07: Ban quản lý phòng khám muốn hệ thống xuất các loại báo cáo thống kê nào hàng tuần/hàng tháng (số lượt khám, tỷ lệ vắng mặt, doanh thu, thời gian chờ)?

**Câu hỏi đóng:**

1. Q-CLOSED-01: Khoảng thời gian chuẩn dành cho một khung giờ khám của bác sĩ là bao nhiêu phút (15, 20 hay 30 phút)?
2. Q-CLOSED-02: Phòng khám có quy định giới hạn số lượng bệnh nhân tối đa mà một bác sĩ tiếp nhận trong một ca làm việc hay không (Có / Không)?
3. Q-CLOSED-03: Bệnh nhân đến trễ quá bao nhiêu phút thì lịch hẹn sẽ tự động bị hủy hoặc chuyển thành lượt khám đợi (Walk-in)?
4. Q-CLOSED-04: Bệnh nhân có được phép tự thay đổi hoặc hủy lịch hẹn trước thời điểm khám 2 tiếng không (Có / Không)?
5. Q-CLOSED-05: Hệ thống có cần tự động gửi tin nhắn SMS/Zalo thông báo hủy/dời lịch cho bệnh nhân ngay khi bác sĩ báo nghỉ không (Có / Không)?

**Câu hỏi ngoại lệ và phi chức năng:**

1. Q-EXCEPT-01: Nhân viên tiếp nhận có quyền chỉnh sửa thông tin hành chính (họ tên, ngày sinh, SĐT) do bệnh nhân tự khai báo trực tuyến hay không, và lịch sử sửa đổi có cần lưu lại không?
2. Q-EXCEPT-02: Nếu bệnh nhân đặt lịch trùng cho 2 bác sĩ thuộc 2 chuyên khoa khác nhau trong cùng một khung giờ, hệ thống sẽ cảnh báo hay chặn hoàn toàn?
3. Q-EXCEPT-03: Trong trường hợp phòng khám bị mất kết nối Internet, nhân viên tiếp nhận cần một giải pháp dự phòng như thế nào để không làm gián đoạn tiếp nhận?
4. Q-EXCEPT-04: Dữ liệu lịch hẹn và thông tin bệnh nhân cần phải được lưu trữ lịch sử tối thiểu trong bao lâu để phục vụ tra cứu?
5. Q-EXCEPT-05: Hệ thống cần đáp ứng khả năng chịu tải bao nhiêu lượt truy cập đồng thời trong các khung giờ cao điểm?

## 5. Giả định và vấn đề cần xác nhận

- **A-01:** Mốc hủy / đổi trước 2 giờ xuất hiện trong câu hỏi khảo sát và scenario, nhưng chưa có biên bản trả lời stakeholder. Bản này tạm mô tả “từ 2 giờ trở lên được phép”; cần xác nhận, đặc biệt tại đúng ranh giới 2 giờ.
- **A-02:** Độ dài slot 15-30 phút là ví dụ trong glossary, chưa phải chính sách đã duyệt.
- **A-03:** Chưa xác nhận kênh thông báo; SMS/Email/Zalo chỉ là lựa chọn trong tài liệu khảo sát, không được mặc định là cấu hình cuối.
- **A-04:** Quy tắc NFR-01 “dưới 3 lần click” chưa định nghĩa cách đếm, thiết bị và phạm vi thao tác.
- **A-05:** Chu kỳ đo uptime 99%, tải đo NFR-02 và thời hạn hoàn tiền CR-01 chưa được thống nhất.
- **A-06:** Nhà cung cấp/cơ chế thanh toán, video, thông báo và chính sách bảo mật cần được lựa chọn, thẩm định.
- **Q-OPEN:** Chưa có câu trả lời khảo sát, biên bản phỏng vấn, thời gian lưu dữ liệu, quy tắc đến trễ / no-show, no internet, tải đồng thời hoặc quyền sửa hồ sơ. Các nội dung này không được xem là quyết định nghiệp vụ đã chốt.

## 6. Đặc tả scenario

### SC-01: Bệnh nhân đặt lịch khám trực tiếp thành công

- **Tác nhân chính:** Bệnh nhân.
- **Tiền điều kiện:** Bệnh nhân đăng nhập; hệ thống có slot khả dụng.
- **Kích hoạt:** Bệnh nhân chọn “Đặt lịch khám”.
- **Luồng chính:**  
  1) Chọn chuyên khoa / bác sĩ.  
  2) Hệ thống hiển thị slot.  
  3) Bệnh nhân chọn ngày / slot.  
  4) Xác nhận thông tin người khám.  
  5) Bệnh nhân điền / kiểm tra thông tin và nhấn "Xác nhận đặt lịch".  
  6) Hệ thống kiểm tra tính khả dụng của slot, ghi nhận thông tin đặt lịch vào cơ sở dữ liệu và đánh dấu slot đó đã được giữ chỗ.  
  7) Hệ thống hiển thị thông báo đặt lịch thành công kèm Booking ID.  
  8) Hệ thống gửi tin nhắn SMS / Email xác nhận lịch hẹn đến số điện thoại / email của bệnh nhân.
- **Luồng thay thế / Ngoại lệ:**
  - **4a. Bệnh nhân đăng ký cho người thân:**
    - Tại bước 4, bệnh nhân chọn tùy chọn "Đặt lịch cho người thân".
    - Bệnh nhân nhập thông tin hành chính của người thân.
    - Hệ thống lưu thông tin người khám kèm liên kết với tài khoản đặt lịch và tiếp tục bước 5.
  - **6a. Thông tin khai báo chưa hợp lệ:**
    - Tại bước 6, nếu SĐT hoặc các trường thông tin bắt buộc bị bỏ trống/sai định dạng.
    - Hệ thống hiển thị thông báo lỗi chi tiết tại trường bị sai và yêu cầu bệnh nhân nhập lại (Quay lại bước 5).
- **Hậu điều kiện:**
  - **Thành công:** Lịch hẹn được lưu vào hệ thống với trạng thái `Đã xác nhận`. Số lượng slot trống của bác sĩ trong khung giờ đó giảm đi 1.
  - **Thất bại:** Hệ thống giữ nguyên trạng thái cũ, không lưu thông tin đặt lịch dở dang.

### SC-02: Khung giờ hoặc bác sĩ không còn khả dụng

- **Tác nhân chính:** Bệnh nhân.
- **Tiền điều kiện:** Bệnh nhân đang chọn slot còn hiển thị.
- **Kích hoạt:** Bệnh nhân xác nhận đặt lịch.
- **Luồng chính:**  
  1) Bệnh nhân nhấn nút "Xác nhận đặt lịch".  
  2) Hệ thống tiến hành khóa giao dịch và kiểm tra lại trạng thái của khung giờ trong cơ sở dữ liệu.  
  3) Hệ thống phát hiện khung giờ đã bị bệnh nhân khác đặt thành công trước đó vài giây / bác sĩ vừa cập nhật lịch nghỉ.  
  4) Hệ thống từ chối ghi nhận lịch hẹn mới, thông báo slot không còn khả dụng và làm mới danh sách.  
  5) Bệnh nhân chọn một khung giờ khả dụng khác và tiếp tục quy trình đặt lịch.
- **Luồng thay thế / Ngoại lệ:**
  - **6a. Tất cả khung giờ trong ngày của bác sĩ đó đã kín chỗ:**
    - Hệ thống gợi ý cho bệnh nhân chọn ngày tiếp theo còn trống của bác sĩ đó hoặc gợi ý bác sĩ khác cùng chuyên khoa.
  - **7a. Bệnh nhân hủy thao tác:**
    - Bệnh nhân không muốn chọn giờ khác và nhấn "Hủy bỏ", hệ thống quay về màn hình trang chủ.

- **Hậu điều kiện:**
  - **Thành công:** Bệnh nhân chuyển sang chọn slot mới thành công mà không bị ghi nhận dữ liệu trùng lặp (Overbooking).
  - **Thất bại:** Hệ thống báo lỗi rõ ràng, không lưu bất kỳ giao dịch hỏng nào.

### SC-03: Bệnh nhân đổi hoặc hủy lịch

- **Tác nhân chính:** Bệnh nhân.
- **Tiền điều kiện:** Bệnh nhân đăng nhập và có lịch xác nhận.
- **Kích hoạt:** Chọn “Đổi lịch” hoặc “Hủy lịch” trong danh sách lịch hẹn.
- **Luồng chính - Hủy:**  
  1) Bệnh nhân chọn lịch hẹn cần hủy và nhấn "Hủy lịch".  
  2) Hệ thống kiểm tra điều kiện thời gian hủy (Phải trước thời điểm khám tối thiểu 02 tiếng theo quy định).  
  3) Hệ thống hiển thị cửa sổ xác nhận hủy lịch kèm lý do hủy mà người dùng chọn từ danh sách hoặc nhập lý do.  
  4) Bệnh nhân chọn lý do và nhấn "Đồng ý hủy".  
  5) Hệ thống chuyển trạng thái lịch hẹn thành `Đã hủy` và cộng lại 01 slot trống cho khung giờ tương ứng của bác sĩ.  
  6) Hệ thống thông báo hủy thành công và gửi SMS / Email xác nhận hủy lịch.
- **Luồng thay thế - Kịch bản Đổi lịch:**
  - **1a. Bệnh nhân chọn "Đổi lịch":**
    - Hệ thống kiểm tra điều kiện thời gian dời lịch (trước thời điểm khám tối thiểu 02 tiếng).
    - Hệ thống hiển thị lịch làm việc khả dụng mới của bác sĩ.
    - Bệnh nhân chọn ngày và khung giờ mới.
    - Bệnh nhân xác nhận thay đổi.
    - Hệ thống giải phóng slot cũ, ghi nhận slot mới và cập nhật trạng thái lịch hẹn.
    - Hệ thống gửi SMS/Email thông báo lịch hẹn mới.

- **Luồng ngoại lệ (Exception Flows):**
  - **2a. Hủy/Đổi lịch sát giờ khám (Dưới 02 tiếng):**
    - Tại bước 2, hệ thống phát hiện thời gian còn lại đến giờ khám ít hơn 02 tiếng.
    - Hệ thống từ chối thao tác tự động, hiển thị thông báo: *"Không thể tự đổi/hủy lịch trước giờ khám 2 tiếng. Vui lòng liên hệ hotline phòng khám để được hỗ trợ."*

- **Hậu điều kiện:**
  - **Thành công:** Trạng thái lịch hẹn được cập nhật chính xác thành `Đã hủy` hoặc thời gian mới. Slot cũ được giải phóng để người khác đăng ký.
  - **Thất bại:** Lịch hẹn giữ nguyên trạng thái ban đầu.

### SC-04: Bác sĩ nghỉ đột xuất và xử lý lịch bị ảnh hưởng

- **Tác nhân chính:** Nhân viên tiếp nhận / quản lý.
- **Tiền điều kiện:** Có lịch bệnh nhân trong ca bác sĩ nghỉ.
- **Kích hoạt:** Nhân viên chọn chức năng báo nghỉ đột xuất.
- **Luồng chính:**  
  1) Chọn bác sĩ, ngày, ca và lý do.  
  2) Hệ thống liệt kê lịch / slot bị ảnh hưởng.  
  3) Nhân viên xác nhận phương án hủy lịch bị ảnh hưởng và gửi hướng dẫn đặt lại.  
  4) Hệ thống khóa slot mới, chuyển các lịch bị ảnh hưởng sang trạng thái hủy do bác sĩ nghỉ.  
  5) Hệ thống gửi thông báo qua kênh cấu hình, kèm đường dẫn ưu tiên chọn lịch mới hoặc bác sĩ khác, rồi tổng hợp kết quả.
- **Luồng thay thế / Ngoại lệ:**
  - **7a. Gửi tin nhắn thông báo thất bại (Lỗi cổng SMS/Mạng):**
    - Hệ thống đánh dấu trạng thái `Gửi thông báo thất bại` đối với các bệnh nhân không nhận được tin.
    - Hệ thống tạo danh sách công việc đề xuất nhân viên tiếp nhận thực hiện cuộc gọi trực tiếp cho các bệnh nhân này.

- **Hậu điều kiện (Post-conditions):**
  - **Thành công:** Toàn bộ lịch hẹn bị ảnh hưởng được hủy an toàn, không cho phép đăng ký mới vào ca nghỉ. Bệnh nhân nhận được thông báo hướng dẫn dời lịch.
  - **Thất bại:** Hệ thống cảnh báo sự cố, giữ nguyên trạng thái lịch hẹn để nhân viên xử lý thủ công.

### SC-05: Bệnh nhân đặt khám trực tuyến trả trước

- **Tác nhân chính:** Bệnh nhân. 
- **Tác nhân phụ:** Cổng thanh toán, bác sĩ.
- **Tiền điều kiện:** Dịch vụ khám trực tuyến và slot được mở; bệnh nhân có tài khoản; tích hợp thanh toán khả dụng.
- **Kích hoạt:** Bệnh nhân chọn loại lịch khám trực tuyến.
- **Luồng chính:**  
  1) Bệnh nhân chọn bác sĩ, slot và xác nhận thông tin.  
  2) Hệ thống khởi tạo thanh toán cho lịch.  
  3) Cổng thanh toán trả kết quả thành công.  
  4) Hệ thống ghi nhận giao dịch và xác nhận lịch.  
  5) Hệ thống cấp link video gắn với lịch và gửi thông báo.
- **Ngoại lệ:** Thanh toán bị từ chối / hết thời gian thì không xác nhận lịch và không cấp link. Nếu thanh toán thành công nhưng hệ thống chưa ghi được lịch, giao dịch phải được đối soát và xử lý theo quy tắc được phê duyệt; không yêu cầu bệnh nhân thanh toán lặp lại một cách mù quáng. Nếu bác sĩ hủy, hệ thống chuyển lịch sang trạng thái hủy, khởi tạo hoàn tiền theo giao dịch gốc và thông báo bệnh nhân.
- **Hậu điều kiện:** 
  - **Thành công:** Có lịch, giao dịch và link liên kết.  
  - **Hủy bởi bác sĩ:** Có yêu cầu hoàn tiền và trạng thái tra cứu được. Trạng thái trung gian, thời hạn hoàn tiền, chống giao dịch trùng và bảo vệ link cần stakeholder xác nhận.

### SC-06: Lễ tân tiếp nhận và bác sĩ theo dõi lịch trong ngày

- **Tác nhân chính:** Nhân viên tiếp nhận.
- **Tác nhân phụ:** Bác sĩ, quản lý.
- **Tiền điều kiện:** Có tài khoản đúng vai trò và lịch trong ngày.
- **Kích hoạt:** Bệnh nhân đến phòng khám hoặc nhân viên mở danh sách lịch.
- **Luồng chính:**  
  1) Lễ tân tra cứu/tạo hồ sơ bệnh nhân và cập nhật thông tin được phép.  
  2) Lễ tân đánh dấu lịch “Đã đến” hoặc “Vắng mặt”.  
  3) Bác sĩ xem danh sách bệnh nhân trong ngày.  
  4) Quản lý xuất báo cáo theo ngày/tuần/tháng.
- **Ngoại lệ:** Người dùng không đủ quyền bị từ chối, quy tắc lưu lịch sử sửa hồ sơ và định nghĩa tỷ lệ vắng mặt cần xác nhận.
- **Hậu điều kiện:** Hồ sơ, trạng thái lịch và số liệu báo cáo phản ánh cùng dữ liệu nguồn.

### SC-07: Lễ tân chèn ca khám khẩn

- **Tác nhân chính:** Nhân viên tiếp nhận.
- **Tác nhân phụ:** Bác sĩ.
- **Tiền điều kiện:** Bác sĩ có lịch làm việc; nhân viên tiếp nhận có quyền quản lý lịch.
- **Kích hoạt:** Nhân viên tiếp nhận chọn chức năng chèn ca khám khẩn.
- **Luồng chính:**  
  1) Nhân viên chọn bác sĩ, thời gian và thông tin lượt khám khẩn.  
  2) Hệ thống kiểm tra lịch hiện tại và hiển thị xung đột nếu có.  
  3) Nhân viên xác nhận chèn ca.  
  4) Hệ thống ghi nhận lượt khám khẩn mà không xóa hoặc ghi đè các lịch đã xác nhận trước đó.  
  5) Hệ thống cập nhật danh sách lịch để bác sĩ và nhân viên tiếp nhận tra cứu.
- **Ngoại lệ:** Nếu thời gian bị trùng hoặc không thể chèn mà vẫn bảo toàn lịch hiện hữu, hệ thống báo xung đột và yêu cầu nhân viên chọn cách xử lý được phòng khám phê duyệt; không tự ý thay đổi lịch đã xác nhận.
- **Hậu điều kiện:** Ca khám khẩn được ghi nhận hoặc không thay đổi dữ liệu nếu thao tác thất bại; các lịch đã xác nhận trước đó vẫn được bảo toàn.

## 7. Catalogue yêu cầu

Độ ưu tiên trong bảng là **đề xuất của nhóm**: Must = cần có cho phạm vi hiện tại; Should = quan trọng nhưng có thể xếp sau; Could = có thể cân nhắc. Nguồn chỉ ra stakeholder / CR hoặc scenario gắn với nhu cầu; các tiêu chí có TBD cần được stakeholder xác nhận trước nghiệm thu.

### 7.1 Yêu cầu chức năng

| ID | Loại | Nguồn | Ưu tiên | Phiên bản | Mô tả yêu cầu | Lý do | Tiêu chí kiểm chứng |
|---|---|---|---|---|---|---|---|
| FR-01 | Chức năng | STK-PAT; SC-01 | Must | 1.0 | Hệ thống phải cho phép bệnh nhân tạo lịch mới bằng cách chọn bác sĩ và slot còn trống. | Giảm phụ thuộc đặt lịch qua điện thoại/sổ. | Với slot hợp lệ, hệ thống lưu một lịch, trả Booking ID và không ghi lịch nếu xác nhận thất bại. |
| FR-02 | Chức năng | STK-PAT; Q-CLOSED-04; SC-03; A-01 | Must | 1.0 | Hệ thống phải cho phép bệnh nhân tự hủy lịch khi còn từ 2 giờ trở lên trước giờ khám; dưới 2 giờ phải từ chối thao tác tự phục vụ. | Giải phóng slot và áp dụng quy tắc hủy nhất quán. | Kiểm tra đúng 2 giờ và dưới 2 giờ; kết quả theo quyết định REV-02. Quy tắc biên chờ stakeholder xác nhận. |
| FR-03 | Chức năng | STK-PAT, STK-REC; SC-01, SC-02 | Must | 1.0 | Hệ thống phải hiển thị các slot khả dụng của từng bác sĩ và cập nhật tính khả dụng trước khi ghi lịch. | Tránh đặt vào slot đã kín hoặc bác sĩ đã nghỉ. | Slot đã được giữ / đặt không thể được xác nhận lần thứ hai; danh sách sau lỗi được làm mới. |
| FR-04 | Chức năng | STK-DOC; hiện trạng; SC-06 | Must | 1.0 | Hệ thống phải cho phép bác sĩ xem danh sách bệnh nhân có lịch trong ngày. | Giúp bác sĩ chuẩn bị ca khám. | Tài khoản bác sĩ được phân quyền xem đúng lịch theo ngày / bác sĩ; dữ liệu khớp lịch đã xác nhận. |
| FR-05 | Chức năng | STK-REC; SC-06 | Must | 1.0 | Hệ thống phải cho phép nhân viên tiếp nhận cập nhật trạng thái “Đã đến” hoặc “Vắng mặt”. | Thay sổ giấy và hỗ trợ theo dõi lượt khám thực tế. | Lễ tân cập nhật được hai trạng thái; thay đổi hiển thị nhất quán trong danh sách / báo cáo. |
| FR-06 | Chức năng | STK-PAT, STK-REC; SC-01 | Must | 1.0 | Hệ thống phải gửi thông báo xác nhận sau khi lịch được ghi nhận thành công. | Giúp bệnh nhân và phòng khám nắm trạng thái lịch. | Gửi kết quả kèm lịch; bên thứ ba, thời điểm, gửi lại và xử lý gửi trùng là TBD theo REV-03. |
| FR-07 | Chức năng | STK-REC; Q-EXCEPT-01; SC-06 | Must | 1.0 | Hệ thống phải cho phép lễ tân tạo và cập nhật hồ sơ thông tin cá nhân bệnh nhân. | Hỗ trợ tiếp nhận bệnh nhân mới và cập nhật thông tin. | Lễ tân tạo / sửa được các trường được phép; trường, quyền sửa và lịch sử thay đổi cần stakeholder xác nhận. |
| FR-08 | Chức năng | STK-MGR; Q-OPEN-07; SC-06 | Should | 1.0 | Hệ thống phải cho phép quản lý xuất báo cáo lượt đặt, lượt khám thực tế và tỷ lệ vắng mặt theo ngày, tuần, tháng. | Hỗ trợ theo dõi hoạt động phòng khám. | Với dữ liệu kiểm thử đã biết, báo cáo đúng kỳ và số liệu; định nghĩa mẫu số tỷ lệ vắng mặt cần xác nhận. |
| FR-09 | Chức năng | STK-MNG, STK-DOC, STK-REC; SC-04 | Must | 1.0 | Hệ thống phải cho phép quản lý hoặc bác sĩ cập nhật lịch nghỉ định kỳ / đột xuất và khóa slot tương ứng. | Ngăn đặt mới vào thời gian bác sĩ không làm việc. | Slot bị khóa không thể đặt mới; lịch đã có được đưa vào danh sách xử lý và không tự mất dữ liệu. |
| FR-10 | Chức năng | STK-REC; Q-OPEN-04; SC-07 | Should | 1.0 | Hệ thống phải cho phép lễ tân chèn ca khám khẩn mà không xóa / ghi đè lịch đã xác nhận trước đó. | Hỗ trợ ngoại lệ khám gấp mà giữ tính toàn vẹn lịch. | Chèn ca khẩn thành công; các lịch trước đó vẫn tồn tại và không bị sửa ngoài chủ ý. Cách xử lý xung đột thời gian cần xác nhận. |
| FR-11 | Chức năng | CR-01; STK-PAT | Must | 1.1 | Với khám trực tuyến, hệ thống phải tích hợp thanh toán và chỉ xác nhận lịch sau khi nhận kết quả thanh toán thành công. | Điều kiện nghiệp vụ bắt buộc của dịch vụ khám online. | Thanh toán bị từ chối không tạo lịch xác nhận / link; thành công có giao dịch liên kết với lịch. Quy tắc đối soát / lỗi cần chốt. |
| FR-12 | Chức năng | CR-01; STK-PAT, STK-DOC | Must | 1.1 | Sau khi lịch khám trực tuyến được xác nhận, hệ thống phải cấp link gọi video cho lịch đó. | Cho phép hai bên tham gia buổi khám từ xa. | Link chỉ được cấp sau khi lịch online được xác nhận; thời hạn, xác thực và quyền truy cập thuộc TBD. |
| FR-13 | Chức năng | CR-01; STK-PAT | Must | 1.1 | Khi bác sĩ hủy lịch khám trực tuyến, hệ thống phải khởi tạo hoàn tiền và thông báo bệnh nhân. | Thực hiện cam kết của CR-01 và tránh bệnh nhân mất phí. | Có yêu cầu hoàn tiền tham chiếu giao dịch gốc và thông báo; thời hạn, lỗi hoàn tiền và chống hoàn trùng thuộc TBD. |

### 7.2 Yêu cầu phi chức năng

| ID / nhóm | Loại | Nguồn | Ưu tiên | Phiên bản | Mô tả yêu cầu | Lý do | Tiêu chí kiểm chứng |
|---|---|---|---|---|---|---|---|
| NFR-01 / Product - Usability | Phi chức năng | STK-PAT | Should | 1.0 | Quy trình đặt lịch phải thân thiện; nguồn đặt mục tiêu hoàn thành dưới 3 lần click. | Giảm ma sát khi bệnh nhân đặt lịch. | Ghi nhận số thao tác trên một quy trình và thiết bị đã thống nhất; phạm vi đếm/ngưỡng chính xác thuộc TBD (REV-01). |
| NFR-02 / Product - Performance | Phi chức năng | STK-PAT, STK-REC | Must | 1.0 | Dữ liệu slot trống phải tải không quá 2 giây. | Cần phản hồi nhanh khi chọn lịch. | Đo từ yêu cầu tải đến lúc slot hiển thị; tải đồng thời, dữ liệu và môi trường đo thuộc TBD (REV-04). |
| NFR-03 / Product - Reliability | Phi chức năng | STK-MGR, STK-REC | Should | 1.0 | Ứng dụng phải hoạt động ổn định 99% thời gian. | Hạn chế gián đoạn đặt và tiếp nhận lịch. | Theo dõi availability; chu kỳ tính, quy tắc downtime / bảo trì thuộc TBD (REV-05). |
| NFR-04 / External - Privacy | Phi chức năng | STK-PAT; CR-01 | Must | 1.1 | Dữ liệu bệnh nhân phải được bảo vệ bằng mã hóa để hạn chế rò rỉ. | Hồ sơ và nội dung khám là dữ liệu nhạy cảm. | Kiểm tra mã hóa/phân quyền theo phạm vi được duyệt; dữ liệu, khi truyền/lưu trữ, nhật ký và cách thử thuộc TBD (REV-06). |
| NFR-05 / Process - Delivery | Phi chức năng | STK-MGR | Should | 1.0 | Chức năng cốt lõi phải được bàn giao trước hạn 1 tháng để nhân viên dùng thử. | Cần thời gian thử nghiệm trước vận hành. | Đối chiếu biên bản bàn giao với mốc dự án đã chốt; ngày bắt đầu và định nghĩa “chức năng cốt lõi” thuộc TBD. |
| NFR-06 / External - Interoperability | Phi chức năng | STK-PAT, STK-REC | Should | 1.0 | Hệ thống phải dùng được trên trình duyệt máy tính và di động. | Phục vụ bệnh nhân và nhân viên trên các thiết bị khác nhau. | Chạy bộ kiểm tra trên ma trận trình duyệt / phiên bản / thiết bị do stakeholder phê duyệt; ma trận hiện thuộc TBD. |

## 8. Thay đổi đến CR-01

### 8.1 Nội dung và tác động

Phòng khám bắt đầu cung cấp khám trực tuyến. Bệnh nhân phải thanh toán trước để xác nhận lịch; nếu bác sĩ hủy, hệ thống hoàn tiền và thông báo bệnh nhân. Thay đổi bổ sung FR-11, FR-12, FR-13 và SC-05; ảnh hưởng FR-01, FR-03, FR-06, trạng thái lịch, luồng thanh toán, link video, thông báo và các tiêu chí NFR-04, NFR-06. Dữ liệu cần truy vết gồm loại hình / trạng thái lịch, mã và trạng thái giao dịch thanh toán / hoàn tiền, thông tin truy cập link video và kết quả gửi thông báo. Cần liên kết giao dịch thanh toán / hoàn tiền với lịch; trường dữ liệu và thời hạn lưu cần được phê duyệt.

### 8.2 Rủi ro và câu hỏi mới

1. Cổng thanh toán báo thành công nhưng lịch không được ghi nhận, hoặc callback bị gửi lặp: cần quy tắc đối soát, chống xử lý trùng và xử lý giao dịch không khớp.
2. Bác sĩ hủy nhưng hoàn tiền lỗi / chậm: cần xác định trạng thái trung gian, thời hạn xử lý, người chịu trách nhiệm và thông báo bệnh nhân.
3. Link gọi video bị chia sẻ hoặc truy cập sai người: cần chốt xác thực, thời hạn hiệu lực và quyền truy cập; đánh giá bảo mật dữ liệu cuộc khám.
4. Bệnh nhân không dùng được công cụ gọi video: cần xác định hướng dẫn / hỗ trợ kỹ thuật và phương án thay thế.
5. Cần làm rõ hủy / đổi do bệnh nhân, hoàn tiền một phần / toàn phần, phí dịch vụ, nhà cung cấp cổng thanh toán và cách đối soát.

## 9. Test cases và cách kiểm chứng

Các test case dưới đây kiểm chứng những luồng đã mô tả; các ngưỡng/điều kiện đang TBD chỉ được nghiệm thu sau khi stakeholder xác nhận.

| ID | Phạm vi | Tiền điều kiện / dữ liệu | Các bước chính | Kết quả mong đợi |
|---|---|---|---|---|
| TC-01 | Đặt lịch trực tiếp; FR-01, FR-03, NFR-01, NFR-02, NFR-06 | Bệnh nhân đăng nhập, có slot trống; dùng thiết bị/trình duyệt trong ma trận được duyệt. | Chọn chuyên khoa, bác sĩ, ngày và slot; xác nhận đặt lịch. Thử lại với slot vừa được đặt bởi tài khoản khác. | Lần đầu tạo đúng một lịch và trả Booking ID; lần đặt trùng bị từ chối, danh sách slot được làm mới. Ghi nhận thời gian tải và số thao tác theo cách đo đã được duyệt; kiểm tra trên ma trận thiết bị / trình duyệt được duyệt. |
| TC-02 | Đổi / hủy lịch; FR-02 | Có lịch xác nhận; đồng hồ kiểm thử cho phép điều khiển thời điểm đến khám. | Thử hủy / đổi tại đúng mốc 2 giờ, dưới 2 giờ và trên 2 giờ; thử lỗi khi cập nhật. | Kết quả tại mốc 2 giờ theo quyết định stakeholder; dưới 2 giờ bị từ chối tự phục vụ; thao tác thất bại không đổi lịch / slot. Khi thành công, trạng thái và slot được cập nhật đúng một lần. |
| TC-03 | Tiếp nhận,  danh sách bệnh nhân có lịch khám trong ngày mà bác sĩ xem, báo cáo và quyền truy cập; FR-04, FR-05, FR-07, FR-08, NFR-04, NFR-06 | Có tài khoản bệnh nhân, lễ tân, bác sĩ và quản lý; có dữ liệu lịch mẫu. | Lễ tân tạo / cập nhật hồ sơ và trạng thái đến / vắng mặt; bác sĩ xem lịch; quản lý xuất báo cáo; thử truy cập trái quyền và kiểm tra bảo vệ dữ liệu theo tiêu chí đã duyệt. | Mỗi vai trò chỉ thực hiện được thao tác được cấp quyền; lịch, hồ sơ và báo cáo nhất quán với dữ liệu nguồn. Quyền sửa, lịch sử thay đổi, định nghĩa báo cáo và tiêu chí bảo mật phải được xác nhận trước nghiệm thu. |
| TC-04 | Thông báo xác nhận; FR-06 | Có lịch hợp lệ và kênh thông báo bên thứ ba được cấu hình. | Tạo lịch thành công; mô phỏng gửi thông báo thành công và lỗi. | Có kết quả gửi gắn với lịch; lỗi gửi được ghi nhận và xử lý theo chính sách gửi lại / kênh đã được duyệt, không làm lịch thành công bị mất. |
| TC-05 | Bác sĩ nghỉ đột xuất; FR-09 | Có lịch đã đặt và slot trống trong ca bác sĩ nghỉ. | Ghi nhận ca nghỉ; xác nhận xử lý lịch bị ảnh hưởng; mô phỏng lỗi gửi thông báo hoặc lỗi cập nhật lịch. | Slot nghỉ bị khóa; lịch đã có được xử lý theo xác nhận, không mất dữ liệu âm thầm; lỗi thông báo tạo danh sách gọi thủ công, lỗi cập nhật giữ lịch để xử lý. |
| TC-06 | Khám trực tuyến trả trước; FR-11, FR-12, FR-13, NFR-04, NFR-06 | Có slot online, tích hợp thanh toán / video ở môi trường kiểm thử và cấu hình thiết bị được duyệt. | Thử thanh toán thành công, bị từ chối / hết hạn, callback lặp, lỗi ghi lịch sau thanh toán và bác sĩ hủy lịch. | Chỉ thanh toán thành công mới xác nhận lịch / cấp link; giao dịch được liên kết với lịch, xử lý lỗi / đối soát không yêu cầu thanh toán lặp mù quáng; bác sĩ hủy tạo yêu cầu hoàn tiền theo giao dịch gốc và thông báo. Kiểm tra bảo vệ link theo tiêu chí đã duyệt. |
| TC-07 | Chèn ca khám khẩn; FR-10 | Có lịch đã xác nhận của bác sĩ và tài khoản lễ tân đủ quyền. | Chèn một ca khẩn không xung đột; tiếp tục thử tình huống xung đột thời gian và lỗi lưu. | Ca khẩn được ghi nhận khi hợp lệ; mọi lịch đã xác nhận trước đó được giữ nguyên. Khi xung đột / lỗi, hệ thống báo rõ và không tự ý sửa hoặc xóa lịch cũ. |

- NFR-03 được kiểm chứng bằng theo dõi availability theo chu kỳ và quy tắc downtime do stakeholder xác nhận.
- NFR-05 được kiểm chứng bằng đối chiếu biên bản bàn giao với mốc dự án đã duyệt.

## 10. Validation

| ID | Phát hiện | Quyết định |
|---|---|---|
| REV-01 | NFR-01 chưa định nghĩa cách đếm “click”. | Giữ ngưỡng nguồn; để cách đo TBD, chờ stakeholder. |
| REV-02 | FR-02 và SC-03 có thể hiểu khác nhau ở ranh giới 2 giờ. | Chuẩn hóa tạm thành từ 2 giờ trở lên; xác nhận với stakeholder. |
| REV-03 | FR-06/SC-01 chưa thống nhất kênh và lỗi gửi tin. | Dùng kênh cấu hình; retry/kênh bắt buộc TBD. |
| REV-04 | NFR-02 thiếu điều kiện đo. | Giữ ngưỡng 2 giây; tải và môi trường đo TBD. |
| REV-05 | NFR-03 thiếu chu kỳ tính uptime. | Giữ mục tiêu 99%; quy tắc downtime TBD. |
| REV-06 | NFR-04 chưa nêu phạm vi bảo vệ dữ liệu. | Giữ yêu cầu; chờ chốt mã hóa, phân quyền và cách kiểm thử. |
| REV-07 | CR-01 thiếu scenario và các nhánh thanh toán / hoàn tiền; SC-01 chưa phân biệt lịch online. | Thêm SC-05; trạng thái trung gian và quy tắc giao dịch TBD. |
| REV-08 | Catalogue thiếu nguồn, ưu tiên, lý do, tiêu chí kiểm chứng. | Bổ sung các trường trong mục 7; ưu tiên đề xuất cần duyệt. |

## 11. Ma trận truy vết

| Nhu cầu | Stakeholder | Requirement ID | Scenario | Test / cách kiểm chứng | Change Request |
|---|---|---|---|---|---|
| N-01 Đặt lịch nhanh, không phải gọi nhiều lần | STK-PAT | FR-01, FR-03, NFR-01, NFR-02 | SC-01, SC-02, SC-05 | TC-01, TC-06 | CR-01 |
| N-02 Tự đổi/hủy lịch | STK-PAT | FR-02 | SC-03 | TC-02 | — |
| N-03 Biết bệnh nhân và hồ sơ cần chuẩn bị | STK-DOC | FR-04, FR-07 | SC-06 | TC-03 | — |
| N-04 Lịch cập nhật, xử lý tiếp nhận và nghỉ đột xuất | STK-REC | FR-05, FR-06, FR-09, FR-10 | SC-04, SC-05, SC-06, SC-07 | TC-03, TC-04, TC-05, TC-07 | CR-01 |
| N-05 Theo dõi hoạt động phòng khám | STK-MGR | FR-08, NFR-05 | SC-06 | TC-03; đối chiếu mốc bàn giao NFR-05 | — |
| N-06 Bảo vệ thông tin bệnh nhân | STK-PAT, STK-MGR | NFR-04 | SC-05, SC-06 | TC-03, TC-06; tiêu chí bảo mật chờ xác nhận | CR-01 |
| N-07 Cung cấp khám trực tuyến trả trước | STK-PAT, STK-DOC | FR-11, FR-12, FR-13, NFR-04, NFR-06 | SC-05 | TC-06 | CR-01 |

### 11.1 Bảng liên kết Requirement - Test

| Requirement ID | Test scenario / phương pháp |
|---|---|
| FR-01, FR-03, NFR-01, NFR-02, NFR-06 | TC-01; NFR-06 kiểm tra bổ sung trong TC-03 và TC-06 |
| FR-02 | TC-02 |
| FR-04, FR-05, FR-07, FR-08, NFR-04, NFR-06 | TC-03 |
| FR-06 | TC-04, TC-05; thông báo trong luồng khám online: TC-06 |
| FR-09 | TC-05 |
| FR-10 | TC-07 |
| FR-11, FR-12, FR-13, NFR-04, NFR-06 | TC-06 |
| NFR-03 | Theo dõi availability trong chu kỳ stakeholder xác nhận; ngưỡng 99% chưa thể kết luận đến khi chốt cách đo. |
| NFR-05 | Đối chiếu biên bản bàn giao với mốc dự án được duyệt; đây là kiểm tra quy trình, không phải kiểm thử chức năng. |
