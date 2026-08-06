PHẦN 1: BÁO CÁO THỰC HÀNH AI WORKFLOW (Bằng HTML/JS)
1. Bài toán và yêu cầu:

Tên bài toán: Xây dựng Web App mini quản lý mượn/trả sách thư viện.

Yêu cầu: Có một giao diện (Form) để thủ thư nhập thông tin: Tên sinh viên, Tên sách, Ngày mượn, Ngày trả dự kiến. Khi bấm nút "Thêm", thông tin sẽ bay xuống một bảng (Table) danh sách bên dưới. Cần có tính năng cảnh báo nếu sách bị quá hạn.

2. Các bước làm việc với AI & Prompt đã sử dụng:

Bước 1: Requirement & Planning (Phân tích và thiết kế UI)

Prompt sử dụng: "Đóng vai trò là Web Developer. Tôi muốn làm một ứng dụng web tĩnh đơn giản (chỉ dùng HTML, CSS, JavaScript) để quản lý mượn trả sách thư viện. Hãy phác thảo cho tôi các thành phần cần có trên giao diện (UI) và luồng hoạt động cơ bản của trang web."

Kết quả AI tạo ra: AI chia trang web làm 2 phần: Nửa trên là Form nhập liệu (Input), nửa dưới là Bảng hiển thị (Table). AI cũng liệt kê luồng dữ liệu: Bấm Submit -> JS đọc dữ liệu -> Tạo hàng mới trong Table.

Bước 2: Design & Coding (Lập trình - Tạo khung)

Prompt sử dụng: "Hãy viết toàn bộ code HTML, CSS và JavaScript cho giao diện trên và gộp chung vào một file index.html duy nhất để tôi dễ chạy thử. Yêu cầu CSS thiết kế hiện đại, sạch sẽ. JS có hàm lấy dữ liệu từ Form và đẩy xuống Table."

Kết quả AI tạo ra: AI sinh ra một đoạn code dài (khoảng 100 dòng). Bạn chỉ cần copy toàn bộ, dán vào Notepad, lưu lại với tên index.html và mở bằng trình duyệt là thấy web chạy. (Chụp màn hình giao diện web lúc này làm minh chứng).

Bước 3: Testing (Kiểm thử - Tìm ra điểm yếu của AI)

Kịch bản test: Bạn mở web lên, không nhập bất kỳ chữ nào vào Form, cứ thế bấm nút "Thêm sách" liên tục 3 lần.

Kết quả thực tế (Minh chứng AI sai): Trang web ngớ ngẩn tạo ra 3 dòng trống trơn trong bảng. Lỗi ở đây là AI viết code tạo tính năng, nhưng quên mất logic kiểm duyệt dữ liệu (Form Validation).

Prompt sửa lỗi: "Giao diện chạy rất tốt, nhưng có lỗ hổng logic. Khi tôi để trống các ô nhập liệu và bấm Thêm, hệ thống vẫn chèn các dòng rỗng vào bảng. Hãy sửa lại mã JavaScript: Bắt buộc người dùng phải điền đủ thông tin, nếu thiếu thì hiển thị thông báo lỗi (alert) và không cho chèn vào bảng."

Kết quả: AI bổ sung thêm lệnh if (ten == "" || sach == "") { alert("Vui lòng nhập đủ thông tin!"); return; }. Code đã chặt chẽ hơn.

Bước 4: Review & Tối ưu (Nâng cấp tính năng)

Prompt sử dụng: "Code hiện tại đã bắt lỗi tốt. Bây giờ tôi muốn thêm tính năng thông minh: Trong hàm chèn dữ liệu vào bảng của JavaScript, hãy viết thêm logic lấy ngày hiện tại (Today) so sánh với 'Ngày trả dự kiến'. Nếu ngày hiện tại lớn hơn ngày trả dự kiến (tức là quá hạn), hãy đổi màu nền của dòng đó (tr) thành màu đỏ nhạt để cảnh báo thủ thư."

Kết quả: AI sử dụng đối tượng new Date() trong JS để làm toán thời gian và tự động đổi style.backgroundColor của hàng đó. Giao diện lúc này sẽ cực kỳ sinh động.

PHẦN 2: TRẢ LỜI CÂU HỎI TRỌNG TÂM CỦA GIẢNG VIÊN
1. AI hỗ trợ bạn tốt nhất ở bước nào?
AI làm xuất sắc nhất ở bước Thiết kế giao diện (Design & Coding). Việc viết mã CSS để căn chỉnh màu sắc, bo góc, tạo bảng thường mất rất nhiều thời gian gõ code thủ công (boilerplate). AI giải quyết khối lượng công việc này chỉ trong vài giây, tạo ra một giao diện đẹp mắt để lập trình viên có thể tập trung ngay vào phần logic.

2. AI đã tạo ra kết quả sai hoặc chưa phù hợp ở đâu?
AI thường gặp điểm mù ở khâu Kiểm soát tính hợp lệ của dữ liệu (Validation & Edge Cases). AI có xu hướng mặc định rằng "người dùng luôn thao tác đúng". Trong bài toán trên, mã nguồn ban đầu không hề có cơ chế phòng thủ khi người dùng nhập dữ liệu rỗng, nhập sai định dạng thời gian. Nếu áp dụng thẳng code này vào thực tế, hệ thống sẽ chứa toàn dữ liệu rác.

3. Bạn đã phải kiểm tra và chỉnh sửa kết quả của AI như thế nào?
Quá trình kiểm tra diễn ra bằng phương pháp Kiểm thử hộp đen (Black-box testing): Mình đóng vai một người dùng cố tình thao tác sai (nhấn nút khi chưa nhập liệu, nhập ngày mượn lớn hơn ngày trả). Khi phát hiện lỗi, thay vì tự sửa code, mình phản hồi lại chính xác hành vi bị lỗi đó cho AI bằng ngôn ngữ tự nhiên để AI tự động vá lỗ hổng trong hàm JavaScript.

4. Theo bạn, trong quy trình trên con người và AI nên đảm nhận vai trò gì?

Con người (Product Manager & QA): Đóng vai trò định hình bài toán, vạch ra các quy tắc nghiệp vụ (ví dụ: thế nào là quá hạn, giao diện cần tính năng gì) và đóng vai trò kiểm thử viên cực đoan để bẻ gãy code của AI, từ đó ép AI hoàn thiện.

AI (UI Designer & Junior Coder): Đóng vai trò người thợ xây. Nhận bản vẽ từ con người để chuyển hóa ý tưởng thành mã nguồn (HTML/CSS/JS) một cách nhanh chóng, giúp rút ngắn thời gian phát triển sản phẩm từ vài ngày xuống còn vài chục phút.