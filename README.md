# CSDL.ten.QLSV
## BÀI TẬP VỀ NHÀ 02 - MÔN HỆ QUẢN TRỊ CSDL của Phạm Duy Tiến Minh, MSV: K225480106048

## DEADLINE: 23H59 NGÀY 25/03/2025

## ĐIỀU KIỆN: (ĐÃ LÀM XONG BÀI 1)
1. Đã cài đặt SQL Server 2022 Dev.
2. Đã cài đặt SQL Managerment Studio bản mới nhất.
3. Đã kết nối từ SQL Managerment Studio vào SQL Server.
4. Đã có tài khoản github, biết cách tạo repository(kho lưu trữ) cho phép truy cập public.

## BÀI TOÁN:
- Tạo csdl quan hệ với tên QLSV gồm các bảng sau:
  + SinhVien(#masv,hoten,NgaySinh)
  + Lop(#maLop,tenLop)
  + GVCN(#@maLop,#@magv,#HK)
  + LopSV(#@maLop,#@maSV,ChucVu)
  + GiaoVien(#magv,hoten,NgaySinh,@maBM)
  + BoMon(#MaBM,tenBM,@maKhoa)
  + Khoa(#maKhoa,tenKhoa)
  + MonHoc(#mamon,Tenmon,STC)
  + LopHP(#maLopHP,TenLopHP,HK,@maMon,@maGV)
  + DKMH(#@maLopHP,#@maSV,DiemTP,DiemThi,PhanTramThi)

YÊU CẦU:
1. Thực hiện các hành động sau trên giao diện đồ hoạ để tạo cơ sở dữ liệu cho bài toán:
  + Tạo database mới, mô tả các tham số(nếu có) trong quá trình.
  + Tạo các bảng dữ liệu với các trường như mô tả, chọn kiểu dữ liệu phù hợp với thực tế (tự tìm hiểu)
  + Mỗi bảng cần thiết lập PK, FK(s) và CK(s) nếu cần thiết. (chú ý dấu # và @: # là chỉ PK, @ chỉ FK)
2. Chuyển các thao tác đồ hoạ trên thành lệnh SQL tương đương. lưu tất cả các lệnh SQL trong file: Script_DML.sql

## Chú ý:
1. Được phép dùng AI và tham khảo bài của bạn, nhưng phải có sự khác biệt đáng kể.
2. Nghiêm cấm copy, clone. Tham khảo và copy là 2 việc khác hẳn nhau. Thầy có tool để check!
3. Bài làm phải có dấu ấn cá nhân (hãy sáng tạo và biết cách bảo vệ mình nếu bạn là bản chính)
4. Kết quả AI phải phù hợp với yêu cầu, nếu quá sai lệch <=> sv ko đọc => Cấm thi
5. Nên nhớ: cấm thi là ko có vùng cấm và thầy chưa bao giờ nói đùa về việc cấm thi.

---

## Tạo Database QLSV:
   * Mở SSMS và kết nối đến SQL Server.
   * Chuột phải vào "Databases" trong Object Explorer, chọn "New Database...".
     
![image](https://github.com/user-attachments/assets/bf3a65e3-3fc1-4691-a667-991fb0e6a35b)

   * Nhập "QLSV" vào ô "Database name".
   * Nhấn "OK".
     
![image](https://github.com/user-attachments/assets/69596d9c-8c86-4e84-b6bb-061b32342b57)

## Tạo các bảng:
   * Trong Object Explorer, mở rộng "QLSV" database, chuột phải vào "Tables", chọn "New" -> "Table...".
     
![image](https://github.com/user-attachments/assets/2d5d700e-0e55-4f0c-b2aa-c1c389b988fd)

   * Nhập tên cột, kiểu dữ liệu và chuột phải dòng dữ liệu đã chọn để thay đổi các ràng buộc (PK, FK, CK) nhưng ở đây chúng ta có Primery Key tạm thời chúng ta sẽ chọn làm PK trước, sau đó Ctrl+S đặt tên bảng của dữ liệu đã nhập.
   * Và ở Data Type:
     
CHAR(10): Dùng cho các mã khóa chính, đảm bảo độ dài cố định (ở đây là 10).

NVARCHAR(50): Dùng cho tên, có hỗ trợ Unicode tối đa 50 ký tự.

VARCHAR(20): Chứa chuỗi lưu trữ ký tự tối đa là 20.

DATE: Dùng cho ngày tháng.

INT: Dùng cho số nguyên như HK, STC.

FLOAT: Dùng cho điểm thi.

CHECK: Đảm bảo giá trị hợp lệ.

FOREIGN KEY: Định nghĩa khóa ngoại liên kết giữa các bảng.
     
![image](https://github.com/user-attachments/assets/53e28fd2-8269-41a5-bb37-31b952334e83)

   * Lặp lại bước trên để nhập tất cả dữ liệu cùng tên bảng.
   * Và sau đây chúng ta tới bước cài Foreign Key, chúng ta chuột phải vào dòng dữ liệu muốn set, bấm Relationship ta sẽ có bảng sau, bấm Add để tạo thêm khóa và tại dòng Table And Columns Spec bấm mũi tên bên cạnh để expand và cuối dòng đó sẽ có nút ... ta bấm vào nó để bắt đầu set up FK
     
![image](https://github.com/user-attachments/assets/d16c6e3f-40c2-47ba-ad2e-979d91e7938b)

   * Trong giao diện sau ta bắt đầu sửa tên theo tùy người muốn đã cho và chọn setting PK và FK theo đề bài đã cho, rồi ta bấm OK để save.
     
![image](https://github.com/user-attachments/assets/e922c31b-5bf7-4cc6-9951-5c868ab6d972)



