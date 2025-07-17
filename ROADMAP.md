### **TÀI LIỆU LỘ TRÌNH SẢN PHẨM TOÀN DIỆN**

*   **Dự án:** Trải nghiệm Khách hàng số _ IQR
*   **Phiên bản:** 4.0 (Tập trung vào Giá trị & Chiến lược)
*   **Mục đích:** Cung cấp một cái nhìn toàn cảnh về lộ trình phát triển sản phẩm, được thiết kế để mọi đối tượng - từ Founder, Kinh doanh, Kỹ sư, Thiết kế đến người dùng cuối - đều có thể hiểu rõ giá trị, mục tiêu và đối tượng hưởng lợi của từng tính năng.

---

### **Triết lý & Cấu trúc Lộ trình**

Tài liệu này phác thảo lộ trình phát triển sản phẩm với 96 tính năng, được chia thành 8 giai đoạn chiến lược. Mục tiêu là cung cấp một cái nhìn toàn cảnh, từ những chức năng cơ bản nhất cho đến tầm nhìn dài hạn, giúp toàn bộ đội ngũ từ kỹ sư, thiết kế, kinh doanh đến ban lãnh đạo có một ngôn ngữ và định hướng chung.

#### **1. Quy ước đặt mã tính năng:**

Mỗi tính năng được định danh bằng một mã duy nhất theo cấu trúc: `MODULE-PHASE-ID`

*   **MODULE:** Đại diện cho phân hệ chức năng chính của sản phẩm.
    *   `ONB`: Onboarding & Access (Tiếp cận & Truy cập)
    *   `MENU`: Menu Discovery & Experience (Khám phá & Trải nghiệm Menu)
    *   `ORD`: Ordering & Order Management (Đặt món & Quản lý Đơn hàng)
    *   `PAY`: Payment & Billing (Thanh toán & Hóa đơn)
    *   `LOY`: Loyalty & Engagement (Khách hàng Thân thiết & Tương tác)
    *   `STAFF`: Staff Tools & Operations (Công cụ & Vận hành cho Nhân viên)
    *   `ADM`: Admin & Business Intelligence (Quản trị & Phân tích Kinh doanh)
    *   `DATA`: Data Platform & Analytics (Nền tảng & Phân tích Dữ liệu)
    *   `MKT`: Marketing & Communication (Tiếp thị & Giao tiếp)
    *   `GEN`: General / Platform (Tổng quát / Nền tảng)

*   **PHASE (Giai đoạn):** Con số đầu tiên của ID, thể hiện giai đoạn phát triển chiến lược.
    *   `1xx`: **Must Have** (Nền tảng Sinh tồn)
    *   `2xx`: **Shall Have** (Cam kết Sau Ra mắt)
    *   `3xx`: **Will Have** (Lộ trình Cam kết)
    *   `4xx`: **Should Have** (Khuyến nghị Cạnh tranh)
    *   `5xx`: **Can Have** (Cơ hội Khả thi)
    *   `6xx`: **Could Have** (Không gian Sáng tạo)
    *   `7xx`: **May Have** (Kế hoạch Dự phòng)
    *   `8xx`: **Might Have** (Tầm nhìn Dài hạn)

*   **ID:** Số thứ tự của tính năng trong giai đoạn đó.

**Ví dụ:** `PAY-301` có nghĩa là:
*   `PAY`: Tính năng thuộc module Thanh toán.
*   `3xx`: Thuộc giai đoạn **Will Have** (Lộ trình Cam kết).
*   `01`: Là tính năng số 1 trong module này ở giai đoạn đó.

---

### **Giải thích Cấu trúc Bảng**

*   **Mã tính năng:** Định danh duy nhất để theo dõi.
*   **Tên tính năng:** Tên gọi chính thức, dễ hiểu.
*   **Mục tiêu Chiến lược (Dành cho Founder, Business):** Trả lời câu hỏi: "Tại sao chúng ta lại xây dựng tính năng này? Nó phục vụ mục tiêu kinh doanh nào?"
*   **Đối tượng Hưởng lợi (Dành cho tất cả mọi người):** Trả lời câu hỏi: "Ai là người được hưởng lợi chính từ tính năng này?"
*   **Giá trị Cốt lõi (Dành cho User, Designer):** Trả lời câu hỏi: "Tính năng này giải quyết nỗi đau hay mang lại niềm vui gì cụ thể?"

---

