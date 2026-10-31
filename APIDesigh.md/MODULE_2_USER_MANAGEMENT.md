# MODULE 2: USER MANAGEMENT – QUẢN LÝ NGƯỜI DÙNG

## Danh sách API

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách người dùng | GET | `/users` |
| Chi tiết người dùng | GET | `/users/{id}` |
| Tạo người dùng | POST | `/users` |
| Cập nhật người dùng | PUT | `/users/{id}` |
| Khóa/mở tài khoản | PATCH | `/users/{id}/status` |
| Xóa người dùng | DELETE | `/users/{id}` |

### GET `/users?page=1&limit=10&status=ACTIVE`
Response 200:
```json
{"success":true,"message":"Lấy danh sách người dùng thành công","data":{"items":[{"id":1,"fullName":"Nguyen Van A","email":"owner@example.com","phone":"0900000000","role":"OWNER","status":"ACTIVE"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/users/{id}`
Response 200:
```json
{"success":true,"message":"Lấy thông tin người dùng thành công","data":{"id":2,"fullName":"Tran Van B","email":"staff@example.com","phone":"0911111111","role":"STAFF","status":"ACTIVE"}}
```

### POST `/users`
Request:
```json
{"fullName":"Tran Van B","email":"staff@example.com","phone":"0911111111","password":"ExamplePassword123","role":"STAFF"}
```
Response 201:
```json
{"success":true,"message":"Tạo người dùng thành công","data":{"id":2,"fullName":"Tran Van B","email":"staff@example.com","phone":"0911111111","role":"STAFF","status":"ACTIVE"}}
```

### PUT `/users/{id}`
Request:
```json
{"fullName":"Tran Van B","phone":"0922222222","role":"STAFF"}
```
Response 200:
```json
{"success":true,"message":"Cập nhật người dùng thành công","data":{"id":2,"fullName":"Tran Van B","phone":"0922222222","role":"STAFF"}}
```

### PATCH `/users/{id}/status`
Request:
```json
{"status":"INACTIVE"}
```
Response 200:
```json
{"success":true,"message":"Cập nhật trạng thái thành công","data":{"id":2,"status":"INACTIVE"}}
```

### DELETE `/users/{id}`
Response 200:
```json
{"success":true,"message":"Xóa người dùng thành công","data":null}
```

## Yêu cầu xử lý
- Email phải duy nhất.
- Chỉ chủ nhà/người có quyền mới được quản lý tài khoản.
- Không trả mật khẩu trong response; ưu tiên khóa tài khoản thay vì xóa cứng.
