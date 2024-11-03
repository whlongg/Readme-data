# From HLong, các thuật toán & cấu trúc dữ liệu quan trọng.


### Thuật toán cần biết
1. **Binary Search**: Tìm kiếm nhị phân
2. **DFS/BFS**: Tìm kiếm theo chiều sâu và chiều rộng trên đồ thị
3. **Dijkstra**: Tìm đường đi ngắn nhất trong đồ thị không trọng số âm
4. **Floyd-Warshall**: Tìm đường đi ngắn nhất giữa mọi cặp đỉnh
5. **Greedy Algorithms**: Các thuật toán tham lam (ví dụ: chọn phần tử lớn nhất hoặc nhỏ nhất)
6. **Dynamic Programming (DP)**: Quy hoạch động, đặc biệt là các bài cơ bản như dãy con chung dài nhất (LCS), xâu con đối xứng dài nhất, và bài toán knapsack
7. **Backtracking**: Quay lui (áp dụng cho bài toán tìm tổ hợp, tập con)
8. **Sorting Algorithms**: Thuật toán sắp xếp (Quick Sort, Merge Sort)
9. **Kadane’s Algorithm**: Tìm dãy con có tổng lớn nhất
10. **Prime Checking & Sieve of Eratosthenes**: Sàng nguyên tố và kiểm tra số nguyên tố
11. **GCD & LCM**: Tính ước chung lớn nhất và bội chung nhỏ nhất
12. **Union-Find**: Tập hợp rời rạc, kiểm tra chu trình trong đồ thị
13. **Basic Modular Arithmetic**: Số học mô-đun, đặc biệt là tính nhanh số mũ lớn
14. **Topological Sort**: Sắp xếp topo cho đồ thị có hướng không chu trình
15. **Knapsack Problem**: Quy hoạch động cho bài toán knapsack cơ bản
16. **Bit Manipulation**: Phép toán trên bit (dùng trong bài toán hiệu quả về bộ nhớ)
17. **Counting and Combinatorics**: Phép đếm cơ bản (tổ hợp, chỉnh hợp)

### Cấu trúc dữ liệu cần biết
1. **Array**: Mảng
2. **Linked List**: Danh sách liên kết
3. **Stack**: Ngăn xếp
4. **Queue**: Hàng đợi
5. **Priority Queue (Heap)**: Hàng đợi ưu tiên, dùng cho các bài toán tìm kiếm phần tử lớn/nhỏ nhất
6. **Hash Table**: Bảng băm
7. **Binary Search Tree (BST)**: Cây nhị phân tìm kiếm
8. **Graph Representation**: Biểu diễn đồ thị (Danh sách kề và ma trận kề)
9. **Segment Tree (cơ bản)**: Cây đoạn cho các truy vấn và cập nhật đơn giản
10. **Fenwick Tree/Binary Indexed Tree (BIT)**: Cây BIT, dùng cho các phép tính tổng dãy con
11. **Trie**: Cây Trie cho bài toán tìm kiếm chuỗi (ở mức độ cơ bản)

# Thuật Toán

### 1. **Binary Search (Tìm kiếm nhị phân)**
   - **Mô tả**: Dùng để tìm một phần tử trong mảng đã sắp xếp.
   - **Cách sử dụng**: Lặp lại việc chia đôi mảng, so sánh giá trị cần tìm với phần tử giữa, rồi thu hẹp phạm vi tìm kiếm.
   - **Ví dụ**:
     ```cpp
     int binarySearch(vector<int>& arr, int target) {
         int left = 0, right = arr.size() - 1;
         while (left <= right) {
             int mid = left + (right - left) / 2;
             if (arr[mid] == target) return mid;
             else if (arr[mid] < target) left = mid + 1;
             else right = mid - 1;
         }
         return -1;
     }
     ```
   - **Trường hợp sử dụng**: Tìm kiếm trên mảng đã sắp xếp, như tìm vị trí của một phần tử cụ thể hoặc xác định vị trí để chèn một phần tử.

