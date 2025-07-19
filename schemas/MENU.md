## **Kiến trúc Dữ liệu Sản phẩm: Domain MENU (Khám phá Thực đơn)**

### **Giới thiệu**

Phiên bản này của data schema được thiết kế với mục tiêu **tối đa hóa chiều sâu và khả năng mở rộng**. Chúng ta không chỉ định nghĩa dữ liệu cho các tính năng trước mắt, mà còn xây dựng nền móng vững chắc cho toàn bộ tầm nhìn 15 giai đoạn, bao gồm cả những ý tưởng "moonshot" như truy xuất nguồn gốc bằng blockchain, cá nhân hóa dựa trên DNA, và AI sáng tạo công thức.

Kiến trúc này được chia thành 6 phần logic để dễ hiểu:
-   **Phần A: Cấu trúc Sản phẩm Cốt lõi:** Định nghĩa "món ăn" là gì.
-   **Phần B: Làm giàu Nội dung & Trải nghiệm:** Kể "câu chuyện" của món ăn.
-   **Phần C: Thành phần, Dinh dưỡng & An toàn:** Trả lời câu hỏi "trong món ăn có gì?".
-   **Phần D: Nguồn gốc & Chuỗi cung ứng:** Trả lời câu hỏi "nguyên liệu đến từ đâu?".
-   **Phần E: Quy tắc Kinh doanh & Vận hành:** Định nghĩa "khi nào và với giá bao nhiêu?".
-   **Phần F: Hiệu suất & Phân tích:** Trả lời câu hỏi "món ăn này hoạt động ra sao?".

---

#### **Phần A: Cấu trúc Sản phẩm Cốt lõi**

**Bảng 1: `menus`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của thực đơn. | 1 |
| `restaurant_id` | `UUID` | Khóa ngoại, liên kết đến nhà hàng sở hữu thực đơn này. | 1 |
| `name` | `String` | Tên của thực đơn (ví dụ: "Thực đơn chính", "Menu Món Nước"). | 1 |
| `description` | `Text` | Mô tả ngắn về mục đích hoặc chủ đề của thực đơn. | 1 |
| `is_active` | `Boolean` | Cờ xác định thực đơn này có đang được áp dụng và hiển thị cho khách hàng hay không. | 1 |
| `availability_schedule` | `JSONB` | Lịch hoạt động của menu (ví dụ: `{"days": [1,2,3,4,5], "from": "07:00", "to": "11:00"}`). | 3 |
| `status` | `Enum` | Trạng thái của menu: `DRAFT`, `PUBLISHED`, `ARCHIVED`. | 5 |
| `version` | `Integer` | Số phiên bản của menu, giúp theo dõi lịch sử thay đổi. | 5 |
| `published_at` | `Timestamp` | Dấu thời gian khi phiên bản menu này được công bố. | 5 |
| `created_by_staff_id` | `UUID` | ID nhân viên đã tạo menu. | 5 |
| `target_audience` | `Enum` | Đối tượng mục tiêu: `PUBLIC`, `VIP_ONLY`, `STAFF_ONLY`. | 7 |
| `display_order` | `Integer` | Thứ tự hiển thị nếu nhà hàng có nhiều menu hoạt động cùng lúc. | 3 |
| `created_at` | `Timestamp` | Dấu thời gian khi thực đơn được tạo. | 1 |
| `updated_at` | `Timestamp` | Dấu thời gian khi thực đơn được cập nhật lần cuối. | 1 |

