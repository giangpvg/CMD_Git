# Bảng Lệnh Ubuntu & Linux System Administration

Tài liệu tra cứu các lệnh Ubuntu/Linux thông dụng: quản lý đĩa cứng, tiến trình, nén file, quyền truy cập, APT và systemd.

---

<details open>
  <summary><strong>1. Kiểm Tra Dung Lượng & Ổ Cứng (Disk Usage)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `df -h` | `df -h` | Xem tổng dung lượng đĩa trống / đã dùng của tất cả phân vùng ổ cứng. |
| `du -h --max-depth=1` | `sudo du -h --max-depth=1 /home/giangpv102/ \| sort -h` | Đếm dung lượng từng thư mục con cấp 1 và sắp xếp tăng dần để tìm thư mục nặng nhất. |
| `du -sh` | `du -sh /var/log` | Xem tổng dung lượng của một thư mục cụ thể dạng dễ đọc (GB, MB). |
| `lsblk` | `lsblk` | Liệt kê cấu trúc danh sách các ổ đĩa và phân vùng ổ cứng dạng cây. |

</details>

<details open>
  <summary><strong>2. Giám Sát Hệ Thống & Tiến Trình (System & Processes)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `htop` | `htop` | Giao diện trực quan giám sát phần trăm CPU, dung lượng RAM và tiến trình thời gian thực. |
| `free -h` | `free -h` | Kiểm tra dung lượng bộ nhớ RAM đang dùng, RAM trống và dung lượng Swap. |
| `ps aux \| grep` | `ps aux \| grep python` | Tìm kiếm thông tin tiến trình đang chạy theo tên dịch vụ hoặc từ khóa. |
| `kill -9` | `sudo kill -9 1234` | Ép buộc diệt (kill) ngay lập tức tiến trình treo dựa trên Process ID (PID). |
| `uptime` | `uptime` | Xem thời gian máy chủ đã bật liên tục và chỉ số nạp trung bình (load average). |

</details>

<details open>
  <summary><strong>3. Tìm Kiếm, Nén & Quản Lý File (Files & Archives)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `ls -la` | `ls -la` | Liệt kê tất cả file/thư mục (bao gồm file ẩn) kèm phân quyền chi tiết. |
| `find` | `find /var/log -name "*.log" -type f` | Tìm kiếm file theo đường dẫn, đuôi file tên hoặc kích thước. |
| `grep -rnw` | `grep -rnw '/path/to/dir/' -e 'pattern'` | Tìm từ khóa xuất hiện bên trong nội dung của tất cả file trong thư mục. |
| `tar -czvf` | `tar -czvf archive.tar.gz /path/to/folder` | Nén thư mục thành định dạng nén `.tar.gz`. |
| `tar -xzvf` | `tar -xzvf archive.tar.gz` | Giải nén file nén `.tar.gz`. |

</details>

<details open>
  <summary><strong>4. Phân Quyền & Người Dùng (Permissions & Ownership)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `chmod +x` | `chmod +x script.sh` | Cấp quyền thực thi (executable) cho file kịch bản Shell Script. |
| `chmod -R 755` | `chmod -R 755 /var/www/html` | Đặt quyền truy cập chuẩn 755 đệ quy cho thư mục web. |
| `chown -R` | `sudo chown -R www-data:www-data /var/www` | Thay đổi quyền sở hữu (User & Group) của file/thư mục. |

</details>

<details open>
  <summary><strong>5. Quản Lý Gói Phần Mềm APT (Package Manager)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `sudo apt update` | `sudo apt update && sudo apt upgrade -y` | Cập nhật danh sách phần mềm mới nhất và nâng cấp toàn bộ hệ thống. |
| `sudo apt install` | `sudo apt install -y htop curl git` | Cài đặt các phần mềm / gói công cụ mới vào hệ thống Ubuntu. |
| `sudo apt autoremove` | `sudo apt autoremove -y` | Dọn dẹp tự động các gói phụ thuộc cũ thừa không còn được dùng. |

</details>

<details open>
  <summary><strong>6. Quản Lý Dịch Vụ Systemd (Services & Systemctl)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `systemctl status` | `sudo systemctl status nginx` | Kiểm tra trạng thái đang chạy (Active) hay bị lỗi của dịch vụ systemd. |
| `systemctl restart` | `sudo systemctl restart nginx` | Khởi động lại một dịch vụ hệ thống sau khi thay đổi file cấu hình. |
| `journalctl -u` | `sudo journalctl -u nginx -f` | Xem log trực tiếp thời gian thực của dịch vụ hệ thống để gỡ lỗi. |

</details>
