# 🎉 Tool-Setup-Guide — Cài đặt môi trường chạy tool Node.js & Python

> **Chỉ cần biết xài chuột là cài được. Không phải dân code cũng làm được trong 5 phút.** ✨

Bộ hướng dẫn này dành cho **người chưa từng biết code** muốn chạy các tool tự động (bot request, airdrop, cào dữ liệu, automation…) viết bằng **Node.js** hoặc **Python**.

Mọi thứ đã được mình mô tả từng cú nhấp chuột, kèm screenshot trang tải chính chủ và placeholder ảnh để chèn thêm khi bạn chạy thực tế trên máy. 💪

---

## 🗺️ Bạn đang dùng hệ điều hành nào?

### 🪟 Windows 10 / 11 (đa số người dùng) — KHÔNG cần venv

| 🔢 | 📚 Tài liệu | 👀 Bạn sẽ học được gì |
|---:|------------|----------------------|
| 1️⃣ | [docs/nodejs-setup.md](docs/nodejs-setup.md) | Cài **Node.js LTS** bằng file `.msi` + chạy `node demo.js` đầu tiên |
| 2️⃣ | [docs/python-setup.md](docs/python-setup.md) | Cài **Python** bằng file `.exe` (nhớ tích **`Add python.exe to PATH`** ⚠️), cài thư viện thẳng vào máy với `pip install -r requirements.txt`, KHÔNG dùng venv |
| 3️⃣ | [docs/troubleshooting.md](docs/troubleshooting.md) | 95% lỗi Windows hay gặp đã có sẵn lời giải |

### 🐧 Linux (Ubuntu) — DÙNG venv

> Nếu bạn dùng Ubuntu hoặc VPS Linux, các hướng dẫn cũ (có dùng `venv`) vẫn được giữ tại đây:

- 🟢 [docs/linux/nodejs-setup.md](docs/linux/nodejs-setup.md)
- 🐍 [docs/linux/python-setup.md](docs/linux/python-setup.md) (kèm `venv` chuẩn chỉnh)
- 🛠️ [docs/linux/troubleshooting.md](docs/linux/troubleshooting.md)

---

## 📂 Cấu trúc thư mục

```text
Tool-Setup-Guide/
├── README.md                           ← bạn đang đọc 👋
├── docs/
│   ├── nodejs-setup.md                 ← hướng dẫn Node.js trên Windows
│   ├── python-setup.md                 ← hướng dẫn Python trên Windows (KHÔNG venv)
│   ├── troubleshooting.md              ← gỡ rối lỗi Windows
│   └── linux/
│       ├── nodejs-setup.md             ← phiên bản Linux/Ubuntu
│       ├── python-setup.md             ← phiên bản Linux/Ubuntu (có venv)
│       └── troubleshooting.md          ← gỡ rối lỗi Linux
├── demo_scripts/
│   ├── demo.js                         ← tool demo Node.js (mô phỏng auto request)
│   ├── demo.py                         ← tool demo Python (mô phỏng auto request)
│   └── requirements.txt                ← chỉ cần `requests`
└── media/
    ├── node-download-win.png           ← ảnh trang tải Node.js cho Windows
    ├── python-download-win.png         ← ảnh trang tải Python cho Windows
    ├── node-install.mp4                ← video cài Node.js trên Linux
    ├── node-demo-result.png            ← kết quả chạy demo Node trên Linux
    ├── python-install.mp4              ← video cài Python trên Linux
    ├── python-venv.mp4                 ← video tạo venv trên Linux
    └── python-demo-result.png          ← kết quả chạy demo Python trên Linux
```

---

## 🖥️ Yêu cầu của máy bạn

- **Windows 10 / Windows 11** (đa số người Việt) **hoặc** Ubuntu 20.04 / 22.04 / 24.04.
- Có kết nối Internet 🌐.
- Trên Windows: tài khoản Admin (khi cài hỏi mật khẩu thì có thể nhập).

---

## 🚀 Bắt đầu ngay

### 👉 Tool người ta gửi cho bạn là `.js` (Node.js)?
👉 Mở [docs/nodejs-setup.md](docs/nodejs-setup.md) ra làm theo từ đầu.

### 👉 Tool người ta gửi cho bạn là `.py` (Python)?
👉 Mở [docs/python-setup.md](docs/python-setup.md) ra làm theo từ đầu (đặc biệt **lưu ý ô tích `Add python.exe to PATH`** ⚠️).

### 👉 Bị lỗi giữa chừng?
👉 [docs/troubleshooting.md](docs/troubleshooting.md) là cứu cánh 🛠️.

---

## ❤️ Lời nhắn dễ thương

Cài tool lần đầu thường **hơi run tay**, đó là chuyện **rất bình thường**. Cứ Next-Next-Install theo đúng hướng dẫn, đặc biệt KHÔNG quên ô **`Add python.exe to PATH`** khi cài Python — là 95% bạn sẽ thành công ngay từ lần đầu. 🥰

Nếu kẹt, mở [troubleshooting.md](docs/troubleshooting.md) hoặc nhắn lại cho người gửi tool — đừng xóa máy / format ổ cứng đâu nha 😄.

**Bạn làm được mà! Bắt đầu thôi 💪🔥**