**Bảng 2: `menu_categories`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của danh mục. | 1 |
| `menu_id` | `UUID` | Khóa ngoại, liên kết đến thực đơn chứa danh mục này. | 1 |
| `parent_category_id` | `UUID` | Khóa ngoại tự tham chiếu, cho phép tạo danh mục con (ví dụ: Đồ uống -> Cà phê). | 3 |
| `name` | `String` | Tên của danh mục (ví dụ: "Món khai vị"). | 1 |
| `description` | `Text` | Mô tả tùy chọn cho danh mục. | 1 |
| `image_url` | `String` | URL hình ảnh đại diện cho cả danh mục. | 3 |
| `translations` | `JSONB` | Lưu trữ bản dịch cho tên và mô tả của danh mục. | 3 |
| `is_hidden` | `Boolean` | Cờ để ẩn danh mục tạm thời mà không cần xóa (ví dụ: món mùa đông). | 3 |
| `display_order` | `Integer` | Số thứ tự để sắp xếp các danh mục trên giao diện người dùng. | 1 |
| `created_at` | `Timestamp` | Dấu thời gian khi danh mục được tạo. | 1 |
| `updated_at` | `Timestamp` | Dấu thời gian khi danh mục được cập nhật lần cuối. | 1 |

**Bảng 3: `menu_items`** (Bảng định danh món ăn)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của món ăn. | 1 |
| `category_id` | `UUID` | Khóa ngoại, liên kết đến danh mục chứa món ăn này. | 1 |
| `item_type` | `Enum` | Loại sản phẩm: `FOOD`, `BEVERAGE`, `MERCHANDISE`. | 5 |
| `name` | `String` | Tên món ăn (ví dụ: "Phở Bò Tái"). | 1 |
| `short_description` | `String(255)` | Mô tả ngắn gọn, hấp dẫn, hiển thị trên danh sách menu. | 1 |
| `long_description` | `Text` | Mô tả chi tiết về thành phần, hương vị, hiển thị trên trang chi tiết món ăn. | 1 |
| `chef_notes` | `Text` | Ghi chú hoặc lời khuyên từ đầu bếp về cách thưởng thức món ăn. | 6 |
| `translations` | `JSONB` | Lưu trữ các bản dịch cho `name` và các `description`. | 3 |
| `serving_temperature` | `Enum` | Nhiệt độ phục vụ: `HOT`, `COLD`, `ROOM_TEMP`. | 4 |
| `spiciness_level` | `Integer` | Mức độ cay (0-5), cho phép khách hàng lọc và chọn. | 4 |
| `preparation_time_range_minutes` | `Int4Range` | Khoảng thời gian chuẩn bị ước tính (ví dụ: `[10, 15]`). | 5 |
| `is_signature_dish` | `Boolean` | Cờ xác định đây có phải là món ăn đặc trưng của nhà hàng hay không. | 3 |
| `is_available_for_dine_in` | `Boolean` | Có sẵn cho ăn tại chỗ. | 4 |
| `is_available_for_pickup` | `Boolean` | Có sẵn cho mang về. | 4 |
| `is_available_for_delivery` | `Boolean` | Có sẵn cho giao hàng. | 4 |
| `is_archived` | `Boolean` | Cờ xác định món ăn đã bị ẩn đi (thay vì xóa cứng). | 2 |
| `created_at` | `Timestamp` | Dấu thời gian khi món ăn được tạo. | 1 |
| `updated_at` | `Timestamp` | Dấu thời gian khi món ăn được cập nhật lần cuối. | 1 |

**Bảng 4: `item_variants`** (Bảng định nghĩa đơn vị bán được)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của biến thể. | 2 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn gốc. | 2 |
| `name` | `String` | Tên của biến thể (ví dụ: "Size M", "Ly nhỏ"). | 2 |
| `price` | `Decimal` | Giá bán của biến thể này. | 1 |
| `cost_price` | `Decimal` | Giá vốn hàng bán, để tính toán lợi nhuận. | 7 |
| `sku` | `String` | Mã SKU duy nhất cho biến thể này để quản lý tồn kho chính xác. | 5 |
| `barcode` | `String` | Mã vạch (EAN/UPC) nếu đây là sản phẩm bán lẻ. | 8 |
| `status` | `Enum` | Trạng thái của biến thể: `AVAILABLE`, `LOW_STOCK`, `OUT_OF_STOCK`. | 2 |
| `low_stock_threshold` | `Integer` | Ngưỡng cảnh báo tồn kho thấp. | 5 |
| `gross_weight_grams` | `Integer` | Trọng lượng cả bì. | 5 |
| `net_weight_grams` | `Integer` | Trọng lượng tịnh. | 5 |
| `is_default` | `Boolean` | Cờ xác định đây có phải là biến thể được chọn mặc định hay không. | 2 |
| `display_order` | `Integer` | Thứ tự hiển thị các biến thể. | 2 |

