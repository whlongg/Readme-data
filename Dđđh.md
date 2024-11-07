
# From HLong with love, đồ thị dao động điều hòa 

## 1. Đồ thị Li độ (x) theo thời gian

Li độ `x(t)` là vị trí của vật dao động tại thời điểm `t`. Phương trình của li độ dao động điều hòa có dạng:

```
x(t) = A * cos(ω * t + φ₀)
```

Trong đó:
- `A` là biên độ dao động (vị trí cực đại).
- `ω` là tần số góc (radians trên giây).
- `φ₀` là pha ban đầu.

**Đặc điểm đồ thị:**
- Đồ thị li độ có dạng sóng **cosin** hoặc **sin**, phụ thuộc vào pha ban đầu.
- Vật dao động qua vị trí cân bằng (x = 0) và di chuyển tới biên độ cực đại (x = A) và cực tiểu (x = -A).
- Khi `x = A`, pha ban đầu `φ₀ = 0`; khi `x = -A`, pha ban đầu `φ₀ = π`.

### Ví dụ:
Phương trình dao động: `x(t) = 3 * cos(2 * t + π/2)`
- Biên độ `A = 3 cm`.
- Tần số góc `ω = 2 rad/s`.
- Pha ban đầu `φ₀ = π/2`.

---

## 2. Đồ thị Vận tốc (v) theo thời gian

Vận tốc `v(t)` là đạo hàm của li độ theo thời gian:

```
v(t) = -A * ω * sin(ω * t + φ₀)
```

**Đặc điểm đồ thị:**
- Đồ thị vận tốc có dạng sóng **sin**.
- Vận tốc đạt cực đại tại vị trí cân bằng (x = 0).
- Vận tốc bằng không khi vật ở biên độ (x = ±A).

### Ví dụ:
Phương trình vận tốc:

```
v(t) = -3 * 2 * sin(2 * t + π/2) = -6 * sin(2 * t + π/2)
```

---

## 3. Đồ thị Gia tốc (a) theo thời gian

Gia tốc `a(t)` là đạo hàm của vận tốc theo thời gian:

```
a(t) = -A * ω² * cos(ω * t + φ₀)
```

**Đặc điểm đồ thị:**
- Đồ thị gia tốc có dạng sóng **cosin**.
- Gia tốc đạt cực đại tại biên độ (x = ±A) và bằng không tại vị trí cân bằng (x = 0).

### Ví dụ:
Phương trình gia tốc:

```
a(t) = -3 * 2² * cos(2 * t + π/2) = -12 * cos(2 * t + π/2)
```

---

## 4. Đồ thị Cơ năng (W) theo thời gian

**Cơ năng** trong dao động điều hòa là tổng của động năng và thế năng, và được bảo toàn (không thay đổi theo thời gian). Cơ năng có giá trị bằng:

```
W = 1/2 * m * ω² * A²
```

**Đặc điểm đồ thị:**
- Cơ năng là **hằng số** theo thời gian, không thay đổi.

### Ví dụ:
Giả sử `m = 2 kg`, `ω = 4 rad/s`, và `A = 5 cm`. Cơ năng tính được là:

```
W = 1/2 * 2 * 4² * (0.05)² = 0.08 J
```

---

## 5. Đồ thị Thế năng (Wₜ) theo thời gian

**Thế năng** trong dao động điều hòa là năng lượng liên quan đến sự biến dạng của lò xo hoặc lực phục hồi.

```
Wₜ = 1/2 * k * x²
```

Trong đó, `k` là độ cứng của lò xo và `x(t)` là li độ của vật.

**Đặc điểm đồ thị:**
- Thế năng đạt cực đại tại biên độ (x = ±A) và bằng không tại vị trí cân bằng (x = 0).

### Ví dụ:
Giả sử `k = 100 N/m`, `A = 0.1 m`, và `x(t) = 0.05 m`. Thế năng tại `x(t) = 0.05 m` là:

```
Wₜ = 1/2 * 100 * (0.05)² = 0.125 J
```

---

## 6. Đồ thị Động năng (W₋đ) theo thời gian

**Động năng** trong dao động điều hòa là năng lượng liên quan đến chuyển động của vật:

```
W₋đ = 1/2 * m * v²(t)
```

Động năng đạt cực đại tại vị trí cân bằng (x = 0) và bằng không tại biên độ (x = ±A).

**Đặc điểm đồ thị:**
- Động năng đạt cực đại tại vị trí cân bằng và bằng không khi vật ở biên độ.

### Ví dụ:
Giả sử `m = 1 kg`, `v(t) = 4 m/s`, động năng tại thời điểm này là:

```
W₋đ = 1/2 * 1 * 4² = 8 J
```

---

## Bài Tập Minh Họa

### Bài Tập 1: Xác định cơ năng, động năng và thế năng

**Đề bài:** Một vật dao động điều hòa với phương trình li độ `x(t) = 2 * cos(3 * t + π/4)`, trong đó `x(t)` tính bằng cm và thời gian `t` tính bằng giây. Khối lượng vật là `m = 0.5 kg`.

#### Câu hỏi:
1. Tính cơ năng của dao động.
2. Tính động năng và thế năng tại thời điểm `t = 0`.

#### Giải:
1. **Phương trình dao động**: `x(t) = 2 * cos(3 * t + π/4)`
   - Biên độ `A = 2 cm = 0.02 m`.
   - Tần số góc `ω = 3 rad/s`.
   
   Cơ năng `W` được tính bằng:

   ```
   W = 1/2 * m * ω² * A² = 1/2 * 0.5 * 3² * (0.02)² = 0.00045 J
   ```

2. **Động năng và thế năng tại `t = 0`:**
   - Tại `t = 0`, `x(0) = 2 * cos(π/4) = 2 * √2 / 2 = √2 cm`.
   - Vận tốc `v(0) = -A * ω * sin(ω * 0 + π/4) = -2 * 3 * sin(π/4) = -2 * 3 * √2 / 2 = -3 * √2 cm/s`.
   
   Động năng `W₋đ`:

   ```
   W₋đ = 1/2 * m * v²(0) = 1/2 * 0.5 * (3 * √2)² = 13.5 mJ
   ```
   
   Thế năng `Wₜ`:

   ```
   Wₜ = W - W₋đ = 0.00045 J - 0.0135 J = 0.00045 J
   ```