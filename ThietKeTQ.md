## Thiết kế Hệ thống Học tập Nhập vai - CHRONOSCAPE

**#1. Kiến trúc Tổng quan**

**1.1. Mục tiêu**

*   **Trải nghiệm học tập nhập vai:** Biến việc học ở *mọi lĩnh vực* thành một cuộc phiêu lưu RPG thú vị, đầy động lực, thúc đẩy người dùng học tập chủ động và liên tục.
*   **Gamification toàn diện:** Tích hợp đầy đủ các yếu tố trò chơi để tăng tính tương tác và hứng thú:
    *   **Nhiệm vụ (Quests):** Đa dạng, phong phú, bao gồm:
        *   **Loại nhiệm vụ:** Đọc tài liệu, Làm bài tập trắc nghiệm, Xem video bài giảng, Tham gia thảo luận, Viết bài luận, Thực hành kỹ năng, Làm project, *Quest tùy chỉnh (do người dùng tạo)*.
        *   **Phân loại:** Theo Môn học (Toán, Lý, Hóa, Văn, Sử, Địa...), Chủ đề (Học toán 45 phút, học tiếng Anh 45 phút,...etc), Loại nhiệm vụ, Độ khó (Dễ, Trung bình, Khó - phân theo thời gian, chủ đề).
        *   **Chi tiết:** Mô tả rõ ràng, thời gian, phần thưởng XP, tài liệu/liên kết đính kèm.
    *   **Điểm kinh nghiệm (XP) và Cấp độ (Level):**
        *   **XP:** Tích lũy khi hoàn thành nhiệm vụ. Cơ chế tính XP:
            *   **Quest hệ thống:** Dựa trên độ khó và loại nhiệm vụ (do hệ thống xác định).
            *   **Quest tùy chỉnh:** 0.2 XP/phút (dựa trên thời gian ước tính do người dùng nhập).
        *   **Level:** Tăng khi đạt đủ XP. Đường cong XP được thiết kế hợp lý, không quá dễ cũng không quá khó, tạo động lực liên tục.
    *   **Phần thưởng (Rewards):**
        *   **Đa dạng:** Vật phẩm ảo (trang phục, danh hiệu, biểu tượng...), đặc quyền (mở khóa tính năng, nội dung...), phần thưởng thực tế (tùy chọn).
        *   **Giá trị sử dụng:** Có thể hiển thị, trang bị, sử dụng trong hệ thống.
        *   **Hệ thống phần thưởng:** Cân bằng, hấp dẫn, tạo động lực.
    *   **Thử thách (Challenges):**
        *   **Boss fights:** Bài kiểm tra lớn, dự án phức tạp, yêu cầu kiến thức và kỹ năng tổng hợp.
        *   **Streaks:** Thưởng cho việc học tập liên tục (ví dụ: hoàn thành nhiệm vụ mỗi ngày).
        *   **Achievements:** Thành tích đặc biệt, mở khóa khi đạt các cột mốc (ví dụ: đạt level 10, hoàn thành 100 nhiệm vụ, đạt điểm tuyệt đối trong boss fights...).
        *   **Boss Fight hợp tác:** Cho phép người dùng cùng nhau vượt qua thử thách lớn.
    *   **Tương tác cộng đồng (Guild/Study Group):**
        *   **Kết nối:** Tạo/tham gia nhóm theo sở thích, môn học, mục tiêu.
        *   **Học tập nhóm:** Nhiệm vụ chung, đua xếp hạng, project lớn, etc... .
        *   **Nhiệm vụ Guild:** Cùng nhau hoàn thành để nhận phần thưởng chung.
        *   **Bảng xếp hạng Guild:** Cạnh tranh lành mạnh giữa các nhóm.
