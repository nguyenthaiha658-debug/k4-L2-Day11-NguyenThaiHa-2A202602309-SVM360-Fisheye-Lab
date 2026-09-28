# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Đèn pha rọi ban đêm, trời mưa văng kính, vật thể xa mép trên | Độ chói làm mất biên dạng xe, giọt nước làm méo quang học | Fisheye image space gốc kèm thông số intrinsic/distortion | 2 reviewer độc lập + 1 expert adjudicator phân xử |
| rear | Trẻ em/vật cản thấp dưới 0.5m, đèn hậu phản chiếu | Góc nhìn dốc xuống, vật nhỏ dễ nhầm với chi tiết mặt đường | Fisheye image space kèm mask vùng cản xe ego | Dual-blind annotation + kiểm tra kích thước bounding box |
| left | Xe máy lách sát mép gương, vật thể nằm ở seam trước-trái | Méo thấu kính cực đại ở rìa, một phần vật thể bị cắt sang cam front | Fisheye space + đồng bộ timestamp với cam front/rear | Cross-camera consistency check trước khi phê duyệt |
| right | Người đi bộ bước từ vỉa hè khuất bóng râm, seam trước-phải | Tương phản ánh sáng mạnh, điểm mù cột bên phụ | Fisheye space + đồng bộ timestamp với cam front/rear | Đối chiếu đa khung hình liên tiếp để xác nhận object |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): Cần làm mới khi thay đổi phần cứng camera (độ phân giải, lens FOV), khi cập nhật bảng quy tắc gán nhãn (ví dụ thay đổi định nghĩa class/ngưỡng H), hoặc sau khi hiệu chỉnh lại calibration rig định kỳ.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: Cần có bằng chứng đồng bộ timestamp chính xác, ma trận calibration hình học giữa 2 camera và luật kiểm tra (IoU chiếu 3D/BEV) trước khi gán cùng Track ID hoặc merge box ở vùng giao thoa.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: Mỗi camera có góc nhìn, độ cao, phân bố méo quang học và điều kiện ánh sáng khác nhau. Báo cáo tốt trên một camera đơn lẻ không đại diện cho vùng seam hay các điểm mù đặc thù của 3 camera còn lại.