### **MODULE: ONB - Onboarding & Access**
*Mục tiêu: Đảm bảo khách hàng có thể tiếp cận và bắt đầu trải nghiệm một cách nhanh chóng, liền mạch và dễ dàng nhất.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `ONB-101` | Truy cập Menu qua mã QR | Xây dựng "cửa ngõ" cơ bản nhất để khách hàng bắt đầu trải nghiệm số. | Mọi khách hàng | Để vào xem thực đơn ngay lập tức chỉ bằng camera điện thoại. |
| `ONB-201` | Hướng dẫn & Xử lý Lỗi Quét QR | Giảm tỷ lệ người dùng bỏ cuộc, đảm bảo mọi khách hàng đều có thể truy cập. | Khách hàng (đặc biệt là người lớn tuổi) | Để không bị bối rối khi quét mã không thành công và có hướng dẫn rõ ràng. |
| `ONB-401` | Đăng nhập/Đăng ký qua Mạng xã hội | Giảm rào cản đăng ký, tăng tốc độ thu thập dữ liệu người dùng. | Khách hàng mới | Để tạo tài khoản nhanh chóng chỉ bằng một cú nhấp chuột, không cần nhớ mật khẩu. |
| `ONB-501` | Truy cập Menu qua NFC | Tạo ra trải nghiệm truy cập đẳng cấp, "không ma sát", khác biệt hóa thương hiệu. | Khách hàng sành công nghệ | Để vào menu chỉ bằng một cú chạm nhẹ, không cần mở camera. |
| `ONB-601` | Nhận diện Khách quen qua Bluetooth/Wifi | Tạo hiệu ứng "wow", khiến khách hàng trung thành cảm thấy được nhận diện và trân trọng. | Khách hàng trung thành | Để được hệ thống chào đúng tên ngay khi bước vào quán. |

---
### **MODULE: MENU - Menu Discovery & Experience**
*Mục tiêu: Tạo ra một trải nghiệm khám phá thực đơn hấp dẫn, thông minh và đáp ứng mọi nhu cầu thông tin của khách hàng.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `MENU-101` | Xem Menu theo Danh mục | Cung cấp cấu trúc điều hướng cơ bản nhất cho thực đơn. | Mọi khách hàng | Để dễ dàng tìm thấy các nhóm món ăn (món chính, khai vị, tráng miệng...). |
| `MENU-102` | Xem Chi tiết Món ăn Cơ bản | Cung cấp đủ thông tin cần thiết để khách hàng ra quyết định đặt món. | Mọi khách hàng | Để biết rõ giá tiền, hình ảnh và mô tả của món ăn. |
| `MENU-201` | Tìm kiếm Món ăn Cơ bản (Hỗ trợ không dấu) | Tăng tốc độ tìm kiếm, cải thiện trải nghiệm cho người dùng có mục đích rõ ràng. | Khách hàng | Để tìm ngay được món mình muốn mà không cần duyệt qua các danh mục. |
| `MENU-202` | Hiển thị Trạng thái Món (Cập nhật thủ công) | Ngăn chặn trải nghiệm tiêu cực nhất: đặt món xong báo hết. | Mọi khách hàng, Nhân viên | Để biết chắc chắn món ăn còn hàng trước khi đặt. |
| `MENU-301` | Chuyển đổi Ngôn ngữ | Mở rộng thị trường, phục vụ khách du lịch và nâng tầm thương hiệu. | Khách du lịch, người nước ngoài | Để đọc hiểu thực đơn bằng ngôn ngữ mẹ đẻ của mình. |
| `MENU-401` | Lọc món theo Chế độ ăn & Dị ứng | Thể hiện sự quan tâm và trách nhiệm, xây dựng niềm tin về an toàn thực phẩm. | Khách có nhu cầu đặc biệt | Để nhanh chóng tìm thấy các món ăn phù hợp và an toàn cho sức khỏe. |
| `MENU-402` | Hiển thị Thông tin Dinh dưỡng (Calories) | Đáp ứng xu hướng sống khỏe, thu hút tệp khách hàng quan tâm sức khỏe. | Khách hàng quan tâm sức khỏe | Để kiểm soát lượng calo và lựa chọn món ăn phù hợp với chế độ dinh dưỡng. |
| `MENU-501` | Menu Kể Chuyện theo Bộ sưu tập | Tăng tương tác và dẫn dắt khám phá, giảm "tê liệt lựa chọn". | Khách hàng mới, người hay do dự | Để khám phá thực đơn một cách thú vị hơn, như lướt xem các bộ sưu tập phim. |
| `MENU-502` | Hiển thị Đánh giá Món ăn (Social Proof) | Tận dụng hiệu ứng đám đông để tăng tỷ lệ chuyển đổi và sự tự tin khi đặt món. | Mọi khách hàng | Để biết món nào đang được nhiều người yêu thích và đánh giá cao. |
| `MENU-601` | AI Tìm kiếm Thông minh bằng Ngữ nghĩa | Tạo ra sự khác biệt đột phá trong trải nghiệm tìm kiếm. | Mọi khách hàng | Để tìm kiếm món ăn theo cảm xúc hoặc nhu cầu ("món gì giải nhiệt", "đồ ăn không béo"). |
| `MENU-602` | AI Gợi ý Món ăn kèm (Upsell/Cross-sell) | Tăng giá trị đơn hàng trung bình (AOV) một cách tự nhiên. | Mọi khách hàng, Chủ quán | Để được gợi ý các món ăn kèm phù hợp, giúp bữa ăn ngon và trọn vẹn hơn. |
| `MENU-701` | Xem trước món ăn bằng AR | Tạo hiệu ứng "wow" và sự khác biệt hóa mạnh mẽ về mặt công nghệ. | Khách hàng trẻ, sành công nghệ | Để "đặt thử" mô hình 3D của món ăn lên bàn thật trước khi gọi. |
| `MENU-801` | Menu Cá nhân hóa Tuyệt đối | Đỉnh cao của trải nghiệm khách hàng, biến mỗi lần ghé thăm thành độc nhất. | Khách hàng trung thành | Để thấy một thực đơn được tạo ra riêng cho mình, dựa trên sở thích và lịch sử ăn uống. |

