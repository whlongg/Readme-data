# From HLong, các kĩ thuật tối ưu code C++

### 1. **Sử dụng `ios_base::sync_with_stdio(false);` và `cin.tie(nullptr);`**

   - **Nguyên lí**: Vô hiệu hóa đồng bộ hóa giữa `cin`/`cout` và `scanf`/`printf` giúp tăng tốc độ I/O.
   - **Ví dụ**:
     ```cpp
     #include <iostream>
     using namespace std;

     int main() {
         ios_base::sync_with_stdio(false);
         cin.tie(nullptr);

         int n;
         cin >> n;
         cout << n << "\n";
         return 0;
     }
     ```
   - **Trường hợp sử dụng**: Khi cần xử lý đầu vào/đầu ra nhanh chóng, ví dụ khi đọc và ghi số lượng lớn dữ liệu.

---

### 2. **Sử dụng `scanf` và `printf` thay vì `cin` và `cout`**

   - **Nguyên lí**: `scanf` và `printf` nhanh hơn `cin` và `cout` trong các bài toán yêu cầu tốc độ cao.
   - **Ví dụ**:
     ```cpp
     #include <cstdio>

     int main() {
         int n;
         scanf("%d", &n);
         printf("%d\n", n);
         return 0;
     }
     ```
   - **Trường hợp sử dụng**: Khi cần hiệu suất đầu vào/đầu ra tối ưu, đặc biệt trong các bài toán xử lý dữ liệu lớn.

---

### 3. **Sử dụng `\n` thay vì `endl`**

   - **Nguyên lí**: `endl` thêm dấu xuống dòng và xả (flush) bộ đệm, gây chậm hơn so với `\n`.
   - **Ví dụ**:
     ```cpp
     #include <iostream>
     using namespace std;

     int main() {
         cout << "Hello World\n";  // Nhanh hơn so với cout << "Hello World" << endl;
         return 0;
     }
     ```
   - **Trường hợp sử dụng**: Khi chỉ cần xuống dòng mà không cần xả bộ đệm, ví dụ khi xuất nhiều dòng liên tiếp.

---

### 4. **Sử dụng `++i` thay vì `i++`**

   - **Nguyên lí**: `++i` không tạo biến tạm nên nhanh hơn `i++`, đặc biệt trong vòng lặp lớn.
   - **Ví dụ**:
     ```cpp
     for (int i = 0; i < n; ++i) {
         // Do something
     }
     ```
   - **Trường hợp sử dụng**: Khi lặp qua nhiều phần tử và không cần giữ giá trị trước khi tăng biến.

---

### 5. **Xử lý bit thay vì nhân và chia cho `2^x`**

   - **Nguyên lí**: Dịch trái/phải nhanh hơn phép nhân/chia, thích hợp khi nhân hoặc chia cho số mũ của 2.
   - **Ví dụ**:
     ```cpp
     int n = 8;
     int result_multiply = n << 2; // Nhân n với 2^2, tương đương 8 * 4 = 32
     int result_divide = n >> 1;   // Chia n cho 2^1, tương đương 8 / 2 = 4
     ```
   - **Trường hợp sử dụng**: Khi cần tính toán nhân/chia nhanh với các số mũ của 2.

---

### 6. **Kiểm tra tính chẵn lẻ bằng phép AND**

   - **Nguyên lí**: Kiểm tra `n & 1` để xác định tính chẵn lẻ của `n`, nhanh hơn phép chia.
   - **Ví dụ**:
     ```cpp
     int n = 5;
     if (n & 1) {
         cout << "n là số lẻ\n";
     } else {
         cout << "n là số chẵn\n";
     }
     ```
   - **Trường hợp sử dụng**: Kiểm tra tính chẵn lẻ trong các vòng lặp hoặc điều kiện phức tạp.

---

