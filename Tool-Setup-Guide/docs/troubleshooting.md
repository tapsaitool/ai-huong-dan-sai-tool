# 🛠️ Troubleshooting — Gỡ rối lỗi thường gặp

> **Đừng lo nếu bạn không biết code, cứ làm y hệt từng bước dưới đây là tool sẽ chạy mượt.** ✨

File này tập hợp **những lỗi mà 95% người mới gặp** khi làm theo [nodejs-setup.md](nodejs-setup.md) và [python-setup.md](python-setup.md). Trước khi hoảng, bạn cứ Ctrl+F (hoặc kéo xuống) để xem lỗi của mình nằm ở đâu nhé. 🤝

---

## 📑 Mục lục nhanh

- [🔑 Lỗi liên quan đến `sudo` / mật khẩu](#-lỗi-liên-quan-đến-sudo--mật-khẩu)
- [🌐 Lỗi mạng / không tải được package](#-lỗi-mạng--không-tải-được-package)
- [🟢 Lỗi Node.js](#-lỗi-nodejs)
- [🐍 Lỗi Python](#-lỗi-python)
- [📦 Lỗi venv](#-lỗi-venv)
- [📂 Lỗi `nano` / chỉnh file](#-lỗi-nano--chỉnh-file)
- [🆘 Vẫn không xử lý được?](#-vẫn-không-xử-lý-được)

---

## 🔑 Lỗi liên quan đến `sudo` / mật khẩu

### ❓ Gõ mật khẩu mà KHÔNG thấy chữ hiện lên?
**Đó là TÍNH NĂNG, không phải lỗi.** 😄 Trên Linux, khi gõ mật khẩu sudo, hệ thống cố tình KHÔNG hiện ra (kể cả dấu `*`) để **người đứng sau không nhìn lén được**. Cứ gõ tiếp rồi Enter, sẽ chạy bình thường.

### ❓ Báo `username is not in the sudoers file`?
Tài khoản của bạn không có quyền `sudo`. **Liên hệ chủ máy / chủ VPS** để được cấp quyền, hoặc đăng nhập bằng tài khoản `root` rồi bỏ chữ `sudo` ở đầu mỗi lệnh.

### ❓ Báo `sudo: command not found`?
Hệ thống không có sẵn `sudo`. Đăng nhập với `root` rồi cài: `apt-get install -y sudo`.

---

## 🌐 Lỗi mạng / không tải được package

### ❓ Báo `Could not resolve host` / `Temporary failure in name resolution`?
👉 Máy bạn **mất Internet** hoặc DNS bị lỗi.

📋 Test thử:
```bash
ping -c 3 google.com
```

- Nếu báo lỗi → kiểm tra lại WiFi / cáp mạng / VPN.
- Nếu vẫn `Connected` mà tải gói lỗi → đợi 1–2 phút rồi thử lại, có thể server đang bận.

### ❓ Báo `403 Forbidden` khi tải `setup_lts.x` của NodeSource?
Hiếm gặp, thử lại sau 5 phút. Hoặc dùng cách "không cần NodeSource":

📋 Dùng `nvm` (Node Version Manager) — đây là cách dự phòng:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Sau đó **đóng Terminal → mở lại**, rồi:

```bash
nvm install --lts
nvm use --lts
```

Kiểm tra: `node -v` phải in ra version.

---

## 🟢 Lỗi Node.js

### ❓ `node: command not found`
Nguyên nhân: Cài chưa xong, hoặc PATH chưa được cập nhật.

📋 Thử đóng Terminal → mở lại (Ctrl + Alt + T mới), rồi gõ:

```bash
node -v
```

Nếu vẫn báo lỗi → cài lại bằng:

```bash
sudo apt-get install -y --reinstall nodejs
```

### ❓ `npm: command not found` (nhưng `node` chạy được)
NodeSource đôi khi tách `npm` ra. Cài thêm:

```bash
sudo apt-get install -y npm
```

### ❓ `EACCES: permission denied` khi `npm install -g <gói>`
Đừng dùng `sudo` để fix — sẽ làm hỏng hệ thống. **Cách đúng:** cấu hình prefix riêng:

```bash
mkdir -p ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

Giờ `npm install -g` sẽ không cần sudo nữa.

---

## 🐍 Lỗi Python

### ❓ `python3: command not found`
Cài lại bằng:

```bash
sudo apt-get install -y --reinstall python3
```

### ❓ `pip3: command not found` (nhưng `python3` chạy được)
Pip chưa được cài. Lệnh này sẽ fix:

```bash
sudo apt-get install -y python3-pip
```

### ❓ Báo `error: externally-managed-environment` khi gõ `pip install <gì-đó>`?
Đây là **cảnh báo** từ Ubuntu mới, **để bảo vệ Python hệ thống**. Cách xử lý ĐÚNG là **dùng `venv`** (xem [python-setup.md - Bước 4](python-setup.md#-bước-4--tạo-môi-trường-ảo-venv-cực-kỳ-quan-trọng-)).

> ❌ KHÔNG nên dùng `--break-system-packages` để né lỗi này — nó sẽ làm hỏng các tool hệ thống về lâu dài.

### ❓ Báo `ModuleNotFoundError: No module named 'requests'` (hoặc tên thư viện khác) khi chạy file `.py`?
Nguyên nhân: Bạn **chưa kích hoạt venv** hoặc **cài thư viện ở venv khác**.

📋 Sửa:
1. `cd` đến thư mục có `venv/`.
2. Gõ `source venv/bin/activate` (đảm bảo có `(venv)` ở đầu dòng).
3. Cài lại: `pip install -r requirements.txt`.
4. Chạy lại: `python3 demo.py`.

---

## 📦 Lỗi venv

### ❓ Báo `The virtual environment was not created successfully because ensurepip is not available`?
Thiếu gói `python3-venv`. Cài bổ sung:

```bash
sudo apt-get install -y python3-venv
```

Sau đó xoá folder `venv/` cũ và tạo lại:

```bash
rm -rf venv
python3 -m venv venv
```

### ❓ Đã gõ `source venv/bin/activate` rồi mà KHÔNG thấy chữ `(venv)` xuất hiện?

**Checklist** (làm theo thứ tự):

1. **Bạn đang đứng đúng thư mục chứa folder `venv/` chưa?** Gõ `ls` xem có folder `venv` không. Nếu không, `cd` về thư mục đó.

2. **Đường dẫn có viết sai không?** Lệnh chuẩn là `source venv/bin/activate` — KHÔNG phải `source venv\bin\activate` (đó là Windows).

3. **Shell bạn đang dùng có hỗ trợ `source` không?** Nếu dùng `sh` (`/bin/sh`), thử dùng dấu chấm: `. venv/bin/activate`.

4. **Folder `venv/` có file `bin/activate` không?** Gõ `ls venv/bin/activate` — nếu báo lỗi thì venv tạo bị hỏng → `rm -rf venv && python3 -m venv venv` rồi thử lại.

### ❓ `(venv)` không biến mất sau khi gõ `deactivate`?
Đóng Terminal → mở lại Terminal mới (Ctrl + Alt + T) là sạch.

---

## 📂 Lỗi `nano` / chỉnh file

### ❓ Vào `nano` rồi không biết thoát ra như thế nào?

| Phím | Tác dụng |
|------|----------|
| `Ctrl + O` | **O**h, save file (nhấn Enter để xác nhận tên) |
| `Ctrl + X` | E**X**it ra ngoài |
| `Ctrl + K` | Cắt 1 dòng (như Ctrl+X copy) |
| `Ctrl + W` | **W**here is — tìm chữ trong file |

### ❓ Paste vào `nano` mà code lệch dòng / thừa khoảng trắng?

Nano đôi khi tự **auto-indent** làm code lệch. Cách fix:
- Trước khi paste, nhấn `Alt + I` để TẮT auto-indent (sẽ thấy thông báo `Auto indent disabled`).
- Hoặc dùng `Ctrl + Shift + V` (paste sạch) thay vì chuột phải Paste.

### ❓ Tôi muốn dùng tool khác thay nano (vd: `vim` hoặc `gedit`)?

- **`gedit`** = Notepad của Ubuntu, có giao diện. Mở bằng: `gedit demo.py`.
- **`vim`** = mạnh hơn nhưng khó với người mới — bỏ qua nếu chưa biết.

---

## 🆘 Vẫn không xử lý được?

Đừng nản! 🤗 Bạn có thể:

1. **Chụp màn hình lỗi** (cả phần lệnh đã gõ + thông báo lỗi).
2. **Copy nguyên đoạn lỗi** vào ô tìm kiếm Google — 99% lỗi đã có người gặp trước rồi.
3. **Gửi lại cho người đã gửi tool cho bạn**, họ sẽ debug giúp.
4. **Ghi rõ:** bạn đang ở bước nào trong [nodejs-setup.md](nodejs-setup.md) hoặc [python-setup.md](python-setup.md), để hỗ trợ nhanh hơn.

> 🌟 **Nhớ:** Mọi developer kỳ cựu cũng đã từng "vò đầu bứt tóc" với những lỗi y chang vầy hồi mới học. Càng gặp nhiều lỗi → càng giỏi nhanh hơn. **Bạn đang đi đúng hướng!** 💪🔥