---
### **MODULE: ORD - Ordering & Order Management**
*Mục tiêu: Cung cấp một quy trình đặt món chính xác, linh hoạt và minh bạch, từ lúc chọn món đến khi món được phục vụ.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `ORD-101` | Thêm Món vào Giỏ hàng | Chức năng cơ bản nhất của một hệ thống gọi món. | Mọi khách hàng | Để chọn món ăn mình muốn. |
| `ORD-102` | Tùy chỉnh Món (Structured Options) | Tăng tính linh hoạt, đáp ứng các nhu cầu phổ biến của khách hàng. | Mọi khách hàng | Để tùy chọn size, mức đường/đá... theo ý muốn. |
| `ORD-103` | Quản lý Giỏ hàng | Đảm bảo sự chính xác trước khi gửi đơn, giảm sai sót. | Mọi khách hàng | Để xem lại, thay đổi số lượng hoặc xóa món khỏi giỏ hàng. |
| `ORD-104` | Gửi Đơn hàng & Nhận Xác nhận | Cung cấp sự yên tâm cho khách hàng, xác nhận giao dịch đã bắt đầu. | Mọi khách hàng | Để biết chắc chắn đơn hàng đã được gửi đến bếp thành công. |
| `ORD-201` | Ghi chú Tự do cho Món ăn | Đáp ứng các yêu cầu đặc biệt không có sẵn, tăng sự hài lòng. | Khách hàng có yêu cầu đặc biệt | Để ghi chú các yêu cầu riêng như "không hành", "ít cay"... |
| `ORD-202` | Theo dõi Trạng thái Đơn hàng (Đơn giản) | Quản lý kỳ vọng, giảm sự sốt ruột của khách hàng trong lúc chờ đợi. | Mọi khách hàng | Để biết món ăn của mình đang ở giai đoạn nào (Đã nhận, Đang chuẩn bị...). |
| `ORD-203` | Đặt thêm Món vào Đơn hàng hiện tại | Tăng doanh thu, giải quyết nhu cầu phát sinh một cách liền mạch. | Mọi khách hàng | Để dễ dàng gọi thêm món mà không cần gọi nhân viên hay tạo đơn mới. |
| `ORD-301` | Yêu cầu Hủy món (Trong thời gian giới hạn) | Giảm trải nghiệm tiêu cực khi đặt nhầm, tăng sự tin tưởng vào hệ thống. | Mọi khách hàng | Để có thể sửa sai ngay lập tức nếu lỡ tay đặt nhầm món. |
| `ORD-401` | Đặt món Trước khi đến (Pre-order/Pickup) | Mở rộng mô hình kinh doanh, phục vụ tệp khách hàng bận rộn. | Dân văn phòng, người bận rộn | Để đặt món trước và đến lấy ngay, không phải chờ đợi. |
| `ORD-402` | Chức năng Đặt món Chung (Group Order Host) | Giải quyết vấn đề gọi món cho nhóm lớn, thu hút khách đi theo nhóm. | Nhóm bạn, đồng nghiệp | Để một người có thể mời cả nhóm cùng vào chọn món trên một đơn hàng chung. |
| `ORD-501` | Xem Thời gian chờ Ước tính (ETA) | Nâng cao trải nghiệm chờ đợi bằng cách cung cấp thông tin cụ thể. | Mọi khách hàng | Để biết khoảng thời gian dự kiến có món, giúp chủ động hơn. |
| `ORD-601` | Gửi tặng Món ăn cho bàn khác | Tạo ra các tương tác xã hội thú vị, tăng sự gắn kết trong không gian quán. | Các cặp đôi, nhóm bạn | Để tạo bất ngờ cho bạn bè hoặc người thân bằng một món quà. |
| `ORD-701` | Tích hợp với các App Giao hàng | Mở rộng kênh bán hàng ra các nền tảng lớn nếu có chiến lược. | Chủ quán | Để quản lý đơn hàng từ GrabFood, ShopeeFood... ngay trên hệ thống. |
| `ORD-702` | Đặt Gói ăn theo Tuần (Weekly Meal Plan) | Tạo ra một mô hình kinh doanh mới với doanh thu định kỳ. | Khách hàng theo chế độ, dân văn phòng | Để đăng ký một gói ăn cho cả tuần mà không cần chọn món mỗi ngày. |
| `ORD-801` | AI Tự động Đặt món (Predictive Ordering) | Đỉnh cao của sự tiện lợi, dự đoán nhu cầu của khách hàng. | Khách hàng trung thành | Để hệ thống tự gợi ý một đơn hàng hoàn chỉnh dựa trên thói quen của bạn. |
| `ORD-803` | Giao hàng bằng Drone tự hành | Tầm nhìn về tương lai của ngành giao vận F&B. | Khách hàng ở khu vực lân cận | Để nhận đồ ăn một cách nhanh chóng và ngoạn mục. |

