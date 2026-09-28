# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Đây KHÔNG phải là lỗi `DUPLICATE` mà cần một quy tắc riêng (Cross-camera Seam Policy). Bởi vì mỗi camera quan sát vật thể từ một góc nhìn (viewpoint) quang học độc lập với độ méo và điểm mù riêng. Việc một vật thể lọt vào vùng giao thoa của 2 camera là hiện tượng vật lý tự nhiên; khi chưa có thông số calibration chính xác và đồng bộ timestamp để chiếu lên không gian 3D/BEV thì mỗi camera vẫn phải gán nhãn đầy đủ cho phần nhìn thấy của vật thể đó.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Nêu bằng chứng sẽ cần trước khi nối track qua hai camera. Giữ cùng Track ID khi vật thể di chuyển liên tục và có thể quan sát được quỹ đạo di chuyển. Đặt trạng thái Outside khi vật thể tạm thời khuất sau chướng ngại vật hoặc ra ngoài khung nhìn của camera trong một số frame rồi quay lại. Để nối track qua hai camera khác nhau, bắt buộc phải có 3 bằng chứng: (1) Đồng bộ thời gian chính xác (hardware timestamp), (2) Ma trận hiệu chuẩn ngoại (extrinsic calibration) giữa các camera, và (3) Kết quả phân tích nhất quán không gian 3D/BEV hoặc mô hình Re-ID.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Trong frame `adasind_014670.jpg` tại đối tượng L3 (xe tải nhỏ thùng hở ở rìa), reference đánh nhãn là Truck còn một số quan sát ban đầu nhầm sang Bus. Tôi đã rà soát lại theo quy tắc R04 và đối chiếu ảnh gốc để giữ vững phân loại theo công năng thực tế. Nếu làm lại slice này, tôi sẽ cẩn trọng đo kích thước chiều cao $H \ge 40\text{ px}$ bằng công cụ đo trước khi vẽ để tránh vẽ thừa các đối tượng nhỏ ở hậu cảnh.
