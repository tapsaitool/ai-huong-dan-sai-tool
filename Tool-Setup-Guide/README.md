# 🎉 Tool-Setup-Guide — Cài đặt tool Node.js & Python từ A → Z

> **Đừng lo nếu bạn không biết code, cứ làm y hệt từng bước dưới đây là tool sẽ chạy mượt.** ✨

Đây là bộ hướng dẫn dành riêng cho **người chưa từng biết code** muốn cài đặt môi trường để chạy các tool tự động (automation, cào dữ liệu, bot…) viết bằng **Node.js** hoặc **Python** trên máy tính **Ubuntu**.

Mọi thứ đã được mình quay video + chụp ảnh trực tiếp trên máy thật, bạn chỉ cần **bấm Copy → Paste vào Terminal → Enter** là xong. 💪

---

## 🗺️ Lộ trình học (chỉ mất ~10 phút)

| 🔢 | 📚 Tài liệu | 👀 Bạn sẽ học được gì |
|---:|------------|----------------------|
| 1️⃣ | [docs/nodejs-setup.md](docs/nodejs-setup.md) | Cách cài **Node.js LTS** + chạy file `.js` đầu tiên |
| 2️⃣ | [docs/python-setup.md](docs/python-setup.md) | Cách cài **Python3 + pip + venv** + chạy file `.py` đầu tiên |
| 3️⃣ | [docs/troubleshooting.md](docs/troubleshooting.md) | Cách xử lý khi gặp lỗi (đừng hoảng nha 🙂) |

---

## 📂 Cấu trúc thư mục

```text
Tool-Setup-Guide/
├── README.md                  ← bạn đang đọc file này 👋
├── docs/
│   ├── nodejs-setup.md        ← hướng dẫn Node.js
│   ├── python-setup.md        ← hướng dẫn Python
│   └── troubleshooting.md     ← gỡ rối lỗi thường gặp
├── demo_scripts/
│   ├── demo.js                ← tool demo Node.js
│   ├── demo.py                ← tool demo Python
│   └── requirements.txt       ← thư viện Python cần cài
└── media/
    ├── node-install.mp4       ← video cài Node.js
    ├── node-demo-result.png   ← ảnh kết quả chạy demo Node
    ├── python-install.mp4     ← video cài Python
    ├── python-venv.mp4        ← video tạo & kích hoạt venv (xem chậm!)
    └── python-demo-result.png ← ảnh kết quả chạy demo Python
```

---

## 🖥️ Yêu cầu của máy bạn

- Hệ điều hành: **Ubuntu 20.04 / 22.04 / 24.04** (hoặc các bản Linux dựa trên Debian)
- Có kết nối Internet 🌐
- Tài khoản người dùng có quyền `sudo` (gõ `sudo` mà không bị từ chối)

> 💡 **Bí kíp dành cho người mới:** Nếu bạn dùng Windows hoặc Mac, hãy dùng **WSL (Ubuntu)** trên Windows hoặc **VPS Ubuntu giá rẻ** rồi làm theo hướng dẫn này.

---

## 🚀 Bắt đầu ngay

### 👉 Nếu bạn muốn chạy tool viết bằng **Node.js** (`.js`):
👉 Vào [docs/nodejs-setup.md](docs/nodejs-setup.md)

### 👉 Nếu bạn muốn chạy tool viết bằng **Python** (`.py`):
👉 Vào [docs/python-setup.md](docs/python-setup.md)

### 👉 Nếu chạy bị lỗi:
👉 Mở [docs/troubleshooting.md](docs/troubleshooting.md) ra xem nhé 🛠️

---

## ❤️ Lời nhắn dễ thương

Cài tool lần đầu thường **hơi run tay**, đó là chuyện **bình thường**. Bạn cứ copy đúng lệnh, nhìn màn hình, đối chiếu với ảnh trong tài liệu là sẽ qua. **Bạn làm được mà!** 🥰

Nếu kẹt ở đâu, mở `docs/troubleshooting.md` ra hoặc nhắn lại cho người gửi tool cho bạn — đừng xóa máy hay format ổ cứng đâu nha 😄.
