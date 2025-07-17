# Bảng tra cứu Toàn bộ các Thực thể Dữ liệu (Master Datatable List)

Bảng dưới đây liệt kê tất cả các datatable tiềm năng, được phân loại để dễ hiểu, cùng với mục đích và giai đoạn triển khai lần đầu.

**Phân loại Bảng:**
*   **Primary Entity:** Thực thể cốt lõi, có thể tồn tại độc lập.
*   **Supporting Entity:** Thực thể phụ, bổ sung thông tin cho một Primary Entity.
*   **Junction Table:** Bảng nối, tạo ra mối quan hệ nhiều-nhiều giữa hai bảng khác.
*   **Log Table:** Bảng ghi nhật ký, lưu lại lịch sử các sự kiện.

---

## I. CORE & LOCATION (LÕI & KHÔNG GIAN)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`brands`** | Primary Entity | Quản lý thông tin thương hiệu tổng. | **Phase 1** - `ONB-101` |
| **`locations`** | Primary Entity | Quản lý thông tin, trạng thái của từng chi nhánh. | **Phase 1** - `ONB-101` |
| **`tables`** | Supporting Entity | Quản lý từng bàn ăn vật lý trong một chi nhánh. | **Phase 1** - `ONB-101` |

## II. USER & STAFF (NGƯỜI DÙNG & NHÂN VIÊN)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`users`** | Primary Entity | Hồ sơ 360° của khách hàng đã đăng ký. | **Phase 3** - `ONB-301` |
| **`staff`** | Primary Entity | Hồ sơ năng lực và hiệu suất của nhân viên. | **Phase 1** - `ADM-101` |
| **`roles`** | Supporting Entity | Định nghĩa các vai trò trong hệ thống (Quản lý, Bếp...). | **Phase 3** - `ADM-301` |
| **`permissions`** | Junction Table | Gán các quyền hạn cụ thể cho từng vai trò. | **Phase 3** - `ADM-301` |

## III. MENU & DISHES (THỰC ĐƠN & MÓN ĂN)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`dishes`** | Primary Entity | Bản thiết kế toàn diện của một món ăn. | **Phase 1** - `MENU-101` |
| **`categories`** | Supporting Entity | Phân loại các món ăn vào các nhóm (Món chính, Đồ uống...). | **Phase 1** - `MENU-101` |
| **`tags`** | Supporting Entity | Định nghĩa các nhãn dán (Bestseller, Món mới...). | **Phase 3** - `MENU-302` |
| **`dishTags`** | Junction Table | Nối món ăn với các nhãn dán (quan hệ nhiều-nhiều). | **Phase 3** - `MENU-302` |
| **`optionGroups`** | Supporting Entity | Nhóm các tùy chọn (VD: "Độ chín", "Mức đường"). | **Phase 2** - `ORD-201` |
| **`options`** | Supporting Entity | Các tùy chọn cụ thể trong một nhóm (VD: "Tái", "70% đường"). | **Phase 2** - `ORD-201` |
| **`allergens`** | Supporting Entity | Danh sách các chất gây dị ứng tiềm năng (Đậu phộng, Sữa...). | **Phase 4** - `MENU-401` |
| **`dishAllergens`** | Junction Table | Nối món ăn với các chất gây dị ứng. | **Phase 4** - `MENU-401` |

## IV. ORDERING & PAYMENTS (ĐẶT MÓN & THANH TOÁN)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`orders`** | Primary Entity | Tài liệu giao dịch sống, theo dõi toàn bộ một đơn hàng. | **Phase 1** - `ORD-103` |
| **`orderItems`** | Supporting Entity | Chi tiết từng món ăn trong một đơn hàng. | **Phase 1** - `ORD-101` |
| **`orderItemOptions`** | Junction Table | Ghi lại các tùy chọn mà khách đã chọn cho một món. | **Phase 2** - `ORD-201` |
| **`payments`** | Supporting Entity | Ghi nhận các giao dịch thanh toán cho một đơn hàng. | **Phase 1** - `PAY-102` |
| **`billSplits`** | Supporting Entity | Quản lý một phiên chia hóa đơn. | **Phase 3** - `PAY-301` |
| **`splitParticipants`** | Supporting Entity | Ghi nhận phần tiền của mỗi người trong một phiên chia hóa đơn. | **Phase 3** - `PAY-301` |

