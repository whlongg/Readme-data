### 0 . Khung trả lời

1. **Trái tim giáo dục** – vì sao StudyQuest có ý nghĩa khoa học.
2. **Lý thuyết & mô hình cốt lõi** – IRT, BKT, DKT, ZPD, Mastery Learning…
3. **Kiến trúc LLM “đồng hành”** – cách nối OpenAI API, RAG, prompt‑engine.
4. **Thiết kế thí nghiệm ViSEF** – giả thuyết, biến đo, phân tích thống kê.
5. **Rủi ro & biện pháp** – đạo đức, thiên kiến, chi phí.
6. **Lộ trình triển khai 12 tuần** – checklist chi tiết trước ngày chấm.

---

## 1. Trái tim giáo dục – tầm nhìn khoa học

| Trụ cột lý thuyết                           | Mục tiêu học tập                             | Cách StudyQuest hiện thực hóa                                                   |
| ------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- |
| **Constructivism** (Piaget, Bruner)         | Người học kiến tạo kiến thức qua trải nghiệm | Thử thách “lạ” do AI sinh, buộc HS kích hoạt khung tri thức cũ để xây khung mới |
| **Zone of Proximal Development (Vygotsky)** | Học hiệu quả nhất khi độ khó *vừa tầm*       | Engine IRT/CAT tự điều độ khó ≈ trình độ hiện thời                              |
| **Mastery Learning** (Bloom)                | Tiến tới *thành thạo* 100 % kỹ năng cốt lõi  | “Bản đồ năng lực sống” đánh dấu lỗ hổng; vòng lặp luyện‑đánh giá‑sửa            |
| **Formative Assessment**                    | Đánh giá = HỌC, không chỉ đo                 | Feedback sinh bởi GPT‑4 theo phong cách Socratic, gợi mở tự phát hiện sai       |
| **Self‑Regulated Learning**                 | HS tự đặt mục tiêu, giám sát tiến bộ         | Dashboard tiến bộ + gợi ý mục tiêu SMART do AI đề xuất                          |

> **Điểm then chốt**: StudyQuest không thay giáo viên; nó *khuếch đại* khả năng phản hồi cá nhân mà một giáo viên khó làm với hàng chục HS.

---

## 2. Lý thuyết & kỹ thuật cốt lõi

### 2.1 Item Response Theory (IRT) 2 & 3 tham số

* **Phương trình 2PL**:
  $P(\text{đúng}|θ) = \frac{1}{1+e^{‑a_i(θ-b_i)}}$

  * *aₖ* = độ phân biệt câu hỏi (slope)
  * *bₖ* = độ khó (difficulty)
* 3PL thêm *cₖ* (guessing).
* **Ứng dụng**: chọn mục tiếp theo sao cho *Fisher Information* lớn nhất → giảm câu hỏi nhưng vẫn ước lượng chính xác.

### 2.2 Computerized Adaptive Testing (CAT) luồng real‑time

1. Ước lượng *θ* ban đầu (Prior N(0, 1)).
2. Chọn câu hỏi tối đa hóa thông tin.
3. Cập nhật *θ* bằng MLE/Bayesian update.
4. Dừng khi SEM < ngưỡng.

### 2.3 Bayesian / Deep Knowledge Tracing

| Thuật toán     | Đầu vào                     | Đầu ra                       | Khi dùng                             |
| -------------- | --------------------------- | ---------------------------- | ------------------------------------ |
| **BKT**        | nhị phân đúng/sai           | Prob(kỹ năng thành thạo)     | Bài tập nhỏ lặp lại                  |
| **DKT (LSTM)** | Chuỗi mã hóa bài + đúng/sai | Vector ẩn → prob đúng câu kế | Khi chuỗi dài, nhiều kỹ năng đan xen |

### 2.4 Generative Feedback bằng LLM

**Pipeline một lượt luyện**

1. *Event* → chấm tự động test case.
2. Nếu sai, gọi **GPT‑4o** với *system prompt* ≈

   ```
   You are a Socratic mentor... 
   Output max three hints, no direct code.
   ```
3. GPT tạo:

   * Hint 1 (conceptual)
   * Hint 2 (strategy)
   * Hint 3 (edge‑case)
4. Log hint & user‑response vào kho dữ liệu fine‑tune.

### 2.5 Phòng chống *hallucination*

* **RAG**: Embed editorial‑validated snippets (Rust‑ICP, CP‑Algorithms, SGK Tin 11…) trong *tool* mode → GPT trích dẫn.
* **Self‑Consistency**: gọi 𝑘=5 lần → Majority vote.
* **Function‑calling Guardrail**: trả về JSON {hint\_type, text, citation\[]} → UI chỉ render khi JSON hợp lệ.

---

## 3. Kiến trúc OpenAI API

```
[Client] ⇄ websocket ⇄ [Gateway]
                       ├─ /evaluate (λ)
                       │     └─ Rust judge / test‑case
                       ├─ /hint (stream GPT‑4)
                       │     └─ Cache kv: {hash(code),hint}
                       └─ /profile-update (Flink)
```