---
### **MODULE: PAY - Payment & Billing**
*Mục tiêu: Mang đến một trải nghiệm thanh toán không ma sát, nhanh chóng, linh hoạt và an toàn.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `PAY-101` | Xem Hóa đơn Tạm tính | Cung cấp sự minh bạch về chi phí, một yêu cầu cơ bản của mọi giao dịch. | Mọi khách hàng | Để kiểm tra tổng số tiền đã chi tiêu bất cứ lúc nào. |
| `PAY-102` | Thanh toán bằng mã VietQR Động | Cung cấp phương thức thanh toán số cơ bản, hiệu quả và phổ biến nhất. | Mọi khách hàng | Để thanh toán nhanh chóng bằng cách quét mã QR từ ứng dụng ngân hàng. |
| `PAY-201` | Thanh toán bằng Tiền mặt (Thông minh) | Tối ưu hóa quy trình thủ công, giảm thời gian chờ và tăng hiệu suất nhân viên. | Khách dùng tiền mặt, Nhân viên | Để quá trình trả tiền mặt diễn ra nhanh hơn, nhân viên không phải đi lại nhiều lần. |
| `PAY-301` | Chức năng Chia hóa đơn Theo món | Giải quyết "cơn ác mộng" chia tiền, một "killer feature" cho khách đi nhóm. | Nhóm bạn, đồng nghiệp | Để mỗi người có thể tự chọn và trả tiền cho đúng món mình đã ăn. |
| `PAY-302` | Chức năng Chia hóa đơn Đều | Cung cấp một giải pháp chia tiền đơn giản và nhanh chóng cho các nhóm. | Nhóm bạn, đồng nghiệp | Để chia đều tổng hóa đơn cho mọi người chỉ bằng một cú nhấp chuột. |
| `PAY-401` | Tích hợp Thanh toán qua Ví điện tử | Đa dạng hóa lựa chọn thanh toán, đáp ứng thói quen của nhiều người dùng. | Khách dùng ví điện tử | Để thanh toán tiện lợi bằng MoMo, ZaloPay... ngay trên ứng dụng. |
| `PAY-402` | Tùy chọn Tip cho Nhân viên | Tạo văn hóa cảm ơn, tăng động lực và thu nhập cho nhân viên. | Nhân viên phục vụ, Khách hàng hài lòng | Để có một cách lịch sự và dễ dàng để gửi lời cảm ơn đến nhân viên. |
| `PAY-501` | Nạp Ví & Thanh toán (Wallet) | "Khóa chân" khách hàng, tạo dòng tiền trước và làm nền tảng cho chương trình loyalty. | Khách hàng trung thành, Chủ quán | Để nạp tiền một lần, tiêu dùng nhiều lần và nhận ưu đãi. |
| `PAY-502` | Thanh toán Kết hợp (Ví + Phương thức khác) | Giải quyết tình huống ví không đủ tiền một cách mượt mà, tránh gây khó xử. | Khách hàng dùng ví | Để dễ dàng trả phần còn thiếu bằng một phương thức khác khi ví không đủ tiền. |
| `PAY-701` | Tích hợp Trả góp qua Kredivo/Fundiin | Phục vụ các đơn hàng giá trị lớn như tiệc, sự kiện. | Khách hàng tổ chức tiệc | Để có thể thanh toán các hóa đơn lớn một cách linh hoạt hơn. |
| `PAY-703` | Chấp nhận Thanh toán bằng Tiền mã hóa | Đón đầu xu hướng công nghệ tài chính nếu thị trường và luật pháp cho phép. | Khách hàng dùng crypto | Để có thêm một lựa chọn thanh toán hiện đại. |