**Bảng 5: `item_customization_groups`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của nhóm tùy chọn. | 2 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn có nhóm tùy chọn này. | 2 |
| `name` | `String` | Tên của nhóm tùy chọn (ví dụ: "Mức đường", "Topping"). | 2 |
| `selection_type` | `Enum` | Kiểu lựa chọn: `SINGLE` (chỉ được chọn 1) hoặc `MULTIPLE` (được chọn nhiều). | 2 |
| `min_selections` | `Integer` | Số lượng tùy chọn tối thiểu phải chọn (ví dụ: 0 hoặc 1). | 2 |
| `max_selections` | `Integer` | Số lượng tùy chọn tối đa được phép chọn. | 2 |
| `display_order` | `Integer` | Thứ tự hiển thị các nhóm tùy chọn. | 2 |

**Bảng 6: `item_customization_options`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của tùy chọn. | 2 |
| `group_id` | `UUID` | Khóa ngoại, liên kết đến nhóm tùy chọn chứa nó. | 2 |
| `name` | `String` | Tên của tùy chọn (ví dụ: "70% đường", "Trân châu đen"). | 2 |
| `price_adjustment` | `Decimal` | Mức giá thay đổi (cộng hoặc trừ) khi chọn tùy chọn này. | 2 |
| `ingredient_id` | `UUID` | (Nullable) Khóa ngoại, liên kết đến bảng `ingredients`. Giúp tự động tính toán dinh dưỡng và dị ứng. | 5 |
| `quantity_change` | `Float` | Số lượng nguyên liệu thay đổi (ví dụ: thêm 1 shot espresso). | 5 |
| `status` | `Enum` | Trạng thái của tùy chọn: `AVAILABLE`, `OUT_OF_STOCK`. | 2 |
| `is_default` | `Boolean` | Cờ xác định đây có phải là tùy chọn được chọn mặc định hay không. | 2 |
| `display_order` | `Integer` | Thứ tự hiển thị các tùy chọn trong nhóm. | 2 |

---

#### **Phần B: Làm giàu Nội dung & Trải nghiệm**

**Bảng 7: `item_storytelling_content`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 6 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn. | 6 |
| `content_type` | `Enum` | Loại nội dung: `TEXT_BLOCK`, `IMAGE`, `QUOTE`, `VIDEO_EMBED`, `CHEF_NOTE`, `HISTORICAL_FACT`, `SUPPLIER_SPOTLIGHT`. | 6 |
| `content_data` | `JSONB` | Dữ liệu của khối nội dung (ví dụ: `{"text": "..."}` hoặc `{"url": "...", "caption": "..."}`). | 6 |
| `display_order` | `Integer` | Thứ tự hiển thị các khối nội dung. | 6 |

**Bảng 8: `item_media_gallery`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của media. | 1 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn. | 1 |
| `media_type` | `Enum` | Loại media: `IMAGE`, `VIDEO`, `GIF`, `AR_MODEL`, `3D_MODEL`. | 1 |
| `url` | `String` | URL của file media. | 1 |
| `alt_text` | `String` | Văn bản thay thế cho hình ảnh, tốt cho SEO và tiếp cận. | 1 |
| `source` | `Enum` | Nguồn gốc media: `PROFESSIONAL`, `USER_GENERATED`. | 1 |
| `uploader_user_id` | `UUID` | (Nullable) Khóa ngoại, liên kết đến người dùng nếu là `USER_GENERATED`. | 8 |
| `review_status` | `Enum` | Trạng thái duyệt media: `PENDING`, `APPROVED`, `REJECTED`. | 8 |
| `focal_point` | `Point` | Tọa độ (x,y) của điểm lấy nét chính trong ảnh để crop thông minh. | 8 |
| `metadata` | `JSONB` | Dữ liệu meta của file (kích thước, độ phân giải, EXIF...). | 8 |
| `display_order` | `Integer` | Thứ tự hiển thị media trong gallery. | 1 |

