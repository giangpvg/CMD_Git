# Bảng Lệnh Docker & Docker Compose Cơ Bản

Tài liệu tra cứu các lệnh Docker & Docker Compose.

---

<details open>
  <summary><strong>1. Docker Compose (Quản Lý Dự Án Đa Dịch Vụ)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `docker compose up -d` | `docker compose up -d` | Khởi chạy các container dưới nền (detached mode). Dùng khi muốn chạy nhanh dự án mà không cần thay đổi code/Dockerfile. |
| `docker compose up --build -d` | `docker compose up --build -d` | Build lại Image và chạy dưới nền. Dùng nhiều nhất khi vừa sửa code backend, Dockerfile hoặc requirements.txt. |
| `docker compose -f <path> --env-file <path> up -d` | `docker compose -f prod.yml --env-file .env.prod up -d` | Chạy docker compose với file cấu hình và file môi trường tùy chọn. |
| `docker compose down` | `docker compose down` | Dừng toàn bộ các container và xóa mạng nội bộ (network) vừa tạo để giải phóng RAM/CPU. |
| `docker compose down -v` | `docker compose down -v` | Dừng container và xóa sạch luôn toàn bộ volume dữ liệu đã mount (Cẩn thận mất DB local!). |
| `docker compose ps` | `docker compose ps` | Xem trạng thái các container trong dự án (kiểm tra container nào Up hay bị lỗi Exit/Restarting). |
| `docker compose logs -f` | `docker compose logs -f` | Xem logs (nhật ký chạy) thời gian thực của tất cả các dịch vụ trong dự án. |
| `docker compose logs -f <service_name>` | `docker compose logs -f orchestrator` | Xem logs thời gian thực của riêng một dịch vụ cụ thể. |
| `docker compose restart <service_name>` | `docker compose restart orchestrator` | Khởi động lại một dịch vụ cụ thể mà không làm ảnh hưởng tới các dịch vụ khác. |
| `docker compose exec <service_name> bash` | `docker compose exec orchestrator bash` | Đi vào bên trong shell của container đang chạy để debug, kiểm tra file trực tiếp. |

</details>

<details open>
  <summary><strong>2. Docker CLI Cơ Bản (Quản Lý Container Đơn Lẻ)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `docker ps` | `docker ps` | Liệt kê danh sách các container đang chạy trên toàn bộ hệ thống. |
| `docker ps -a` | `docker ps -a` | Liệt kê tất cả container trên máy (bao gồm cả container đang chạy lẫn đã dừng). |
| `docker run -d -p` | `docker run -d -p 8080:80 --name my-web nginx:alpine` | Tải và chạy một container mới từ Image trên Docker Hub. |
| `docker stop` | `docker stop deploy-orchestrator-1` | Dừng một container đang chạy. |
| `docker start` | `docker start deploy-orchestrator-1` | Khởi động lại một container đã bị dừng trước đó. |
| `docker rm` | `docker rm deploy-orchestrator-1` | Xóa một container đã dừng (giúp giải phóng tên container). |
| `docker rm -f` | `docker rm -f my-web` | Ép buộc dừng và xóa container ngay lập tức (kể cả đang chạy). |

</details>

<details open>
  <summary><strong>3. Quản Lý Docker Images & Volumes</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `docker images` | `docker images` | Hiển thị tất cả các Docker Images hiện có trên máy và kích thước của chúng. |
| `docker rmi` | `docker rmi nginx:alpine` | Xóa một image khỏi máy để giải phóng dung lượng ổ cứng. |
| `docker volume ls` | `docker volume ls` | Liệt kê tất cả các volume dữ liệu độc lập lưu trữ lâu dài. |
| `docker volume rm` | `docker volume rm my_db_data` | Xóa một volume dữ liệu cụ thể (chỉ dùng khi chắc chắn không dùng nữa). |

</details>

<details open>
  <summary><strong>4. Dọn Dẹp Hệ Thống (Giải Phong Dung Lượng Ổ Cứng)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `docker system prune` | `docker system prune` | Xóa các Container đã dừng, Network không dùng và các Image không tag (dangling). |
| `docker system prune -a` | `docker system prune -a` | Xóa sạch hơn (bao gồm cả các Image cũ không được container nào sử dụng). |
| `docker system prune -a --volumes` | `docker system prune -a --volumes` | Xóa cực kỳ sạch sẽ (Xóa cả Volume không dùng - Cẩn thận mất Database local!). |

</details>

<details open>
  <summary><strong>5. Gỡ Lỗi & Giám Sát Hệ Thống (Debugging & Stats)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `docker stats` | `docker stats` | Xem dung lượng RAM, phần trăm CPU và lưu lượng mạng thời gian thực của từng container. |
| `docker cp` | `docker cp container:/app/logs ./host_logs` | Copy file từ Container ra ngoài máy host hoặc ngược lại. |
| `docker inspect` | `docker inspect deploy-orchestrator-1` | Hiển thị chi tiết cấu hình JSON (mạng, IP, biến môi trường, mount volume). |

</details>

<details open>
  <summary><strong>6. Công Cụ Đồng Bộ MinIO (MinIO Client - mc)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa / Khi nào dùng? |
| :--- | :--- | :--- |
| `mc alias set` | `mc alias set serverA http://IP:9000 ACCESS_KEY SECRET_KEY` | Cấu hình thông tin kết nối và xác thực cho MinIO Server. |
| `mc mb` | `mc mb serverB/ten-bucket` | Tạo một bucket mới trên MinIO Server. |
| `mc mirror` | `mc mirror serverA/ten-bucket serverB/ten-bucket` | Đồng bộ dữ liệu từ bucket nguồn (serverA) sang bucket đích (serverB). |
| `mc mirror --overwrite --remove` | `mc mirror --overwrite --remove serverA/bucket serverB/bucket` | Đồng bộ chính xác 100% (bao gồm ghi đè file cũ và xóa file rác trên máy đích). |

</details>
