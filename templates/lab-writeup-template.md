# 📝 Lab Write-up Template

> **Tên bài Lab:** [Tên bài Lab / Challenge]  
> **Nguồn:** [PortSwigger Academy / Hack The Box / Khác]  
> **Độ khó:** [Apprentice / Practitioner / Expert]  
> **Loại lỗ hổng:** [SQLi / XSS / CSRF / SSRF / IDOR / ...]

---

## 1. Mục Tiêu Bài Lab (Lab Objective)
- Mô tả mục tiêu cần đạt được (ví dụ: đăng nhập tài khoản administrator, dump mật khẩu, kích hoạt popup XSS...).

---

## 2. Phân Tích & Nguyên Nhân Lỗ Hổng (Root Cause Analysis)
- **Vị trí lỗ hổng:** Tham số, Header, hoặc Endpoint nào bị lỗi?
- **Nguyên nhân:** Tại sao lỗi lại xảy ra? Ứng dụng đã xử lý đầu vào (input sanitization / validation) thiếu sót ở bước nào?

---

## 3. Các Bước Khai Thác Chi Tiết (Step-by-Step Exploitation)

### Bước 1: Recon & Thăm dò (Probing)
- Request gửi đi và response trả về:
```http
GET /test?param=payload HTTP/1.1
Host: target.com
```

### Bước 2: Tinh chỉnh Payload (Payload Crafting)
- Giải thích payload được xây dựng như thế nào:
```sql
' UNION SELECT NULL, password FROM users--
```

### Bước 3: Hoàn thành mục tiêu (Execution & Result)
- Kết quả đạt được (ảnh chụp màn hình hoặc kết quả text/flag).

---

## 4. Tự Động Hóa (Automation Script - nếu có)
```python
import requests

url = "https://target-lab.web-security-academy.net"
# Script code logic here
```

---

## 5. Bài Học Rút Ra & Biện Pháp Khắc Phục (Key Takeaways & Remediation)
- **Phía lập trình viên (Developer Fix):** Code sửa lỗi an toàn.
- **Phía pentester:** Dấu hiệu nhận biết nhanh khi gặp dạng bài tương tự.
