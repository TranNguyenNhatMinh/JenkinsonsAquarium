# Jenkinson's – Website Giới Thiệu & Thương Mại

> **Dự án web full-stack** mô phỏng trang thông tin và bán hàng cho khu phức hợp Jenkinson's (Aquarium, Boardwalk, Sweet Shop). Dự án phù hợp để nhà tuyển dụng đánh giá năng lực **PHP, MySQL, HTML/CSS/JS** và cách tổ chức code.

---

## Tổng quan

Website gồm **3 khu vực chính** (Aquarium, Boardwalk, Sweet Shop) với trang chủ, các trang nội dung tĩnh/động, **hệ thống đăng nhập/đăng ký**, **giỏ hàng & thanh toán**, **đăng ký sự kiện**, và **khu vực quản trị (Admin)** quản lý sản phẩm, đơn hàng, người dùng và đăng ký newsletter/sự kiện.

- **Đối tượng:** Khách xem thông tin, đặt trải nghiệm, mua sản phẩm; Admin quản lý nội dung và đơn hàng.
- **Mục đích dự án:** Thể hiện kỹ năng xây dựng web từ giao diện đến backend, database và bảo mật cơ bản.

---

## Công nghệ sử dụng

| Thành phần | Công nghệ |
|------------|-----------|
| **Backend** | PHP (thuần, hướng thủ tục + hàm) |
| **Database** | MySQL (MariaDB), UTF-8 |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Framework CSS** | Bootstrap 5 |
| **Font & Icon** | Google Fonts (Poppins, Source Sans 3), Font Awesome, Bootstrap Icons |
| **Môi trường chạy** | XAMPP (Apache + PHP + MySQL) |

---

## Tính năng chính

### 1. Trang công khai (Public)

- **Trang chủ (Aquarium):** Hero, About, Upcoming Events, Featured Experiences, Attractions.
- **Đa site:** Chuyển giữa Aquarium / Boardwalk / Sweet Shop; header/footer và CSS load theo từng site.
- **Nội dung:** Our Mission, Event Detail, Experience Detail, đăng ký sự kiện (form + lưu DB).
- **Sweet Shop:** Trang sản phẩm theo danh mục, chi tiết sản phẩm, thêm vào giỏ.
- **Boardwalk:** Các trang con (Beach, Arcades, Fun Games, Mini Golf, Shopping, Adventure Lookout…).

### 2. Người dùng (Auth & Profile)

- Đăng ký, đăng nhập, đăng xuất (session, bảo mật mật khẩu bằng `password_hash`).
- Phân quyền: **customer** / **admin** (admin vào được `/admin/`).
- Profile: cập nhật họ tên, email, số điện thoại, địa chỉ.

### 3. Giỏ hàng & Đơn hàng

- Giỏ hàng dựa trên **session** (không cần đăng nhập để thêm vào giỏ).
- Trang giỏ hàng, cập nhật số lượng, xóa sản phẩm.
- Checkout: nhập thông tin giao hàng, lưu đơn vào DB (orders, order_items).
- Trang “My Orders”: xem lịch sử đơn (khi đã đăng nhập).

### 4. API / AJAX

- **Newsletter:** Form đăng ký nhận tin (footer); API nhận email, lưu vào bảng `subscriptions` (AJAX).

### 5. Khu vực Admin

- **Dashboard:** Thống kê nhanh (đơn hàng, user, v.v. tùy hiện thực).
- **Quản lý sản phẩm:** Danh sách, thêm/sửa/xóa (categories, products).
- **Quản lý đơn hàng:** Danh sách đơn, xem chi tiết đơn, cập nhật trạng thái.
- **Quản lý người dùng:** Danh sách user, phân quyền/trạng thái (nếu có).
- **Đăng ký sự kiện:** Xem danh sách đăng ký event.
- **Newsletter:** Xem danh sách email đăng ký tin.

---

## Cấu trúc thư mục

```
eProject_2_2/
├── index.php                 # Trang chủ Aquarium
├── includes/
│   ├── header.php            # Header chung (menu, logo, CSS theo site)
│   ├── footer.php            # Footer chung (newsletter, link)
│   ├── auth.php              # Session, đăng nhập/đăng ký, isLoggedIn(), isAdmin()
│   └── functions.php         # Hàm dùng chung: sanitize, formatCurrency, cart, DB...
├── componets/                # Trang nội dung (Boardwalk, Sweet Shop, event, experience...)
├── product/                  # Giỏ hàng, checkout, my_orders, order_detail
├── auth/                     # login, register, logout, profile
├── admin/                    # Trang quản trị (dashboard, products, orders, users...)
├── api/                      # subscribe.php (newsletter)
├── database/
│   ├── config.php            # Kết nối MySQL (getDBConnection)
│   └── full_database.sql     # Schema + dữ liệu mẫu
├── css/                      # Giao diện (variables, reset, header, từng trang...)
├── js/                       # Script (homepage, newsletter, product-detail...)
└── img/                      # Hình ảnh
```

---

## Cơ sở dữ liệu

- **Database:** `project_data` (UTF-8).
- **Bảng chính:** `users`, `categories`, `products`, `orders`, `order_items`, `subscriptions`, `event_registrations`.
- **Mẫu:** Có sẵn admin (username: `admin`, password: `password` thường dùng trong môi trường dev), categories, products mẫu.
- Import: Chạy file `database/full_database.sql` trong phpMyAdmin hoặc MySQL.

---

## Cách chạy dự án

1. **Cài đặt môi trường:** XAMPP (Apache + PHP 7.4+ + MySQL/MariaDB).
2. **Database:** Tạo database `project_data`, import `database/full_database.sql`.
3. **Cấu hình:** Sửa `database/config.php` nếu cần (host, user, password, DB name).
4. **Đặt mã nguồn:** Đặt thư mục dự án vào `htdocs` (ví dụ: `C:\xampp\htdocs\eProject_2_2`).
5. **Truy cập:** Mở trình duyệt: `http://localhost/eProject_2_2/` hoặc `http://localhost/eProject_2_2/index.php`.

---

## Điểm nổi bật cho đánh giá

- **Tổ chức code:** Tách header/footer, auth, functions; đường dẫn CSS/JS theo từng trang/site.
- **Bảo mật cơ bản:** Mật khẩu hash, kiểm tra đăng nhập/role trước khi vào admin, sanitize input.
- **Trải nghiệm người dùng:** Giao diện responsive (Bootstrap), nhiều section rõ ràng, form đăng ký sự kiện và newsletter.
- **Chức năng thương mại:** Giỏ hàng session, checkout, lưu đơn hàng, quản lý đơn ở admin.
- **Mở rộng:** Dễ thêm trang mới, thêm bảng hoặc cột trong DB, thêm quyền hoặc tính năng admin.

---

## Tài liệu kèm theo

- **HUONG_DAN_CHI_TIET.md:** Hướng dẫn chi tiết cho người chưa quen code (cấu trúc thư mục, luồng trang, một số file quan trọng).

---

*Dự án phát triển với mục đích học tập và làm đồ án môn học / portfolio. Nội dung và hình ảnh mang tính minh họa.*
