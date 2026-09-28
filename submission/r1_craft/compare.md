# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_014670.jpg
- L3+R5 mid WRONG_CLASS
- L5 center SPURIOUS
## adasind_032280.jpg
- L7 mid SPURIOUS
- L8 edge SPURIOUS
## adasind_034080.jpg
- L4+R2 center BOX_GEOMETRY
- L6 mid SPURIOUS
- L8 center SPURIOUS
- L11 center SPURIOUS
- R9 center MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 7 | 5 | 2 | 4 |
| mid | 11 | 10 | 1 | 3 |
| edge | 2 | 2 | 0 | 1 |
