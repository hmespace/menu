# Dự án IQR - Trung tâm Tài liệu

Chào mừng bạn đến với Nguồn Sự Thật Duy Nhất (Single Source of Truth) của dự án IQR.

Kho lưu trữ này không chứa code. Đây là nơi lưu giữ và kết nối định hướng chiến lược với thiết kế kỹ thuật, đảm bảo toàn bộ đội ngũ có một ngôn ngữ chung.

---

## 1. Hệ thống Phân cấp Tài liệu

Mọi công việc đều bắt đầu từ định hướng chiến lược. Hãy luôn tham khảo theo thứ tự sau:

*   **Cấp 1: `ROADMAP.md` - La bàn Chiến lược (The "Why")**
    *   **Đây là nguồn tham chiếu chính và tối cao.** Nó trả lời câu hỏi **TẠI SAO** chúng ta xây dựng một tính năng. Mọi ưu tiên và định hướng đều bắt nguồn từ đây.

*   **Cấp 2: Thư mục `/docs` - Bản thiết kế Trải nghiệm (The "What")**
    *   Sau khi đã có "Why", các file LFP trong này sẽ mô tả chi tiết **CÁI GÌ** chúng ta cần xây dựng – luồng người dùng, các kịch bản, và nguyên tắc thiết kế.

*   **Cấp 3: `DATASET.md` & `/mocks` - Từ điển Dữ liệu Tham khảo (The "How")**
    *   Đây là các tài liệu **tham khảo** về kiến trúc dữ liệu trong tương lai. Chúng cung cấp cảm hứng và định hướng cho câu hỏi **NHƯ THẾ NÀO** dữ liệu có thể được cấu trúc.

---

## 2. Vai trò của Frontend Prototype

**Dữ liệu trong `/mocks` có thể là giả, nhưng vai trò của prototype bạn xây dựng từ nó là cực kỳ quan trọng và có thật.**

Frontend không chỉ xây dựng giao diện. Các bạn đang xây dựng **sân khấu** nơi công sức của tất cả các đội ngũ khác được trình diễn và kết nối. Một prototype tương tác được là công cụ giao tiếp hiệu quả nhất, giúp các đội ngũ khác trả lời những câu hỏi cụ thể:

*   **Với team Backend & Database:**
    *   Prototype của bạn là một **bản hợp đồng API sống động**. Thay vì đọc tài liệu dài, họ có thể tương tác với giao diện và thấy chính xác: "À, màn hình này cần trường `averageRating` và `reviewCount` từ bảng `dishes`." Nó biến yêu cầu trừu tượng thành một cấu trúc JSON cụ thể.

*   **Với team AI & Blockchain:**
    *   Prototype của bạn **biến các thuật toán phức tạp thành một tương tác hữu hình**. Team AI sẽ biết chính xác "kết quả gợi ý món ăn" (`MENU-702`) sẽ hiển thị ở đâu và như thế nào. Team Blockchain sẽ thấy "lịch sử giao dịch on-chain" được trình bày ra sao cho người dùng. Nó cung cấp "điểm chạm" để họ tích hợp.

*   **Với toàn bộ team Product & Business:**
    *   Prototype của bạn giúp mọi người "cảm nhận" được sản phẩm trước khi có một dòng code backend nào được viết. Nó giúp kiểm chứng ý tưởng, thu thập phản hồi sớm, và đảm bảo tất cả mọi người đang cùng nhìn về một hướng.

---

## 3. Luồng làm việc Thực tế cho Frontend

Chúng tôi tin tưởng vào chuyên môn của bạn. Hãy sử dụng các tài liệu này một cách linh hoạt.

1.  **Bắt đầu từ Định hướng:** Luôn đọc `ROADMAP.md` và LFP trong `/docs` trước tiên để hiểu rõ mục tiêu.

2.  **Tạo Mock Data Tối giản của riêng bạn:**
    *   **Đây là bước được khuyến khích.** Đừng cố gắng implement toàn bộ `mocks/database`. Hãy tạo một file mock nhỏ, chỉ chứa những dữ liệu bạn thực sự cần cho component đang làm.

3.  **Coi `mocks/database` như một Từ điển:**
    *   Khi bạn cần mở rộng component hoặc muốn biết một thuộc tính trong tương lai có thể trông như thế nào, hãy mở `database.json` ra để **tra cứu và tham khảo**.

Tóm lại, vai trò của các bạn là then chốt. Các bạn là người đầu tiên biến ý tưởng thành hiện thực, tạo ra một nền tảng trực quan để toàn bộ các đội ngũ kỹ thuật khác có thể kết nối và xây dựng dựa trên đó.
