# Monolithic Demo - Pickleball Tournament Management

Ứng dụng quản lý giải đấu Pickleball với chức năng đăng ký vận động viên và quản lý danh sách thi đấu.

## Tính năng

- Đăng ký/Đăng nhập người dùng
- Đăng ký vận động viên tham gia giải đấu
- Upload ảnh vận động viên
- Quản lý danh sách thi đấu (User/Admin)
- Phân quyền người dùng (User/BTC)

## Công nghệ sử dụng

- **Backend**: Node.js, Express.js
- **Database**: MySQL
- **Template Engine**: EJS
- **File Upload**: Multer
- **Session Management**: Express-session

## Cài đặt và chạy locally

1. Clone repository:
```bash
git clone <repository-url>
cd monolithic-demo
```

2. Cài đặt dependencies:
```bash
npm install
```

3. Tạo database MySQL:
```sql
CREATE DATABASE pickleball CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

4. Import database schema (nếu có file SQL)

5. Tạo file .env:
```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=pickleball
DB_PORT=3306
SESSION_SECRET=your_session_secret
```

6. Chạy ứng dụng:
```bash
npm start
```

Ứng dụng sẽ chạy tại: http://localhost:3000

## Deploy lên Railway

### Bước 1: Chuẩn bị
- Đảm bảo code đã được commit lên GitHub
- Có tài khoản Railway

### Bước 2: Tạo project trên Railway
1. Đăng nhập Railway Dashboard
2. Click "New Project"
3. Chọn "Deploy from GitHub repo"
4. Chọn repository của bạn

### Bước 3: Cấu hình Database
1. Trong project Railway, click "New"
2. Chọn "Database" → "MySQL"
3. Ghi nhớ thông tin kết nối

### Bước 4: Cấu hình Environment Variables
Trong project Railway, vào tab "Variables" và thêm:
```
DB_HOST=<mysql_host_from_railway>
DB_USER=<mysql_user_from_railway>
DB_PASSWORD=<mysql_password_from_railway>
DB_NAME=<mysql_database_from_railway>
DB_PORT=3306
SESSION_SECRET=<your_random_secret>
```

### Bước 5: Deploy
Railway sẽ tự động deploy khi có thay đổi trên GitHub.

## Cấu trúc Database

### Bảng `user`
- id (PRIMARY KEY)
- username
- password
- role (User/BTC)

### Bảng `registration`
- registration_id (PRIMARY KEY)
- envent_id
- leader_name
- leader_phone
- user_id (FOREIGN KEY)

### Bảng `players`
- id (PRIMARY KEY)
- registration_id (FOREIGN KEY)
- category
- full_name
- nick_name
- phone_number
- gender
- date_of_birth
- avatar_path

## API Endpoints

- `GET /` - Redirect to home
- `GET /home` - Trang chủ (cần đăng nhập)
- `GET /form` - Form đăng ký VĐV (cần đăng nhập)
- `GET /dstd_user` - Danh sách thi đấu (User)
- `GET /dstd_admin` - Danh sách thi đấu (Admin)
- `POST /api/add-player` - Thêm VĐV mới
- `POST /api/update-player` - Cập nhật VĐV
- `GET /api/tournament-data` - Lấy dữ liệu thi đấu (User)
- `GET /api/admin-tournament-data` - Lấy dữ liệu thi đấu (Admin)

## Tác giả

[Tran Huu Tin]