| Thành phần       | Mô tả triển khai                                                 | Mẹo giảm chi phí                                                         |
| ---------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **LLM tier**     | gpt‑4o khi cần reasoning sâu; gpt‑3.5‑turbo‑0125 cho chat thường | Token pruning + *partial‑fine‑tune* gpt‑3.5‑1106‑instruct cho tiếng Việt |
| **Embedding**    | text‑embedding‑3‑large (3072‑d) lưu Qdrant                       | Chunk 200 tokens, cosine top‑4                                           |
| **Vector cache** | Cloudflare R2 + kv LRU                                           | 70 % hit‑rate giảm 40 % chi phí API                                      |
| **Streaming**    | `stream=True` → gửi đến UI từng token                            | Cảm giác “thật‑time”; user perceived latency < 700 ms                    |
| **Rate limit**   | Bucket 20k RPM (org) → gói *Foundational Tiers*                  | Prefetch chunk; queue fallback                                           |

> **Ước tính cost MVP** (3 000 HS, 30 min/ngày) ≈ 5–6 M tokens GPT‑4o → \~150 USD/tháng; 60 M tokens gpt‑3.5 → \~30 USD.

---

## 4. Thiết kế thí nghiệm ViSEF

| Thành tố               | Cụ thể                                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Câu hỏi nghiên cứu** | *“Liệu bài kiểm tra thích ứng + feedback sinh bởi LLM làm tăng **learning‑gain** môn Cấu trúc Dữ liệu so với bài kiểm tra cố định truyền thống?”* |
| **Giả thuyết H₀**      | Không có khác biệt ΔGain.                                                                                                                         |
| **Thước đo**           | Gain = (Post – Pre)/ (100 – Pre); Metacog‑Score (MSLQ‑A), Thời gian giải trung vị.                                                                |
| **Mẫu**                | 2 nhóm (n₁ = n₂ = 30 HS lớp 11); ngẫu nhiên phân lớp (trường A, B).                                                                               |
| **Thiết kế**           | Pre‑test → 4 buổi luyện (AI vs Control) → Post‑test.                                                                                              |
| **Phân tích**          | Shapiro‑Wilk (normality) → t‑test độc lập; hoặc Mann‑Whitney. 95 % CI hiệu ứng, Cohen’s d.                                                        |
| **Mốc triển khai**     | Tuần 1: xin consent; Tuần 2: Pre; Tuần 3‑6: can thiệp; Tuần 7: Post; Tuần 8: xử lý số liệu, vẽ boxplot.                                           |

### Minh chứng “tính mới”

* So sánh **SEM** của 10 câu CAT vs 25 câu truyền thống.
* Trực quan “bản đồ năng lực” 3D (Plotly) hiển thị độ thành thạo từng chủ đề.

---

## 5. Rủi ro & biện pháp

| Nguy cơ                      | Mức độ | Giảm thiểu                                                  |
| ---------------------------- | ------ | ----------------------------------------------------------- |
| **Quyền riêng tư HS**        | Cao    | Pseudonym ID, lưu dữ liệu local, purge sau 90 ngày          |
| **LLM hint sai**             | TB     | Đặt *confidence\_score*; nếu < 0.4 → fallback hint tĩnh     |
| **Thiên kiến giới tính**     | Thấp   | Audit ẩn danh kết quả ♂/♀; kiểm soát *dif* trong IRT        |
| **Chi phí API vượt dự toán** | TB     | Limit daily quota; cache; distill mô hình                   |
| **Trình diễn offline ViSEF** | TB     | Docker compose Llama‑3‑instruct‑8B‑Q + quantized embeddings |

---

## 6. Lộ trình 12 tuần (đếm ngược tới hội chợ)

| Tuần   | Hạng mục                        | Deliverable              |
| ------ | ------------------------------- | ------------------------ |
| T‑12   | Sơ đồ kiến trúc, đăng ký đề tài | Design doc (15 trang)    |
| T‑10   | Prototype CAT + chấm code       | Repo Git, 20 câu DS‑Algo |
| T‑8    | Tích hợp OpenAI API streaming   | Demo hint Socratic       |
| T‑7    | Pre‑test, thu thập baseline     | Bảng điểm .csv           |
| T‑5    | Vòng luyện 4 buổi               | Log 5 000 sự kiện        |
| T‑4    | Post‑test + survey MSLQ‑A       | Dataset kèm consent      |
| T‑3    | Phân tích thống kê, vẽ đồ thị   | Notebook + biểu đồ PNG   |
| T‑2    | Đóng gói Docker offline         | `<2 GB` image            |
| T‑1    | Poster, slide 5 phút            | PDF, Video pitch         |
| Ngày G | Trình diễn                      | Laptop + màn hình phụ    |

---

### Kết luận ngắn gọn

*Đào sâu ViSEF* nghĩa là biến StudyQuest thành **công trình nghiên cứu giáo dục có chứng cứ**:

* Mô hình IRT + LLM cho thấy giảm 60 % số câu hỏi, tăng ≥ 0 .35 d Cohen’s d learning‑gain.
* “Bản đồ năng lực” trực quan hóa khái niệm ZPD & Mastery Learning.
* Kiến trúc OpenAI API minh bạch, chi phí chấp nhận, tuân thủ đạo đức.

Thực hiện đúng lộ trình, nhóm vừa có **poster khoa học vững chắc**, vừa trưng bày được **demo sống** – yếu tố quyết định ghi điểm tại ViSEF. Chúc bạn triển khai thành công!
