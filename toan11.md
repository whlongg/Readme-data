**a)**

*   Nhân cả tử và mẫu với biểu thức liên hợp của tử số.
*   Rút gọn tử số.
*   Chia cả tử và mẫu cho x.
*   Tính giới hạn.

**b)**

*   Xác định dấu của tử số và mẫu số khi $x$ tiến tới 3 từ bên trái.
*   Tính giới hạn.

**c)**

*   Nhân cả tử và mẫu với biểu thức liên hợp của tử số.
*   Rút gọn tử số.
*   Phân tích mẫu số thành nhân tử.
*   Rút gọn (x-1) ở cả tử và mẫu.
*   Tính giới hạn.
---



## Đề bài

Cho hàm số 
f(x)=
{
x^2+mx+n, khi x < -5,
x+17, khi -5 ≤ x ≤ 10,
mx+n+10, khi x > 10,
}
biết f liên tục trên R. Xét các mệnh đề:

1. f(-5)=12 và f(10)=27. 
2. m > 0, n > 0. 
3. 2m + n là số nguyên tố. 
4. Giá trị lớn nhất của hàm y = msinx + ncosx là √12.

Hỏi mệnh đề nào đúng, mệnh đề nào sai?

## Giải chi tiết

### Bước 1. Liên tục tại x = -5

- Với x < -5, ta có f(x)=x^2+mx+n.
- Với -5 ≤ x ≤ 10, ta có f(x)=x+17.

Vì f liên tục tại x=-5, nên
lim(x→-5^-) f(x) = f(-5) = lim(x→-5^+) f(x).

- Ở bên trái: 
  lim(x→-5^-)(x^2 + mx + n) = 25 - 5m + n.
- Ở bên phải (hay trực tiếp tại -5) do -5 ∈ [-5,10]:
  f(-5) = -5 + 17 = 12.

Do đó,  
25 - 5m + n = 12 => -5m + n = -13 => n = 5m - 13. (1)

### Bước 2. Liên tục tại x = 10

- Với -5 ≤ x ≤ 10, ta có f(x)=x+17.
- Với x > 10, ta có f(x)=mx + n + 10.

Tương tự, tính liên tục tại x=10 đòi hỏi
lim(x→10^-) f(x) = f(10) = lim(x→10^+) f(x).

- Ở bên trái (hoặc ngay tại 10):
  f(10) = 10 + 17 = 27.
- Ở bên phải:
  lim(x→10^+) (mx + n + 10) = 10m + n + 10.

Vậy,
10m + n + 10 = 27 => 10m + n = 17 => n = 17 - 10m. (2)

### Bước 3. Giải hệ phương trình (1) và (2)

Từ (1) và (2):
{
n = 5m - 13,
n = 17 - 10m.
}
Suy ra
5m - 13 = 17 - 10m => 5m + 10m = 17 + 13 => 15m = 30 => m = 2.
Thay m=2 vào một trong hai biểu thức trên, chẳng hạn (1):
n = 5 * 2 - 13 = 10 - 13 = -3.

Vậy để hàm liên tục trên R, bắt buộc
m = 2, n = -3.

### Bước 4. Kiểm tra các mệnh đề

1. f(-5) = 12 và f(10) = 27

   - Thực tế, ngay theo định nghĩa của nhánh -5 ≤ x ≤ 10, ta luôn có
       f(-5) = -5 + 17 = 12, 
       f(10) = 10 + 17 = 27.
   - Điều này hoàn toàn đúng với giá trị hàm trên đoạn [-5, 10]. 
   (a) ĐÚNG.

2. m>0, n>0

   - Vừa tìm được m=2>0 (đúng) nhưng n=-3<0 (không dương). 
   (b) SAI.

3. 2m + n là số nguyên tố

   - Thay m=2, n=-3:
     2m + n = 2*2 + (-3) = 4 - 3 = 1.
   - Số 1 không được coi là số nguyên tố. 
   (c) SAI.

4. Giá trị lớn nhất của y = msinx + ncosx là √12

   - Công thức quen thuộc: max (Asinx + Bcosx) = √(A^2 + B^2).
   - Ở đây A = m=2, B = n=-3, nên
     max (2sinx - 3cosx) = √(2^2 + (-3)^2) = √(4 + 9) = √13.
   - Đề cho kết quả √12 (tức √(4*3)=2√3), không khớp √13. 
   (d) SAI.