**Bảng 9: `item_tags`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 3 |
| `name` | `String` | Tên của nhãn (ví dụ: "Bestseller", "Món chay", "Cay"). | 3 |
| `tag_type` | `Enum` | Loại nhãn: `BADGE` (Bestseller), `LABEL` (Cay), `DIETARY` (Chay), `PROMOTIONAL` (Giảm giá). | 3 |
| `icon` | `String` | Tên icon hoặc URL của icon hiển thị trên UI. | 3 |
| `color` | `String` | Mã màu (HEX) để hiển thị nhãn trên UI. | 3 |

**Bảng 10: `item_tag_associations`** (Bảng trung gian)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn. | 3 |
| `tag_id` | `UUID` | Khóa ngoại, liên kết đến nhãn. | 3 |

**Bảng 11: `item_pairing_suggestions`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `source_item_id` | `UUID` | Khóa ngoại, món ăn gốc. | 7 |
| `paired_item_id` | `UUID` | Khóa ngoại, món ăn/đồ uống được gợi ý kết hợp. | 7 |
| `description` | `Text` | Giải thích tại sao chúng lại hợp nhau. | 7 |
| `suggestion_type` | `Enum` | Loại gợi ý: `DRINK_PAIRING`, `FOOD_PAIRING`, `UPSELL`, `CROSS_SELL`. | 7 |
| `created_by` | `Enum` | Nguồn tạo gợi ý: `ADMIN`, `AI`, `COMMUNITY`. | 7 |
| `upvote_count` | `Integer` | Số lượt bình chọn từ cộng đồng cho gợi ý. | 7 |
| `downvote_count` | `Integer` | Số lượt không đồng tình từ cộng đồng. | 7 |

**Bảng 12: `menu_collections`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của bộ sưu tập. | 6 |
| `restaurant_id` | `UUID` | Khóa ngoại, liên kết đến nhà hàng. | 6 |
| `name` | `String` | Tên bộ sưu tập (ví dụ: "Món ngon ngày mưa", "Top 5 món phải thử"). | 6 |
| `description` | `Text` | Mô tả câu chuyện đằng sau bộ sưu tập. | 6 |
| `image_url` | `String` | URL hình ảnh bìa của bộ sưu tập. | 6 |
| `is_featured` | `Boolean` | Cờ xác định bộ sưu tập này có được hiển thị nổi bật trên trang chủ hay không. | 6 |

**Bảng 13: `menu_collection_items`** (Bảng trung gian)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `collection_id` | `UUID` | Khóa ngoại, liên kết đến bộ sưu tập. | 6 |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn. | 6 |
| `display_order` | `Integer` | Thứ tự hiển thị món ăn trong bộ sưu tập. | 6 |

---

#### **Phần C: Thành phần, Dinh dưỡng & An toàn**

**Bảng 14: `ingredients`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 5 |
| `name` | `String` | Tên nguyên liệu (ví dụ: "Hành lá", "Bột mì số 13"). | 5 |
| `description` | `Text` | Mô tả chi tiết về nguyên liệu. | 5 |
| `ingredient_category` | `Enum` | Phân loại nguyên liệu: `VEGETABLE`, `MEAT`, `DAIRY`, `SPICE`, `GRAIN`. | 5 |
| `is_allergen` | `Boolean` | Cờ xác định nguyên liệu này có phải là một chất gây dị ứng phổ biến hay không. | 4 |
| `is_organic` | `Boolean` | Cờ xác định nguyên liệu có phải hữu cơ không. | 4 |
| `is_gmo_free` | `Boolean` | Cờ xác định nguyên liệu có biến đổi gen không. | 4 |
| `is_halal` | `Boolean` | Cờ xác định nguyên liệu có đạt chuẩn Halal không. | 4 |
| `is_kosher` | `Boolean` | Cờ xác định nguyên liệu có đạt chuẩn Kosher không. | 4 |
| `nutritional_info_per_100g` | `JSONB` | Dữ liệu dinh dưỡng chuẩn cho 100g nguyên liệu. | 4 |
| `storage_instructions` | `Text` | Hướng dẫn bảo quản. | 5 |
| `country_of_origin` | `String` | Quốc gia xuất xứ. | 11 |
| `supplier_id` | `UUID` | Khóa ngoại, liên kết đến nhà cung cấp chính. | 8 |

