Bai 40.10/a :
```bash
SELECT *
FROM PHONGBAN
```

Bai 40.10/b :
```bash
SELECT *
FROM NHANVIEN
WHERE MONTH([NGAYSINH]) = '10'
```

Bai 40.10/c :
Bai Lam :
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
