# Sensor context

- Rig: Camera đơn góc rộng fisheye gắn phía trước xe 2 bánh (xe máy/scooter), đặt ở độ cao ngang tầm ngực/tay lái người lái và hướng nhìn thẳng về phía trước theo hướng di chuyển của xe.
- `ego_body`: Nhìn thấy ở phần dưới góc trái khung hình (thường là tay áo, cánh tay, vai hoặc một phần ghi-đông tay lái của người điều khiển xe ego; một số frame khi góc quay lệch hoặc không có phần người lọt vào thì không thấy).
- Vòng kính (lens circle): Vòng tròn quang học của thấu kính fisheye nằm ở trung tâm khung hình dọc (1080 × 1920), vùng ngoài vòng tròn tạo thành viền đen (lens_border) ở đỉnh trên và đáy dưới chiếm khoảng 25–30% diện tích khung hình.