**Bảng 15: `allergens`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 4 |
| `name` | `String` | Tên chất gây dị ứng (ví dụ: "Đậu phộng", "Gluten", "Sữa"). | 4 |
| `icon_url` | `String` | URL của icon đại diện cho chất gây dị ứng. | 4 |
| `severity_warning` | `Text` | Cảnh báo về mức độ nghiêm trọng (ví dụ: "Có thể gây sốc phản vệ"). | 4 |
| `is_major_allergen` | `Boolean` | Cờ xác định đây có phải là 1 trong 8 (hoặc 14) chất gây dị ứng chính theo quy định hay không. | 4 |
| `common_reactions` | `Text` | Mô tả các phản ứng phổ biến khi bị dị ứng. | 4 |

**Bảng 16: `recipes`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 5 |
| `target_id` | `UUID` | ID của đối tượng sở hữu công thức (có thể là `menu_item_id` hoặc `item_variant_id`). | 5 |
| `target_type` | `Enum` | Loại đối tượng: `ITEM` hoặc `VARIANT`. | 5 |
| `instructions` | `Text` | Hướng dẫn các bước thực hiện (dành cho nội bộ). | 5 |
| `difficulty_level` | `Integer` | Mức độ khó của công thức (1-5). | 5 |
| `yield_quantity` | `Decimal` | Số lượng thành phẩm. | 5 |
| `yield_unit` | `String` | Đơn vị thành phẩm (ví dụ: "phần", "cái"). | 5 |
| `notes_for_chef` | `Text` | Ghi chú đặc biệt cho đầu bếp khi thực hiện. | 5 |
| `version` | `Integer` | Phiên bản của công thức. | 5 |

**Bảng 17: `recipe_ingredients`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `recipe_id` | `UUID` | Khóa ngoại, liên kết đến công thức. | 5 |
| `ingredient_id` | `UUID` | Khóa ngoại, liên kết đến nguyên liệu. | 5 |
| `quantity` | `Decimal` | Số lượng nguyên liệu cần dùng. | 5 |
| `unit` | `String` | Đơn vị tính (ví dụ: "g", "ml", "cái"). | 5 |
| `preparation_note` | `String` | Ghi chú về cách sơ chế (ví dụ: "thái hạt lựu", "băm nhỏ"). | 5 |
| `is_optional` | `Boolean` | Cờ xác định nguyên liệu này có thể bỏ qua hay không. | 5 |

**Bảng 18: `item_explicit_allergens`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `menu_item_id` | `UUID` | Khóa ngoại, liên kết đến món ăn. | 4 |
| `allergen_id` | `UUID` | Khóa ngoại, liên kết đến chất gây dị ứng. | 4 |
| `cross_contamination_risk` | `Boolean` | Cờ cảnh báo nguy cơ lây nhiễm chéo. | 4 |
| `risk_level` | `Enum` | Mức độ rủi ro: `LOW`, `MEDIUM`, `HIGH`. | 4 |
| `notes` | `Text` | Ghi chú cụ thể (ví dụ: "Có thể yêu cầu phiên bản không chứa gluten"). | 4 |

---

#### **Phần D: Nguồn gốc & Chuỗi cung ứng**

**Bảng 19: `suppliers`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 8 |
| `name` | `String` | Tên nhà cung cấp. | 8 |
| `contact_info` | `JSONB` | Thông tin liên hệ (địa chỉ, email, SĐT). | 8 |
| `supplier_type` | `Enum` | Loại nhà cung cấp: `FARM`, `DISTRIBUTOR`, `LOCAL_ARTISAN`. | 8 |
| `sustainability_score` | `Float` | Điểm số về tính bền vững. | 11 |
| `onboarding_date` | `Date` | Ngày bắt đầu hợp tác. | 8 |
| `certifications` | `JSONB` | Lưu trữ chi tiết các chứng nhận (`{"name": "VietGAP", "expiry": "2025-12-31"}`). | 8 |
| `rating` | `Float` | Điểm đánh giá nội bộ cho nhà cung cấp. | 8 |

