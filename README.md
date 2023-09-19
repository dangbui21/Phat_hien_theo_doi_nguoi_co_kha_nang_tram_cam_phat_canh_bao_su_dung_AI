# Phat_hien_theo_doi_nguoi_co_kha_nang_tram_cam_phat_canh_bao_su_dung_AI

# Link download data : https://drive.google.com/drive/folders/100QXBdffojAyhXTNJR5WsXFl8_gzPKZ4?usp=drive_link
# Link download model : https://drive.google.com/file/d/1PbobBnANK6RvBZW6XRJgpLOEsrVea_i5/view?usp=drive_link

Hướng dẫn(trong code đã comment khá chi tiết) :

1.Xây model 

Làm việc trên bộ dữ liệu Suicide_Detection.csv sử dụng LSTM đọc báo cáo để hiểu chi tiết.

2.Lấy dữ liệu

Lấy dữ liệu từ bài viết trên trang cá nhân của tất cả dối tượng có trong data/links_facebook để làm dữ liệu phân loại cho từng cá nhân sau này
Các kĩ thuật sử dụng chủ yếu thao tác trên selenium để thao tác trên trình duyệt chrome.
Dữ liệu lấy dược nằm trong data/output_data.csv

3. Chuyển data lấy được sang tiếng Anh

Do mô hình train từ dữ liệu tiếng Anh nên việc chuyển  đổi là bắt buộc.
Kĩ thuật sử dụng : sử dụng thư viện mở Translator với những model có sẵn hỗ trợ chuyển đổi tiếng Việt qua tiếng Anh trên máy cá nhân vô cùng nhanh chóng.
Dữ liệu chuyển đôi xong nằm trong data/data_da_chuyen_doi.csv.
4.Phân loại

Từ dữ liệu từ mục 3 ta phân loại cho từng bài viết , có khả năng trầm cảm gắn nhãn 1, không có thì nhãn 0 bằng cách sử dụng model đã train được phán đoán. 
Cần chỉnh ngưỡng sao cho phù hợp và khồng nhất thiết chỉ 1 ngưỡng mà có thể dùng nhiều ngưỡng để phân các cấp dộ khác nhau.
Đầu ra là data/data_da_chuyen_doi.csv đã đánh nhãn xong.

5. Theo doi đối tượng và lấy thông tin bạn bè

Từ data/data_da_chuyen_doi.csv ta truy ra những đôi tượng có nguy cơ trầm cảm.
Khi ta đã có danh sách đường link của đối tượng có nguy cơ và số lần xuất hiện bài viết có nguy cơ. Ta sẽ có thể tiến hành theo dõi đánh giá kĩ hơn các đối tượng này . 
Nghiện cứu thêm về cách tính trọng số đánh giá mức độ trầm cảm sẽ là một hướng đi tốt. ý tưởng hiện tại : dựa vào số bài viết có nguy cơ , tần suất xuất hiện của chúng,
kết hợp với dùng ngưỡng phần loại threshold của model để kết hợp tính toán. Từ đó làm căn cứ phát đi cảnh báo sau này. Để có thể làm vậy thì ta sẽ thu thập thêm dữ liệu từ bạn bè.
Kĩ thuật sử dụng chủ yếu trên selenium một vài cấu trúc dữ liệu khác áp dụng để có thể lấy được dữ liệu bạn bè cho từng dối tượng.

6. Phát cảnh báo

KHI ĐÔI TƯỢNG ĐƯỢC THEO DÕI ĐẠT ĐẾN MỘT NGUY CƠ NHẤT ĐỊNH SẼ PHÁT ĐI CẢNH BÁO.  CƠ CHẾ TÍNH TRỌNG SỐ ĐỂ PHÁT ĐI CẢNH BÁO VẪN TRONG QUÁ TRÌNH NGHIÊN CỨU. 
TUY NHIÊN TA SẼ THỰC HIỆN CHỨC NĂNG PHÁT CẢNH BÁO LUÔN ĐỂ KHI HOÀN THÀNH CƠ CHẾ TÍNH TRỌNG SỐ LÀ PHÁT ĐI ĐƯỢC NGAY
kĩ thuật sử dụng : thao tác bằng selenium để duyệt web truy cập tới messge bạn bè sau đó gửi đi cảnh báo bằng cách sử dụng thư viện pyautogui và pyperclip.

CHÚC MỌI NGƯỜI THÀNH CÔNG !!!!
