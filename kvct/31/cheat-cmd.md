## Trạng thái

- **xuco** - Xu co, dùng biến `dUR[fN]` ✓ Đã test
- **uydanh** - Uy Danh, dùng `QX2(fN, Ir, d2h)` ✓ Đã test
- **vinhduvolam** - Vinh dự Võ Lâm, dùng `QX2(fN, Ir, d2g)` ✓ Đã test
- **nhht** - NHHT, dùng `QX2(fN, Ir, d2j)` ✓ Đã test
- **chankhi** - Chân Khí, dùng `QX2(fN, Ir, d2k)` ✓ Đã test
- **hiepkhach** - Hiệp Khách Lệnh, trực tiếp set `dp6[fN]=dp6[fN]+Ir` ✓ Đã test
- **lenhbaithuonghoi** - Gọi `Oll(fN,1,Ir)` đến `Oll(fN,13,Ir)` - cộng vào TẤT CẢ 13 index ✓ Đã test
- **congtrang** - Công trạng, dùng `Olb(fN, Ir, olW)` → tự động cập nhật cache và gọi `QCF(fN)` ✓ Đã test
- **nangdong** - Năng động, trực tiếp set `dpk[fN]=dpk[fN]+Ir` ✓ Đã test
- **danhvongnghiaquan** - Danh vọng nghĩa quân, trực tiếp set `dpb[fN]=dpb[fN]+Ir` ✓ Đã test
- **bac** - Bạc, dùng `OlI(fN, Ir, olW)` → tự động cập nhật cache và hiển thị ✓ Đã test
- **capbanghoi** - Cấp bang hội, trực tiếp set `ols[fN]=ols[fN]+Ir` (chỉ cập nhật giá trị, không cập nhật UI để tránh lỗi) ✓ Đã test
- **quyxaydungbang** - Quỹ xây dựng bang, trực tiếp set `dph[fN]=dph[fN]+Ir` ✓ Đã test
- **conghienbang** - Cống hiến bang, trực tiếp set `dpn[fN]=dpn[fN]+Ir` ✓ Đã test

## Ghi chú

- Tất cả lệnh trên đã được test và hoạt động chính xác ✓
- Lệnh bài thương hội có 13 index (1-13)
- `lenhbaithuonghoi 5` sẽ gọi `Oll(fN,1,5)` đến `Oll(fN,13,5)` - cộng 5 vào cả 13 index
- `hiepkhach` trực tiếp cộng vào `dp6[fN]` (Hiệp Khách Lệnh)
- Các lệnh dùng `QX2` với các constant: `d2h` (Uy Danh), `d2g` (Vinh dự Võ Lâm), `d2j` (NHHT), `d2k` (Chân Khí)

## Biến lưu trữ các giá trị

| Giá trị | Biến | Ghi chú |
|---------|------|---------|
| **Danh vọng trang bị** | `LoadStr(ft,Oyw(d74,fN*(10)),index)` hoặc `LoadInteger(ft,Oyw(d74,fN),index)` | Lưu trong game cache với key `d74`, index 1-10 cho các trang bị (Nón, Áo, Lưng, Tay, Giày, Vũ Khí, Liên, Nhẫn, Bội, Phù) |
| **Uy Danh** | `d29[fN]` | Giá trị uy danh |
| **Cấp Uy Danh** | `d20[fN]` | Cấp uy danh (tính từ d29: `R2I((d29[fN]-b5)/olL)`) |
| **Bạc** | `ol5[fN]` | Cập nhật: **Trực tiếp** `ol5[fN]=ol5[fN]+value` hoặc qua hàm `Ol5(fN, b1, oR3)` / `OlI(fN, b1, oR3)`. Cũng lưu trong game cache với key `old`, index (2). Hàm `Ol5` sẽ tự động cập nhật game cache và hiển thị |
| **Xu co** | `dUR[fN]` | Giá trị thực = `dUR[fN]-b5`. Cũng lưu trong game cache với key `old` |
| **NHHT** | `d2X[fN]` | |
| **Hiệp Khách Lệnh** | `dp6[fN]` | Giá trị thực = `dp6[fN]-olQ` |
| **Vinh dự Võ Lâm** | `d2M[fN]` | Giá trị thực = `d2M[fN]-b5` |
| **Danh vọng nghĩa quân** | `dpb[fN]` | Giá trị thực = `dpb[fN]-b5` |
| **Cống hiến bang** | `dpn[fN]` | Giá trị thực = `dpn[fN]-bY-olz` |
| **Quỹ xây dựng bang** | `dph[fN]` | Giá trị thực = `dph[fN]-b5-olQ` |
| **Cấp bang hội** | `ols[fN]` | Cập nhật: **Trực tiếp** `ols[fN]=ols[fN]+value` hoặc tự động khi điều kiện đạt (quỹ xây dựng bang đủ). Có thể load từ game cache: `LoadInteger(ft,Oyw(dtE,fN),$69)`. Khi tăng cấp tự động sẽ gọi `mFM` để cập nhật UI |
| **Chân Khí** | `olO[fN]` | Giá trị thực = `olO[fN]-b5` |
| **Công trạng** | `d2z[fN]` | Cập nhật: **Qua hàm** `Olb(fN, b1, oR3)` → `d2z[fN]=d2z[fN]+b1`. Hàm `mit(fN, b1, d27)` gọi `Olb(fN, b1, olW)` với `d27` là constant cho công trạng. Hàm `Olb` sẽ tự động cập nhật game cache với key `old` và gọi `QCF(fN)`. Giá trị thực = `d2z[fN]-b5` |
| **Năng động** | `dpk[fN]` | Cập nhật: **Trực tiếp** `dpk[fN]=dpk[fN]+value` hoặc `dpk[fN]=value+b5` khi điều kiện đạt. Nhận thưởng năng động, giá trị thực = `dpk[fN]-b5` |
| **Tích lũy năng động** | `dCd[fN]` | Cập nhật: **Tự động** `dCd[fN]=dCd[fN]+1` khi điều kiện đạt (`dpA[fN]-bY>=(dCd[fN]+1)*5*d2u`). Có thể load từ game cache: `LoadInteger(ft,Oyw(dtQ,fN),$84)`. Tích lũy năng động |
| **Lệnh bài thương hội** | `O8W(O8O(dCF,fN),Ir)` | Lưu trong game cache với key `dCF`, index 1-13. Hàm cộng: `Oll(fN,Ir,Iy)` với `Ir` là index (1-13), `Iy` là giá trị cộng vào. Giá trị thực = `O8W(O8O(dCF,fN),Ir)/(2)`. Có 13 loại: (1) Bách Niên Thiên Lao, (2) Ác Nhân Cốc, (3) Vạn Hoa Cốc, (4) Lâu Lan Cổ Thành, (5) Hoạt Tử Nhân Mộ, (6) Long Môn Phi Kiếm, (7) Tiêu Dao Cốc, (8) Thời Quang Điện, (9) Minh Linh Đinh Viện, (10) Thiên Quỳnh Cung, (11) Thiên Long Tự, (12) Thần Trùng Trấn, (13) Thiên Tử Đảo |
