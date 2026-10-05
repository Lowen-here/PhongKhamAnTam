> Tài liệu đầu vào phiên bản 1.0, lập trước peer review. Bản chuẩn sau rà soát là `tongket.md` phiên bản 1.1; các nguồn/ưu tiên/lý do/tiêu chí kiểm chứng đã được bổ sung tại đó.

+ **Yêu cầu chức năng (FR):**
	+ FR-01:  Hệ thống cho phép bệnh nhân tạo lịch hẹn mới bằng cách chọn bác sĩ và giờ trống.
    
	- FR-02: Hệ thống cho phép bệnh nhân hủy lịch hẹn chậm nhất 2 giờ trước khi đến khám.
    
	- FR-03: Hệ thống hiển thị danh sách giờ khám trống của từng bác sĩ theo thời gian thực.
    
	- FR-04: Hệ thống cho phép bác sĩ xem danh sách bệnh nhân trong ngày.
    
	- FR-05: Hệ thống cho phép nhân viên tiếp nhận cập nhật trạng thái "Đã đến" hoặc "Vắng mặt".
    
	- FR-06: Hệ thống tự động gửi tin nhắn xác nhận lịch hẹn.
	
	- FR-07: Hệ thống cho phép nhân viên tiếp nhận tạo mới và cập nhật hồ sơ thông tin cá nhân của bệnh nhân khi họ đến khám lần đầu hoặc có thay đổi thông tin.
    
	- FR-08: Hệ thống cho phép quản lý phòng khám xuất báo cáo thống kê số lượng lượt đặt lịch, lượt khám thực tế và tỷ lệ vắng mặt theo ngày, tuần, tháng.
    
	- FR-09: Hệ thống cho phép quản lý hoặc bác sĩ cập nhật lịch nghỉ phép định kỳ hoặc đột xuất, tự động khóa các khung giờ tương ứng để chặn hệ thống nhận thêm lịch hẹn mới.
    
	- FR-10: Hệ thống cung cấp chức năng cho nhân viên tiếp nhận chèn một ca khám khẩn cấp (khám gấp) vào lịch trình hiện tại của bác sĩ mà không làm mất dữ liệu của các lịch hẹn đã được xác nhận trước đó.
	
+ **Yêu cầu phi chức năng (NFR):**
	- NFR-01 (Product - Usability): Giao diện đặt lịch phải thân thiện, bệnh nhân có thể hoàn thành việc đặt lịch dưới 3 lần click chuột.
    
	- NFR-02 (Product - Performance): Thời gian tải dữ liệu lịch trống của bác sĩ không quá 2 giây.
    
	- NFR-03 (Product - Reliability): Ứng dụng phải hoạt động ổn định 99% thời gian trong ngày.
    
	- NFR-04 (External - Privacy): Mọi dữ liệu về bệnh nhân phải được mã hóa tránh rò rỉ.
    
	- NFR-05 (Process - Delivery): Chức năng cốt lõi phải được bàn giao trước hạn 1 tháng để nhân viên dùng thử.
    
	- NFR-06 (External - Interoperability): Hệ thống phải có khả năng tương thích tốt cả trên trình duyệt máy tính lẫn di động.
+ **CR-01: Khám trực tuyến**
	- Phân tích tác động: Quy trình vận hành bị thay đổi. Bệnh nhân phải thanh toán trước.
    
	- Yêu cầu thay đổi/Bổ sung: Phải tạo thêm FR-11 (Hệ thống tích hợp cổng thanh toán trực tuyến cho khám online); FR-12 (Tự động cấp link gọi video); FR-13 (Cơ chế hoàn tiền tự động nếu bác sĩ hủy ca).
    
	- Rủi ro: Cổng thanh toán lỗi gây mất tiền nhưng lịch chưa được lên; Bệnh nhân không biết xài ứng dụng gọi video; Rủi ro bảo mật cuộc gọi y tế.