# 🎯 Hack The Box Journey Hub

Trang tổng quan theo dõi quá trình giải các phòng máy (Machines) và thử thách (Challenges) trên nền tảng **Hack The Box**.

---

## 🧭 Cấu Trúc Quản Lý Bài Viết

Để giữ cho repository luôn gọn gàng và khoa học, toàn bộ write-up của HTB sẽ được tổ chức thành các thư mục con bên trong `docs/hackthebox/`:

```text
docs/hackthebox/
├── README.md               # Trang tổng quan này
├── machines/               # Thư mục chứa các máy đã hoàn thành
│   ├── easy/               # Các máy cấp độ Easy (ví dụ: Sau, Lame, CozyHosting,...)
│   │   └── [box-name]/     # Thư mục riêng cho từng máy (writeup.md, nmap.txt, exploit scripts)
│   └── medium/             # Các máy cấp độ Medium
└── challenges/             # Thư mục chứa các web challenges
    └── [challenge-name]/
```

---

## 📈 Bảng Thống Kê Máy & Challenges

| Tên Target / Machine | Thể Loại | Cấp Độ | Hệ Điều Hành | Trọng Tâm Khai Thác | Trạng Thái | Link Write-up |
| :--- | :---: | :---: | :---: | :--- | :---: | :---: |
| *Sẽ cập nhật khi hoàn thành* | Web / System | Easy | Linux | Enumeration, Entry Foothold, PrivEsc | ⏳ | *Pending* |

---

## 📝 Nội Dung Mỗi Bài Write-up HTB
Khi giải xong một máy và đưa lên repo, bài viết sẽ tuân theo cấu trúc:
1. **Reconnaissance:** Port scanning (Nmap), Web content discovery (FFUF/Gobuster), Fingerprinting.
2. **Initial Access (Foothold):** Phân tích điểm yếu đầu vào, khai thác lấy Reverse Shell.
3. **Privilege Escalation:** Leo thang đặc quyền lên user thường hoặc `root`.
4. **Key Takeaways:** Những kiến thức, kỹ thuật hoặc bài học kinh nghiệm mới rút ra được.
