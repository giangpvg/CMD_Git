# Bảng Lệnh Git & GitHub Cơ Bản

Tài liệu tra cứu các lệnh Git & GitHub.

---

<details open>
  <summary><strong>1. Cấu Hình Ban Đầu & Khởi Tạo Dự Án</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git config --global` | `git config --global user.name "Nguyen Van A"` | Cấu hình tên người dùng trên máy local |
| `git config --global` | `git config --global user.email "a@example.com"` | Cấu hình email người dùng trên máy local |
| `git init` | `git init` | Khởi tạo kho chứa Git mới tại thư mục |
| `git clone` | `git clone https://github.com/user/repo.git` | Sao chép repository từ GitHub về máy local |

</details>

<details open>
  <summary><strong>2. Quy Trình Làm Việc Cơ Bản (Workflow)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git status` | `git status` | Kiểm tra trạng thái các file (Modified, Staged, Untracked) |
| `git add` | `git add app.py` | Thêm file `app.py` vào Staging Area |
| `git add .` | `git add .` | Thêm tất cả các file đã thay đổi vào Staging Area |
| `git commit -m` | `git commit -m "commit"` | Lưu phiên bản (commit) kèm thông điệp mô tả |
| `git commit -am` | `git commit -am "Add ssh cmd"` | Lệnh gộp vừa `git add` (tất cả file đã theo dõi) vừa `commit` nhanh |
| `git log` | `git log --oneline` | Xem lịch sử các lần commit dạng 1 dòng ngắn gọn |
| `git diff` | `git diff` | Xem chi tiết nội dung thay đổi chưa add |

</details>

<details open>
  <summary><strong>3. Quản Lý Nhánh (Branching & Merging)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git branch` | `git branch` | Xem danh sách các nhánh hiện có |
| `git branch` | `git branch dev` | Tạo nhánh mới có tên `dev` |
| `git checkout` | `git checkout main` | Chuyển sang làm việc ở nhánh `main` |
| `git checkout -b` | `git checkout -b dev` | Tạo nhánh mới tên `dev` và chuyển sang ngay |
| `git switch -c` | `git switch -c dev` | (Cú pháp mới) Tạo và chuyển sang nhánh `dev` |
| `git merge` | `git merge dev` | Gộp nhánh `dev` vào nhánh hiện tại |
| `git branch -d` | `git branch -d dev` | Xóa nhánh `dev` sau khi đã gộp |

</details>

<details open>
  <summary><strong>4. Tương Tác Với GitHub (Remote Operations)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git remote add` | `git remote add origin https://github.com/user/repo.git` | Liên kết kho chứa local với repository trên GitHub |
| `git remote -v` | `git remote -v` | Xem danh sách các kho chứa từ xa đã liên kết |
| `git push -u` | `git push -u origin main` | Đẩy code từ máy local lên kho chứa GitHub lần đầu |
| `git push` | `git push` | Đẩy các commit mới nhất lên GitHub |
| `git pull` | `git pull origin main` | Kéo dữ liệu mới nhất từ GitHub về máy và tự động gộp |
| `git fetch` | `git fetch` | Tải thông tin mới nhất từ GitHub về (chưa gộp) |

</details>

<details open>
  <summary><strong>5. Hoàn Tác & Phục Hồi (Undo & Reset)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git restore` | `git restore app.py` | Hủy bỏ các thay đổi chưa `add` của file `app.py` |
| `git restore --staged` | `git restore --staged app.py` | Đưa file `app.py` từ Staging Area về Unstaged |
| `git reset --soft` | `git reset --soft HEAD~1` | Hủy commit gần nhất nhưng vẫn giữ nguyên code thay đổi |
| `git reset --hard` | `git reset --hard HEAD~1` | Hủy hoàn toàn commit gần nhất và toàn bộ code thay đổi |
| `git revert` | `git revert a1b2c3d` | Tạo commit mới để đảo ngược thay đổi của commit `a1b2c3d` |

</details>

<details open>
  <summary><strong>6. Lưu Tạm Thay Đổi (Stash)</strong></summary>

| câu lệnh chung | Ví dụ | Ý nghĩa |
| :--- | :--- | :--- |
| `git stash` | `git stash` | Tạm thời cất giấu các thay đổi chưa commit |
| `git stash pop` | `git stash pop` | Lấy lại và áp dụng thay đổi đã cất giấu gần nhất |
| `git stash list` | `git stash list` | Xem danh sách tất cả các lần cất giấu (stash) |

</details>

---

## Khối Code Đẩy Dự Án Lên GitHub

```bash
# 1. Khởi tạo kho chứa cục bộ
git init

# 2. Thêm file vào Staging Area
git add app.py

# 3. Tạo commit
git commit -m "commit"

# 4. Đổi tên nhánh chính
git branch -M main

# 5. Liên kết với GitHub
git remote add origin https://github.com/USERNAME/REPOSITORY.git

# 6. Đẩy code lên GitHub
git push -u origin main
```