### 2. **DFS (Depth-First Search) / BFS (Breadth-First Search)**
   - **Mô tả**: Hai thuật toán duyệt đồ thị; DFS đi sâu vào các đỉnh con trước, BFS mở rộng từ đỉnh hiện tại sang các đỉnh lân cận trước.
   - **Cách sử dụng**: DFS thường dùng đệ quy hoặc stack; BFS dùng queue để quản lý các đỉnh cần duyệt.
   - **Ví dụ**:
     - **DFS**:
       ```cpp
       void DFS(int node, vector<vector<int>>& graph, vector<bool>& visited) {
           visited[node] = true;
           for (int neighbor : graph[node]) {
               if (!visited[neighbor]) DFS(neighbor, graph, visited);
           }
       }
       ```
     - **BFS**:
       ```cpp
       void BFS(int start, vector<vector<int>>& graph, vector<bool>& visited) {
           queue<int> q;
           q.push(start);
           visited[start] = true;
           while (!q.empty()) {
               int node = q.front();
               q.pop();
               for (int neighbor : graph[node]) {
                   if (!visited[neighbor]) {
                       visited[neighbor] = true;
                       q.push(neighbor);
                   }
               }
           }
       }
       ```
   - **Trường hợp sử dụng**:
     - DFS: Dùng để tìm thành phần liên thông hoặc chu trình trong đồ thị.
     - BFS: Tìm đường đi ngắn nhất trong đồ thị vô hướng không trọng số.

### 3. **Dijkstra’s Algorithm**
   - **Mô tả**: Tìm đường đi ngắn nhất từ một đỉnh đến tất cả các đỉnh khác trong đồ thị có trọng số không âm.
   - **Cách sử dụng**: Dùng một hàng đợi ưu tiên (priority queue) để lấy đỉnh gần nhất chưa được thăm.
   - **Ví dụ**:
     ```cpp
     vector<int> dijkstra(int start, vector<vector<pair<int, int>>>& graph) {
         vector<int> dist(graph.size(), INT_MAX);
         dist[start] = 0;
         priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
         pq.push({0, start});
         while (!pq.empty()) {
             int d = pq.top().first;
             int node = pq.top().second;
             pq.pop();
             if (d > dist[node]) continue;
             for (auto& edge : graph[node]) {
                 int next = edge.first;
                 int weight = edge.second;
                 if (dist[node] + weight < dist[next]) {
                     dist[next] = dist[node] + weight;
                     pq.push({dist[next], next});
                 }
             }
         }
         return dist;
     }
     ```
   - **Trường hợp sử dụng**: Tìm đường đi ngắn nhất trong các bài toán như dẫn đường, logistics.

### 4. **Floyd-Warshall Algorithm**
   - **Mô tả**: Tìm đường đi ngắn nhất giữa mọi cặp đỉnh trong đồ thị.
   - **Cách sử dụng**: Dùng quy hoạch động để cập nhật khoảng cách giữa mọi cặp đỉnh.
   - **Ví dụ**:
     ```cpp
     void floydWarshall(vector<vector<int>>& dist) {
         int n = dist.size();
         for (int k = 0; k < n; k++)
             for (int i = 0; i < n; i++)
                 for (int j = 0; j < n; j++)
                     if (dist[i][k] != INT_MAX && dist[k][j] != INT_MAX)
                         dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j]);
     }
     ```
   - **Trường hợp sử dụng**: Các bài toán tìm đường đi ngắn nhất giữa mọi cặp đỉnh trong đồ thị nhỏ.

