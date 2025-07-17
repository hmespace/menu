Chắc chắn rồi. Anh đã chỉ ra một hướng đi chiến lược rõ ràng. Việc chính thức hóa triết lý **"Frontend-First"** sẽ mang lại sự tập trung và hiệu quả cho toàn bộ quá trình phát triển.

Đây là phiên bản `README.md` được thiết kế lại để phản ánh chính xác triết lý này. Nó không chỉ là một tài liệu, mà là một tuyên ngôn về cách chúng ta làm việc: **bắt đầu từ trải nghiệm người dùng, và để trải nghiệm đó định hình nên hệ thống kỹ thuật.**

---

# Dự án IQR - Trung tâm Tài liệu Chiến lược & Kỹ thuật

Chào mừng bạn đến với Nguồn Sự Thật Duy Nhất (Single Source of Truth) của dự án IQR.

Kho lưu trữ này hoạt động dựa trên triết lý **Frontend-First**. Nó không chứa code, mà là nơi kết nối định hướng chiến lược với thiết kế kỹ thuật, đảm bảo toàn bộ đội ngũ có một ngôn ngữ chung và một quy trình làm việc hiệu quả.

---

## 1. Triết lý Phát triển của chúng ta: Frontend-First

Chúng ta giảm thiểu rủi ro và tăng tốc độ bằng cách xây dựng thứ mà người dùng có thể thấy và tương tác trước.

1.  **Bắt đầu từ Trải nghiệm:** Chúng ta ưu tiên thiết kế và xây dựng giao diện người dùng trước tiên.
2.  **Prototype là Hợp đồng:** Một prototype tương tác được do đội ngũ frontend xây dựng sẽ trở thành **bản hợp đồng API sống động**. Nó định nghĩa chính xác dữ liệu cần thiết để trải nghiệm đó hoạt động.
3.  **Backend Hiện thực hóa Hợp đồng:** Nhiệm vụ của đội ngũ backend là xây dựng hệ thống vững chắc để cung cấp dữ liệu theo đúng hợp đồng mà prototype đã định ra.

---

## 2. Quy trình & Hệ thống Tài liệu

Quy trình làm việc của chúng ta tuân theo triết lý Frontend-First, với các tài liệu hỗ trợ tương ứng:

*   **Bước 1: Định hướng Chiến lược (The "Why")**
    *   **Tài liệu:** [`ROADMAP.md`](./ROADMAP.md)
    *   **Mục đích:** Đây là la bàn, là nguồn tham chiếu tối cao về mặt định hướng. Mọi công việc đều bắt đầu từ việc xác định **TẠI SAO** chúng ta làm một tính năng.

*   **Bước 2: Thiết kế Trải nghiệm (The "What")**
    *   **Tài liệu:** Thư mục [`docs`](./docs)
    *   **Mục đích:** Các file LFP trong này mô tả chi tiết **CÁI GÌ** chúng ta cần xây dựng – luồng người dùng, các kịch bản, và nguyên tắc thiết kế.

*   **Bước 3: Xây dựng Prototype & Định nghĩa Hợp đồng API (Vai trò Cốt lõi của Frontend)**
    *   **Hành động:** Đội ngũ frontend nhận bản thiết kế trải nghiệm và xây dựng một prototype tương tác được, sử dụng dữ liệu giả (mock data).
    *   **Kết quả:** Prototype này không chỉ là một bản demo. Nó chính là **bản hợp đồng API** cho các đội ngũ khác. Nó cho thấy chính xác dữ liệu nào cần được cung cấp.
    *   **Tài liệu tham khảo:** [`DATASETS.md`](./DATASETS.md) & [`/mocks`](./mocks) được dùng như một **từ điển** để tra cứu và lấy cảm hứng về cấu trúc dữ liệu tiềm năng.

*   **Bước 4: Hiện thực hóa Backend & Tích hợp**
    *   **Hành động:** Các đội ngũ Backend, Database, AI, và Blockchain nhận prototype (hợp đồng API) và bắt tay vào xây dựng hệ thống để đáp ứng các yêu cầu đó.

---

## 3. Tầm quan trọng của Frontend Prototype

Prototype của bạn là **sân khấu chung** nơi công sức của tất cả các đội ngũ khác được trình diễn và kết nối.

*   **Với team Backend & Database:** Prototype của bạn là một **yêu cầu kỹ thuật trực quan**. Họ sẽ nhìn vào đó để thiết kế schema và xây dựng các API endpoint chính xác.

*   **Với team AI & Blockchain:** Prototype của bạn cung cấp **"điểm chạm" hữu hình** để họ tích hợp các thuật toán và logic phức tạp của mình vào một luồng người dùng có thật.

*   **Với toàn bộ team Product & Business:** Prototype của bạn giúp mọi người **"cảm nhận" được sản phẩm** từ rất sớm, giúp kiểm chứng ý tưởng và đảm bảo tất cả đang cùng nhìn về một hướng.

---

## 4. Hướng dẫn làm việc với Dữ liệu Giả

Chúng tôi tin tưởng vào chuyên môn của bạn.

1.  **Tạo Mock Data Tối giản của riêng bạn:** **Đây là cách làm được khuyến khích.** Hãy tạo một file mock nhỏ, chỉ chứa những dữ liệu bạn thực sự cần cho component đang làm.
2.  **Coi `/mocks/database.json` như một Từ điển:** Khi bạn cần mở rộng component hoặc muốn biết một thuộc tính trong tương lai có thể trông như thế nào, hãy mở [`database.json`](./mocks/database.json) ra để **tra cứu và tham khảo**.

Vai trò của các bạn là then chốt. Các bạn là người đầu tiên biến ý tưởng thành hiện thực, tạo ra một nền tảng trực quan để toàn bộ các đội ngũ kỹ thuật khác có thể kết nối và xây dựng dựa trên đó.