### 7. **Sử dụng mảng tĩnh thay vì `vector` khi có thể**

   - **Nguyên lí**: Mảng tĩnh có độ phức tạp thấp hơn và nhanh hơn `vector`.
   - **Ví dụ**:
     ```cpp
     int arr[100];  // Mảng tĩnh với kích thước cố định
     ```
   - **Trường hợp sử dụng**: Khi kích thước mảng được biết trước và không thay đổi trong quá trình xử lý.

---

### 8. **Truyền tham số bằng tham chiếu**

   - **Nguyên lí**: Truyền tham số bằng tham chiếu giúp tránh sao chép dữ liệu, tiết kiệm bộ nhớ.
   - **Ví dụ**:
     ```cpp
     void process(const vector<int>& data) {
         // Xử lý data mà không sao chép
     }
     ```
   - **Trường hợp sử dụng**: Khi truyền đối tượng lớn hoặc mảng vào hàm để tối ưu hóa bộ nhớ.

---

### 9. **Sử dụng `aligned_alloc()` thay vì `malloc()`**

   - **Nguyên lí**: `aligned_alloc()` cho phép cấp phát bộ nhớ tối ưu và căn chỉnh dữ liệu, hiệu quả cho các hệ thống yêu cầu hiệu suất cao.
   - **Ví dụ**:
     ```cpp
     int* data = static_cast<int*>(aligned_alloc(alignof(int), sizeof(int) * n));
     ```
   - **Trường hợp sử dụng**: Khi cần căn chỉnh bộ nhớ, đặc biệt trên các kiến trúc yêu cầu điều chỉnh bộ nhớ cao.

---

### 10. **Sử dụng thuật toán tối ưu hóa của Knuth**

   - **Nguyên lí**: Knuth tối ưu hóa thuật toán bằng cách giảm số lần truy cập và thao tác dữ liệu.
   - **Ví dụ**:
     ```cpp
     // Ví dụ minh họa thuật toán tối ưu hóa của Knuth có thể được áp dụng
     // cho nhiều bài toán sắp xếp và tính toán trong lập trình thi đấu.
     ```
   - **Trường hợp sử dụng**: Khi xử lý dữ liệu lớn và cần giảm thiểu số phép tính lặp lại.

---

### 11. **Ưu tiên biến cục bộ hơn biến toàn cục**

   - **Nguyên lí**: Biến cục bộ được lưu trong stack và nhanh hơn biến toàn cục, tránh chiếm dung lượng bộ nhớ toàn cục.
   - **Ví dụ**:
     ```cpp
     void process() {
         int local_var = 10; // Biến cục bộ trong hàm
     }
     ```
   - **Trường hợp sử dụng**: Khi có thể sử dụng biến cục bộ trong hàm mà không cần biến toàn cục.

---

### 12. **Hạn chế sử dụng `float` khi có thể**

   - **Nguyên lí**: `float` ít chính xác và hiệu suất thấp hơn `int`, `double` cho các phép tính số nguyên.
   - **Ví dụ**:
     ```cpp
     double d = 1.0 / 3.0;  // Chính xác hơn so với float
     ```
   - **Trường hợp sử dụng**: Khi phép tính không yêu cầu giá trị thập phân hoặc tính toán chính xác cao.

---

### 13. **Sử dụng từ khóa `register` (nếu có thể)**

   - **Nguyên lí**: Từ khóa `register` yêu cầu compiler lưu biến vào thanh ghi CPU, tăng tốc truy cập.
   - **Ví dụ**:
     ```cpp
     register int i = 0; // Đề xuất lưu biến vào thanh ghi CPU
     ```
   - **Trường hợp sử dụng**: Khi cần truy cập nhiều vào biến trong vòng lặp.

---

### 14. **Tránh tạo đối tượng mới nếu có thể tái sử dụng**

   - **Nguyên lí**: Tạo và hủy đối tượng tiêu tốn tài nguyên; tái sử dụng sẽ tối ưu hơn.
   - **Ví dụ**:
     ```cpp
     vector<int> data(100);
     data.clear();  // Tái sử dụng thay vì tạo vector mới
     ```
   - **Trường hợp sử dụng**: Khi cần tạo nhiều đối tượng cùng kiểu, như trong các thuật toán xử lý nhiều phần tử.

