# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 7 | 2 | 4 | 3 | 7 | SPURIOUS (3) |
| mid | 11 | 1 | 3 | 5 | 7 | SPURIOUS (2) |
| edge | 2 | 0 | 1 | 0 | 1 | SPURIOUS (1) |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: Cả người gán nhãn (L) và model (M) gặp nhiều lỗi nhất ở vùng `center` (L có 4 spurious, 2 missing; M có 7 spurious, 3 missing) và vùng `mid` (L có 3 spurious, 1 missing; M có 7 spurious, 5 missing). Vùng `edge` có số lượng đối tượng ít hơn (2 ref) và đạt độ khớp tương đối cao (matched 2, 0 missing).
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: Vùng center và mid có mật độ phương tiện và người đi bộ đông đúc, khoảng cách xa dần về hậu cảnh nên dễ nhầm lẫn hoặc sót vật thể nhỏ (ngưỡng H=40px). Model thường xuyên bắt thừa các cụm chi tiết nền hoặc bóng xe thành box rời rạc (M thừa 7 ở center và 7 ở mid), đồng thời không nhận diện tốt các xe đặc thù (ThreeWheeler). Giới hạn của slice 3 frame chỉ phản ánh tình huống cục bộ của 1 camera đơn, chưa đại diện cho toàn bộ 4 camera và các góc nhìn khác nhau quanh xe.
