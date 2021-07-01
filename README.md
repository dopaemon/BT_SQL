# Bài 40.10
```bash
Cho Lược đồ cơ sở dữ liệu quản lý nhân viên của một công ty nhƣ sau:
__Nhanvien__(MANV,HOTEN, NU,NGAYSINH,LUONG,MAPB, MACV)
Mỗi nhân viên có một mã nhân viên (MANV) duy nhất, mỗi mã nhân viên xác định họ
và tên nhân viên (HOTEN), giới tính (NU), lƣơng (LUONG), mã phòng ban (MAPB), mã
chức vụ (MACV).
__Phongban__(MAPB,TENPB,TRUSO,MANVPHUTRACH,KINHPHI,DOANHTHU)
Mỗi phòng ban có tên gọi phòng ban(TENPB), địa điểm đặt trụ sở (TRUSO), mã nhân
viên phụ trách(MANVPHUTRACH), kinh phí hoạt động (KINHPHI), và doanh
thu(DOANHTHU)
__Chucvu__(MACV,TENCV,LUONGTHAPNHAT,LUONGCAONHAT)
Mỗi chức vụ co tên gọi chức vụ (TENCV), mức lương tối
thiểu(LUONGTHAPNHAT), mức lương tối đa (LUONGCAONHAT).
Hãy biểu diễn các câu hỏi sau bằng SQL

a.Lập danh sách gồm các thông tin về các phòng ban trong công ty nhƣ: mã số phòng
ban, tên phòng ban, địa điểm trụ sở, mã số ngƣời phụ trách, kinh phí hoạt động, doanh thu.

b.Lập danh sách những nhân viên sinh nhật trong tháng 10

c.Lập danh sách gồm các thông tin mã số nhân viên, họ và tên và lương cả năm của các
nhân viên (giả sử rằng luơng cả năm =12*lƣơng)
```
## Bài 40.10/a :
```bash
SELECT *
FROM PHONGBAN
```
Giải Thích :
```bash
```

## Bài 40.10/b :
```bash
SELECT *
FROM NHANVIEN
WHERE MONTH([NGAYSINH]) = '10'
```

Giải Thích :
```bash
Chọn Tất Cả Từ NHANVIEN Tìm Tháng Sinh Của Nhân Viên Có Tháng 10
```

## Bài 40.10/c :
Bài Làm :
```bash
SELECT A.MAVN, A.HOTEN, (B.LUONGTHAPNHAT)*12 AS LUONGTHAPNHAT
FROM NHANVIEN A INNER JOIN CHUCVU B ON A.MACV = B.MACV
WHERE 
```

Giải Thích :
```bash
Chọn A.MANV, A.HOTEN, (B.LUONGTHAPNHAT)*12 Như LUONGTHAPNHAT
Từ NHANVIEN A Trả về các bản ghi có giá trị phù hợp trong cả hai bảng Chức vụ B Trên A.MACV = B.MACV  

```