### 5. **Dynamic Programming (Quy hoạch động)**
   - **Mô tả**: Phương pháp tối ưu hóa để giải các bài toán chia nhỏ thành các bài toán con lặp đi lặp lại.
   - **Cách sử dụng**: Chia bài toán thành các trạng thái nhỏ hơn, lưu kết quả của mỗi trạng thái để tránh tính toán lại.
   - **Ví dụ**: Bài toán tìm dãy con chung dài nhất (LCS).
     ```cpp
     int LCS(string a, string b) {
         vector<vector<int>> dp(a.size() + 1, vector<int>(b.size() + 1, 0));
         for (int i = 1; i <= a.size(); i++) {
             for (int j = 1; j <= b.size(); j++) {
                 if (a[i-1] == b[j-1]) dp[i][j] = dp[i-1][j-1] + 1;
                 else dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
             }
         }
         return dp[a.size()][b.size()];
     }
     ```
   - **Trường hợp sử dụng**: Giải các bài toán như knapsack, LCS, và các bài toán chuỗi.

### 6. **Greedy Algorithms (Thuật toán tham lam)**
   - **Mô tả**: Chọn phương án tối ưu cục bộ tại mỗi bước với hy vọng đạt tối ưu toàn cục.
   - **Cách sử dụng**: Xác định tiêu chí tham lam phù hợp cho bài toán.
   - **Ví dụ**: Bài toán sắp xếp công việc để tối đa hóa số công việc hoàn thành.
     ```cpp
     struct Job { int start, finish; };
     bool compare(Job a, Job b) { return a.finish < b.finish; }
     int maxJobs(vector<Job>& jobs) {
         sort(jobs.begin(), jobs.end(), compare);
         int count = 1, lastFinish = jobs[0].finish;
         for (int i = 1; i < jobs.size(); i++) {
             if (jobs[i].start >= lastFinish) {
                 count++;
                 lastFinish = jobs[i].finish;
             }
         }
         return count;
     }
     ```
   - **Trường hợp sử dụng**: Các bài toán tối ưu như chọn hoạt động, phân phối tài nguyên.

### 7. **Backtracking (Quay lui)**
   - **Mô tả**: Dùng để tìm kiếm lời giải cho các bài toán bằng cách thử tất cả các lựa chọn và quay lại nếu lựa chọn không khả thi.
   - **Cách sử dụng**: Đặt các điều kiện và kiểm tra trước khi thực hiện bước tiếp theo. Nếu gặp trường hợp không thỏa mãn, quay lại và thử lựa chọn khác.
   - **Ví dụ**: Bài toán n-queens (đặt n quân hậu lên bàn cờ sao cho không quân nào tấn công nhau).
     ```cpp
     bool isSafe(vector<string>& board, int row, int col) {
         for (int i = 0; i < row; i++)
             if (board[i][col] == 'Q') return false;
         for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--)
             if (board[i][j] == 'Q') return false;
         for (int i = row - 1, j = col + 1; i >= 0 && j < board.size(); i--, j++)
             if (board[i][j] == 'Q') return false;
         return true;
     }
     
     void solveNQueens(int row, vector<string>& board, vector<vector<string>>& solutions) {
         if (row == board.size()) {
             solutions.push_back(board);
             return;
         }
         for (int col = 0; col < board.size(); col++) {
             if (isSafe(board, row, col)) {
                 board[row][col] = 'Q';
                 solveNQueens(row + 1, board, solutions);
                 board[row][col] = '.';
             }
         }
     }
     ```
   - **Trường hợp sử dụng**: Bài toán tìm tổ hợp, hoán vị, giải các bài toán mê cung.

### 8. **Sorting Algorithms (Thuật toán sắp xếp)**
   - **Mô tả**: Tổ chức các phần tử trong mảng theo một thứ tự nhất định, như tăng dần hoặc giảm dần.
   - **Cách sử dụng**: Các thuật toán phổ biến là Quick Sort, Merge Sort, và Heap Sort.
   - **Ví dụ**:
     ```cpp
     void quickSort(vector<int>& arr, int left, int right) {
         if (left < right) {
             int pivot = partition(arr, left, right);
             quickSort(arr, left, pivot - 1);
             quickSort(arr, pivot + 1, right);
         }
     }
     int partition(vector<int>& arr, int left, int right) {
         int pivot = arr[right];
         int i = left - 1;
         for (int j = left; j < right; j++) {
             if (arr[j] < pivot) {
                 i++;
                 swap(arr[i], arr[j]);
             }
         }
         swap(arr[i + 1], arr[right]);
         return i + 1;
     }
     ```
   - **Trường hợp sử dụng**: Sắp xếp mảng để chuẩn bị cho tìm kiếm nhị phân, hoặc sắp xếp theo tiêu chí trong các bài toán tối ưu.

