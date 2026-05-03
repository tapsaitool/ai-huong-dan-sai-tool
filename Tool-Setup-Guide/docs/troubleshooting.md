# 🛠️ Troubleshooting (Windows) — Gỡ rối lỗi thường gặp

> **Đừng hoảng — 95% lỗi mà người dùng Windows gặp đã có sẵn lời giải ngay dưới đây.** 🙌

File này tập hợp các lỗi mà người mới hay gặp khi làm theo [nodejs-setup.md](nodejs-setup.md) và [python-setup.md](python-setup.md). Bấm **Ctrl + F** trên trình duyệt để tìm nhanh thông báo lỗi của bạn.

> 🐧 Nếu bạn đang dùng **Linux/Ubuntu**, xem hướng dẫn cũ tại [docs/linux/troubleshooting.md](linux/troubleshooting.md).

---

## 📑 Mục lục nhanh

- [🚧 Lỗi tải / cài file `.msi` / `.exe`](#-lỗi-tải--cài-file-msi--exe)
- [🟢 Node not recognized trên Windows](#-node-not-recognized-trên-windows)
- [🐍 Python not recognized trên Windows](#-python-not-recognized-trên-windows)
- [📦 Lỗi `pip install`](#-lỗi-pip-install)
- [📂 Lỗi tạo file `demo.js` / `demo.py`](#-lỗi-tạo-file-demojs--demopy)
- [🆘 Vẫn bí?](#-vẫn-bí)

---

## 🚧 Lỗi tải / cài file `.msi` / `.exe`

### ❓ Trình duyệt báo "This file may harm your computer"?
Đó là **cảnh báo mặc định** của Chrome/Edge với mọi file `.msi` / `.exe`. File từ `nodejs.org` và `python.org` là **chính chủ, an toàn 100%**. Bấm **Keep / Giữ lại** để tải tiếp.

### ❓ Mở file `.msi` / `.exe` lên không có chuyện gì xảy ra?
- Có thể Windows đã chặn file lạ. **Bấm chuột phải vào file → Properties → Tích ô "Unblock" → OK** → mở lại.
- Đảm bảo bạn **nhấp đúp chuột trái** (không phải Enter sau khi chọn file).

### ❓ Cửa sổ "Do you want to allow this app to make changes…?" hiện ra?
**Bình thường.** Bấm **Yes**. Đó là Windows User Account Control (UAC), bảo vệ máy bạn khỏi phần mềm lạ. Node.js & Python là phần mềm chính chủ.

### ❓ Báo lỗi "The system administrator has set policies to prevent this installation"?
Bạn không có quyền Admin. Đăng nhập bằng tài khoản **Administrator** (hoặc nhờ chủ máy), hoặc bấm chuột phải vào file `.msi` / `.exe` → **Run as administrator**.

---

## 🟢 Node not recognized trên Windows

### ❓ Báo `'node' is not recognized as an internal or external command, operable program or batch file`?

**Nguyên nhân:** Cửa sổ CMD đang mở **trước khi** Node.js được cài → CMD không biết Node.js mới có. Hoặc trình cài chưa thêm Node vào PATH.

### 🔧 Cách fix:
1. **Đóng tất cả cửa sổ CMD đang mở.**
2. Mở CMD MỚI bằng mẹo "thần thánh" — gõ `cmd` vào thanh địa chỉ File Explorer.
3. Gõ lại `node -v`.
4. Nếu vẫn lỗi → **Restart máy** rồi thử lại.
5. Vẫn lỗi → vào **Settings → Apps → Installed apps**, tìm Node.js, bấm **Uninstall**, rồi cài lại theo [nodejs-setup.md](nodejs-setup.md).

### ❓ Báo `'npm' is not recognized…` (nhưng `node` chạy được)?
Hiếm gặp. Cài lại Node.js — trình installer mới sẽ kèm cả `npm`.

### ❓ `npm install` báo `EACCES` hoặc `permission denied`?
- Đóng CMD, **bấm chuột phải Start → "Terminal (Admin)"** → chạy lại lệnh.
- Hoặc đảm bảo thư mục tool **không nằm trong** `C:\Program Files\` (Windows hạn chế ghi vào đó).

### ❓ `npm install` chạy mãi không xong / treo?
- Internet chậm. Đợi thêm. Mỗi tool có thể cần tải vài chục MB.
- Hoặc chuyển registry: `npm config set registry https://registry.npmmirror.com` rồi `npm install` lại.

---

## 🐍 Python not recognized trên Windows

### ❓ Báo `'python' is not recognized as an internal or external command…`?

**95% nguyên nhân:** Bạn **quên tích ô `Add python.exe to PATH`** ở Bước 2 của [python-setup.md](python-setup.md). 😅

### 🔧 Cách fix nhanh nhất:
1. Vào **Settings → Apps → Installed apps**.
2. Tìm **"Python 3.x.x"** trong danh sách.
3. Bấm vào → **Uninstall**.
4. Vào lại trang `python.org/downloads/windows/` → tải `.exe` mới.
5. Mở file installer, **TÍCH NGAY ô `Add python.exe to PATH`** ở dưới cùng cửa sổ đầu tiên ⚠️.
6. Bấm **Install Now** → Finish.
7. **Đóng tất cả CMD cũ → mở CMD mới** → gõ `python --version`.

> 🚨 **Bài học rút ra:** Mỗi lần cài Python, ô `Add python.exe to PATH` luôn là thứ TÍCH ĐẦU TIÊN, trước cả khi bấm Install. Khắc cốt ghi tâm! 🙏

### ❓ `python --version` không lỗi, nhưng `pip --version` lại báo not recognized?
- Đóng CMD → mở CMD mới (mẹo `cmd` trong thanh địa chỉ).
- Hoặc thử: `python -m pip --version`.

### ❓ Gõ `python` thì cửa sổ Microsoft Store mở ra (không phải Python)?
Windows 10/11 mặc định có "Python từ Microsoft Store" giả mạo gây nhầm lẫn. Cách fix:
1. Vào **Settings → Apps → Advanced app settings → App execution aliases**.
2. **Tắt 2 dòng:** "App Installer python.exe" và "App Installer python3.exe".
3. Mở CMD mới → `python --version`. Lần này sẽ ra Python thật.

---

## 📦 Lỗi `pip install`

### ❓ Báo `error: externally-managed-environment`?
Hiếm gặp trên Windows (thường là Linux). Nếu gặp:
```cmd
pip install -r requirements.txt --user
```
Tham số `--user` cài thư viện vào thư mục riêng của user, né được giới hạn này.

### ❓ Báo `Could not find a version that satisfies the requirement <thư-viện>`?
- Có thể Internet bị chặn. Thử đổi mirror: `pip install -r requirements.txt -i https://pypi.org/simple/`.
- Hoặc kiểm tra `requirements.txt` xem có gõ sai tên thư viện không.

### ❓ Báo `SSL: CERTIFICATE_VERIFY_FAILED`?
Cài lại Python (chọn "Disable path length limit" ở cuối installer giúp tránh lỗi này luôn). Hoặc tạm bypass: `pip install -r requirements.txt --trusted-host pypi.org --trusted-host files.pythonhosted.org`.

### ❓ Báo `Microsoft Visual C++ 14.0 or greater is required`?
Một số thư viện cần **C++ Build Tools**. Tải về tại: `https://visualstudio.microsoft.com/visual-cpp-build-tools/` → cài, tích "C++ build tools" → Install. Sau đó `pip install` lại.

---

## 📂 Lỗi tạo file `demo.js` / `demo.py`

### ❓ Tôi tạo file `demo.js` mà nó hiện thành `demo.js.txt`?
Windows ẩn đuôi mặc định. Cách hiện đuôi:
1. Mở **File Explorer** → bấm tab **View** ở thanh trên cùng.
2. Tích ô **"File name extensions"**.
3. Đổi tên file thành `demo.js` (xoá phần `.txt` đuôi).

> 💡 **Cách bypass nhanh:** Khi tạo file, gõ tên trong dấu nháy kép: `"demo.js"`. Windows sẽ giữ nguyên đuôi.

### ❓ File `demo.py` lưu rồi nhưng `python demo.py` lại báo lỗi cú pháp lạ?
Notepad đôi khi lưu file với encoding **UTF-16 BOM** làm Python không đọc được. Cách fix:
1. Mở file bằng **Notepad++** (tải free) hoặc **VS Code**.
2. Chuyển encoding sang **UTF-8 (không BOM)**.
3. Lưu lại → chạy lại `python demo.py`.

### ❓ Code có emoji nhưng CMD không hiển thị được?
CMD mặc định không hỗ trợ emoji tốt. Có 2 cách:
- **Cách dễ:** dùng **Windows Terminal** (tải free từ Microsoft Store) — hỗ trợ emoji đầy đủ.
- **Cách khác:** thay emoji bằng chữ ASCII trong code (ví dụ `[OK]` thay cho `✅`). Tool vẫn chạy bình thường.

---

## 🆘 Vẫn bí?

Đừng nản! 🤗

1. **Chụp màn hình lỗi** (cả lệnh đã gõ + thông báo lỗi) bằng phím **Win + Shift + S**.
2. **Copy nguyên đoạn lỗi** vào Google — 99% lỗi đã có người gặp trước.
3. **Gửi lại cho người đã cho bạn tool**, kèm screenshot và mô tả: bạn đang ở bước nào trong [nodejs-setup.md](nodejs-setup.md) hoặc [python-setup.md](python-setup.md).

> 🌟 **Nhớ:** Mọi developer kỳ cựu cũng từng "vò đầu bứt tóc" với những lỗi y hệt vầy hồi mới học. **Bạn đang đi đúng hướng!** 💪🔥
