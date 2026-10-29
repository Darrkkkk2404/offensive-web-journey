# 🧪 Demo Assessment Report: Larpshop E-Commerce Web Application

> **Dự án mẫu:** Kiểm thử đánh giá bảo mật ứng dụng bán hàng Demo (Larpshop / Laravel Architecture).  
> **Loại hình kiểm thử:** Grey-Box Penetration Testing  
> **Chuẩn đánh giá:** OWASP WSTG v4.2 & CVSS v3.1  
> **Người thực hiện:** Triệu Minh Trí

---

## 1. Tóm Tắt Dành Cho Nhà Quản Lý (Executive Summary)

Trong đợt đánh giá an toàn thông tin ứng dụng web **LarpShop**, mục tiêu là xác định các lỗ hổng có thể bị kẻ tấn công khai thác để chiếm quyền kiểm soát tài khoản, truy cập dữ liệu đơn hàng nhạy cảm hoặc can thiệp vào tiến trình thanh toán.

### Biểu đồ phân bổ mức độ rủi ro (Risk Summary)
- 🔴 **Critical:** 1 (SQL Injection dẫn đến rò rỉ toàn bộ cơ sở dữ liệu)
- 🟠 **High:** 1 (IDOR tại API cập nhật địa chỉ giao hàng)
- 🟡 **Medium:** 2 (Stored XSS tại phần bình luận sản phẩm, Thiếu Rate Limiting tại Login)
- 🟢 **Low / Informational:** 1 (Lộ thông tin phiên bản PHP/Laravel qua response header)

---

## 2. Phạm Vi Đánh Giá (Assessment Scope)

| Hạng mục | Chi tiết |
| :--- | :--- |
| **Target URL** | `http://LarpShop.local` / `http://staging.LarpShop.demo` |
| **Tech Stack** | PHP 8.2, Laravel 10, MySQL 8.0, Blade Template |
| **Tài khoản kiểm thử** | `customer1@demo.local` (User), `customer2@demo.local` (User) |
| **Ngoài phạm vi** | DoS/DDoS, Hạ tầng máy chủ vật lý, Nhà cung cấp cổng thanh toán |

---

## 3. Danh Sách Lỗ Hổng Tiêu Biểu (Detailed Findings)

### FINDING-01: In-Band SQL Injection tại tính năng Lọc Sản Phẩm (Critical)
- **Vulnerability Type:** SQL Injection (CWE-89)
- **CVSS v3.1 Score:** `9.8` (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)
- **Endpoint bị ảnh hưởng:** `GET /products?category=1`
- **Mô tả:** Ứng dụng nối chuỗi trực tiếp tham số `category` vào câu lệnh SQL raw query của Eloquent DB thay vì sử dụng Prepared Statements (`DB::raw("SELECT * FROM products WHERE category_id = " . $category)`).
- **Proof-of-Concept (PoC):**
  ```http
  GET /products?category=1%20UNION%20SELECT%20NULL,username,password,email,NULL%20FROM%20users-- HTTP/1.1
  Host: LarpShop.local
  ```
- **Tác động:** Cho phép kẻ tấn công không cần xác thực đọc toàn bộ bảng `users` (chứa password hashes, email, số điện thoại khách hàng).
- **Biện pháp khắc phục (Remediation):**
  Sử dụng cơ chế Parameter Binding có sẵn của Laravel:
  ```php
  // Khắc phục:
  $products = DB::table('products')->where('category_id', $categoryId)->get();
  ```

---

### FINDING-02: Insecure Direct Object References (IDOR) tại chức năng Xem Đơn Hàng (High)
- **Vulnerability Type:** Broken Access Control (CWE-639)
- **CVSS v3.1 Score:** `7.5` (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N)
- **Endpoint bị ảnh hưởng:** `GET /api/v1/orders/{order_id}`
- **Mô tả:** Hệ thống chỉ kiểm tra user đã login hay chưa, không kiểm tra quyền sở hữu giữa `order_id` và `Auth::id()`.
- **Proof-of-Concept (PoC):**
  User `customer1` (ID: 10) có thể xem đơn hàng của `customer2` (ID: 11) bằng cách thay đổi giá trị `{order_id}` từ `1001` sang `1002`.
- **Biện pháp khắc phục:**
  Sử dụng Laravel Policy hoặc kiểm tra ràng buộc quan hệ:
  ```php
  // Khắc phục trong OrderController:
  $order = Auth::user()->orders()->findOrFail($orderId);
  ```

---

## 4. Kết Luận & Khuyến Nghị Tổng Thể
Ứng dụng cần áp dụng nguyên tắc **Defense-in-Depth**:
1. Chuẩn hóa toàn bộ câu truy vấn dữ liệu sang ORM / Parameterized Queries.
2. Thiết lập Role-Based Access Control (RBAC) chặt chẽ ở cấp độ Controller/Middleware.
3. Kích hoạt Content Security Policy (CSP) và cấu hình lại session cookies (`HttpOnly`, `Secure`, `SameSite=Lax`).