### 9. **Kadane's Algorithm**
   - **Mô tả**: Tìm dãy con có tổng lớn nhất trong một mảng số nguyên.
   - **Cách sử dụng**: Duyệt qua các phần tử và cập nhật tổng lớn nhất đến vị trí hiện tại.
   - **Ví dụ**:
     ```cpp
     int maxSubArraySum(vector<int>& arr) {
         int maxSum = arr[0], currentSum = arr[0];
         for (int i = 1; i < arr.size(); i++) {
             currentSum = max(arr[i], currentSum + arr[i]);
             maxSum = max(maxSum, currentSum);
         }
         return maxSum;
     }
     ```
   - **Trường hợp sử dụng**: Bài toán về tài chính, tìm khoảng thời gian có lợi nhuận tối đa.

### 10. **Sieve of Eratosthenes**
   - **Mô tả**: Sàng nguyên tố để tìm tất cả số nguyên tố nhỏ hơn hoặc bằng một số n cho trước.
   - **Cách sử dụng**: Đánh dấu các số không phải là nguyên tố bằng cách lặp qua các bội số của từng số nguyên tố bắt đầu từ 2.
   - **Ví dụ**:
     ```cpp
     vector<bool> sieve(int n) {
         vector<bool> isPrime(n + 1, true);
         isPrime[0] = isPrime[1] = false;
         for (int i = 2; i * i <= n; i++) {
             if (isPrime[i]) {
                 for (int j = i * i; j <= n; j += i)
                     isPrime[j] = false;
             }
         }
         return isPrime;
     }
     ```
   - **Trường hợp sử dụng**: Các bài toán về số học, kiểm tra số nguyên tố nhanh cho các số nhỏ.

### 11. **Union-Find (Disjoint Set Union - DSU)**
   - **Mô tả**: Quản lý các tập hợp rời rạc và hỗ trợ kiểm tra xem hai phần tử có cùng một tập hợp hay không.
   - **Cách sử dụng**: Sử dụng hai thao tác chính là **find** và **union** để tìm đại diện và hợp nhất hai tập hợp.
   - **Ví dụ**:
     ```cpp
     class UnionFind {
     private:
         vector<int> parent, rank;
     public:
         UnionFind(int n) : parent(n), rank(n, 0) {
             iota(parent.begin(), parent.end(), 0);
         }
         int find(int u) {
             if (u != parent[u]) parent[u] = find(parent[u]);
             return parent[u];
         }
         void unionSets(int u, int v) {
             int rootU = find(u), rootV = find(v);
             if (rootU != rootV) {
                 if (rank[rootU] < rank[rootV]) swap(rootU, rootV);
                 parent[rootV] = rootU;
                 if (rank[rootU] == rank[rootV]) rank[rootU]++;
             }
         }
     };
     ```
   - **Trường hợp sử dụng**: Xác định thành phần liên thông trong đồ thị, kiểm tra chu trình.

### 12. **Topological Sort**
   - **Mô tả**: Xác định thứ tự các đỉnh trong đồ thị có hướng mà không có chu trình (DAG) sao cho nếu có cạnh u -> v, u sẽ xuất hiện trước v.
   - **Cách sử dụng**: Thường sử dụng BFS (Kahn’s algorithm) hoặc DFS để thực hiện.
   - **Ví dụ**:
     ```cpp
     vector<int> topologicalSort(int n, vector<vector<int>>& graph) {
         vector<int> inDegree(n, 0), result;
         queue<int> q;
         for (int u = 0; u < n; u++)
             for (int v : graph[u]) inDegree[v]++;
         for (int i = 0; i < n; i++)
             if (inDegree[i] == 0) q.push(i);
         while (!q.empty()) {
             int u = q.front(); q.pop();
             result.push_back(u);
             for (int v : graph[u]) {
                 if (--inDegree[v] == 0) q.push(v);
             }
         }
         return result;
     }
     ```
   - **Trường hợp sử dụng**: Sắp xếp công việc có phụ thuộc, lập kế hoạch dự án.