---
### **MODULE: LOY - Loyalty & Engagement**
*Mục tiêu: Biến một giao dịch thành một mối quan hệ, khuyến khích khách hàng quay lại và tăng cường tương tác với thương hiệu.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `LOY-201` | Đánh giá Trải nghiệm (5 sao & Bình luận) | Thu thập "dữ liệu vàng" để cải tiến sản phẩm và dịch vụ một cách liên tục. | Chủ quán, Khách hàng | Để chia sẻ cảm nhận về bữa ăn và giúp nhà hàng trở nên tốt hơn. |
| `LOY-301` | Lưu Món ăn Yêu thích | Tăng sự tiện lợi và cá nhân hóa, giúp khách hàng trung thành quay lại dễ dàng hơn. | Khách hàng trung thành | Để lưu lại các món "tủ" và đặt lại nhanh chóng trong những lần sau. |
| `LOY-401` | Chương trình Tích điểm Cơ bản | Xây dựng nền tảng đầu tiên cho lòng trung thành, khuyến khích khách hàng chi tiêu nhiều hơn. | Khách hàng trung thành | Để được tích điểm sau mỗi lần ăn và dùng điểm đó cho các ưu đãi. |
| `LOY-501` | Cá nhân hóa Cơ bản (Chào mừng & Gợi ý) | Khiến khách hàng cảm thấy được nhận ra và trân trọng, tăng sự gắn kết. | Khách hàng trung thành | Để được hệ thống chào đúng tên và gợi ý lại món ăn quen thuộc. |
| `LOY-601` | Gamification - Hệ thống Nhiệm vụ & Huy hiệu | Tăng tần suất quay lại và tương tác bằng cách biến trải nghiệm thành một trò chơi. | Khách hàng trẻ, người thích thử thách | Để hoàn thành các thử thách ("ăn 5 món phở khác nhau") và nhận phần thưởng. |
| `LOY-602` | Vòng quay May mắn & Phần thưởng Bất ngờ | Tạo yếu tố phấn khích và bất ngờ, giữ chân người dùng. | Mọi khách hàng | Để có cơ hội nhận được các voucher, món ăn miễn phí một cách vui vẻ. |
| `LOY-603` | Hệ thống Hạng thành viên (Silver, Gold, Platinum) | Tạo ra một lộ trình và mục tiêu rõ ràng cho khách hàng thân thiết phấn đấu. | Khách hàng trung thành nhất | Để đạt được các cấp độ thành viên cao hơn và hưởng những đặc quyền riêng biệt. |
| `LOY-701` | Marketplace Đổi quà | Tăng giá trị của điểm tích lũy, tạo hệ sinh thái với các đối tác. | Khách hàng có nhiều điểm | Để dùng điểm tích lũy đổi quà không chỉ của quán mà còn của các thương hiệu khác. |
| `LOY-801` | Trợ lý Ẩm thực Cá nhân (AI Concierge) | Đỉnh cao của dịch vụ chăm sóc khách hàng, cung cấp giá trị vượt ngoài bữa ăn. | Khách hàng quan tâm sức khỏe | Để có một trợ lý AI tư vấn dinh dưỡng và lên kế hoạch ăn uống cho mình. |

