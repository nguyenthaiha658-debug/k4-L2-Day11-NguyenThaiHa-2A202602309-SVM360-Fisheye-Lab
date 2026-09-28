# Guideline patch

- **Rule mới đề xuất:** R12 — Quy tắc nhận diện phương tiện chở hàng 3 bánh cải tiến và xe kéo tự chế: Bổ sung định nghĩa chi tiết cho các phương tiện 3 bánh lai ghép chở hàng (như e-rickshaw thùng kín, xe ba gác máy chở cồng kềnh) được quy định chặt chẽ vào class `ThreeWheeler` nếu có 3 bánh tiếp đất, bất kể phần thùng sau có dạng tương tự thùng xe tải nhỏ.
- **Áp dụng cho:** Class `ThreeWheeler` và `Truck`, áp dụng trên toàn bộ các zone (`center`, `mid`, `edge`).
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Luật hiện tại (R04) chỉ đề cập chung auto-rickshaw và e-rickshaw chở khách, dẫn đến sự nhầm lẫn giữa xe 3 bánh chở hàng thùng vuông với xe bán tải/xe tải nhỏ `Truck`.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** r1_craft / rework trở đi.
