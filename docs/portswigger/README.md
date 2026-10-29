# 🎯 PortSwigger Web Security Academy Hub

Chào mừng đến với không gian ghi chép lộ trình **PortSwigger Web Security Academy**. 

Tại đây, mỗi chuyên đề lỗ hổng sẽ được tổ chức thành một thư mục con riêng biệt. Mỗi bài lab đều bao gồm:
1. **Lý thuyết nền tảng & Cơ chế lỗ hổng:** Do chính mình tự tìm hiểu, nghiên cứu và đúc kết lại bằng ngôn từ của bản thân.
2. **Lab Write-up chi tiết:** Các bước thăm dò (recon), phân tích request/response và payload thực tế.
3. **Payload & Exploit Script:** Mã khai thác tự động (Python / Burp macro) nếu có.

---

## 📊 Bảng Theo Dõi Chuyên Đề (Topic Progress)

| Chuyên Đề (Topic) | Thư Mục | Trạng Thái | Số Lab Hoàn Thành | Ghi Chú |
| :--- | :---: | :---: | :---: | :--- |
| **SQL Injection** | [`SQLI/`](SQLI/) | 🟢 Active | **17 / 18** | Đã xử lý Union, Error, Blind (Đang làm OAST) |
| **NoSQL Injection** | `NOSQLI/` | 🟡 Up Next | 0 / 4 | Cú pháp BSON/JSON, auth bypass, operator injection |
| **Authentication & Access Control** | `AUTH/` | ⚪ Planning | 0 / 14 | Password reset, MFA bypass, IDOR |
| **Cross-Site Scripting** | `XSS/` | ⚪ Planning | 0 / 30 | Reflected, Stored, DOM-based, CSP bypass |
| **CSRF & SSRF** | `CSRF-SSRF/` | ⚪ Planning | 0 / 17 | Token bypass, Cloud metadata exfiltration |
| **File Upload Vulnerabilities** | `FILE-UPLOAD/` | ⚪ Planning | 0 / 7 | MIME validation, Path traversal, Web shell |

---

## 🗂️ Quy Chuẩn Cấu Trúc Nhánh Con

Khi bắt đầu học một chuyên đề mới, một thư mục con tương ứng sẽ được tạo (ví dụ: `SQLI/`, `NOSQLI/`):
```text
docs/portswigger/
├── README.md                   # Trang tổng quan này
├── SQLI/                       # Thư mục chuyên đề SQL Injection
│   ├── README.md               # Tổng hợp lý thuyết, danh sách lab của chuyên đề
│   ├── lab-01-where-clause.md  # Writeup + lý thuyết riêng của bài lab
│   └── scripts/                # Script Python khai thác tự động
└── NOSQLI/                     # Chuyên đề NoSQL Injection (sắp tới)
```