---

### 15. **Tránh sử dụng đệ quy sâu nếu có thể**

   - **Nguyên lí**: Đệ quy sâu có thể gây tràn stack; thuật toán lặp giúp tiết kiệm bộ nhớ.
   - **Ví dụ**:
     ```cpp
     // Tính giai thừa bằng vòng lặp thay vì đệ quy
     int factorial(int n) {
         int result = 1;
         for (int i = 2; i <= n; ++i) result *= i;
         return result;
     }
     ```
   - **Trường hợp sử dụng**: Khi giới hạn độ sâu đệ quy có thể bị vượt quá hoặc tối ưu không gian bộ nhớ là cần thiết.
### 16. **Sử dụng `memset` để khởi tạo nhanh mảng**

   - **Nguyên lí**: `memset` hiệu quả hơn vòng lặp khi khởi tạo mảng với giá trị cố định.
   - **Ví dụ**:
     ```cpp
     int arr[1000];
     memset(arr, 0, sizeof(arr));  // Khởi tạo tất cả phần tử của arr thành 0
     ```
   - **Trường hợp sử dụng**: Khi cần đặt toàn bộ mảng về một giá trị nhất định, thường là `0` hoặc `-1`.

---

### 17. **Dùng `std::pair` để gán nhanh hai giá trị**

   - **Nguyên lí**: `std::pair` cho phép gán nhanh hai giá trị cùng lúc, tiết kiệm dòng lệnh và rõ ràng.
   - **Ví dụ**:
     ```cpp
     std::pair<int, int> p = {1, 2};
     ```
   - **Trường hợp sử dụng**: Khi cần lưu trữ cặp giá trị, chẳng hạn như tọa độ hoặc các tham số đi kèm.

---

### 18. **Ưu tiên sử dụng `auto` để giảm thời gian biên dịch**

   - **Nguyên lí**: `auto` giúp compiler suy diễn kiểu, giảm thời gian và số dòng code.
   - **Ví dụ**:
     ```cpp
     auto it = m.begin();
     ```
   - **Trường hợp sử dụng**: Khi kiểu dữ liệu phức tạp hoặc không cần khai báo rõ ràng.

---

### 19. **Sử dụng `std::move` để chuyển dữ liệu thay vì sao chép**

   - **Nguyên lí**: `std::move` chuyển tài nguyên thay vì sao chép, tránh tạo bản sao không cần thiết.
   - **Ví dụ**:
     ```cpp
     vector<int> v = {1, 2, 3};
     vector<int> new_v = std::move(v);  // Chuyển tài nguyên từ v sang new_v
     ```
   - **Trường hợp sử dụng**: Khi cần chuyển dữ liệu từ biến tạm mà không cần bản sao.

---

### 20. **Sử dụng `std::array` cho mảng tĩnh**

   - **Nguyên lí**: `std::array` an toàn và hiệu quả hơn mảng C thông thường.
   - **Ví dụ**:
     ```cpp
     std::array<int, 100> arr;
     ```
   - **Trường hợp sử dụng**: Khi mảng có kích thước cố định và cần bảo toàn hiệu suất.

---

### 21. **Dùng `unordered_set` thay vì `vector` để loại bỏ trùng lặp**

   - **Nguyên lí**: `unordered_set` có O(1) cho thêm và kiểm tra trùng lặp, tốt hơn `vector`.
   - **Ví dụ**:
     ```cpp
     std::unordered_set<int> s;
     s.insert(10);
     ```
   - **Trường hợp sử dụng**: Khi cần lưu các giá trị duy nhất và tốc độ là yếu tố chính.

---

