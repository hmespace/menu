# MENU-101 - Living Feature Profile: Xem Menu & Chi tiết Món ăn

- **Status:** `Approved` | **Owner:** Mespace | **Updated:** 2025-06-27

---

### 🎯 THE STRATEGIC WHY
> **Mission:** Biến việc xem menu từ một danh sách nhàm chán thành một hành trình khám phá ẩm thực hấp dẫn và trực quan.

- **Hypothesis:** We believe **hiển thị thực đơn với hình ảnh, mô tả và giá cả rõ ràng** for **mọi khách hàng** will result in **tăng sự tự tin và tốc độ ra quyết định đặt món**.
- **Success is:** Tỷ lệ người dùng click xem chi tiết ít nhất một món ăn `> 80%`.
- **Also track:** `Thời gian trung bình trên trang menu`, `Tỷ lệ thêm món vào giỏ hàng từ trang chi tiết`, `Lighthouse Performance Score`.

---

### 🎨 THE USER EXPERIENCE
- **Core User Flow:**
  1.  Người dùng truy cập trang Menu, thấy ngay các danh mục và các món ăn nổi bật.
  2.  Lướt xem hoặc chọn một danh mục (VD: "Phở", "Bún", "Đồ uống").
  3.  Nhấn vào một món ăn để xem chi tiết.
  4.  Trang/Modal chi tiết hiện ra với hình ảnh lớn, mô tả đầy đủ, giá và nút "Thêm vào giỏ hàng".
- **Design Principles:**
  - `Visual First:` Hình ảnh món ăn là nhân vật chính. Phải to, sắc nét và tải nhanh.
  - `Information at a Glance:` Giá cả và tên món phải được thấy ngay lập tức, không cần thao tác phụ.
  - `Effortless Navigation:` Việc di chuyển giữa các danh mục và món ăn phải mượt mà, không giật lag.
- **Must-Handle Scenarios:**
  - ✅ **Happy Path:** Người dùng xem menu, chọn món, xem chi tiết và thêm vào giỏ hàng thành công.
  - ⏳ **Loading:** Sử dụng **Skeleton UI** cho cả danh sách menu và trang chi tiết để tạo cảm giác nhanh chóng. Đây là yêu cầu bắt buộc.
  - ❌ **Error:**
    - **Không tải được menu:** Hiển thị thông báo lỗi thân thiện và nút "Tải lại".
    - **Hình ảnh món ăn bị lỗi:** Hiển thị một ảnh placeholder mặc định, tuyệt đối không làm vỡ layout.

---