*   **Hỗ trợ người dùng tối đa:**
    *   **Giao diện:** Trực quan, thân thiện, tối ưu hóa cho cả PC và mobile (thiết kế PC-first, responsive).
    *   **Study Island:**
        *   Hiển thị thông tin quan trọng: XP, level, streak, thông báo, tiến độ nhiệm vụ...
        *   Tương tác nhanh: Click/chạm để xem chi tiết, nút hành động nhanh.
        *   Tùy biến cao: Cho phép người dùng tùy chỉnh thông tin hiển thị.
    *   **Quest Log (Bảng nhiệm vụ):**
        *   Cá nhân hóa: Hiển thị nhiệm vụ theo sở thích, mục tiêu, tiến độ.
        *   Bộ lọc đa dạng: Môn học, chủ đề, loại, độ khó, thời gian, trạng thái.
        *   Hiển thị chi tiết: Mô tả, XP, thời gian, trạng thái, nút "Bắt đầu nhanh".
    *   **Chat AI (LLMs):**
        *   Tư vấn học tập thông minh, đa lĩnh vực.
        *   Gợi ý, cá nhân hóa lộ trình học tập.
        *   Thiết kế như một nhân vật trong game (avatar, tên gọi).
        *   Lưu trữ lịch sử chat.
    *   **Guild/Study Group:** (Chi tiết như trên)
    *   **Calendar:**
        *   Tích hợp lịch cá nhân.
        *   Hiển thị nhiệm vụ, sự kiện, deadline, streak.
        *  Hỗ trợ kéo thả quest vào lịch
    *   **Thông báo đẩy:** Nhắc nhở nhiệm vụ, sự kiện, tin nhắn, hoạt động guild.
    *   **Âm thanh và hiệu ứng:** Tăng trải nghiệm tương tác.
*   **Nền tảng:**
    *   **Linh hoạt:** Dễ dàng mở rộng (thêm môn học, lĩnh vực, loại hình nội dung, tính năng mới).
    *   **Cá nhân hóa:** Đáp ứng nhu cầu, mục tiêu, sở thích học tập của từng người dùng.
    *   **Dữ liệu & AI:** Sử dụng để liên tục cải thiện trải nghiệm.

**1.2. Công nghệ đề xuất**

*   **Frontend:** Next.js (React) + Tailwind CSS.
*   **Backend:** NestJS (typescript).
*   **Cơ sở dữ liệu:** PostgreSQL.
*   **Tích hợp AI:** OpenAI API (hoặc các mô hình tương tự).
*   **Deployment:** Vercel (frontend), AWS (backend).
*   **Real-time Communication:** WebSocket (Socket.IO).

**#2. Thiết kế Frontend**

**2.1. Giao diện & UI/UX (PC-first, Responsive)**

*   **Dashboard chính:**
    *   **Study Island:**
        *   **Vị trí (PC):** Góc trên cùng ở giữa.
        *   **Vị trí (Mobile):** Tích hợp vào header hoặc nút nổi.
        *   **Hình dạng:** Hình chữ nhật bo tròn (hoặc tùy biến).
        *   **Nội dung hiển thị (linh hoạt, tùy chỉnh):**
            *   Mặc định: XP, level, streak, thông báo hệ thống.
            *   Khi có sự kiện: Đếm ngược, thông báo, tiến độ nhiệm vụ...
        *   **Tương tác:** Click/chạm để xem chi tiết, nút hành động nhanh, vuốt để ẩn/hiện (mobile).
        *   **Animation:** Mượt mà, hiệu ứng "pulse" khi có thông báo mới, thay đổi kích thước, hình dạng, nội dung mượt mà.
    *   **Bố cục (PC):** Header (chứa Study Island), Sidebar, Main Content Area, Footer.
    *   **Bố cục (Mobile):** Header (tích hợp Study Island hoặc nút nổi), Hamburger menu, Main Content Area, Footer.
    *   **Hiển thị tiến độ:** Thanh progress bar (XP, level), biểu đồ trực quan hóa dữ liệu học tập (tùy chỉnh).
    *   **Quest Log:**
        *   Thẻ nhiệm vụ (task card): Môn học, chủ đề, loại, độ khó, thời gian, mô tả, XP, trạng thái.
        *   Nút "Bắt đầu nhanh".
        *   Bộ lọc và sắp xếp.
        *   Khu vực riêng cho nhiệm vụ được gợi ý.
        *   *Tab riêng cho Quest tùy chỉnh.*
    *   **Leaderboard:** Cá nhân và nhóm, lọc theo thời gian và môn học (tùy chọn).
    *   **Widget Chat AI:** Thiết kế như "NPC", gợi ý câu hỏi, lưu lịch sử chat, chủ động đưa ra lời khuyên.
    *   **Profile & Customization:** Thông tin cá nhân, avatar, danh hiệu, bộ sưu tập, thống kê, achievement, mục tiêu, lịch sử học tập.
    *   **Guild/Study Group:** Tạo/tham gia, công cụ hỗ trợ, nhiệm vụ Guild, bảng xếp hạng, quản lý thành viên, thảo luận.
    *   **Calendar:** Tích hợp, hiển thị nhiệm vụ, sự kiện, deadline, streak. *Hỗ trợ kéo thả quest.*
    *   **Thông báo đẩy.**
    *   **Âm thanh và hiệu ứng.**
    *   **Reward Inventory:** Xem, trang bị phần thưởng.
    *    **Giao diện tạo và quản lý Quest tùy chỉnh:** (Chi tiết như đã mô tả ở phần trả lời trước)
    *   **Giao diện tạo và quản lý lịch trình:** (Chi tiết như đã mô tả ở phần trả lời trước)

