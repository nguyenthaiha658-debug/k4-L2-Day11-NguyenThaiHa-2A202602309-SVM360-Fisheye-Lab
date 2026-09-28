# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Các vạch sơn trắng phân chia từng ô đỗ ở khu vực tiền cảnh (phía dưới và giữa bãi đỗ), bám sát dọc theo dải sơn nhìn thấy rõ ràng trên mặt đường.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Không vẽ các vạch kẻ xa mờ ở hậu cảnh và mép vỉa hè/lề đường, vì các vạch này là ranh giới ngoài của bãi đỗ / lối xe chạy hoặc không đủ độ tin cậy để xác định là vạch chia ô đỗ riêng lẻ.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Vùng `free_space` bao phủ toàn bộ mặt đường trống nhìn thấy của lối xe chạy chính trong bãi đỗ, đường bao dừng chính xác tại mép bánh xe đỗ, chân vỉa hè (curb) và không vẽ xuyên qua các xe đang đỗ hay bóng cây/vùng bị che khuất.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): Các đoạn vạch sơn bị đứt quãng hoặc bị mòn mờ ở phía xa gần các xe đỗ phía sau.