---
### **MODULE: STAFF - Staff Tools & Operations**
*Mục tiêu: Cung cấp các công cụ mạnh mẽ để nhân viên (bếp, phục vụ, quản lý) vận hành hiệu quả, giảm sai sót và nâng cao chất lượng dịch vụ.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `STAFF-101` | Màn hình Bếp (KDS) nhận đơn hàng | Xây dựng cầu nối bắt buộc giữa khách hàng và nhà bếp, số hóa quy trình cốt lõi. | Nhân viên bếp | Để nhận đơn hàng một cách rõ ràng, chính xác và có hệ thống. |
| `STAFF-102` | Đánh dấu Hoàn thành Món ăn | Đồng bộ thông tin giữa bếp và phục vụ, tăng tốc độ mang món ra cho khách. | Nhân viên bếp, Nhân viên phục vụ | Để biết chính xác khi nào món ăn đã sẵn sàng để phục vụ. |
| `STAFF-201` | Chức năng Gọi Nhân viên Hỗ trợ | Cung cấp kênh giao tiếp văn minh, đảm bảo không bỏ sót yêu cầu của khách. | Khách hàng, Nhân viên phục vụ | Để gọi nhân viên một cách lịch sự và nhận được phản hồi nhanh chóng. |
| `STAFF-301` | Giao tiếp Nội bộ (Bếp <-> Phục vụ) | Tối ưu luồng vận hành, giảm việc phải chạy đi chạy lại và gọi nhau. | Nhân viên bếp, Nhân viên phục vụ | Để trao đổi thông tin nhanh chóng ngay trên hệ thống (VD: "Bàn 5 hỏi món..."). |
| `STAFF-302` | Phân công Bàn cho Nhân viên | Giúp quản lý phân công khu vực phụ trách rõ ràng, tăng trách nhiệm. | Quản lý, Nhân viên phục vụ | Để biết rõ mình chịu trách nhiệm cho những bàn nào trong ca làm việc. |
| `STAFF-401` | Theo dõi Hiệu suất Nhân viên (KPIs) | Cung cấp dữ liệu để quản lý đánh giá nhân viên một cách khách quan. | Quản lý, Chủ quán | Để biết nhân viên nào đang làm việc hiệu quả dựa trên dữ liệu thực tế. |
| `STAFF-501` | Quản lý Tồn kho Cơ bản (Nhập/Xuất thủ công) | Giúp nhà hàng kiểm soát lượng nguyên vật liệu, tránh tình trạng hết đột ngột. | Quản lý, Nhân viên kho | Để theo dõi số lượng tồn kho của các nguyên vật liệu chính. |
| `STAFF-601` | Tự động tính Tồn kho theo Nguyên vật liệu | Tự động hóa hoàn toàn việc quản lý kho, giảm sai sót và lãng phí. | Quản lý, Đầu bếp | Để hệ thống tự động tính toán số lượng món có thể bán dựa trên NVL còn lại. |
| `STAFF-701` | Tích hợp Hệ thống Chấm công | Mở rộng sản phẩm thành một giải pháp quản lý nhà hàng toàn diện hơn. | Quản lý, Nhân viên | Để quản lý lịch làm việc và chấm công ngay trên một hệ thống duy nhất. |
| `STAFF-702` | Tích hợp Thiết bị IoT trong bếp | Đón đầu xu hướng nhà bếp thông minh, thu thập dữ liệu vận hành chính xác. | Đầu bếp, Quản lý | Để các thiết bị như lò nướng, tủ lạnh có thể gửi dữ liệu lên hệ thống. |
| `STAFF-801` | Tích hợp Robot Chế biến & Phục vụ | Tầm nhìn về nhà hàng tự động hóa, phần mềm là "bộ não" điều khiển. | Chủ quán | Để tự động hóa các công việc lặp đi lặp lại, tối ưu hóa chi phí nhân sự. |