**Bảng 20: `ingredient_sourcing`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 11 |
| `ingredient_id` | `UUID` | Khóa ngoại, liên kết đến nguyên liệu. | 11 |
| `supplier_id` | `UUID` | Khóa ngoại, liên kết đến nhà cung cấp. | 11 |
| `purchase_order_id` | `UUID` | Khóa ngoại, liên kết đến đơn đặt hàng nhà cung cấp. | 9 |
| `lot_number` | `String` | Mã lô hàng để truy xuất nguồn gốc. | 11 |
| `harvest_date` | `Date` | Ngày thu hoạch/sản xuất. | 11 |
| `expiration_date` | `Date` | Hạn sử dụng. | 9 |
| `quality_check_status` | `Enum` | Trạng thái kiểm tra chất lượng: `PENDING`, `PASSED`, `FAILED`. | 9 |
| `origin_location` | `Point` | Tọa độ địa lý của nơi sản xuất (dùng kiểu dữ liệu GIS). | 11 |
| `blockchain_transaction_id` | `String` | (Nullable) ID giao dịch trên blockchain để xác thực. | 11 |

---

#### **Phần E: Quy tắc Kinh doanh & Vận hành**

**Bảng 21: `special_pricing_rules`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính duy nhất của quy tắc. | 8 |
| `restaurant_id` | `UUID` | Khóa ngoại, liên kết đến nhà hàng áp dụng quy tắc. | 8 |
| `name` | `String` | Tên của chương trình giá đặc biệt (ví dụ: "Happy Hour 5-7 PM"). | 8 |
| `rule_type` | `Enum` | Loại quy tắc: `HAPPY_HOUR`, `DAILY_SPECIAL`, `COMBO_DEAL`. | 8 |
| `discount_type` | `Enum` | Loại giảm giá: `PERCENTAGE`, `FIXED_AMOUNT`, `NEW_PRICE`. | 8 |
| `value` | `Decimal` | Giá trị của việc giảm giá. | 8 |
| `schedule` | `JSONB` | Lịch áp dụng chi tiết (ngày trong tuần, giờ bắt đầu, giờ kết thúc). | 8 |
| `priority` | `Integer` | Độ ưu tiên nếu nhiều quy tắc trùng lặp. | 8 |
| `usage_limit_per_customer` | `Integer` | Giới hạn sử dụng cho mỗi khách hàng. | 8 |
| `total_usage_limit` | `Integer` | Tổng giới hạn sử dụng của chương trình. | 8 |
| `required_membership_tier` | `String` | Yêu cầu hạng thành viên để áp dụng. | 8 |
| `is_active` | `Boolean` | Cờ xác định quy tắc có đang hoạt động hay không. | 8 |

**Bảng 22: `pricing_rule_targets`** (Bảng trung gian)
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `rule_id` | `UUID` | Khóa ngoại, liên kết đến quy tắc giá. | 8 |
| `target_id` | `UUID` | ID của đối tượng được áp dụng (có thể là `menu_item_id`, `category_id`). | 8 |
| `target_type` | `Enum` | Loại đối tượng: `ITEM` hoặc `CATEGORY`. | 8 |

**Bảng 23: `item_channel_availability`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `item_variant_id` | `UUID` | Khóa ngoại, liên kết đến biến thể cụ thể. | 4 |
| `channel` | `Enum` | Kênh bán hàng: `DINE_IN`, `PICKUP`, `DELIVERY_GRAB`, `DELIVERY_SHOPEEFOOD`. | 4 |
| `is_available` | `Boolean` | Cờ xác định có bán trên kênh này hay không. | 4 |
| `channel_specific_price` | `Decimal` | (Nullable) Giá bán riêng cho kênh này nếu có. | 4 |

