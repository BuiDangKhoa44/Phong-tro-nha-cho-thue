# MODULE 3: ROOM – QUẢN LÝ PHÒNG TRỌ

## Danh sách API

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách phòng | GET | `/rooms` |
| Chi tiết phòng | GET | `/rooms/{id}` |
| Thêm phòng | POST | `/rooms` |
| Cập nhật phòng | PUT | `/rooms/{id}` |
| Cập nhật trạng thái | PATCH | `/rooms/{id}/status` |
| Cập nhật giá thuê | PATCH | `/rooms/{id}/price` |
| Xóa phòng | DELETE | `/rooms/{id}` |

### GET `/rooms?page=1&limit=10&status=AVAILABLE`
Response 200:
```json
{"success":true,"message":"Lấy danh sách phòng thành công","data":{"items":[{"id":101,"roomCode":"P101","floor":1,"area":25,"price":3000000,"status":"AVAILABLE","description":"Phòng có cửa sổ"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/rooms/{id}`
Response 200:
```json
{"success":true,"message":"Lấy thông tin phòng thành công","data":{"id":101,"roomCode":"P101","floor":1,"area":25,"price":3000000,"status":"AVAILABLE","description":"Phòng có cửa sổ"}}
```

### POST `/rooms`
Request:
```json
{"roomCode":"P102","floor":1,"area":30,"price":3500000,"description":"Phòng có ban công"}
```
Response 201:
```json
{"success":true,"message":"Thêm phòng thành công","data":{"id":102,"roomCode":"P102","floor":1,"area":30,"price":3500000,"status":"AVAILABLE"}}
```

### PUT `/rooms/{id}`
Request:
```json
{"floor":2,"area":30,"description":"Phòng tầng 2, có ban công"}
```
Response 200:
```json
{"success":true,"message":"Cập nhật phòng thành công","data":{"id":102,"roomCode":"P102","floor":2,"area":30,"description":"Phòng tầng 2, có ban công"}}
```

### PATCH `/rooms/{id}/status`
Request:
```json
{"status":"MAINTENANCE"}
```
Response 200:
```json
{"success":true,"message":"Cập nhật trạng thái phòng thành công","data":{"id":102,"status":"MAINTENANCE"}}
```

### PATCH `/rooms/{id}/price`
Request:
```json
{"price":3800000,"effectiveDate":"2026-11-01"}
```
Response 200:
```json
{"success":true,"message":"Cập nhật giá thuê thành công","data":{"id":102,"price":3800000,"effectiveDate":"2026-11-01"}}
```

### DELETE `/rooms/{id}`
Response 200:
```json
{"success":true,"message":"Xóa phòng thành công","data":null}
```

## Yêu cầu xử lý
- Mã phòng duy nhất; giá và diện tích không âm.
- Không xóa phòng đang có hợp đồng hiệu lực hoặc dữ liệu lịch sử cần lưu.
- Trạng thái phòng đồng bộ với hợp đồng và bảo trì; lưu lịch sử thay đổi giá.
