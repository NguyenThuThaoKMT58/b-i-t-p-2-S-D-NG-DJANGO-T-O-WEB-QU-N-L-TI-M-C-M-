# b-i-t-p-2-S-D-NG-DJANGO-T-O-WEB-QU-N-L-TI-M-C-M-

1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

   <img width="538" height="713" alt="image" src="https://github.com/user-attachments/assets/98f4ccaa-db2a-446a-84ee-81bbc9836ed5" />

   
2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:

Mariadb : chứa csdl của hệ thống này

Phpmyadmin: để soi được csdl (chỉ để xem, ko cần tạo bảng từ đây, django sẽ làm hết)

Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file

sau khi có 3 service này trong file docker-compose.yml :

run nó, cấu hình để Django nhận csdl mariadb (sửa file settings.py), cấu hình user login ban đầu, mô tả các bảng trong models.py, .... (đc phép sử dụng AI để làm)

=> KQ được trang admin, y/c đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại 
trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)

chú ý kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file.

sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!

sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain => chụp kết quả

 -------------------------------

 - Tạo thư mục project, Dockerfile cho Django, requirements.txt, docker-compose.yml, sau đó build container

   <img width="1131" height="1011" alt="image" src="https://github.com/user-attachments/assets/9109b62a-243e-4567-ab9b-08eac31e29b3" />

<img width="1095" height="547" alt="image" src="https://github.com/user-attachments/assets/9f5c3fb6-4ecf-4e6b-942b-6f7458ef6b17" />

- sửa file settings.py, cấu hình user login ban đầu, mô tả các bảng trong models.py,

  <img width="1081" height="823" alt="image" src="https://github.com/user-attachments/assets/6c2846b4-c03f-4628-9135-86c42f981b58" />

-sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!

<img width="867" height="150" alt="image" src="https://github.com/user-attachments/assets/0144d3cc-428d-4756-875e-79a0abb68e36" />


 trang liệt kê các con nợ đến hạn chưa trả

  <img width="1292" height="693" alt="image" src="https://github.com/user-attachments/assets/0d2fae74-4f22-4b44-8448-bfe47a4a272a" />

- đăng nhập trang admin

  <img width="883" height="642" alt="image" src="https://github.com/user-attachments/assets/896ece64-e504-432f-a492-3863a9c7ca07" />

  Thêm dữ liệu

  <img width="873" height="876" alt="image" src="https://github.com/user-attachments/assets/66af7562-f553-4402-8148-5ba7aab65ef2" />

- Sau khi thêm dữ liệu

  <img width="803" height="593" alt="image" src="https://github.com/user-attachments/assets/79a659c2-64f1-42ef-8775-bc86f99820c2" />

-Vào phpMyAdmin kiểm tra khóa ngoại

<img width="873" height="771" alt="image" src="https://github.com/user-attachments/assets/9e56d65a-b4c1-4e5a-b573-03841cde314d" />

- sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain : https://debt.thao04.io.vn/

  <img width="745" height="453" alt="image" src="https://github.com/user-attachments/assets/97fcee95-e470-44fe-933c-4e5deccd57de" />
