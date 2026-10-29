# 💉 SQL Injection (SQLi) Module

> **Tiến độ hiện tại:** 17/18 Labs Solved (Đang giải quyết lab OAST)

Thư mục này tập trung toàn bộ tài liệu nghiên cứu, lý thuyết tự viết, write-up chi tiết từng bài lab và script tự động hóa cho chuyên đề **SQL Injection** trên PortSwigger Web Security Academy.

---

## 📋 Danh Sách Lab & Trạng Thái

| Lab # | Tên Bài Lab | Cấp Độ | Trọng Tâm Kỹ Thuật | Trạng Thái | Write-up |
| :---: | :--- | :---: | :--- | :---: | :---: |
| 01 | SQLi vulnerability in WHERE clause allowing retrieval of hidden data | Apprentice | Basic Tautology (`' OR 1=1--`) | ✅ | *Pending write-up* |
| 02 | SQLi vulnerability allowing login bypass | Apprentice | Authentication Bypass | ✅ | *Pending write-up* |
| 03 | SQLi UNION attack, determining the number of columns returned | Practitioner | `ORDER BY` / `UNION SELECT NULL` | ✅ | *Pending write-up* |
| 04 | SQLi UNION attack, finding a column containing text | Practitioner | Xác định kiểu dữ liệu cột trả về | ✅ | *Pending write-up* |
| 05 | SQLi UNION attack, retrieving data from other tables | Practitioner | Khai thác dữ liệu bảng `users` | ✅ | *Pending write-up* |
| 06 | SQLi UNION attack, retrieving multiple values in a single column | Practitioner | Kỹ thuật nối chuỗi (Concatenation) | ✅ | *Pending write-up* |
| 07 | SQLi attack, querying the database type and version on Oracle | Practitioner | Tra cứu phiên bản trên Oracle (`v$version`) | ✅ | *Pending write-up* |
| 08 | SQLi attack, querying the database type and version on MySQL and Microsoft | Practitioner | Tra cứu phiên bản (`@@version`) | ✅ | *Pending write-up* |
| 09 | SQLi attack, listing the database contents on non-Oracle databases | Practitioner | Schema enumeration (`information_schema`) | ✅ | *Pending write-up* |
| 10 | SQLi attack, listing the database contents on Oracle | Practitioner | Schema enumeration trên Oracle (`all_tables`) | ✅ | *Pending write-up* |
| 11 | Blind SQLi with conditional responses | Practitioner | Boolean-based Blind SQLi | ✅ | *Pending write-up* |
| 12 | Blind SQLi with conditional errors | Practitioner | Error-conditional Blind SQLi | ✅ | *Pending write-up* |
| 13 | Visible error-based SQLi | Practitioner | Trích xuất dữ liệu qua Error message | ✅ | *Pending write-up* |
| 14 | Blind SQLi with time delays | Practitioner | Time-based SQLi (`pg_sleep`) | ✅ | *Pending write-up* |
| 15 | Blind SQLi with time delays and information retrieval | Practitioner | Time-based data exfiltration | ✅ | *Pending write-up* |
| 16 | Blind SQLi with out-of-band interaction | Practitioner | Out-of-band OAST DNS pingback | ⏳ In Progress | *Pending* |
| 17 | SQLi with filter bypass via XML encoding | Practitioner | XML entity encoding bypass | ✅ | *Pending write-up* |
| 18 | Blind SQLi with out-of-band data exfiltration | Practitioner | OAST data exfiltration qua Burp Collaborator | ⏳ In Progress | *Pending* |

---

## 📌 Cách Thức Ghi Chép Cho Từng Bài Lab
Mỗi bài lab khi bạn cung cấp lý thuyết tự đúc kết và nội dung giải sẽ được tách thành file riêng (hoặc nhóm theo kỹ thuật), bao gồm:
- **Nguyên nhân gốc rễ (Root Cause):** Đoạn mã hoặc cơ chế logic phía backend bị lỗi.
- **Phương pháp tiếp cận:** Cách thăm dò số cột, loại DB, ký tự thoát chuỗi.
- **Payload giải thích chi tiết:** Ý nghĩa từng thành phần trong câu lệnh tiêm vào.
- **Script (nếu có):** Python automation script (như tìm kiếm nhị phân cho Blind SQLi).