**2.2. Thành phần cụ thể**

*   **Header (PC):** Logo, Study Island.
*   **Header (Mobile):** Logo, hamburger menu, Study Island (tích hợp hoặc nút nổi).
*   **Sidebar (PC):** menu chính (Dashboard, Nhiệm vụ, Leaderboard, Profile, Chat AI, Guilds, *Quest tùy chỉnh*, *Lịch trình*), cài đặt, logout.
*   **Sidebar (Mobile):** Dạng "drawer" với nội dung tương tự sidebar PC.
*   **Main Content Area:** Hiển thị nội dung chính.
*   **Footer:** Liên hệ, thông tin bản quyền, FAQ, điều khoản.

**2.3. Tương tác & Animation**

*   **Study Island:** Animation mượt mà, hiệu ứng "pulse".
*   **Quest Log:** Hiệu ứng di chuột, click, chuyển trạng thái.
*   **Achievement:** Animation "pop-up", hiệu ứng đặc biệt.
*   **Guild:** Hiệu ứng tin nhắn mới, hoàn thành nhiệm vụ nhóm.
*   **Hoàn thành nhiệm vụ:** Hiệu ứng "XP +xx", "mở khóa" phần thưởng.
*   **Lên cấp:** Animation "Level Up".
*   **Streak:** "Ngọn lửa streak", animation khi đạt mốc.
*   **Boss Fight:** Hiệu ứng đặc biệt.
*   **Phản hồi tương tác:** Hiệu ứng "nhấn", "hover".
*   **Thất bại/bỏ qua nhiệm vụ:** Thông báo/animation nhẹ nhàng.
*   **Quest tùy chỉnh:** Animation khi tạo, chỉnh sửa, xóa, hoàn thành.
* **Lịch trình:** Kéo thả mượt mà

**2.4. API Calls**

*   **User:**
    *   `GET /api/v1/user`
    *   `PUT /api/v1/user`
    *   `GET /api/v1/user/rewards`
    *    `POST /api/v1/user/equip`
    *   `GET /api/v1/user/achievements`
*   **Tasks:**
    *   `GET /api/v1/tasks`
    *   `GET /api/v1/tasks/{task_id}`
    *   `POST /api/v1/tasks/{task_id}/complete`
    *   `POST /api/v1/tasks/{task_id}/skip`
      * `POST /api/v1/tasks/{task_id}/start`
*   **Leaderboard:**
    *   `GET /api/v1/leaderboard`
    *   `GET /api/v1/guilds/leaderboard`
*   **Chat AI:**
    *   `POST /api/v1/chat`
    *   `GET /api/v1/chat/history`
*   **Guilds:**
    *   `GET /api/v1/guilds`
    *   `POST /api/v1/guilds`
    *   `POST /api/v1/guilds/{guild_id}/join`
    *   `GET /api/v1/guilds/{guild_id}`
    *   `GET /api/v1/guilds/{guild_id}/members`
    *   `GET /api/v1/guilds/{guild_id}/tasks`
    *   `POST /api/v1/guilds/message`
      *  `POST /api/v1/guilds/{guild_id}/tasks`
    *   `PUT/PATCH /api/v1/guilds/{guild_id}/tasks/{task_id}`
    *   `DELETE /api/v1/guilds/{guild_id}/tasks/{task_id}`
    *   `POST /api/v1/guilds/{guild_id}/tasks/{task_id}/complete`