---
### **MODULE: ADM - Admin & Business Intelligence**
*Mục tiêu: Trao quyền cho chủ sở hữu và quản lý nhà hàng với các công cụ quản trị mạnh mẽ và dữ liệu thông minh để ra quyết định kinh doanh.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `ADM-101` | Quản trị Menu (Thêm/Sửa/Xóa Món) | Cung cấp công cụ tối thiểu để chủ quán có thể quản lý "sản phẩm" của mình. | Chủ quán, Quản lý | Để dễ dàng thay đổi thực đơn, giá cả và hình ảnh món ăn. |
| `ADM-201` | Báo cáo Doanh thu theo Ngày | Cung cấp cái nhìn cơ bản nhất về hiệu quả kinh doanh hàng ngày. | Chủ quán, Quản lý | Để biết được doanh thu mỗi ngày và theo dõi xu hướng. |
| `ADM-202` | Quản lý Bàn & Mã QR | Cung cấp công cụ để chủ quán tự set up và quản lý sơ đồ bàn của mình. | Chủ quán, Quản lý | Để tự tạo và quản lý mã QR cho từng bàn trong nhà hàng. |
| `ADM-203` | Xem Lịch sử Đơn hàng | Cần thiết cho việc đối soát, giải quyết khiếu nại và phân tích sau này. | Chủ quán, Quản lý | Để tra cứu lại thông tin chi tiết của bất kỳ đơn hàng nào đã phát sinh. |
| `ADM-301` | Quản lý Khuyến mãi Đơn giản | Cung cấp công cụ marketing cơ bản để thu hút và giữ chân khách hàng. | Chủ quán, Quản lý | Để tự tạo các chương trình giảm giá đơn giản (giảm % trên hóa đơn, tặng món...). |
| `ADM-302` | Phân quyền Nhân viên (Roles & Permissions) | Bảo mật hệ thống, đảm bảo nhân viên chỉ thấy và làm được những gì họ được phép. | Chủ quán, Quản lý | Để tạo các vai trò (quản lý, thu ngân...) với các quyền hạn khác nhau. |
| `ADM-303` | Báo cáo Món ăn Bán chạy | Cung cấp insight quan trọng để tối ưu menu và chiến lược giá. | Chủ quán, Quản lý | Để biết món nào đang mang lại doanh thu tốt nhất và món nào cần cải thiện. |
| `ADM-501` | Quản lý nhiều Chi nhánh | Mở rộng hệ thống để phục vụ các chuỗi nhà hàng, một hướng phát triển quan trọng. | Chủ chuỗi nhà hàng | Để quản lý menu, doanh thu, nhân viên... cho tất cả các chi nhánh từ một nơi. |
| `ADM-601` | Quản lý Feedback & Tự động phản hồi | Hệ thống hóa việc xử lý phản hồi, biến trải nghiệm xấu thành cơ hội. | Quản lý, Chăm sóc khách hàng | Để tập trung mọi đánh giá của khách, tự động gửi voucher xin lỗi cho các đánh giá thấp. |
| `ADM-701` | Tích hợp với Phần mềm Kế toán (MISA) | Tự động hóa công việc tài chính, phục vụ các doanh nghiệp lớn. | Bộ phận kế toán, Chủ quán | Để dữ liệu doanh thu tự động đồng bộ sang phần mềm kế toán, không cần nhập tay. |
| `ADM-801` | Tự động Đặt hàng Nguyên vật liệu | Tối ưu hóa chuỗi cung ứng, giảm lãng phí và chi phí tồn kho. | Quản lý, Chủ quán | Để hệ thống tự dự báo và đặt hàng nguyên vật liệu khi sắp hết. |
| `ADM-802` | Tự động Tối ưu Giá Động (Dynamic Pricing) | Tối đa hóa doanh thu bằng cách điều chỉnh giá linh hoạt theo nhu cầu. | Chủ quán | Để giá món ăn có thể tự động thay đổi vào giờ cao điểm, ngày lễ... |
| `ADM-802` | Quản lý Chuỗi cung ứng trên Blockchain | Tầm nhìn về sự minh bạch tuyệt đối trong nguồn gốc thực phẩm. | Mọi khách hàng, Chủ quán | Để truy xuất được nguồn gốc của từng nguyên liệu, từ nông trại đến bàn ăn. |

---
### **MODULE: DATA - Data Platform & Analytics**
*Mục tiêu: Xây dựng nền tảng dữ liệu vững chắc, biến dữ liệu thô thành các insight giá trị để tối ưu sản phẩm và chiến lược kinh doanh.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `DATA-301` | Dashboard Phân tích Cơ bản | Tập trung các chỉ số quan trọng vào một nơi duy nhất, dễ theo dõi. | Chủ quán, Quản lý | Để có một cái nhìn tổng quan nhanh về "sức khỏe" của nhà hàng mỗi ngày. |
| `DATA-401` | Phân tích Hành vi Người dùng (User Funnel) | Hiểu rõ người dùng đang gặp khó khăn ở bước nào để tối ưu trải nghiệm. | Product Manager, Designer | Để biết được bao nhiêu % người dùng bỏ cuộc ở bước chọn món, đặt hàng, thanh toán... |
| `DATA-402` | Phân tích Giỏ hàng (Market Basket Analysis) | Tìm ra các cặp món ăn thường được mua cùng nhau để tạo combo, upsell hiệu quả. | Marketing, Chủ quán | Để biết "khách ăn phở thường uống gì?", từ đó tạo ra các combo hấp dẫn. |
| `DATA-501` | Phân khúc Khách hàng (RFM Analysis) | Phân loại khách hàng để có chiến lược chăm sóc phù hợp, tăng tỷ lệ giữ chân. | Marketing, CRM | Để biết ai là khách hàng VIP, ai là khách hàng mới, ai sắp "rơi rụng" để có hành động phù hợp. |
| `DATA-601` | A/B Testing Framework | Cho phép thử nghiệm các thay đổi để tìm ra phiên bản hiệu quả nhất một cách khoa học. | Product Manager, Marketing | Để thử nghiệm 2 phiên bản của một nút bấm, một câu chữ... xem cái nào mang lại hiệu quả cao hơn. |
| `DATA-602` | Dự báo Doanh thu (Sales Forecasting) | Giúp chủ quán lên kế hoạch nhân sự và nguyên vật liệu tốt hơn. | Chủ quán, Quản lý | Để dự đoán được doanh thu của tuần tới, tháng tới dựa trên dữ liệu quá khứ. |
| `DATA-701` | Xây dựng Nền tảng Dữ liệu Khách hàng (CDP) | Hợp nhất dữ liệu khách hàng từ mọi nguồn để có cái nhìn 360 độ. | Marketing, Data Analyst | Để có một nơi duy nhất chứa mọi thông tin về một khách hàng. |
| `DATA-702` | AI Chống gian lận (Fraud Detection) | Bảo vệ doanh nghiệp khỏi các hành vi lạm dụng khuyến mãi, trục lợi. | Chủ quán | Để tự động phát hiện và ngăn chặn các tài khoản tạo ra để lạm dụng voucher. |
| `DATA-801` | Phân tích Hình ảnh Món ăn (AI Vision) | Tận dụng nguồn dữ liệu do người dùng tạo ra trên mạng xã hội. | Marketing | Để AI tự động tìm các bài đăng check-in về quán và phân tích. |
| `DATA-802` | Phân tích Cảm xúc qua Giọng nói/Văn bản | Đo lường mức độ hài lòng của khách hàng một cách sâu sắc và tự động. | Chăm sóc khách hàng, Quản lý | Để AI tự động "đọc" các bình luận và phân loại chúng là tích cực, tiêu cực hay trung tính. |

