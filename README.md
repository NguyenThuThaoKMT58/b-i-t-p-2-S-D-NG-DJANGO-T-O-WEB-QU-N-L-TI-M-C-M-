# b-i-t-p-2-S-D-NG-DJANGO-T-O-WEB-QU-N-L-TI-M-C-M-

1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

   <img width="538" height="713" alt="image" src="https://github.com/user-attachments/assets/98f4ccaa-db2a-446a-84ee-81bbc9836ed5" />

   
3. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:

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

1. Tạo project, tạo thư mục django

<img width="1000" height="173" alt="image" src="https://github.com/user-attachments/assets/d0265b3a-6264-4772-a81c-035fc5afb5fb" />
  
2.Tạo file Dockerfile có nội dung như sau:

<img width="963" height="698" alt="image" src="https://github.com/user-attachments/assets/980641b9-7479-4ad3-8cf5-e02d374f7911" />

3. Tạo requirements.txt có nội dung như sau

   <img width="470" height="311" alt="image" src="https://github.com/user-attachments/assets/49174f55-0959-46bb-9b33-94aa7f0ba22c" />

4. quay lại thư mục gốc và tạo docker-compose.yml

   <img width="932" height="657" alt="image" src="https://github.com/user-attachments/assets/9b528e33-418f-44a9-9e93-90870a6b0b86" />

-image: mariadb:11

=> tải MariaDB version 11

-MYSQL_DATABASE: pawnshop_db

=> tự tạo database
   
<img width="602" height="456" alt="image" src="https://github.com/user-attachments/assets/31fbeffd-65a0-4f67-b29f-c12f7b17dc38" />

-PMA_HOST: mariadb

=> phpMyAdmin kết nối container MariaDB

<img width="593" height="497" alt="image" src="https://github.com/user-attachments/assets/b8a92ec0-9fd1-4beb-8e3f-c625b4a51d28" />

- build: ./django_app

=> build image bằng Dockerfile

- volumes:

  - ./django_app:/app

=> mount code thật vào container

=> sửa code bên ngoài là container đổi theo

5. Build container

   <img width="818" height="245" alt="image" src="https://github.com/user-attachments/assets/3df0387d-33d1-4e65-8970-f4dcdd641338" />

6.Tạo APP

<img width="1332" height="100" alt="image" src="https://github.com/user-attachments/assets/e8ebcad8-f399-481f-abc2-b6277b6cfcb2" />

7. Sửa settings.py : thay đoạn databases cũ bằng databases mới 

   <img width="891" height="751" alt="image" src="https://github.com/user-attachments/assets/cd73152f-f14e-4453-87d4-cbba023562fc" />

- installed_apps và allowed_hosts sửa thành
  
<img width="503" height="395" alt="image" src="https://github.com/user-attachments/assets/25b21647-6de0-4084-8ba3-010a1b620cf0" />

8. Tạo Model

   <img width="907" height="755" alt="image" src="https://github.com/user-attachments/assets/3aea69c8-e54e-4cdd-9262-c4ae12d7b418" />
<img width="737" height="605" alt="image" src="https://github.com/user-attachments/assets/5a9eca86-cf95-4837-863d-14373c197f89" />

9. Tạo và đăng kí admin

    <img width="1287" height="207" alt="image" src="https://github.com/user-attachments/assets/47e921f0-eb8d-4961-9a67-c821aecaa3ac" />

<img width="1027" height="442" alt="image" src="https://github.com/user-attachments/assets/2bfd87a9-fa0d-4209-b9e2-5bb5001f7621" />

truy cập http://192.168.1.203:8000/admin

_ có giao diện đăng nhập như sau :

<img width="947" height="742" alt="image" src="https://github.com/user-attachments/assets/55d1651f-7b37-4fef-9544-8af65d7bfb1f" />

- Sau khi đăng nhập :

  <img width="948" height="983" alt="image" src="https://github.com/user-attachments/assets/e8f4047b-d4b7-4655-aeb0-cd26110ab700" />

10. Sửa giao diện cho web

- Tạo file HTML trong thư mục templates xới nội dung :

  <img width="827" height="880" alt="image" src="https://github.com/user-attachments/assets/ca1a78bf-de45-4ce4-b9b9-e2a2f3ed07af" />

- Tạo file views.py

  <img width="737" height="617" alt="image" src="https://github.com/user-attachments/assets/02e01d6c-97da-4577-87ed-9b6b71062469" />
  
- urls_app

  <img width="980" height="480" alt="image" src="https://github.com/user-attachments/assets/34a934f6-be3b-46f9-a9af-9e4e2532357b" />

- urls chính

  <img width="1025" height="590" alt="image" src="https://github.com/user-attachments/assets/e40297ac-5ead-4ac1-bddb-301aeffaa26a" />

- Trang hiển thị danh sách người nợ quá hạn

  <img width="946" height="677" alt="image" src="https://github.com/user-attachments/assets/d7e42929-ab9d-4022-81f1-1c32d675de64" />


Em đang bị lỗi cloudflare tunnel , em đang tìm cách khắc phục ạ