*   **Subjects:** `GET /api/v1/subjects`
*   **Topics:** `GET /api/v1/topics`
*   **Achievements:** `GET /api/v1/achievements`
* **User-Created Quests:**
    *   `POST /api/v1/user/quests`
    *   `GET /api/v1/user/quests`
    *   `GET /api/v1/user/quests/{quest_id}`
    *   `PUT /api/v1/user/quests/{quest_id}`
    *   `DELETE /api/v1/user/quests/{quest_id}`
    *   `POST /api/v1/user/quests/{quest_id}/start`
    *   `POST /api/v1/user/quests/{quest_id}/complete`
    *   `POST /api/v1/user/quests/{quest_id}/skip`
*    **Schedule:**
    *   `GET /api/v1/user/schedule`
    *   `POST /api/v1/user/schedule`
    *   `PUT/PATCH/DELETE /api/v1/user/schedule/{schedule_id}`
*   **Authentication:**
    *   `POST /api/v1/auth/register`: Đăng ký.
    *   `POST /api/v1/auth/login`: Đăng nhập.
    *   `POST /api/v1/auth/logout`: Đăng xuất.
    *   `POST /api/v1/auth/forgot-password`: Quên mật khẩu.
    *   `POST /api/v1/auth/reset-password`: Đặt lại mật khẩu.
    * `POST /api/v1/auth/login/google`: Login with Google
    * `POST /api/v1/auth/login/facebook`: Login with Facebook

**#3. Thiết kế Backend**

**3.1. API & Kiến trúc**
*   **Framework:** FastAPI (Python).
*   **RESTful API (Versioned):** `/api/v1/...`
*   **Endpoints:** (Như đã mô tả trong phần API Calls)
*   **Real-time Updates (WebSocket):** Socket.IO (leaderboard, chat, thông báo, guild activities).
*   **Logging:** Log đầy đủ (Loguru, structlog).

**3.2. Cơ sở dữ liệu**

*   **CSDL:** PostgreSQL.
*   **Các bảng:**
    *   **Users:** `user_id`, `username`, `password`, `email`, `avatar_url`, `xp`, `level`, `current_streak`, `created_at`, `updated_at`, `guild_id`.
    *   **Tasks:** `task_id`, `subject_id`, `topic_id`, `task_type`, `difficulty_level`, `estimated_time`, `description`, `content_url`, `xp_reward`, `created_at`, `updated_at`, `prerequisites`.
    *   **UserTasks:** (Bảng trung gian)
    *   **ProgressLog:** (Lịch sử thay đổi XP, level, streak)
    *   **ChatLogs:**
    *   **Rewards:**
    *   **UserRewards:** (Bảng trung gian)
    *   **Subjects:**
    *   **Topics:**
    *   **Guilds:** `guild_id`, `guild_name`, `description`, `created_at`, `updated_at`.
    *   **GuildMembers:** (Bảng trung gian)
    *   **GuildTasks:**
    *   **UserGuildTasks:** (Bảng trung gian)
    *   **GuildLeaderBoard:**
    *   **Achievements:** `achievement_id`, `achievement_name`, `description`, `criteria`, `reward_xp`, `image_url`.
    *   **UserAchievements:** `user_id`, `achievement_id`, `achieved_at`.
    *   **UserCreatedQuests:** `quest_id`, `user_id`, `quest_name`, `description`, `quest_type`, `subject_id`, `topic_id`, `difficulty_level`, `estimated_time`, `xp_reward`, `completion_criteria`, `attachment_url`, `visibility`, `start_date`, `end_date`, `repeat_frequency`, `created_at`, `updated_at`.
     *   **UserSchedules**: `schedule_id`, `user_id`, `task_id`, `quest_id`, `start_time`, `end_time`, `reminder_time`.
**3.3. Tích hợp AI**

*   **OpenAI API:**
    *   Tư vấn đa lĩnh vực.
    *   Cá nhân hóa.
    *   Prompt Engineering.
    *   *Gợi ý tạo Quest (tương lai).*
    *   *Tự động tạo Quest (tương lai).*
    *   *Tối ưu hóa lịch trình (tương lai).*

**3.4. Tính năng tự động & bảo mật**

