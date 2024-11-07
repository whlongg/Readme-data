# Dao Động Điều Hòa: Đồ Thị và Bài Tập Minh Họa

## 1. Đồ Thị Li Độ (x) Theo Thời Gian
Li độ \(x(t)\) là vị trí của vật dao động tại thời điểm \(t\). Phương trình của li độ dao động điều hòa có dạng:

$$
x(t) = A \cos(\omega t + \varphi_0)
$$

Trong đó:
- \(A\) là biên độ dao động (vị trí cực đại).
- \(\omega\) là tần số góc (radians trên giây).
- \(\varphi_0\) là pha ban đầu.

### Đặc điểm đồ thị:
- Đồ thị li độ có dạng sóng **cosin** hoặc **sin**, phụ thuộc vào pha ban đầu.
- Vật dao động qua vị trí cân bằng (\(x = 0\)) và di chuyển tới biên độ cực đại (\(x = A\)) và cực tiểu (\(x = -A\)).
- Khi \(x = A\), pha ban đầu \(\varphi_0 = 0\); khi \(x = -A\), pha ban đầu \(\varphi_0 = \pi\).

### Ví dụ:
Phương trình dao động: 

$$
x(t) = 3 \cos(2t + \frac{\pi}{2})
$$

- Biên độ \(A = 3\) cm.
- Tần số góc \(\omega = 2\) rad/s.
- Pha ban đầu \(\varphi_0 = \frac{\pi}{2}\).

---

## 2. Đồ Thị Vận Tốc (v) Theo Thời Gian
Vận tốc \(v(t)\) là đạo hàm của li độ theo thời gian:

$$
v(t) = \frac{d}{dt} x(t) = -A \omega \sin(\omega t + \varphi_0)
$$

### Đặc điểm đồ thị:
- Đồ thị vận tốc có dạng sóng **sin**.
- Vận tốc đạt cực đại tại vị trí cân bằng (\(x = 0\)).
- Vận tốc bằng không khi vật ở biên độ (\(x = \pm A\)).

### Ví dụ:
Phương trình vận tốc:

$$
v(t) = -3 \cdot 2 \sin(2t + \frac{\pi}{2}) = -6 \sin(2t + \frac{\pi}{2})
$$

---

## 3. Đồ Thị Gia Tốc (a) Theo Thời Gian
Gia tốc \(a(t)\) là đạo hàm của vận tốc theo thời gian:

$$
a(t) = \frac{d}{dt} v(t) = -A \omega^2 \cos(\omega t + \varphi_0)
$$

### Đặc điểm đồ thị:
- Đồ thị gia tốc có dạng sóng **cosin**.
- Gia tốc đạt cực đại tại biên độ (\(x = \pm A\)) và bằng không tại vị trí cân bằng (\(x = 0\)).

### Ví dụ:
Phương trình gia tốc:

$$
a(t) = -3 \cdot 2^2 \cos(2t + \frac{\pi}{2}) = -12 \cos(2t + \frac{\pi}{2})
$$

---

## 4. Đồ Thị Cơ Năng (W) Theo Thời Gian
**Cơ năng** trong dao động điều hòa là tổng của động năng và thế năng, và được bảo toàn (không thay đổi theo thời gian). Cơ năng có giá trị bằng:

$$
W = \frac{1}{2} m \omega^2 A^2
$$

### Đặc điểm đồ thị:
- Cơ năng là **hằng số** theo thời gian, không thay đổi.

### Ví dụ:
Giả sử \(m = 2 \, \text{kg}\), \(\omega = 4 \, \text{rad/s}\), và \(A = 5 \, \text{cm}\). Cơ năng tính được là:

$$
W = \frac{1}{2} \times 2 \times 4^2 \times (0.05)^2 = 0.08 \, \text{J}
$$

---

## 5. Đồ Thị Thế Năng (W_t) Theo Thời Gian
**Thế năng** trong dao động điều hòa là năng lượng liên quan đến sự biến dạng của lò xo hoặc lực phục hồi:

$$
W_t = \frac{1}{2} k x^2
$$

Trong đó, \(k\) là độ cứng của lò xo và \(x(t)\) là li độ của vật.

### Đặc điểm đồ thị:
- Thế năng đạt cực đại tại biên độ (\(x = \pm A\)) và bằng không tại vị trí cân bằng (\(x = 0\)).

### Ví dụ:
Giả sử \(k = 100 \, \text{N/m}\), \(A = 0.1 \, \text{m}\), và \(x(t) = 0.05 \, \text{m}\). Thế năng tại \(x(t) = 0.05 \, \text{m}\) là:

$$
W_t = \frac{1}{2} \times 100 \times (0.05)^2 = 0.125 \, \text{J}
$$

---

## 6. Đồ Thị Động Năng (W_đ) Theo Thời Gian
**Động năng** trong dao động điều hòa là năng lượng liên quan đến chuyển động của vật:

$$
W_đ = \frac{1}{2} m v^2(t)
$$

Động năng đạt cực đại tại vị trí cân bằng (\(x = 0\)) và bằng không tại biên độ (\(x = \pm A\)).

### Đặc điểm đồ thị:
- Động năng đạt cực đại tại vị trí cân bằng và bằng không khi vật ở biên độ.

### Ví dụ:
Giả sử \(m = 1 \, \text{kg}\), \(v(t) = 4 \, \text{m/s}\), động năng tại thời điểm này là:

$$
W_đ = \frac{1}{2} \times 1 \times 4^2 = 8 \, \text{J}
$$

---

## Bài Tập Minh Họa

### Bài Tập 1: Xác Định Cơ Năng, Động Năng và Thế Năng

**Đề bài:** Một vật dao động điều hòa với phương trình li độ \(x(t) = 2 \cos(3t + \frac{\pi}{4})\), trong đó \(x(t)\) tính bằng cm và thời gian \(t\) tính bằng giây. Khối lượng vật là \(m = 0.5 \, \text{kg}\).

**Câu hỏi:**
1. Tính cơ năng của dao động.
2. Tính động năng và thế năng tại thời điểm \(t = 0\).

**Giải:**
1. **Phương trình dao động**: \(x(t) = 2 \cos(3t + \frac{\pi}{4})\).
   - Biên độ \(A = 2 \, \text{cm} = 0.02 \, \text{m}\).
   - Tần số góc \(\omega = 3 \, \text{rad/s}\).
   
   Cơ năng \(W\) được tính bằng:

$$
W = \frac{1}{2} m \omega^2 A^2 = \frac{1}{2} \times 0.5 \times 3^2 \times (0.02)^2 = 0.00045 \, \text{J}
$$

2. **Động năng và thế năng tại \(t = 0\):**
   - Tại \(t = 0\), \(x(0) = 2 \cos(\frac{\pi}{4}) = 2 \times \frac{\sqrt{2}}{2} = \sqrt{2} \, \text{cm}\).
   - Vận tốc \(v(0) = -A \omega \sin(\omega \cdot 0 + \frac{\pi}{4}) = -2 \times 3 \times \sin(\frac{\pi}{4}) = -2 \times 3 \times \frac{\sqrt{2}}{2} = -3 \sqrt{2} \, \text{cm/s}\).
   
   Động năng \(W_đ\):

$$
W_đ = \frac{1}{2} m v^2(0) = \frac{1}{2} \times 0.5 \times (3 \sqrt{2})^2 = 13.5 \, \text{J}
$$