## V. LOYALTY & ENGAGEMENT (KHÁCH HÀNG THÂN THIẾT & TƯƠNG TÁC)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`loyaltyAccounts`** | Primary Entity | Bảng cân đối lòng trung thành (điểm, hạng, ví...). | **Phase 3** - `LOY-301` |
| **`reviews`** | Primary Entity | Hệ thống lắng nghe, thu thập mọi phản hồi của khách. | **Phase 2** - `LOY-201` |
| **`membershipTiers`** | Supporting Entity | Định nghĩa các hạng thành viên (Silver, Gold...). | **Phase 6** - `LOY-603` |
| **`loyaltyTransactions`**| Log Table | Nhật ký các giao dịch điểm thưởng (tích/tiêu). | **Phase 4** - `LOY-401` |
| **`missions`** | Supporting Entity | Định nghĩa các nhiệm vụ trong hệ thống gamification. | **Phase 6** - `LOY-601` |
| **`badges`** | Supporting Entity | Định nghĩa các huy hiệu mà người dùng có thể đạt được. | **Phase 6** - `LOY-601` |
| **`userBadges`** | Junction Table | Ghi nhận các huy hiệu mà một người dùng đã sở hữu. | **Phase 6** - `LOY-601` |
| **`userGeneratedPhotos`**| Supporting Entity | Lưu trữ các hình ảnh do người dùng tải lên. | **Phase 8** - `MENU-801` |

## VI. MARKETING & PROMOTIONS (TIẾP THỊ & KHUYẾN MÃI)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`promotions`** | Primary Entity | Bộ quy tắc marketing linh hoạt, định nghĩa các chiến dịch. | **Phase 2** - `ADM-202` |
| **`vouchers`** | Supporting Entity | Các mã voucher cụ thể được tạo ra từ một chương trình khuyến mãi. | **Phase 2** - `ADM-202` |
| **`appliedVouchers`** | Junction Table | Ghi lại voucher nào đã được áp dụng cho đơn hàng nào. | **Phase 2** - `ADM-202` |

## VII. OPERATIONS & SUPPLY CHAIN (VẬN HÀNH & CHUỖI CUNG ỨNG)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`inventoryItems`** | Primary Entity | Hồ sơ toàn diện của một nguyên vật liệu/vật tư trong kho. | **Phase 5** - `STAFF-501` |
| **`dishIngredients`** | Junction Table | Định nghĩa công thức: món ăn nào cần bao nhiêu nguyên liệu nào. | **Phase 6** - `STAFF-601` |
| **`suppliers`** | Supporting Entity | Quản lý thông tin các nhà cung cấp. | **Phase 9** - `ADM-901` |
| **`kdsTickets`** | Supporting Entity | Phiếu gọi món hiển thị trên màn hình bếp (KDS). | **Phase 1** - `STAFF-101` |

## VIII. ANALYTICS & LOGGING (PHÂN TÍCH & NHẬT KÝ)

| Tên Bảng (Datatable) | Loại Bảng | Mục đích Cốt lõi | Sử dụng Lần đầu (First Used) |
| :--- | :--- | :--- | :--- |
| **`userEvents`** | Log Table | Ghi lại mọi hành vi quan trọng của người dùng trên app. | **Phase 4** - `DATA-401` |
| **`statusHistory`** | Log Table | Nhật ký thay đổi trạng thái của các thực thể quan trọng (đơn hàng...). | **Phase 2** - `ORD-203` |