*   **Automated XP Update:** Tự động cập nhật XP, level, streak, achievement. *Tính XP cho quest tùy chỉnh dựa trên thời gian ước tính (0.2 XP/phút).*
*   **Scheduled Jobs:** Cập nhật bảng xếp hạng, gửi thông báo.
*   **Bảo mật:** Mã hóa mật khẩu, xác thực, bảo vệ dữ liệu, ngăn chặn XSS, CSRF.
*   **Chống gian lận:**
    *   **Giới hạn quest tùy chỉnh:**
        *   Số lượng quest tối đa có thể tạo trong một khoảng thời gian.
        *   Số XP tối đa có thể nhận từ quest tùy chỉnh trong một khoảng thời gian.
    *   **Kiểm duyệt quest tùy chỉnh (tùy chọn):**
        *   Quest tùy chỉnh ở chế độ công khai có thể cần được duyệt trước khi hiển thị cho người khác.
        *   Hệ thống báo cáo quest vi phạm.
    *   **Phát hiện bất thường:**
        *   Theo dõi thời gian hoàn thành quest thực tế so với thời gian ước tính.
        *   Phát hiện các hành vi bất thường (ví dụ: hoàn thành quá nhiều quest trong thời gian ngắn).
    *   **Xử lý vi phạm:**
        *   Cảnh báo.
        *   Giảm XP.
        *   Khóa tài khoản (tạm thời hoặc vĩnh viễn).

**#4. Phân tích các yếu tố Gamification**

*   **Quests (Nhiệm vụ):**
    *   **Đa dạng hóa:** Nhiều loại hình, chủ đề, độ khó, tạo sự phong phú và lựa chọn cho người dùng.
    *   **Cá nhân hóa:** Quest hệ thống được gợi ý dựa trên sở thích, mục tiêu, tiến độ. Quest tùy chỉnh cho phép người dùng tự tạo nhiệm vụ phù hợp.
    *   **Thử thách:** Độ khó tăng dần, boss fight, hidden quest (tùy chọn).
    *   **Phần thưởng:** XP, vật phẩm, danh hiệu, mở khóa tính năng.
*   **XP & Level:**
    *   **Trực quan:** Thanh tiến độ, biểu đồ.
    *   **Động lực:** Cảm giác tiến bộ, đạt được thành tựu.
    *   **Cân bằng:** Đường cong XP hợp lý, không quá dễ, không quá khó.
*   **Rewards (Phần thưởng):**
    *   **Hấp dẫn:** Vật phẩm ảo, đặc quyền, phần thưởng thực tế (tùy chọn).
    *   **Giá trị:** Có thể sử dụng, hiển thị, tạo sự khác biệt.
*   **Challenges (Thử thách):**
    *   **Boss fights:** Bài kiểm tra lớn, dự án, tạo điểm nhấn.
    *   **Streaks:** Khuyến khích học tập liên tục.
    *   **Achievements:** Ghi nhận thành tích, tạo mục tiêu phấn đấu.
    * **Boss Fight hợp tác:** Thúc đẩy tinh thần đồng đội.
*   **Guild/Study Group:**
    *   **Kết nối:** Tạo cộng đồng, tăng tương tác.
    *   **Học tập nhóm:** Công cụ hỗ trợ, chia sẻ kiến thức.
    *   **Cạnh tranh:** Bảng xếp hạng, nhiệm vụ nhóm, tạo động lực.
*   **Study Island:**
    *   **Trực quan:** Thông tin quan trọng luôn hiển thị.
    *   **Tiện lợi:** Tương tác nhanh.
    *   **Cá nhân hóa:** Tùy chỉnh thông tin hiển thị.
*   **Chat AI (NPC):**
    *   **Hỗ trợ:** Tư vấn, giải đáp thắc mắc.
    *   **Cá nhân hóa:** Gợi ý học tập.
    *   **Nhập vai:** Thiết kế như nhân vật trong game.
*   **Calendar:**
    *   **Quản lý:** Sắp xếp thời gian học tập.
    *   **Trực quan:** Hiển thị nhiệm vụ, sự kiện.
    *   **Nhắc nhở:** Đảm bảo không bỏ lỡ.
*   **Custom Quests and Schedule:**
    * **Chủ động:** Người dùng tự quyết định nội dung và thời gian biểu của mình
    * **Linh động:** Phù hợp với nhiều phong cách học tập
    * **Ownership:** Người dùng sẽ có cảm giác "làm chủ" việc học của mình hơn.

