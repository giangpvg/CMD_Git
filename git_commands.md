# Bảng Trực Quan Các Câu Lệnh Git & GitHub Cơ Bản

Tài liệu tra cứu nhanh các lệnh Git/GitHub được trình bày dưới dạng bảng gồm Cú pháp chung, Ví dụ thực tế và Giải thích ý nghĩa.

---

## 🛠️ 1. Khởi Tạo & Cấu Hình (Setup & Init)

| Cú pháp chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git config --global user.name` | `git config --global user.name "Nguyen Van A"` | Cấu hình tên người dùng trên máy |
| `git config --global user.email` | `git config --global user.email "a@example.com"` | Cấu hình email người dùng |
| `git init` | `git init` | Khởi tạo repository Git mới tại thư mục |
| `git clone` | `git clone https://github.com/user/repo.git` | Sao chép (clone) repository từ GitHub về máy |

---

## 📝 2. Thao Tác Cơ Bản (Basic Workflow)

| Cú pháp chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git status` | `git status` | Kiểm tra trạng thái các file (modified, staged, untracked) |
| `git add` | `git add main.py` | Thêm 1 file cụ thể vào Staging Area |
| `git add` | `git add .` | Thêm tất cả các file đã thay đổi vào Staging Area |
| `git commit -m` | `git commit -m "Initial commit"` | Lưu phiên bản (commit) kèm thông điệp mô tả |
| `git log` | `git log --oneline` | Xem lịch sử các lần commit dạng 1 dòng ngắn gọn |
| `git diff` | `git diff` | Xem chi tiết khác biệt của các file chưa add |

---

## 🌿 3. Quản Lý Nhánh (Branching & Merging)

| Cú pháp chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git branch` | `git branch` | Liệt kê tất cả các nhánh trong repository |
| `git branch` | `git branch feature-login` | Tạo một nhánh mới có tên `feature-login` |
| `git checkout` | `git checkout feature-login` | Chuyển sang làm việc ở nhánh `feature-login` |
| `git checkout -b` | `git checkout -b feature-login` | Tạo mới và chuyển sang nhánh `feature-login` ngay |
| `git switch -c` | `git switch -c feature-login` | (Cú pháp mới) Tạo và chuyển sang nhánh mới |
| `git merge` | `git merge feature-login` | Gộp nhánh `feature-login` vào nhánh hiện tại |
| `git branch -d` | `git branch -d feature-login` | Xóa nhánh `feature-login` sau khi đã gộp |

---

## 🚀 4. Tương Tác Với GitHub (Remote Operations)

| Cú pháp chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git remote add` | `git remote add origin https://github.com/user/repo.git` | Thêm liên kết kho chứa từ xa (remote) |
| `git remote -v` | `git remote -v` | Xem danh sách các URL kho chứa từ xa đã liên kết |
| `git push -u` | `git push -u origin main` | Đẩy code lên nhánh `main` ở GitHub (thiết lập mặc định) |
| `git push` | `git push` | Đẩy các commit mới nhất lên GitHub |
| `git pull` | `git pull origin main` | Tải dữ liệu mới nhất từ GitHub về và tự động gộp |
| `git fetch` | `git fetch` | Tải thông tin mới nhất từ GitHub về (chưa gộp) |

---

## 🔄 5. Hoàn Tác & Khôi Phục (Undo & Reset)

| Cú pháp chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git restore` | `git restore main.py` | Hủy bỏ thay đổi chưa add của file `main.py` |
| `git restore --staged` | `git restore --staged main.py` | Đưa file `main.py` từ Staging Area quay lại Unstaged |
| `git reset --soft` | `git reset --soft HEAD~1` | Hủy commit gần nhất nhưng vẫn giữ nguyên thay đổi file |
| `git reset --hard` | `git reset --hard HEAD~1` | Hủy hoàn toàn commit gần nhất và toàn bộ thay đổi file |
| `git revert` | `git revert a1b2c3d` | Tạo 1 commit mới để đảo ngược thay đổi của commit `a1b2c3d` |

---

## 📦 6. Lưu Tạm Thay Đổi (Stash)

| Cú pháp chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git stash` | `git stash` | Tạm thời cất giấu các thay đổi chưa commit |
| `git stash pop` | `git stash pop` | Lấy lại và áp dụng thay đổi đã cất giấu gần nhất |
| `git stash list` | `git stash list` | Xem danh sách tất cả các lần stash |
