# Nghiên cứu chương trình phân tích cây cú pháp câu tiếng Anh bằng Prolog

## 1. Giới thiệu đề tài

Đề tài này tập trung nghiên cứu và xây dựng chương trình phân tích cây cú pháp cho câu văn tiếng Anh bằng ngôn ngữ lập trình Prolog. Mục tiêu của chương trình là tìm hiểu cách biểu diễn các quy tắc ngữ pháp tiếng Anh bằng các luật logic, từ đó phân tích cấu trúc của câu và xây dựng cây cú pháp tương ứng.

Trong chương trình, em sử dụng Definite Clause Grammar (DCG) để mô tả các thành phần ngữ pháp như câu, cụm danh từ, cụm động từ và các thành phần liên quan. Dựa trên những quy tắc này, chương trình có thể phân tích các câu tiếng Anh thuộc phạm vi ngữ pháp đã được xây dựng.

Bên cạnh việc phân tích cấu trúc câu, chương trình còn hướng đến việc biểu diễn cây cú pháp để người dùng dễ dàng quan sát mối quan hệ giữa các thành phần trong câu.

Thông qua đề tài, em muốn tìm hiểu rõ hơn về khả năng ứng dụng của Prolog trong xử lý ngôn ngữ tự nhiên (Natural Language Processing - NLP), đặc biệt là việc sử dụng các luật ngữ pháp để phân tích cú pháp câu tiếng Anh.

## 2. Công nghệ sử dụng

- **Ngôn ngữ lập trình:** Prolog.
- **Môi trường thực thi:** SWI-Prolog.
- **Phương pháp phân tích cú pháp:** Definite Clause Grammar (DCG).
- **Công cụ quản lý và chia sẻ mã nguồn:** GitHub.
- **Tệp mã nguồn chính:** `syntax_tree.pl`.

## 3. Chức năng chính

Chương trình được xây dựng nhằm thực hiện các chức năng sau:

- Biểu diễn các quy tắc ngữ pháp tiếng Anh bằng DCG.
- Phân tích cấu trúc câu dựa trên những quy tắc đã định nghĩa.
- Xác định mối quan hệ giữa các thành phần ngữ pháp trong câu.
- Xây dựng và hiển thị cây cú pháp bằng công cụ hỗ trợ của SWI-Prolog.
- Hỗ trợ kiểm thử các câu tiếng Anh thuộc phạm vi ngữ pháp mà chương trình đã triển khai.

**Lưu ý:** Khả năng phân tích của chương trình phụ thuộc vào các luật ngữ pháp và từ vựng đã được định nghĩa. Chương trình không mặc nhiên phân tích được tất cả các câu tiếng Anh.

## 4. Yêu cầu hệ thống

Để chạy chương trình, người dùng cần chuẩn bị:

- Máy tính có cài đặt SWI-Prolog.
- Tệp mã nguồn `syntax_tree.pl`.
- Kết nối Internet nếu tải mã nguồn trực tiếp từ GitHub.

Trang chủ SWI-Prolog: https://www.swi-prolog.org/

## 5. Hướng dẫn cài đặt và chạy chương trình

### Bước 1: Tải mã nguồn

Truy cập repository GitHub:

https://github.com/tranquangkhaiabc271-web/Resource-Pack

Mở tệp `syntax_tree.pl`, sau đó tải tệp về máy tính bằng nút Download raw file hoặc lựa chọn tải xuống phù hợp trên giao diện GitHub.

### Bước 2: Cài đặt SWI-Prolog

Truy cập trang chủ SWI-Prolog và tải phiên bản phù hợp với hệ điều hành đang sử dụng. Sau khi cài đặt, mở ứng dụng SWI-Prolog hoặc SWI-Prolog Console.

### Bước 3: Nạp chương trình

Di chuyển đến thư mục chứa tệp `syntax_tree.pl`. Trong cửa sổ SWI-Prolog, nhập lệnh:

```prolog
?- [syntax_tree].
```

Nếu tệp nằm ở thư mục khác, người dùng cần cung cấp đường dẫn chính xác đến tệp. Nếu chương trình được nạp thành công, SWI-Prolog sẽ trở về dấu nhắc nhập truy vấn.

### Bước 4: Thực hiện truy vấn

Các luật DCG trong chương trình có thể được kiểm tra bằng truy vấn phù hợp với cấu trúc đã định nghĩa.

Ví dụ, nếu chương trình có vị từ `sentence//1`, người dùng có thể thử phân tích một danh sách từ bằng lệnh:

```prolog
?- phrase(sentence(Tree), [the, cat, chases, the, mouse]).
```

Đây là ví dụ minh họa cho cách gọi DCG trong Prolog. Tên vị từ và cấu trúc dữ liệu đầu vào cần được điều chỉnh theo mã nguồn thực tế. Nếu chương trình sử dụng vị từ khác để phân tích câu hoặc hiển thị cây cú pháp, người dùng cần gọi đúng vị từ đó.

### Bước 5: Quan sát kết quả

Nếu câu đầu vào phù hợp với các luật ngữ pháp đã xây dựng, chương trình có thể trả về kết quả phân tích hoặc cây cú pháp tương ứng. Với những câu không phù hợp, truy vấn có thể thất bại.

Để quan sát cây cú pháp trực quan, người dùng cần thực hiện truy vấn theo đúng cách hiển thị được cài đặt trong chương trình và bảo đảm các thư viện cần thiết đã được nạp.

## 