**Bảng 24: `dynamic_pricing_signals`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 9 |
| `menu_item_id` | `UUID` | Khóa ngoại. | 9 |
| `signal_type` | `Enum` | Loại tín hiệu: `DEMAND_LEVEL`, `COMPETITOR_PRICE`, `TIME_OF_DAY`. | 9 |
| `value` | `String` | Giá trị của tín hiệu (ví dụ: "HIGH", "150000", "20:00"). | 9 |
| `timestamp` | `Timestamp` | Thời điểm ghi nhận tín hiệu. | 9 |

---

#### **Phần F: Hiệu suất & Phân tích**

**Bảng 25: `item_performance_metrics`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `item_variant_id` | `UUID` | Khóa chính & khóa ngoại, phân tích đến cấp độ biến thể. | 4 |
| `period` | `Date` | Ngày/Tuần/Tháng mà dữ liệu được tổng hợp. | 4 |
| `sales_volume` | `Integer` | Tổng số lượng bán ra. | 4 |
| `total_revenue` | `Decimal` | Tổng doanh thu. | 4 |
| `profit_margin` | `Decimal` | Tỷ suất lợi nhuận (ước tính). | 7 |
| `view_count` | `Integer` | Số lượt xem trên menu. | 7 |
| `add_to_cart_count` | `Integer` | Số lượt thêm vào giỏ hàng. | 7 |
| `conversion_rate` | `Float` | Tỷ lệ chuyển đổi (đặt hàng / xem). | 7 |
| `customer_segment_performance` | `JSONB` | Phân tích hiệu suất theo phân khúc khách hàng (`{"VIP": 100, "NEW": 50}`). | 7 |
| `time_of_day_performance` | `JSONB` | Phân tích hiệu suất theo khung giờ. | 7 |

**Bảng 26: `item_reviews`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `id` | `UUID` | Khóa chính. | 6 |
| `menu_item_id` | `UUID` | Khóa ngoại. | 6 |
| `user_id` | `UUID` | Khóa ngoại. | 6 |
| `order_item_id` | `UUID` | Khóa ngoại, liên kết đến món hàng cụ thể trong đơn hàng để xác thực. | 6 |
| `rating` | `Integer` | Điểm đánh giá (1-5). | 6 |
| `comment` | `Text` | Bình luận chi tiết. | 6 |
| `sentiment_score` | `Float` | Điểm cảm xúc (-1 đến 1) do AI phân tích. | 9 |
| `is_verified_purchase` | `Boolean` | Cờ xác nhận người dùng đã thực sự mua món này. | 6 |
| `is_featured` | `Boolean` | Cờ xác định bình luận này có được hiển thị nổi bật hay không. | 6 |
| `staff_reply_id` | `UUID` | Khóa ngoại, liên kết đến phản hồi của nhân viên. | 6 |
| `helpful_count` | `Integer` | Số người thấy đánh giá này hữu ích. | 6 |
| `created_at` | `Timestamp` | Thời gian tạo. | 6 |

**Bảng 27: `item_search_analytics`**
| Tên thuộc tính | Kiểu dữ liệu | Diễn giải | Giai đoạn |
| :--- | :--- | :--- | :--- |
| `search_term` | `String` | Từ khóa mà người dùng đã tìm kiếm. | 7 |
| `session_id` | `UUID` | ID của phiên làm việc để theo dõi hành trình tìm kiếm. | 7 |
| `menu_item_id` | `UUID` | (Nullable) Món ăn được click vào sau khi tìm kiếm. | 7 |
| `result_position` | `Integer` | Vị trí của món ăn được click trong kết quả tìm kiếm. | 7 |
| `found_results_count` | `Integer` | Số lượng kết quả tìm thấy cho từ khóa. | 7 |
| `search_count` | `Integer` | Số lần từ khóa này được tìm. | 7 |
| `click_count` | `Integer` | Số lần món ăn này được click từ kết quả tìm kiếm. | 7 |
| `timestamp` | `Timestamp` | Thời gian tìm kiếm. | 7 |
