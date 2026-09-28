# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B1 | BOX_GEOMETRY | 1 |
| center | B1 | MISSING | 5 |
| center | B1 | SPURIOUS | 14 |
| center | C0 | BOX_GEOMETRY | 1 |
| center | C0 | SPURIOUS | 2 |
| edge | B1 | BOX_GEOMETRY | 1 |
| edge | B1 | SPURIOUS | 3 |
| edge | C0 | WRONG_CLASS | 1 |
| mid | B1 | MISSING | 5 |
| mid | B1 | SPURIOUS | 11 |
| mid | B1 | WRONG_CLASS | 1 |
| mid | C0 | SPURIOUS | 1 |

## Top defects
- SPURIOUS: 31 (ví dụ frame adasind_019560.jpg)
- MISSING: 10 (ví dụ frame adasind_034080.jpg)
- BOX_GEOMETRY: 3 (ví dụ frame adasind_019560.jpg)

## Phân tích của bạn

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Lỗi nổi bật nhất là SPURIOUS (31 ca) và MISSING (10 ca), tập trung chủ yếu ở vùng `center` và `mid`. Nguyên nhân `E1_annotator_error` xuất phát từ việc người gán nhãn cố vẽ các chi tiết phương tiện/người ở quá xa có chiều cao nhỏ hơn ngưỡng quy định $H < 40\text{ px}$ hoặc gán nhầm bóng râm/biển báo. Đối với model (`E4_model_domain`), model YOLO26m chưa được fine-tune trên tập dữ liệu fisheye góc rộng của Ấn Độ nên bỏ sót nhiều phương tiện đặc thù như ThreeWheeler (auto-rickshaw) và nhận diện sai các cụm vỉa hè, bóng cây thành người đi bộ.
- Cách sửa và ai nhận việc (`owner`): 
  - `annotator`: Thực hiện rà soát nghiêm ngặt theo thước đo ngưỡng $H \ge 40\text{ px}$ trước khi vẽ box; xóa bỏ các box nhỏ hơn 40px ở hậu cảnh.
  - `ai_team`: Thu thập thêm dữ liệu huấn luyện domain fisheye có các class đặc thù (`ThreeWheeler`, `Bike` kèm Rider) và fine-tune lại model phát hiện vật thể.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): Đối chiếu frame `adasind_014670.jpg` (L3+R5, L5) và `adasind_034080.jpg` (L1+R5, R9) trong `findings.csv`; vi phạm quy tắc R01 (ngưỡng H=40), R04 (ánh xạ class ThreeWheeler) và ảnh minh họa lỗi trong `submission/screenshots/prelabel_quality.png`.
