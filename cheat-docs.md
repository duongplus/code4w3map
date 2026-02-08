# Danh sách lệnh cheat (chat bắt đầu bằng `-`)

Chỉ hoạt động khi **Xwb[PI]** (chế độ cheat / debug) được bật.

---

## Lệnh so sánh chuỗi trực tiếp

| Lệnh | Tham số | Mô tả |
|------|--------|------|
| **-showstat** | — | Bật/tắt hiển thị stat (XWC). |
| **-dmg** \<số\> | 1–100 | Nhân sát thương (Damage x N). Lưu vào `vChetDmg[PI]`. |
| **-as** \<số\> | 1–1000 | Tốc độ đánh (Attack speed). Giá trị lưu = số/100 (vd: 100 → 1.0). Gọi `BlzSetUnitAttackCooldown(Rb[PI], 1./vChetAs[PI], 0)`. |
| **-ms** \<số\> | 0–20 | Nhân tốc độ di chuyển (chạy bộ + thú cưỡi). 0 = mặc định, 1–20 = hệ số nhân. Lưu vào `vChetMs[PI]`, áp dụng qua `bvMs(PI)` và trong `bIt` khi cập nhật tốc độ. |
| **-elite** \<số\> | 0–100 | Tỉ lệ xuất hiện tinh anh (%). 0 = mặc định. Lưu vào `XEliteRate`. |
| **-xuco** \<số\> | ≥1 | Nhận Xu Cổ: `-xuco 1000` = nhận 1000 Xu Cổ. Gọi `bEq(PI, Pi, Xgl)`. |
| **-hiepkhach** \<số\> | ≥1 | Cộng Hiệp Khách Lệnh: `-hiepkhach 500` = cộng 500 điểm. Gán `XFY[PI]=XFY[PI]+Pi`. |
| **-vinhduvolam** \<số\> | ≥1 | Cộng Vinh dự Võ Lâm: `-vinhduvolam 100` = cộng 100 điểm. Gán `XgY[PI]=XgY[PI]+Pi`. |
| **-conghienbanghoi** \<số\> | ≥1 | Cộng Cống hiến + Quỹ xây dựng bang (cùng số). Nếu quỹ ≥ ngưỡng `XQX[vQD+1]` thì tự lên level bang (vQD, bUU, bsK, XQu); tối đa 12. Gọi `uNS(PI)`. |
| **-capbh** \<số\> | ≥1 | Nâng cấp bang hội (vQD): `-capbh 5` = cộng 5 cấp, tối đa 12. Gọi `bUU`, `EBN` nếu ≥6, `uNS(PI)`. |
| **-nocd** | — | Bật/tắt No CD: tất cả kỹ năng có thời gian hồi = 0. Lưu vào `vChetNoCd[PI]`, áp dụng qua trigger 0.15s gọi `vChetNoCdApply`. |

---