# STAFF-101 - Living Feature Profile: Màn hình Bếp (KDS) nhận đơn hàng

- **Status:** `Approved` | **Owner:** Mespace | **Updated:** 2025-06-27

---

### 🎯 THE STRATEGIC WHY
> **Mission:** Số hóa quy trình nhận đơn, loại bỏ giấy bút và sai sót, mang lại sự trật tự và hiệu quả cho nhà bếp.

- **Hypothesis:** We believe **hiển thị các đơn hàng mới một cách trực quan trên màn hình bếp** for **nhân viên bếp** will result in **giảm thời gian chế biến món và giảm tỷ lệ làm sai/thiếu món**.
- **Success is:** Thời gian trung bình từ lúc đơn hàng được gửi đến lúc bếp xác nhận xử lý `< 30 giây`.
- **Also track:** `Số lượng đơn hàng sai sót (đo thủ công/khảo sát)`, `Tỷ lệ đơn hàng bị xử lý trễ`.

---

### 🎨 THE USER EXPERIENCE
- **Core User Flow:**
    1.  Một đơn hàng mới từ khách được gửi đến, ngay lập tức xuất hiện trên màn hình KDS dưới dạng một "phiếu" (ticket).
    2.  Phiếu mới có dấu hiệu nổi bật (VD: màu nền, viền, có âm báo) để thu hút sự chú ý.
    3.  Phiếu hiển thị rõ: Số bàn, danh sách các món ăn và số lượng.
    4.  Nhân viên bếp nhấn vào phiếu để xác nhận đã bắt đầu xử lý.
- **Design Principles:**
    - `High Readability:` Font chữ phải lớn, dày, độ tương phản cao. Thiết kế cho môi trường ánh sáng phức tạp và khoảng cách nhìn xa.
    - `Information Density:` Hiển thị đủ thông tin cần thiết nhưng không gây rối mắt. Ưu tiên sự rõ ràng hơn là đẹp.
    - `Efficiency-Driven:` Giảm thiểu số lần chạm. Các hành động quan trọng nhất phải thực hiện được bằng một cú chạm.
- **Must-Handle Scenarios:**
    - ✅ **Happy Path:** Đơn hàng mới vào, hiển thị rõ ràng, nhân viên xác nhận và bắt đầu làm.
    - 🔔 **Alerting:** Có âm báo tùy chọn cho đơn hàng mới.
    - 📈 **Overload:** Giao diện phải xử lý tốt khi có nhiều đơn hàng cùng lúc (VD: có thanh cuộn, phân trang hoặc cột).
    - ❌ **Error:** Nếu mất kết nối mạng, phải có một chỉ báo trực quan rất rõ ràng và cố gắng kết nối lại tự động.

---