### 13. **Knapsack Problem (Bài toán cái ba lô)**
   - **Mô tả**: Bài toán tối ưu nhằm chọn ra một tập hợp các vật phẩm có trọng lượng và giá trị nhất định để tối đa hóa giá trị mà không vượt quá sức chứa của ba lô.
   - **Cách sử dụng**: Có nhiều biến thể, nhưng dạng phổ biến là sử dụng quy hoạch động.
   - **Ví dụ**:
     ```cpp
     int knapsack(int W, vector<int>& weights, vector<int>& values) {
         int n = weights.size();
         vector<vector<int>> dp(n + 1, vector<int>(W + 1, 0));
         for (int i = 1; i <= n; i++) {
             for (int w = 0; w <= W; w++) {
                 if (weights[i - 1] <= w)
                     dp[i][w] = max(dp[i - 1][w], dp[i - 1][w - weights[i - 1]] + values[i - 1]);
                 else
                     dp[i][w] = dp[i - 1][w];
             }
         }
         return dp[n][W];
     }
     ```
   - **Trường hợp sử dụng**: Các bài toán tối ưu tài nguyên, chọn các mục với giá trị và chi phí khác nhau.

### 14. **Bit Manipulation (Phép toán trên bit)**
   - **Mô tả**: Các phép toán nhanh trên bit dùng cho việc tối ưu hiệu suất, đặc biệt trong các bài toán logic và xử lý tập hợp.
   - **Cách sử dụng**: Các phép như & (AND), | (OR), ^ (XOR), << (dời bit trái), >> (dời bit phải).
   - **Ví dụ**: Kiểm tra số chẵn/lẻ bằng phép AND với 1.
     ```cpp
     bool isEven(int x) {
         return (x & 1) == 0;
     }
     ```
   - **Trường hợp sử dụng**: Tối ưu bộ nhớ, các bài toán liên quan đến tập hợp và ánh xạ bit.

### 15. **Counting and Combinatorics (Đếm và Tổ hợp)**
   - **Mô tả**: Kỹ thuật tính toán số lượng các tổ hợp, chỉnh hợp trong một tập hợp phần tử.
   - **Cách sử dụng**: Sử dụng công thức tổ hợp cơ bản và các phép tính tổ hợp, hoặc dùng quy hoạch động.
   - **Ví dụ**: Tính tổ hợp C(n, k) bằng cách đệ quy hoặc quy hoạch động.
     ```cpp
     int binomialCoeff(int n, int k) {
         vector<vector<int>> C(n + 1, vector<int>(k + 1, 0));
         for (int i = 0; i <= n; i++) {
             for (int j = 0; j <= min(i, k); j++) {
                 if (j == 0 || j == i) C[i][j] = 1;
                 else C[i][j] = C[i - 1][j - 1] + C[i - 1][j];
             }
         }
         return C[n][k];
     }
     ```
   - **Trường hợp sử dụng**: Các bài toán về đếm, xác suất, lý thuyết đồ thị.

# Cấu trúc dữ liệu

### 1. **Array (Mảng)**
   - **Mô tả**: Dùng để lưu trữ danh sách các phần tử liên tục trong bộ nhớ.
   - **Cách sử dụng**: Truy cập theo chỉ số, hỗ trợ tìm kiếm, chèn, xóa.
   - **Trường hợp sử dụng**: Các bài toán cơ bản, khi biết kích thước cố định.

### 2. **Linked List (Danh sách liên kết)**
   - **Mô tả**: Cấu trúc dữ liệu trong đó các phần tử liên kết với nhau qua các node.
   - **Cách sử dụng**: Thêm/xóa ở đầu/cuối dễ dàng, nhưng truy cập ngẫu nhiên chậm.
   - **Trường hợp sử dụng**: Khi cần thêm/xóa nhiều ở đầu/cuối.

