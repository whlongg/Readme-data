# Hướng dẫn sử dụng công cụ tóm tắt bài báo khoa học

Công cụ này giúp bạn tìm kiếm và tóm tắt nội dung của các bài báo khoa học một cách nhanh chóng thông qua giao diện dòng lệnh (CLI).

## Cách sử dụng

1. **Mở Terminal hoặc Command Prompt:**  Đảm bảo bạn đã mở cửa sổ dòng lệnh trên máy tính của mình.
2. **Di chuyển đến thư mục chứa tool:** Sử dụng lệnh `cd` để di chuyển đến thư mục nơi bạn đã lưu trữ file Python của công cụ này (ví dụ: `cd path/to/your/tool`).
3. **Chạy công cụ:** Gõ lệnh sau và nhấn Enter để khởi chạy công cụ:

    ```bash
    python your_script_name.py
    ```

    *(Thay thế `your_script_name.py` bằng tên thực tế của file Python)*
    *Mặc định là news.py*
   
## Giao diện Menu

Sau khi khởi chạy, bạn sẽ thấy một banner và menu chính hiển thị các tùy chọn. Để chọn một tùy chọn, hãy nhập số tương ứng với tùy chọn đó và nhấn Enter.

### Menu Chính

Menu chính cung cấp các chức năng sau:

*   **1. Tìm bài (Search) qua từ khoá:**
    *   Chọn tùy chọn này để tìm kiếm các bài báo khoa học dựa trên từ khóa bạn nhập vào.
    *   Công cụ sẽ hỏi bạn nhập từ khóa tìm kiếm và số lượng bài báo bạn muốn tìm.
    *   Kết quả tìm kiếm sẽ được hiển thị và lưu vào file `news.txt`.

*   **2. Summaries Menu (Tóm tắt + Quản lý CHỌN):**
    *   Chọn tùy chọn này để truy cập menu con với các chức năng liên quan đến việc tóm tắt và quản lý các bài báo đã chọn.

*   **3. Thêm link trực tiếp:**
    *   Chọn tùy chọn này để thêm trực tiếp các liên kết (URL) của bài báo mà bạn muốn tóm tắt.
    *   Bạn có thể nhập nhiều liên kết, cách nhau bằng dấu phẩy.

*   **4. Thoát:**
    *   Chọn tùy chọn này để đóng công cụ.

### Summaries Menu (Menu Tóm Tắt)

Nếu bạn chọn tùy chọn `2` từ menu chính, bạn sẽ được đưa đến menu con này:

*   **1. Summarize CHỌN:**
    *   Chọn tùy chọn này để tóm tắt các bài báo đã được thêm vào danh sách "CHỌN".
    *   Công cụ có thể hỏi bạn nhập một prompt tùy chỉnh cho việc tóm tắt, hoặc bạn có thể để trống để sử dụng prompt mặc định.
    *   Kết quả tóm tắt sẽ được hiển thị và lưu vào file `result.md`.

*   **2. Sửa danh sách CHỌN:**
    *   Chọn tùy chọn này để chỉnh sửa danh sách các bài báo bạn đã "CHỌN" để tóm tắt.
    *   Bạn có thể xóa bớt bài hoặc thêm bài từ danh sách "STORED" (các bài đã tìm kiếm hoặc thêm trước đó).

*   **3. Tóm tắt từ link (auto-chọn link mới):**
    *   Chọn tùy chọn này để nhập các liên kết bài báo và tự động thêm chúng vào danh sách "CHỌN" trước khi tiến hành tóm tắt.
    *   Bạn có thể nhập nhiều liên kết, cách nhau bằng dấu phẩy.

*   **4. Quay lại:**
    *   Chọn tùy chọn này để trở lại menu chính.

## Lưu ý khi sử dụng

*   Hãy chắc chắn rằng bạn đã cài đặt đầy đủ các thư viện cần thiết trước khi chạy công cụ. Công cụ sẽ tự động kiểm tra và cài đặt nếu thiếu khi khởi động.
*   Đọc kỹ các hướng dẫn hiển thị trên màn hình để hiểu rõ hơn về cách nhập liệu và tương tác với công cụ.
*   Vui lòng xem kĩ video NẾU không hiểu cách sử dụng.
