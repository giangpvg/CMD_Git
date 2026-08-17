# Bảng Lệnh SSH & Remote Operations

Tài liệu tra cứu các lệnh SSH, quản lý Key, copy file từ xa (SCP/Rsync) và quản lý session.

---

<details open>
  <summary><strong>1. Kết Nối SSH Cơ Bản (Basic SSH Connection)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `ssh` | `ssh root@192.168.1.100` | Kết nối SSH tới server từ xa bằng tên người dùng và IP/domain. |
| `ssh -p` | `ssh -p 2222 root@192.168.1.100` | Kết nối SSH qua cổng (port) tùy chỉnh khác port 22 mặc định. |
| `ssh -i` | `ssh -i ~/.ssh/my_key.pem root@server` | Kết nối SSH sử dụng file khóa riêng tư (Private Key / PEM file). |
| `ssh -v` | `ssh -v root@192.168.1.100` | Chế độ Debug (Verbose) hiển thị chi tiết tiến trình kết nối để sửa lỗi. |
| `exit` | `exit` | Thoát khỏi phiên làm việc SSH từ xa và quay lại terminal local. |

</details>

<details open>
  <summary><strong>2. Quản Lý Khóa SSH & Xác Thực (SSH Keys & Auth)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `ssh-keygen -t rsa -b 4096` | `ssh-keygen -t rsa -b 4096 -C "email@example.com"` | Tạo cặp khóa SSH mới (RSA 4096 bit) kèm ghi chú email. |
| `ssh-keygen -t ed25519` | `ssh-keygen -t ed25519 -C "email@example.com"` | Tạo cặp khóa SSH Ed25519 hiện đại, vừa ngắn vừa bảo mật nhất. |
| `ssh-copy-id` | `ssh-copy-id root@192.168.1.100` | Tự động copy Public Key lên server để đăng nhập không cần gõ mật khẩu. |
| `ssh-add` | `ssh-add ~/.ssh/id_rsa` | Thêm SSH Private Key vào SSH Agent để quản lý xác thực tự động. |
| `ssh-add -l` | `ssh-add -l` | Liệt kê danh sách các SSH Key đang được nạp trong SSH Agent. |

</details>

<details open>
  <summary><strong>3. Truyền / Sao Chép File (SCP & rsync)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `scp` | `scp file.txt root@192.168.1.100:/var/www/` | Sao chép 1 file từ máy local lên server từ xa. |
| `scp` | `scp root@192.168.1.100:/var/log/app.log ./` | Tải 1 file từ server từ xa về máy local. |
| `scp -r` | `scp -r ./my_folder root@192.168.1.100:/var/www/` | Sao chép toàn bộ thư mục (recursive) lên server từ xa. |
| `rsync -avz` | `rsync -avz ./dist/ root@server:/var/www/html/` | Đồng bộ file/thư mục thông minh (chỉ truyền các file có thay đổi, nén dữ liệu). |
| `rsync -avz -e` | `rsync -avz -e "ssh -p 2222" ./dist/ root@server:/app/` | Đồng bộ file rsync qua SSH kết nối cổng (port) tùy chỉnh. |

</details>

<details open>
  <summary><strong>4. Cấu Hình SSH Config (~/.ssh/config)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `nano ~/.ssh/config` | `nano ~/.ssh/config` | Chỉnh sửa file cấu hình SSH local để tạo tên gọi tắt (alias) cho các server. |
| `ssh` | `ssh myserver` | Kết nối nhanh tới server bằng Alias rút gọn đã định nghĩa trong config. |

</details>

<details open>
  <summary><strong>5. Tunneling & Port Forwarding (Chuyển Hướng Cổng)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `ssh -L` | `ssh -L 8080:localhost:80 root@192.168.1.100` | Local Port Forwarding: Ánh xạ cổng server (port 80) về cổng máy local (8080). |
| `ssh -R` | `ssh -R 9000:localhost:3000 root@server` | Remote Port Forwarding: Ánh xạ dịch vụ máy local (port 3000) ra ngoài server. |
| `ssh -D` | `ssh -D 1080 root@192.168.1.100` | Dynamic Port Forwarding (Tạo SOCKS Proxy bảo mật qua SSH). |
| `ssh -N -f` | `ssh -N -f -L 8080:localhost:80 root@server` | Chạy SSH Tunnel dưới nền (Background mode) mà không mở giao diện terminal. |

</details>

<details open>
  <summary><strong>6. Quản Lý Tiến Trình Từ Xa (Remote Commands & Sessions)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `ssh` | `ssh root@192.168.1.100 "df -h"` | Thực thi trực tiếp 1 câu lệnh trên server từ xa rồi thoát ngay. |
| `nohup` | `nohup python3 app.py &` | Chạy chương trình dưới nền trên server ngay cả khi ngắt kết nối SSH. |
| `screen -S` | `screen -S mysession` | Tạo phiên làm việc Screen mới giữ tác vụ chạy ngầm độc lập. |
| `screen -r` | `screen -r mysession` | Quay trở lại phiên Screen đã tạo trước đó. |
| `tmux new -s` | `tmux new -s mysession` | Tạo phiên làm việc Tmux hiện đại chống ngắt kết nối SSH. |
| `tmux a -t` | `tmux a -t mysession` | Reattach kết nối lại vào phiên Tmux đang chạy. |

</details>
