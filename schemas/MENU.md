## **Kiến trúc Dữ liệu cho MENU (Khám phá Thực đơn)**

### **Giới thiệu**

Kiến trúc này được chia thành 5 phần logic để dễ hiểu:
-   **Phần A: Cấu trúc Sản phẩm Cốt lõi:** Định nghĩa "món ăn" là gì.
-   **Phần B: Làm giàu Nội dung & Trải nghiệm:** Kể "câu chuyện" của món ăn.
-   **Phần C: Thành phần, Dinh dưỡng & An toàn:** Trả lời câu hỏi "trong món ăn có gì?".
-   **Phần D: Quy tắc Kinh doanh & Vận hành:** Định nghĩa "khi nào và với giá bao nhiêu?".
-   **Phần E: Hiệu suất & Phân tích:** Trả lời câu hỏi "món ăn này hoạt động ra sao?".

---

#### **Phần A: Cấu trúc Sản phẩm Cốt lõi**

**Bảng 1: `menus`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id`, `restaurant_id`, `name`, `description`, `is_active`, `display_order`, `created_at`, `updated_at` | ... | Như phiên bản trước | 1 |
| `availability_schedule` | `JSONB` | Lịch hoạt động của menu (ví dụ: `{"days": [1,2,3,4,5], "from": "07:00", "to": "11:00"}`). | 3 |
| `version` | `Integer` | Số phiên bản của menu, giúp theo dõi lịch sử thay đổi. | 5 |
| `published_at` | `Timestamp` | Dấu thời gian khi phiên bản menu này được công bố. | 5 |

**Bảng 2: `menu_categories`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id`, `menu_id`, `name`, `description`, `display_order`, `created_at`, `updated_at` | ... | Như phiên bản trước | 1 |
| `parent_category_id` | `UUID` | Khóa ngoại tự tham chiếu, cho phép tạo danh mục con (ví dụ: Đồ uống -> Cà phê). | 3 |
| `image_url` | `String` | URL hình ảnh đại diện cho cả danh mục. | 3 |

**Bảng 3: `menu_items`** (Bảng định danh món ăn)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của món ăn. | 1 |
| `category_id` | `UUID` | Khóa ngoại, liên kết đến danh mục chứa món ăn này. | 1 |
| `name` | `String` | Tên món ăn (ví dụ: "Phở Bò Tái"). | 1 |
| `short_description` | `String(255)` | Mô tả ngắn gọn, hấp dẫn, hiển thị trên danh sách menu. | 1 |
| `long_description` | `Text` | Mô tả chi tiết về thành phần, hương vị, hiển thị trên trang chi tiết món ăn. | 1 |
| `translations` | `JSONB` | Lưu trữ các bản dịch cho `name` và các `description`. | 3 |
| `serving_temperature` | `Enum` | Nhiệt độ phục vụ: `HOT`, `COLD`, `ROOM_TEMP`. | 4 |
| `spiciness_level` | `Integer` | Mức độ cay (0-5), cho phép khách hàng lọc và chọn. | 4 |
| `is_archived` | `Boolean` | Cờ xác định món ăn đã bị ẩn đi (thay vì xóa cứng). | 2 |
| `created_at`, `updated_at` | `Timestamp` | Dấu thời gian. | 1 |

**Bảng 4: `item_variants`** (Bảng định nghĩa đơn vị bán được)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của biến thể. | 2 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn gốc. | 2 |
| `name` | `String` | Tên của biến thể (ví dụ: "Size M", "Ly nhỏ"). | 2 |
| `price` | `Decimal` | Giá bán của biến thể này. | 1 |
| `sku` | `String` | Mã SKU duy nhất cho biến thể này để quản lý tồn kho chính xác. | 5 |
| `status` | `Enum` | Trạng thái của biến thể: `AVAILABLE`, `LOW_STOCK`, `OUT_OF_STOCK`. | 2 |
| `is_default` | `Boolean` | Cờ xác định đây có phải là biến thể được chọn mặc định hay không. | 2 |
| `display_order` | `Integer` | Thứ tự hiển thị các biến thể. | 2 |

