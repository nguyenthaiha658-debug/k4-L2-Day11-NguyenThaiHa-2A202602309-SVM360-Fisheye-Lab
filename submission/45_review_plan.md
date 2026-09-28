# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| adasind_014670.jpg (Vùng rìa kính edge) | 3 ca (WRONG_CLASS, MISSING, SPURIOUS) | Vùng rìa chịu biến dạng quang học méo cực đại, dễ nhầm lớp và sai box geometry | Screenshot crop rìa và so sánh với reference R5 |
| adasind_034080.jpg (Vùng trung tâm center/mid) | 6 ca (MISSING, SPURIOUS ở hậu cảnh) | Mật độ phương tiện hỗn hợp cao, ranh giới ngưỡng H=40px dễ bị vi phạm | Overlay so sánh TP/FP/FN và danh sách finding chi tiết |

Giới hạn của kết luận từ ba frame ADASIND: Ba frame chỉ đại diện cho một camera phía trước trong điều kiện ban ngày thông thường, không phản ánh được điểm mù ở camera sau/hông và vùng chồng hình ảnh (seam) giữa 4 camera.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: Lấy mẫu phân tầng (stratified sampling) cách nhau tối thiểu 5-10 giây để tránh phụ thuộc chuỗi thời gian (temporal correlation). Mỗi camera cần phân bổ đều ca ngày/đêm/thời tiết khắc nghiệt. Phân bổ 200 frame tập trung vào hard case giúp tìm lỗi nghiêm trọng nhanh nhất, nhưng vì tỷ lệ mẫu khó cao hơn thực tế nên không thể dùng làm chỉ số accuracy đo lường phân phối thực tế.