**#5. Quy trình Phát triển & Triển khai**

*   **Iterative Development (Agile/Scrum):**
    *   Chia dự án thành các sprint ngắn (2-4 tuần).
    *   Mỗi sprint tập trung vào một nhóm tính năng.
    *   Liên tục đánh giá, điều chỉnh dựa trên phản hồi.
*   **MVP (Minimum Viable Product):**
    *   Bắt đầu với các tính năng cốt lõi: Quest hệ thống, XP, level, profile, leaderboard cơ bản.
    *   Phát hành sớm, thu thập phản hồi, cải tiến.
*   **Thiết kế UI/UX:**
    *   **Wireframe:** Xác định bố cục, cấu trúc cơ bản.
    *   **Mockup:** Thiết kế giao diện chi tiết.
    *   **Prototype:** Tạo mẫu tương tác để kiểm thử.
*   **Xây dựng Backend, Frontend:**
    *   Phân chia công việc rõ ràng.
    *   Sử dụng Git để quản lý mã nguồn.
    *   Code review thường xuyên.
*   **Kiểm thử:**
    *   **Unit testing:** Kiểm tra từng module, hàm.
    *   **Integration testing:** Kiểm tra sự tương tác giữa các module.
    *   **End-to-end testing:** Kiểm tra toàn bộ hệ thống.
    *   **UI/UX testing:** Kiểm tra giao diện, trải nghiệm người dùng.
    *   **Security testing:** Kiểm tra bảo mật.
    *   **Performance testing:** Kiểm tra hiệu năng, khả năng chịu tải.
    *   **A/B testing:** So sánh các phiên bản khác nhau để tối ưu hóa.
*   **Triển khai:**
    *   **Vercel:** Frontend.
    *   **AWS:** Backend (EC2, RDS, S3...).
    *   **CI/CD:** Tự động hóa quá trình build, test, deploy.
*   **Giám sát:**
    *   **Lưu lượng truy cập:** Số lượng người dùng, tần suất sử dụng.
    *   **Hiệu năng:** Thời gian phản hồi, tải trang.
    *   **Lỗi:** Theo dõi, xử lý lỗi kịp thời.
    *   **Phản hồi người dùng:** Thu thập, phân tích để cải tiến.

**#6. Bổ sung Thiết kế Frontend (Landing Page, Login, Signup)**

**6.1. Landing Page (Trang Chủ)**

*   **Mục tiêu:**
    *   Giới thiệu Chronoscape là gì, dành cho ai, và lợi ích của việc sử dụng nền tảng.
    *   Thu hút người dùng mới đăng ký tài khoản.
    *   Tạo ấn tượng ban đầu tốt đẹp, chuyên nghiệp.
*   **Nội dung:**
    *   **Hero Section:**
        *   Hình ảnh/video background lớn, ấn tượng, thể hiện tinh thần "học tập nhập vai". Có thể là hình ảnh các nhân vật trong game, cảnh quan trong game, hoặc hình ảnh người dùng đang tương tác với hệ thống.
        *   Tiêu đề lớn, hấp dẫn (ví dụ: "Biến việc học thành cuộc phiêu lưu!", "Khám phá thế giới tri thức theo cách của bạn!").
        *   Mô tả ngắn gọn về Chronoscape.
        *   Nút CTA (Call-to-Action) lớn, nổi bật (ví dụ: "Đăng ký miễn phí", "Bắt đầu ngay").
    *   **Giới thiệu tính năng:**
        *   Liệt kê các tính năng chính của Chronoscape (Quest, XP, Level, Rewards, Guild, Chat AI, Calendar...).
        *   Mỗi tính năng có icon/hình ảnh minh họa, mô tả ngắn gọn, dễ hiểu.
        *   Có thể sử dụng hiệu ứng animation, parallax scrolling để tăng tính hấp dẫn.
    *   **Lợi ích:**
        *   Nhấn mạnh lợi ích của việc sử dụng Chronoscape (ví dụ: tăng hứng thú học tập, cải thiện kết quả, kết nối với cộng đồng...).
        *   Có thể sử dụng số liệu thống kê, testimonial (lời chứng thực) từ người dùng thử nghiệm.
    *   **Demo (tùy chọn):**
        *   Một đoạn video ngắn giới thiệu cách sử dụng Chronoscape.
        *   Một phiên bản demo tương tác (cho phép người dùng trải nghiệm một số tính năng cơ bản).
    *   **FAQ (Câu hỏi thường gặp):**
        *   Trả lời các câu hỏi thường gặp về Chronoscape.
    *   **Footer:**
        *   Thông tin liên hệ, mạng xã hội, điều khoản sử dụng, chính sách bảo mật.