---
### **MODULE: MKT - Marketing & Communication**
*Mục tiêu: Cung cấp các công cụ để thu hút, giữ chân và giao tiếp hiệu quả với khách hàng.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `MKT-301` | Tạo Mã giảm giá (Voucher Codes) | Cung cấp công cụ marketing linh hoạt để chạy các chiến dịch cụ thể. | Marketing, Chủ quán | Để tạo ra các mã giảm giá cho các chiến dịch quảng cáo, hợp tác... |
| `MKT-401` | Gửi Thông báo Đẩy (Push Notification) | Cung cấp công cụ re-marketing mạnh mẽ để tiếp cận lại người dùng ngay trên điện thoại. | Marketing | Để gửi thông báo về chương trình khuyến mãi mới hay một món ăn đặc biệt. |
| `MKT-502` | Gửi Email Marketing Tự động | Xây dựng kênh giao tiếp dài hạn với khách hàng một cách tự động. | Marketing | Để tự động gửi email chúc mừng sinh nhật kèm voucher cho khách hàng. |
| `MKT-503` | Chương trình Giới thiệu Bạn bè (Referral Program) | Tận dụng kênh marketing truyền miệng để có thêm khách hàng mới với chi phí thấp. | Mọi khách hàng, Chủ quán | Để cả người giới thiệu và người được giới thiệu đều nhận được ưu đãi. |
| `MKT-601` | AI Tối ưu hóa đơn (Gợi ý để đạt KM) | Tăng giá trị đơn hàng bằng cách gợi ý một cách thông minh và có lợi cho khách. | Khách hàng, Chủ quán | Để được hệ thống gợi ý "thêm một món nhỏ để được giảm giá lớn hơn". |
| `MKT-701` | Xây dựng Nền tảng Affiliate Marketing | Hợp tác với các KOL/Influencer một cách có hệ thống và đo lường được. | Marketing, KOLs/Influencers | Để các đối tác có link riêng để giới thiệu và nhận hoa hồng. |
| `MKT-801` | Tích hợp Thế giới ảo (Metaverse Dining) | Đón đầu tương lai của tương tác số và marketing trải nghiệm. | Khách hàng trẻ, sành công nghệ | Để có thể "ghé thăm" không gian nhà hàng và trải nghiệm trong thế giới ảo. |

---
### **MODULE: GEN - General / Platform**
*Mục tiêu: Thể hiện tầm nhìn cuối cùng về một nền tảng toàn diện, là "Hệ điều hành" cho ngành F&B.*

| Mã tính năng | Tên tính năng | Mục tiêu Chiến lược | Đối tượng Hưởng lợi | Giá trị Cốt lõi |
| :--- | :--- | :--- | :--- | :--- |
| `GEN-801` | Hệ điều hành Toàn diện cho Nhà hàng (Restaurant OS) | Tầm nhìn cuối cùng: một nền tảng duy nhất quản lý mọi khía cạnh của một doanh nghiệp F&B. | Chủ doanh nghiệp F&B | Để có một giải pháp "tất cả trong một" cho việc kinh doanh nhà hàng. |
