# STAFF-102 - Living Feature Profile: Đánh dấu Hoàn thành Món ăn

- **Status:** `Approved` | **Owner:** Mespace | **Updated:** 2025-06-27

---

### 🎯 THE STRATEGIC WHY
> **Mission:** Hoàn thiện vòng lặp giao tiếp giữa bếp và phục vụ, đảm bảo món ăn được mang ra ngay khi sẵn sàng.

- **Hypothesis:** We believe **cho phép nhân viên bếp đánh dấu từng món ăn đã hoàn thành** for **nhân viên bếp và phục vụ** will result in **giảm thời gian món ăn phải chờ tại quầy và tăng tốc độ phục vụ**.
- **Success is:** Giảm thời gian trung bình từ lúc "nhận đơn" đến lúc "tất cả các món được hoàn thành".
- **Also track:** `Số món ăn được đánh dấu hoàn thành mỗi giờ`, `Tỷ lệ đánh dấu nhầm (nếu có thể đo)`.

---

### 🎨 THE USER EXPERIENCE
- **Core User Flow:**
    1.  Trên màn hình KDS, nhân viên bếp xem chi tiết một phiếu gọi món.
    2.  Sau khi chế biến xong một món, họ chạm vào tên món đó trên màn hình.
    3.  Món ăn đó ngay lập tức thay đổi trạng thái (VD: bị gạch đi, mờ đi, hoặc có dấu tick bên cạnh).
    4.  Khi tất cả các món trong phiếu đã được đánh dấu, toàn bộ phiếu sẽ tự động chuyển sang trạng thái "Sẵn sàng" hoặc di chuyển sang cột "Chờ Lấy".
- **Design Principles:**
    - `One-Tap Action:` Hành động đánh dấu hoàn thành phải được thực hiện bằng một cú chạm duy nhất. Nhanh và dứt khoát.
    - `Clear Visual State:` Sự khác biệt giữa món "đang làm" và "đã xong" phải cực kỳ rõ ràng, dễ nhận biết từ xa.
    - `Unambiguous:` Thiết kế không cho phép sự nhầm lẫn. Mỗi hành động phải có một kết quả trực quan rõ ràng.
- **Must-Handle Scenarios:**
    - ✅ **Happy Path:** Chạm vào món, món được đánh dấu hoàn thành. Chạm vào tất cả, phiếu được đánh dấu hoàn thành.
    - ↩️ **Undo Action:** Cung cấp một cách đơn giản để hoàn tác nếu lỡ tay đánh dấu nhầm (VD: chạm lần nữa hoặc một nút "hoàn tác" nhỏ).
    - 🛎️ **Notification:** Khi một phiếu được hoàn thành, có thể gửi một tín hiệu/thông báo đến màn hình của nhân viên phục vụ (tính năng cho giai đoạn sau).
