Jenkinson's Aquarium & Boardwalk – Website

1. Giới thiệu
Website giới thiệu và đặt vé/trải nghiệm cho hệ thống Jenkinson's (Aquarium, Boardwalk, Sweet Shop) tại Point Pleasant Beach, New Jersey (USA).
Người dùng có thể xem thông tin, trải nghiệm/sự kiện, đăng ký tài khoản, mua hàng qua giỏ hàng và đăng ký newsletter. Admin có khu vực riêng để quản lý sản phẩm, đơn hàng, sự kiện, người dùng và newsletter.

2. Công nghệ sử dụng
- Backend: PHP 7.4+
- Frontend: HTML5, CSS3, JavaScript (Vanilla)
- CSS Framework: Bootstrap 5
- Icons: Font Awesome, Bootstrap Icons
- Fonts: Poppins, Source Sans 3
- CSDL: MySQL / MariaDB (phpMyAdmin)
- Server local: XAMPP (Apache + PHP + MySQL)

3. Cấu trúc thư mục chính (rút gọn)
- admin/: khu vực quản trị (products, categories, orders, users, events, event_registrations, subscriptions…)
- auth/: đăng nhập, đăng ký, hồ sơ cá nhân, logout
- product/: giỏ hàng, checkout, đơn hàng (cart.php, checkout.php, my_orders.php, order_detail.php, order_success.php)
- componets/: các trang nội dung (boardwalk, sweet-shop, ourmission, beach, arcades, experience-detail, event-detail, event-register, add_experience_to_cart…)
- includes/: header/footer chung, hàm auth, hàm tiện ích, dữ liệu experiences/events
- api/: subscribe.php xử lý đăng ký newsletter (AJAX)
- css/, js/, img/: giao diện, script, hình ảnh
- database/: config.php và full_database.sql (schema + data)
- index.php: trang chủ Aquarium

4. Chức năng chính
4.1 Người dùng
- Xem nội dung Aquarium, Boardwalk, Sweet Shop và các khu nội dung khác.
- Xem chi tiết trải nghiệm (experience-detail.php) và sự kiện (event-detail.php).
- Đăng ký sự kiện qua trang event-register.php, form gửi qua add_experience_to_cart.php để thêm vào giỏ.
- Thêm sản phẩm/trải nghiệm vào giỏ, chỉnh sửa giỏ tại product/cart.php.
- Thanh toán tại product/checkout.php (yêu cầu đăng nhập), lưu đơn hàng vào orders/order_items.
- Đăng ký tài khoản, đăng nhập, quản lý hồ sơ và xem lịch sử đơn hàng.
- Đăng ký newsletter qua form footer (AJAX đến api/subscribe.php), lưu vào bảng subscriptions.

4.2 Admin
- Dashboard tổng quan (admin/index.php).
- Quản lý sản phẩm và danh mục (products.php, categories.php).
- Quản lý đơn hàng (orders.php, order_detail.php).
- Quản lý người dùng (users.php).
- Quản lý sự kiện và đăng ký sự kiện (events.php, event_registrations.php).
- Quản lý danh sách email newsletter (subscriptions.php).

5. Cơ sở dữ liệu
- Database: project_data.
- Bảng chính: users, categories, products, orders, order_items, subscriptions, event_registrations.
- Import database: dùng phpMyAdmin import file database/full_database.sql, cấu hình kết nối trong database/config.php.

6. Cài đặt & chạy
1) Copy project vào: C:\xampp\htdocs\eProject_2_2
2) Khởi động Apache và MySQL trong XAMPP
3) Tạo database project_data và import database/full_database.sql
4) Kiểm tra database/config.php (DB_HOST, DB_USER, DB_PASS, DB_NAME)
5) Truy cập: http://localhost/eProject_2_2/

7. Hướng phát triển
- Chuyển dữ liệu trải nghiệm/sự kiện từ file PHP sang database để CRUD từ admin.
- Tích hợp cổng thanh toán thực (PayPal, Stripe, VNPay…).
- Bổ sung tìm kiếm, lọc nâng cao, báo cáo thống kê cho admin.