**Bảng 5 & 6: `item_customization_groups` & `item_customization_options`**
| Tên thuộc tính (Options) | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id`, `group_id`, `name`, `price_adjustment`, `is_default`, `display_order` | ... | Như phiên bản trước | 2 |
| `ingredient_id` | `UUID` | (Nullable) Khóa ngoại, liên kết đến bảng `ingredients`. Giúp tự động tính toán dinh dưỡng và dị ứng. | 5 |
| `quantity_change` | `Float` | Số lượng nguyên liệu thay đổi (ví dụ: thêm 1 shot espresso). | 5 |

---

#### **Phần B: Làm giàu Nội dung & Trải nghiệm**

**Bảng 7: `item_storytelling_content`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 6 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn. | 6 |
| `content_type` | `Enum` | Loại nội dung: `TEXT_BLOCK`, `IMAGE`, `QUOTE`, `VIDEO_EMBED`, `CHEF_NOTE`. | 6 |
| `content_data` | `JSONB` | Dữ liệu của khối nội dung (ví dụ: `{"text": "..."}` hoặc `{"url": "...", "caption": "..."}`). | 6 |
| `display_order` | `Integer` | Thứ tự hiển thị các khối nội dung. | 6 |

**Bảng 8: `item_media_gallery`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id`, `menu_item_id`, `url`, `alt_text`, `display_order` | ... | Như phiên bản trước | 1 |
| `media_type` | `Enum` | Loại media: `IMAGE`, `VIDEO`, `GIF`, `AR_MODEL`, `3D_MODEL`. | 1 |
| `source` | `Enum` | Nguồn gốc media: `PROFESSIONAL`, `USER_GENERATED`. | 1 |
| `uploader_user_id` | `UUID` | (Nullable) Khóa ngoại, liên kết đến người dùng nếu là `USER_GENERATED`. | 8 |
| `is_approved` | `Boolean` | Cờ xác định media do người dùng tải lên đã được duyệt hay chưa. | 8 |

**Bảng 9: `item_tags`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 3 |
| `name` | `String` | Tên của nhãn (ví dụ: "Bestseller", "Món chay", "Cay"). | 3 |
| `tag_type` | `Enum` | Loại nhãn: `BADGE` (Bestseller), `LABEL` (Cay), `DIETARY` (Chay). | 3 |
| `icon`, `color` | `String` | Tùy chọn hiển thị. | 3 |

**Bảng 10: `item_tag_associations`** (Bảng trung gian)

**Bảng 11 & 12: `menu_collections` & `menu_collection_items`** (Như phiên bản trước)

---

#### **Phần C: Thành phần, Dinh dưỡng & An toàn**

**Bảng 13: `ingredients`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 5 |
| `name` | `String` | Tên nguyên liệu (ví dụ: "Hành lá", "Bột mì số 13"). | 5 |
| `description` | `Text` | Mô tả chi tiết về nguyên liệu. | 5 |
| `is_allergen` | `Boolean` | Cờ xác định nguyên liệu này có phải là một chất gây dị ứng phổ biến hay không. | 4 |
| `nutritional_info_per_100g` | `JSONB` | Dữ liệu dinh dưỡng chuẩn cho 100g nguyên liệu. | 4 |
| `country_of_origin` | `String` | Quốc gia xuất xứ. | 11 |
| `supplier_id` | `UUID` | Khóa ngoại, liên kết đến nhà cung cấp chính. | 8 |

**Bảng 14: `allergens`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 4 |
| `name` | `String` | Tên chất gây dị ứng (ví dụ: "Đậu phộng", "Gluten", "Sữa"). | 4 |
| `icon_url` | `String` | URL của icon đại diện cho chất gây dị ứng. | 4 |
| `severity_warning` | `Text` | Cảnh báo về mức độ nghiêm trọng (ví dụ: "Có thể gây sốc phản vệ"). | 4 |

**Bảng 15: `recipes`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 5 |
| `target_id`, `target_type` | `UUID`, `Enum` | ID và loại đối tượng sở hữu công thức (`ITEM` hoặc `VARIANT`). | 5 |
| `instructions` | `Text` | Hướng dẫn các bước thực hiện (dành cho nội bộ). | 5 |
| `version` | `Integer` | Phiên bản của công thức. | 5 |

**Bảng 16: `recipe_ingredients`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `recipe_id`, `ingredient_id`, `quantity`, `unit` | ... | Như phiên bản trước | 5 |