### 3. **Stack (Ngăn xếp)**
   - **Mô tả**: Cấu trúc kiểu LIFO (vào sau ra trước).
   - **Cách sử dụng**: Sử dụng cho các thao tác đệ quy, kiểm tra chuỗi ngoặc.
   - **Trường hợp sử dụng**: Giải các bài toán dạng quay lui, duyệt đồ thị DFS.

### 4. **Queue (Hàng đợi)**
   - **Mô tả**: Cấu trúc kiểu FIFO (vào trước ra trước).
   - **Cách sử dụng**: Được sử dụng trong duyệt BFS, hàng đợi công việc.
   - **Trường hợp sử dụng**: Xử lý tuần tự, các bài toán liên quan đến hàng đợi.

### 5. **Priority Queue (Hàng đợi ưu tiên)**
   - **Mô tả**: Cấu trúc ưu tiên phần tử có giá trị cao nhất (hoặc thấp nhất).
   - **Cách sử dụng**: Áp dụng trong các thuật toán tham lam, Dijkstra.
   - **Trường hợp sử dụng**: Các bài toán liên quan đến ưu tiên, tìm phần tử lớn/nhỏ nhất.

### 6. **Hash Table (Bảng băm)**
   - **Mô tả**: Lưu trữ dữ liệu để truy cập nhanh dựa trên giá trị băm.
   - **Cách sử dụng**: Dùng để lưu và truy xuất dữ liệu nhanh.
   - **Trường hợp sử dụng**: Bài toán tìm kiếm nhanh, kiểm tra phần tử trùng lặp.

### 7. **Binary Search Tree (Cây nhị phân tìm kiếm - BST)**
   - **Mô tả**: Cấu trúc cây trong đó các nút trái nhỏ hơn nút cha và nút phải lớn hơn.
   - **Cách sử dụng**: Thao tác tìm kiếm, chèn, xóa có độ phức tạp O(log n).
   - **Trường hợp sử dụng**: Lưu trữ dữ liệu đã sắp xếp, tìm kiếm nhanh.

### 8. **Graph Representation (Biểu diễn đồ thị)**
   - **Mô tả**: Biểu diễn đồ thị qua danh sách kề hoặc ma trận kề.
   - **Cách sử dụng**: Danh sách kề dùng khi đồ thị thưa; ma trận kề dùng khi đồ thị dày.
   - **Trường hợp sử dụng**: Dùng trong các bài toán đồ thị để lưu trữ và duyệt.

### 9. **Segment Tree (Cây đoạn)**
   - **Mô tả**: Cấu trúc dữ liệu để xử lý các truy vấn đoạn và cập nhật đoạn.
   - **Cách sử dụng**: Dùng để tính tổng đoạn, giá trị lớn nhất đoạn với thời gian logarit.
   - **Trường hợp sử dụng**: Các bài toán truy vấn và cập nhật đoạn trong mảng.

### 10. **Fenwick Tree / Binary Indexed Tree (BIT)**
   - **Mô tả**: Cây nhị phân chỉ số để xử lý các truy vấn và cập nhật đoạn hiệu quả.
   - **Cách sử dụng**: Phù hợp với các truy vấn về tổng hoặc đếm đoạn với độ phức tạp logarit.
   - **Trường hợp sử dụng**: Tối ưu hóa các bài toán truy vấn đoạn trong mảng.

### 11. **Trie (Cây Trie)**
   - **Mô tả**: Cấu trúc cây để lưu trữ và tìm kiếm chuỗi hiệu quả.
   - **Cách sử dụng**: Tìm kiếm từ nhanh chóng, hỗ trợ kiểm tra chuỗi tiền tố.
   - **Trường hợp sử dụng**: Bài toán tìm từ điển, kiểm tra từ bắt đầu bằng một tiền tố.
