# Danh sách lệnh cheat (chat bắt đầu bằng `-`)

Chỉ hoạt động khi **Xwb[PI]** (chế độ cheat / debug) được bật.

---

## Lệnh so sánh chuỗi trực tiếp

| Lệnh | Tham số | Mô tả |
|------|--------|------|
| **-showstat** | — | Bật/tắt hiển thị stat (XWC). |
| **-dmg** \<số\> | 1–100 | Nhân sát thương (Damage x N). Lưu vào `vChetDmg[PI]`. |
| **-as** \<số\> | 1–1000 | Tốc độ đánh (Attack speed). Giá trị lưu = số/100 (vd: 100 → 1.0). Gọi `BlzSetUnitAttackCooldown(Rb[PI], 1./vChetAs[PI], 0)`. |
| **-elite** \<số\> | 0–100 | Tỉ lệ xuất hiện tinh anh (%). 0 = mặc định. Lưu vào `XEliteRate`. |

---