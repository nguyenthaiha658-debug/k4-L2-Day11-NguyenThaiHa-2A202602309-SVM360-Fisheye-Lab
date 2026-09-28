# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_019560.jpg
- L2 center SPURIOUS
- L5 mid SPURIOUS
- L6+R5 center BOX_GEOMETRY
- L7+R3 edge WRONG_CLASS
- L8 center SPURIOUS

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 3 | 2 | 1 | 3 |
| mid | 2 | 2 | 0 | 1 |
| edge | 1 | 0 | 1 | 1 |
