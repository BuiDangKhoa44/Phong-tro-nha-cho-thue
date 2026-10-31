# MODULE 1: AUTHENTICATION – XÁC THỰC

Base URL: `/api/v1`. API cần đăng nhập dùng header `Authorization: Bearer <accessToken>`.

## Danh sách API

| Chức năng | Method | Endpoint |
|---|---|---|
| Đăng nhập | POST | `/auth/login` |
| Đăng xuất | POST | `/auth/logout` |
| Làm mới token | POST | `/auth/refresh` |
| Lấy tài khoản hiện tại | GET | `/auth/me` |
| Đổi mật khẩu | PATCH | `/auth/change-password` |

### POST `/auth/login`
Request:
```json
{"email":"owner@example.com","password":"ExamplePassword123"}
```
Response 200:
```json
{"success":true,"message":"Đăng nhập thành công","data":{"user":{"id":1,"fullName":"Nguyen Van A","email":"owner@example.com","role":"OWNER"},"accessToken":"<access-token>","refreshToken":"<refresh-token>","expiresIn":3600}}
```

### POST `/auth/logout`
Request:
```json
{"refreshToken":"<refresh-token>"}
```
Response 200:
```json
{"success":true,"message":"Đăng xuất thành công","data":null}
```

### POST `/auth/refresh`
Request:
```json
{"refreshToken":"<refresh-token>"}
```
Response 200:
```json
{"success":true,"message":"Làm mới token thành công","data":{"accessToken":"<new-access-token>","refreshToken":"<new-refresh-token>","expiresIn":3600}}
```

### GET `/auth/me`
Response 200:
```json
{"success":true,"message":"Lấy thông tin tài khoản thành công","data":{"id":1,"fullName":"Nguyen Van A","email":"owner@example.com","phone":"0900000000","role":"OWNER","status":"ACTIVE"}}
```

### PATCH `/auth/change-password`
Request:
```json
{"currentPassword":"OldPassword123","newPassword":"NewPassword123"}
```
Response 200:
```json
{"success":true,"message":"Đổi mật khẩu thành công","data":null}
```

## Yêu cầu xử lý
- Chỉ tài khoản ACTIVE được đăng nhập.
- Không trả mật khẩu hoặc password hash.
- Lưu mật khẩu dưới dạng hash an toàn.
- Thu hồi Refresh Token khi đăng xuất; kiểm tra hạn dùng và tính hợp lệ của token.