*   **Thiết kế:**
    *   Sử dụng màu sắc, font chữ phù hợp với phong cách "game RPG" nhưng vẫn đảm bảo tính hiện đại, chuyên nghiệp.
    *   Bố cục rõ ràng, dễ theo dõi.
    *   Tối ưu hóa cho cả PC và mobile (responsive).
    *   Sử dụng hình ảnh, video chất lượng cao.

**6.2. Login Page (Trang Đăng Nhập)**

*   **Mục tiêu:**
    *   Cho phép người dùng đã có tài khoản đăng nhập vào hệ thống.
    *   Cung cấp tùy chọn "Quên mật khẩu".
    *   Tùy chọn đăng nhập bằng tài khoản mạng xã hội.
*   **Nội dung:**
    *   Form đăng nhập:
        *   Trường nhập username/email.
        *   Trường nhập password.
        *   Nút "Đăng nhập".
        *   Checkbox "Ghi nhớ đăng nhập" (tùy chọn).
    *   Liên kết "Quên mật khẩu?".
    *   Nút đăng nhập bằng tài khoản mạng xã hội (Google, Facebook...).
*   **Thiết kế:**
    *   Đơn giản, tập trung vào form đăng nhập.
    *   Có thể sử dụng hình ảnh background liên quan đến Chronoscape.
    *   Thông báo lỗi rõ ràng (nếu đăng nhập không thành công).

**6.3. Signup Page (Trang Đăng Ký)**

*   **Mục tiêu:**
    *   Cho phép người dùng mới tạo tài khoản Chronoscape.
*   **Nội dung:**
    *   Form đăng ký:
        *   Trường nhập username.
        *   Trường nhập email.
        *   Trường nhập password.
        *   Trường nhập lại password.
        *   Checkbox đồng ý với điều khoản sử dụng và chính sách bảo mật.
        *   Nút "Đăng ký".
    *   Tùy chọn đăng ký bằng tài khoản mạng xã hội (Google, Facebook...).
*   **Thiết kế:**
    *   Tương tự như trang Login, đơn giản, tập trung vào form đăng ký.
    *   Thông báo lỗi rõ ràng (nếu đăng ký không thành công).
    *   Có thể hiển thị một số thông tin về Chronoscape (tính năng, lợi ích) để khuyến khích người dùng đăng ký.

## Phân cấp giai đoạn
*   **Giai đoạn MVP:**
    *   Thiết kế kiến trúc hệ thống tổng thể.
    *   Lựa chọn công nghệ.
    *   Thiết lập quy trình làm việc.
    *   Hỗ trợ Frontend/Backend Developer.
    *   Tham gia code review.
*   **Giai đoạn Phát triển các tính năng chính:**
    *   Tham gia thiết kế database schema (chi tiết).
    *   Tham gia thiết kế API.
    *   Giải quyết vấn đề kỹ thuật.
    *   Đảm bảo tính scalability, maintainability.
    *   Tham gia code review.
*   **Giai đoạn Tích hợp AI và các tính năng nâng cao:**
    *   Nghiên cứu, lựa chọn giải pháp AI.
    *   Thiết kế kiến trúc tích hợp AI.
    *   Hướng dẫn Backend Developer.
    *   Tham gia code review.

Hệ thống "Chronoscape" là một nền tảng học tập nhập vai toàn diện, kết hợp gamification, giao diện trực quan, AI thông minh, và tính năng cộng đồng để tạo ra trải nghiệm học tập thú vị, hiệu quả. Dự án được phát triển theo hướng lặp, liên tục cải tiến, tập trung vào việc mang lại giá trị cao nhất cho người dùng. Cơ chế quest tùy chỉnh và lịch trình cá nhân cho phép người dùng làm chủ quá trình học, tăng cường tính cá nhân hóa và động lực.