**Bảng 17: `item_explicit_allergens`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `menu_item_id`, `allergen_id` | `UUID` | Khóa ngoại. | 4 |
| `cross_contamination_risk` | `Boolean` | Cờ cảnh báo nguy cơ lây nhiễm chéo. | 4 |
| `notes` | `Text` | Ghi chú cụ thể (ví dụ: "Có thể yêu cầu phiên bản không chứa gluten"). | 4 |

---

#### **Phần D: Quy tắc Kinh doanh & Vận hành**

**Bảng 18: `special_pricing_rules`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id`, `restaurant_id`, `name`, `is_active` | ... | Như phiên bản trước | 8 |
| `rule_type` | `Enum` | Loại quy tắc: `HAPPY_HOUR`, `DAILY_SPECIAL`, `COMBO_DEAL`. | 8 |
| `discount_type` | `Enum` | Loại giảm giá: `PERCENTAGE`, `FIXED_AMOUNT`, `NEW_PRICE`. | 8 |
| `value` | `Decimal` | Giá trị của việc giảm giá. | 8 |
| `schedule` | `JSONB` | Lịch áp dụng chi tiết. | 8 |

**Bảng 19: `pricing_rule_targets`** (Bảng trung gian)

**Bảng 20: `availability_rules`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 7 |
| `target_id`, `target_type` | `UUID`, `Enum` | Đối tượng được áp dụng (`ITEM`, `CATEGORY`, `MENU`). | 7 |
| `rule_condition` | `JSONB` | Điều kiện phức tạp (ví dụ: `{"weather": "rainy"}` hoặc `{"event": "football_match"}`). | 10 |
| `is_available` | `Boolean` | Trạng thái sẵn có khi điều kiện được đáp ứng. | 7 |

**Bảng 21: `dynamic_pricing_signals`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 9 |
| `menu_item_id` | `UUID` | Khóa ngoại. | 9 |
| `signal_type` | `Enum` | Loại tín hiệu: `DEMAND_LEVEL`, `COMPETITOR_PRICE`, `TIME_OF_DAY`. | 9 |
| `value` | `String` | Giá trị của tín hiệu (ví dụ: "HIGH", "150000", "20:00"). | 9 |
| `timestamp` | `Timestamp` | Thời điểm ghi nhận tín hiệu. | 9 |

---

#### **Phần E: Hiệu suất & Phân tích**

**Bảng 22: `item_performance_metrics`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `menu_item_id` | `UUID` | Khóa chính & khóa ngoại. | 4 |
| `period` | `Date` | Ngày/Tuần/Tháng mà dữ liệu được tổng hợp. | 4 |
| `sales_volume` | `Integer` | Tổng số lượng bán ra. | 4 |
| `total_revenue` | `Decimal` | Tổng doanh thu. | 4 |
| `profit_margin` | `Decimal` | Tỷ suất lợi nhuận (ước tính). | 7 |
| `view_count` | `Integer` | Số lượt xem trên menu. | 7 |
| `add_to_cart_count` | `Integer` | Số lượt thêm vào giỏ hàng. | 7 |
| `conversion_rate` | `Float` | Tỷ lệ chuyển đổi (đặt hàng / xem). | 7 |

**Bảng 23: `item_reviews`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 6 |
| `menu_item_id` | `UUID` | Khóa ngoại. | 6 |
| `user_id` | `UUID` | Khóa ngoại. | 6 |
| `rating` | `Integer` | Điểm đánh giá (1-5). | 6 |
| `comment` | `Text` | Bình luận chi tiết. | 6 |
| `is_featured` | `Boolean` | Cờ xác định bình luận này có được hiển thị nổi bật hay không. | 6 |
| `created_at` | `Timestamp` | Thời gian tạo. | 6 |

**Bảng 24: `item_search_analytics`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `search_term` | `String` | Từ khóa mà người dùng đã tìm kiếm. | 7 |
| `menu_item_id` | `UUID` | (Nullable) Món ăn được click vào sau khi tìm kiếm. | 7 |
| `search_count` | `Integer` | Số lần từ khóa này được tìm. | 7 |
| `click_count` | `Integer` | Số lần món ăn này được click từ kết quả tìm kiếm. | 7 |
| `timestamp` | `Timestamp` | Thời gian tìm kiếm. | 7 |
