# Bài Tập SQL
# Tên : Trần Nguyễn Tuấn Anh
# Lớp T3K21
## Bài Tập Có Dùng Các Tài Liệu Tham Khảo Tại
* [**W3SCHOOL**](https://www.w3schools.com/sql/)
* [**QUANTRIMANG**](https://quantrimang.com/)

## Bài 40.10
```bash
Cho Lược đồ cơ sở dữ liệu quản lý nhân viên của một công ty nhƣ sau:

Nhanvien(MANV,HOTEN, NU,NGAYSINH,LUONG,MAPB, MACV)
Mỗi nhân viên có một mã nhân viên (MANV) duy nhất, mỗi mã nhân viên xác định họ
và tên nhân viên (HOTEN), giới tính (NU), lương (LUONG), mã phòng ban (MAPB), mã
chức vụ (MACV).

Phongban(MAPB,TENPB,TRUSO,MANVPHUTRACH,KINHPHI,DOANHTHU)
Mỗi phòng ban có tên gọi phòng ban(TENPB), địa điểm đặt trụ sở (TRUSO), mã nhân
viên phụ trách(MANVPHUTRACH), kinh phí hoạt động (KINHPHI), và doanh thu(DOANHTHU)

Chucvu(MACV,TENCV,LUONGTHAPNHAT,LUONGCAONHAT)
Mỗi chức vụ co tên gọi chức vụ (TENCV), mức lương tối
thiểu(LUONGTHAPNHAT), mức lương tối đa (LUONGCAONHAT).
Hãy biểu diễn các câu hỏi sau bằng SQL

a.Lập danh sách gồm các thông tin về các phòng ban trong công ty nhƣ: mã số phòng
ban, tên phòng ban, địa điểm trụ sở, mã số ngƣời phụ trách, kinh phí hoạt động, doanh thu.

b.Lập danh sách những nhân viên sinh nhật trong tháng 10

c.Lập danh sách gồm các thông tin mã số nhân viên, họ và tên và lương cả năm của các
nhân viên (giả sử rằng luơng cả năm =12*lương)

d.Lập những phòng ban có kinh phí hoạt động cao nhất.

e.Lập danh sách nhân viên của phòng ban có mã số phòng ban là 40.

f.Lập danh sách nhân viên của phòng có mã số phòng ban 10,30,50.

g.Lập danh sách các nhân viên có lương tháng từ 2.500.000 đến 4.000.000

h.Tìm những nhân viên có tuổi cao nhất thuộc phòng ban có MAPB là 10

i.Lập danh sách các nhân viên của phòng 10,30,50. kết quả in ra theo thứ tự tăng dần
của mã phòng nếu trùng mã phòng thì sắp xếp giảm dần theo mức lương.

k.Lập danh sách các nhân viên phòng 10,30,50, chỉ in ra những người là lãnh đạo của
mỗi phòng ban này.

l.lập danh sách gồm mã phòng mà người có mức lương cao nhất của phòng lớn hơn
hoặc bằng 4.000.000 m.Lập mã phòng ban, tên phòng ban, họ và tên của lãnh đạo phòng
tương ứng.

n.Lập danh sách những người làm việc cùng phòng với ông Nguyen Van Thanh

o.Lập biết mã số nhân viên, họ và tên, mức lương của người lãnh đạo ông Nguyen Van
Thanh. 

p.Lập danh sách nhân viên có mức lương lớn hơn hay bằng mức lương cao nhất của
phòng ông Nguyen Van Thanh.

q.Cho biết mã số nhân viên, họ và tên , tổng số nhân viên, mức lương cao nhất, mức
lương thấp nhất, mức lương trung bình của từng phòng ban.

r.Cho biết các nhân viên có mức lương cao nhất của các phòng ban.

s.Cho biết số lượng nhân viên của mỗi phòng ban.
```
### Bài 40.10/a :
```bash
SELECT *
FROM Phongban
```

### Bài 40.10/b :
```bash
SELECT *
FROM Nhanvien
WHERE MONTH([NGAYSINH]) = '10'
```

### Bài 40.10/c :
Bài Làm :
```bash
SELECT MANV, HOTEN, (LUONG)*12
FROM Nhanvien
```
### Bài 40.10/d :
Bài Làm :
```bash
SELECT MAPB, TENPB, TRUSO, MANVPHUTRACH, DOANHTHU, MAX(KINHPHI)
FROM Phongban
```

### Bài 40.10/e :
Bài Làm :
```bash
SELECT MANV, HOTEN, NU, NGAYSINH, LUONG, MACV
FROM Nhanvien 
WHERE MAPB = 40
```

### Bài 40.10/f :
Bài Làm :
```bash
SELECT MANV, HOTEN, NU, NGAYSINH, LUONG, MACV
FROM Nhanvien 
WHERE MAPB = 10 OR MAPB = 30 OR MAPB = 50
```
Hoặc :
```bash
SELECT MANV, HOTEN, NU, NGAYSINH, LUONG, MACV
FROM Nhanvien 
WHERE MAPB IN (10,30,50)
```

### Bài 40.10/g :
Bài Làm :
```bash
SELECT MANV,HOTEN, NU,NGAYSINH,LUONG,MAPB, MACV
FROM Nhanvien
WHERE LUONG >= 2500000 AND LUONG <= 4000000
```
Hoặc :
```bash
SELECT MANV, HOTEN, NU, NGAYSINH, LUONG,MAPB, MACV 
FROM Nhanvien 
WHERE LUONG BETWEEN 2500000 AND 4000000
```

### Bài 40.10/h :
Bài Làm :
```bash
SELECT MANV,HOTEN, NU,NGAYSINH,LUONG,MAPB, MACV 
FROM Nhanvien 
WHERE YEAR(NGAYSINH) = (SELECT YEAR(NGAYSINH) FROM NHANVIEN ORDER BY NGAYSINH ASC LIMIT 1) AND MAPB = 10
```

### Bài 40.10/i :
Bài Làm :
```bash
SELECT MANV,HOTEN, NU,NGAYSINH,LUONG,MAPB, MACV
FROM Nhanvien
WHERE MAPB IN (10,30,50) GROUP BY MAPB ORDER BY MAPB ASC, LUONG DESC
```

### Bài 40.10/k :
Bài Làm :
```bash
SELECT MANV, HOTEN, NU, NGAYSINH, LUONG, MAPB, MACV 
FROM Nhanvien
WHERE MANV IN (SELECT MANVPHUTRACH FROM Phongban WHERE MAPB IN (10,30,50))
```

### Bài 40.10/l :
Bài Làm :
```bash
SELECT *
FROM Phongban 
WHERE MAPB IN (SELECT DISTINCT MAPB FROM Nhanvien a WHERE a.LUONG >= 4000000)
```

### Bài 40.10/n :
Bài Làm :
```bash
SELECT *
FROM Nhanvien 
WHERE MAPB = (SELECT b.MAPB FROM Nhanvien b WHERE b.HOTEN = 'NGUYEN VAN THANH')
```

### Bài 40.10/o :
Bài Làm :
```bash
SELECT * 
FROM Nhanvien a 
WHERE a.MAPB = (SELECT b.MAPB FROM Nhanvien b WHERE b.HOTEN = 'NGUYEN VAN THANH') AND a.MANV = (SELECT b.MANVPHUTRACH FROM Phongban b WHERE b.MAPB = a.MAPB)
```

### Bài 40.10/p :
Bài Làm :
```bash
SELECT * 
FROM Nhanvien a 
WHERE a.MAPB = (SELECT b.MAPB FROM Nhanvien b WHERE b.HOTEN = 'NGUYEN VAN THANH') AND a.LUONG = (SELECT b.LUONGCAONHAT FROM Phongban b WHERE b.MAPB = a.MAPB)
```

### Bài 40.10/q :
Bài Làm :
```bash
SELECT MAPB, COUNT(MANV), MIN(LUONG), MAX(LUONG), AVG(LUONG)
FROM Nhanvien
GROUP BY MAPB
```

### Bài 40.10/r :
Bài Làm :
```bash
SELECT MANV, MAX(LUONG), DISTINCT MAPB
FROM Phongban, Nhanvien
```

### Bài 40.10/s :
Bài Làm :
```bash
SELECT TENPB, MAPB, COUNT(MANV) AS "So luong nhan vien"
FROM Phongban, Nhanvien
GROUP BY TENPB;
```
