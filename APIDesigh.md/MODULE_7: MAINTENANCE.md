# MODULE 7: MAINTENANCE – QUẢN LÝ SỬA CHỮA, BẢO TRÌ

Trạng thái: `PENDING`, `IN_PROGRESS`, `COMPLETED`, `CANCELLED`.

## Danh sách API

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách yêu cầu | GET | `/maintenance` |
| Chi tiết yêu cầu | GET | `/maintenance/{id}` |
| Tạo yêu cầu | POST | `/maintenance` |
| Cập nhật yêu cầu | PUT | `/maintenance/{id}` |
| Cập nhật trạng thái | PATCH | `/maintenance/{id}/status` |
| Xóa yêu cầu | DELETE | `/maintenance/{id}` |

### GET `/maintenance?page=1&limit=10&status=PENDING`
Response:
```json
{"success":true,"message":"Lấy danh sách sửa chữa thành công","data":{"items":[{"id":1,"roomId":101,"title":"Hỏng vòi nước","description":"Vòi nước bị rò rỉ","priority":"MEDIUM","status":"PENDING","createdAt":"2026-10-31T08:00:00Z"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/maintenance/{id}`
Response:
```json
{"success":true,"message":"Lấy chi tiết yêu cầu thành công","data":{"id":1,"roomId":101,"title":"Hỏng vòi nước","description":"Vòi nước bị rò rỉ","priority":"MEDIUM","status":"PENDING","estimatedCost":200000,"actualCost":null}}
```

### POST `/maintenance`
Request:
```json
{"roomId":101,"title":"Hỏng vòi nước","description":"Vòi nước trong nhà vệ sinh bị rò rỉ","priority":"MEDIUM","estimatedCost":200000}
```
Response:
```json
{"success":true,"message":"Tạo yêu cầu sửa chữa thành công","data":{"id":1,"roomId":101,"title":"Hỏng vòi nước","priority":"MEDIUM","status":"PENDING"}}
```

### PUT `/maintenance/{id}`
Request:
```json
{"title":"Thay vòi nước mới","description":"Thay mới vòi nước nhà vệ sinh","priority":"HIGH","estimatedCost":300000}
```
Response:
```json
{"success":true,"message":"Cập nhật yêu cầu thành công","data":{"id":1,"title":"Thay vòi nước mới","priority":"HIGH","estimatedCost":300000}}
```

### PATCH `/maintenance/{id}/status`
Request:
```json
{"status":"COMPLETED","actualCost":280000,"note":"Đã thay vòi nước mới"}
```
Response:
```json
{"success":true,"message":"Cập nhật trạng thái thành công","data":{"id":1,"status":"COMPLETED","actualCost":280000,"completedAt":"2026-11-01T08:00:00Z"}}
```

### DELETE `/maintenance/{id}`
Response:
```json
{"success":true,"message":"Xóa yêu cầu sửa chữa thành công","data":null}
```

## Yêu cầu xử lý
- Yêu cầu phải gắn với phòng tồn tại.
- Mức ưu tiên: `LOW`, `MEDIUM`, `HIGH`.
- Lưu ngày tạo, bắt đầu, hoàn thành và chi phí thực tế.
- Ưu tiên lưu lịch sử thay vì xóa cứng yêu cầu đã hoàn thành.