### 22. **Kỹ thuật "Sáng tạo với Modulo" để tránh số lớn**

   - **Nguyên lí**: Dùng modulo giúp ngăn tràn số khi thực hiện phép nhân lớn.
   - **Ví dụ**:
     ```cpp
     int mod = 1e9 + 7;
     int result = (a * b) % mod;
     ```
   - **Trường hợp sử dụng**: Trong các bài toán số học lớn hoặc tính toán modulo thường gặp.

---

### 23. **Sử dụng `__builtin_popcount` để đếm bit 1**

   - **Nguyên lí**: `__builtin_popcount` nhanh hơn cách thủ công khi đếm số bit 1.
   - **Ví dụ**:
     ```cpp
     int count = __builtin_popcount(15);  // Kết quả là 4 cho số 1111 trong hệ nhị phân
     ```
   - **Trường hợp sử dụng**: Khi cần đếm số bit 1 trong số nguyên lớn.

---

### 24. **Sử dụng `inline` cho hàm nhỏ để tối ưu hóa**

   - **Nguyên lí**: `inline` giúp tránh việc gọi hàm và tăng hiệu suất, đặc biệt với hàm nhỏ.
   - **Ví dụ**:
     ```cpp
     inline int square(int x) { return x * x; }
     ```
   - **Trường hợp sử dụng**: Khi hàm ngắn gọn và gọi nhiều lần trong mã.

---

### 25. **Ưu tiên toán tử ba ngôi thay cho `if-else` đơn giản**

   - **Nguyên lí**: Toán tử ba ngôi thường nhanh và rõ ràng hơn với điều kiện đơn giản.
   - **Ví dụ**:
     ```cpp
     int max_val = (a > b) ? a : b;
     ```
   - **Trường hợp sử dụng**: Khi so sánh đơn giản và gọn gàng.

---

### 26. **Tối ưu hóa phép tính với `const`**

   - **Nguyên lí**: `const` giúp compiler tối ưu hóa, tránh thay đổi giá trị và tăng tốc độ.
   - **Ví dụ**:
     ```cpp
     const int MAX_SIZE = 100;
     ```
   - **Trường hợp sử dụng**: Với biến không thay đổi sau khi khởi tạo.

---

### 27. **Dùng `reserve()` để tối ưu dung lượng bộ nhớ cho `vector`**

   - **Nguyên lí**: Dùng `reserve()` để đặt dung lượng ban đầu cho `vector`, tránh cấp phát bộ nhớ nhiều lần.
   - **Ví dụ**:
     ```cpp
     vector<int> v;
     v.reserve(100);
     ```
   - **Trường hợp sử dụng**: Khi kích thước vector có thể biết trước.

---

### 28. **Giảm số lần gọi hàm với biến tạm**

   - **Nguyên lí**: Biến tạm giúp tránh gọi lại hàm nhiều lần và tối ưu hóa hiệu suất.
   - **Ví dụ**:
     ```cpp
     int len = v.size();
     for (int i = 0; i < len; ++i) { /* ... */ }
     ```
   - **Trường hợp sử dụng**: Khi hàm được gọi nhiều lần trong vòng lặp.

---

### 29. **Ưu tiên `emplace_back` thay vì `push_back` cho các container**

   - **Nguyên lí**: `emplace_back` tạo đối tượng ngay trong container, không tạo bản sao như `push_back`.
   - **Ví dụ**:
     ```cpp
     vector<pair<int, int>> v;
     v.emplace_back(1, 2);
     ```
   - **Trường hợp sử dụng**: Khi thêm phần tử vào `vector` và cần hiệu suất cao hơn.

---

### 30. **Sử dụng `lower_bound`/`upper_bound` để tìm kiếm nhị phân**

   - **Nguyên lí**: `lower_bound` và `upper_bound` cung cấp cách tìm kiếm nhanh với độ phức tạp O(log n).
   - **Ví dụ**:
     ```cpp
     vector<int> v = {1, 3, 5, 7};
     auto pos = lower_bound(v.begin(), v.end(), 5);
     ```
   - **Trường hợp sử dụng**: Khi cần tìm vị trí của phần tử trong mảng đã sắp xếp.
