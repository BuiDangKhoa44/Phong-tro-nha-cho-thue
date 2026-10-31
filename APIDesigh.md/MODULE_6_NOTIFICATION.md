# MODULE 6: NOTIFICATION – QUẢN LÝ THÔNG BÁO

## Danh sách API

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách thông báo | GET | `/notifications` |
| Chi tiết thông báo | GET | `/notifications/{id}` |
| Tạo thông báo | POST | `/notifications` |
| Đánh dấu đã đọc | PATCH | `/notifications/{id}/read` |
| Đánh dấu tất cả đã đọc | PATCH | `/notifications/read-all` |
| Xóa thông báo | DELETE | `/notifications/{id}` |

### GET `/notifications?page=1&limit=10&isRead=false`
Response:
```json
{"success":true,"message":"Lấy danh sách thông báo thành công","data":{"items":[{"id":1,"title":"Hóa đơn phòng 101 đến hạn","content":"Hóa đơn tháng 10 cần thanh toán trước ngày 05/11","type":"INVOICE_DUE","isRead":false,"createdAt":"2026-10-31T08:00:00Z"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/notifications/{id}`
Response:
```json
{"success":true,"message":"Lấy thông tin thông báo thành công","data":{"id":1,"title":"Hóa đơn phòng 101 đến hạn","content":"Vui lòng kiểm tra hóa đơn tháng 10","type":"INVOICE_DUE","referenceId":1,"isRead":false}}
```

### POST `/notifications`
Request:
```json
{"recipientUserId":1,"title":"Hóa đơn phòng 101 đến hạn","content":"Vui lòng kiểm tra hóa đơn tháng 10","type":"INVOICE_DUE","referenceId":1}
```
Response:
```json
{"success":true,"message":"Tạo thông báo thành công","data":{"id":2,"recipientUserId":1,"title":"Hóa đơn phòng 101 đến hạn","isRead":false}}
```

### PATCH `/notifications/{id}/read`
Request Body: Không cần.
Response:
```json
{"success":true,"message":"Đã đánh dấu thông báo đã đọc","data":{"id":1,"isRead":true}}
```

### PATCH `/notifications/read-all`
Request Body: Không cần.
Response:
```json
{"success":true,"message":"Đã đánh dấu tất cả thông báo đã đọc","data":{"updatedCount":5}}
```

### DELETE `/notifications/{id}`
Response:
```json
{"success":true,"message":"Xóa thông báo thành công","data":null}
```

## Yêu cầu xử lý
- Người dùng chỉ xem thông báo của tài khoản mình, trừ người có quyền quản trị.
- Có thể tự động tạo thông báo khi hóa đơn đến hạn, hợp đồng sắp hết hạn hoặc có yêu cầu sửa chữa.
