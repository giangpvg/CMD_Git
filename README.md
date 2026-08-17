# 🛠️ DevOps & Developer Command Cheatsheets

> 🌐 **Trang tra cứu trực tuyến (GitHub Pages)**: [https://giangpvg.github.io/CMD_Git](https://giangpvg.github.io/CMD_Git)

Bộ tài liệu tổng hợp và tra cứu nhanh các câu lệnh thông dụng hàng ngày dành cho Lập trình viên và DevOps Engineer, bao gồm các chủ đề về **Git & GitHub**, **Docker**, và **SSH / Quản Lý Server Remote**.

---

## 📚 Danh Mục Tra Cứu

Tài liệu được chia thành từng chủ đề riêng biệt với các định dạng: **Markdown (`.md`)** để đọc trên GitHub và **Web UI (`.html`)** để xem giao diện trực quan, tìm kiếm & sao chép nhanh trên trình duyệt.

| Chủ đề | Tài liệu Markdown | Giao diện Tra cứu (Online / Local) | Nội dung chính |
| :--- | :--- | :--- | :--- |
| **Git & GitHub** | [git_commands.md](./git_commands.md) | [🌐 Online](https://giangpvg.github.io/CMD_Git/index.html) / [index.html](./index.html) | Khởi tạo, Workflow, Quản lý nhánh (Branch), Tương tác Remote, Phục hồi (Undo/Reset), Stash |
| **Docker** | [docker_commands.md](./docker_commands.md) | [🌐 Online](https://giangpvg.github.io/CMD_Git/docker.html) / [docker.html](./docker.html) | Quản lý Container, Images, Docker Compose, Volumes, Network, Dọn dẹp hệ thống |
| **SSH & Remote Server** | [ssh_commands.md](./ssh_commands.md) | [🌐 Online](https://giangpvg.github.io/CMD_Git/ssh.html) / [ssh.html](./ssh.html) | Kết nối SSH, Quản lý SSH Key, Sao chép file (SCP/Rsync), Tmux/Screen, Tunneling & Port Forwarding |

---

## 🚀 Hướng Dẫn Sử Dụng

### 1. Xem Trực Tuyến Qua GitHub Pages (Khuyên Dùng)
Truy cập nhanh trang tra cứu với giao diện tìm kiếm & copy lệnh 1-click mà không cần tải code về máy:
👉 **[https://giangpvg.github.io/CMD_Git](https://giangpvg.github.io/CMD_Git)**

### 2. Đọc Trực Tiếp Trên GitHub Repository
Bạn có thể nhấp vào các liên kết file `.md` ở danh mục trên để xem danh sách câu lệnh kèm ví dụ và giải thích chi tiết dạng Markdown.

### 3. Chạy Giao Diện Web Trên Máy Cục Bộ (Offline)
- Tải/Clone kho lưu trữ về máy:
  ```bash
  git clone https://github.com/giangpvg/CMD_Git.git
  cd CMD_Git
  ```
- Mở file `index.html`, `docker.html`, hoặc `ssh.html` trực tiếp bằng trình duyệt web (Chrome, Firefox, Edge...).

---

## 📁 Cấu Trúc Thư Mục

```text
Cmd_git/
├── README.md             # Tài liệu giới thiệu tổng quan kho lưu trữ
├── git_commands.md       # Bảng tra cứu lệnh Git & GitHub (Markdown)
├── index.html            # Giao diện tra cứu lệnh Git trực quan (Web)
├── docker_commands.md     # Bảng tra cứu lệnh Docker (Markdown)
├── docker.html           # Giao diện tra cứu lệnh Docker trực quan (Web)
├── Docker.csv            # Dữ liệu bảng lệnh Docker
├── ssh_commands.md        # Bảng tra cứu lệnh SSH & Quản lý Server (Markdown)
└── ssh.html              # Giao diện tra cứu lệnh SSH trực quan (Web)
```

---

## 💡 Đóng Góp & Cập Nhật

Repository này liên tục được bổ sung các lệnh và thủ thuật mới. Nếu bạn muốn đóng góp thêm câu lệnh hoặc cải thiện tài liệu, vui lòng tạo **Pull Request** hoặc mở **Issue**.
