# MODULE 4: TENANT & CONTRACT – NGƯỜI THUÊ VÀ HỢP ĐỒNG

# A. TENANT – QUẢN LÝ NGƯỜI THUÊ

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách người thuê | GET | `/tenants` |
| Chi tiết người thuê | GET | `/tenants/{id}` |
| Thêm người thuê | POST | `/tenants` |
| Cập nhật người thuê | PUT | `/tenants/{id}` |
| Cập nhật trạng thái | PATCH | `/tenants/{id}/status` |
| Xóa người thuê | DELETE | `/tenants/{id}` |

### GET `/tenants?page=1&limit=10`
Response:
```json
{"success":true,"message":"Lấy danh sách người thuê thành công","data":{"items":[{"id":1,"fullName":"Nguyen Van C","phone":"0900000001","email":"tenant@example.com","identityNumber":"079000000000","status":"ACTIVE"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/tenants/{id}`
Response:
```json
{"success":true,"message":"Lấy thông tin người thuê thành công","data":{"id":1,"fullName":"Nguyen Van C","phone":"0900000001","email":"tenant@example.com","identityNumber":"079000000000","address":"Ho Chi Minh City","status":"ACTIVE"}}
```

### POST `/tenants`
Request:
```json
{"fullName":"Nguyen Van C","phone":"0900000001","email":"tenant@example.com","identityNumber":"079000000000","address":"Ho Chi Minh City"}
```
Response:
```json
{"success":true,"message":"Thêm người thuê thành công","data":{"id":1,"fullName":"Nguyen Van C","phone":"0900000001","status":"ACTIVE"}}
```

### PUT `/tenants/{id}`
Request:
```json
{"fullName":"Nguyen Van C","phone":"0900000002","email":"tenant-new@example.com","address":"Thu Duc"}
```
Response:
```json
{"success":true,"message":"Cập nhật người thuê thành công","data":{"id":1,"fullName":"Nguyen Van C","phone":"0900000002","email":"tenant-new@example.com"}}
```

### PATCH `/tenants/{id}/status`
Request:
```json
{"status":"INACTIVE"}
```
Response:
```json
{"success":true,"message":"Cập nhật trạng thái người thuê thành công","data":{"id":1,"status":"INACTIVE"}}
```

### DELETE `/tenants/{id}`
Response:
```json
{"success":true,"message":"Xóa người thuê thành công","data":null}
```

# B. CONTRACT – QUẢN LÝ HỢP ĐỒNG

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách hợp đồng | GET | `/contracts` |
| Chi tiết hợp đồng | GET | `/contracts/{id}` |
| Tạo hợp đồng | POST | `/contracts` |
| Cập nhật hợp đồng | PUT | `/contracts/{id}` |
| Chấm dứt hợp đồng | PATCH | `/contracts/{id}/terminate` |
| Hợp đồng theo phòng | GET | `/rooms/{id}/contracts` |
| Hợp đồng theo người thuê | GET | `/tenants/{id}/contracts` |

### GET `/contracts?page=1&limit=10&status=ACTIVE`
Response:
```json
{"success":true,"message":"Lấy danh sách hợp đồng thành công","data":{"items":[{"id":1,"contractCode":"HD-P101-001","roomId":101,"tenantId":1,"startDate":"2026-10-01","endDate":"2027-10-01","rentPrice":3000000,"status":"ACTIVE"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/contracts/{id}`
Response:
```json
{"success":true,"message":"Lấy chi tiết hợp đồng thành công","data":{"id":1,"contractCode":"HD-P101-001","roomId":101,"tenantId":1,"startDate":"2026-10-01","endDate":"2027-10-01","rentPrice":3000000,"billingCycle":"MONTHLY","depositAmount":3000000,"status":"ACTIVE","terms":"Thanh toán trước ngày 05 hằng tháng"}}
```

### POST `/contracts`
Request:
```json
{"roomId":101,"tenantId":1,"startDate":"2026-10-01","endDate":"2027-10-01","rentPrice":3000000,"billingCycle":"MONTHLY","depositAmount":3000000,"terms":"Thanh toán trước ngày 05 hằng tháng"}
```
Response:
```json
{"success":true,"message":"Tạo hợp đồng thành công","data":{"id":1,"contractCode":"HD-P101-001","roomId":101,"tenantId":1,"rentPrice":3000000,"status":"ACTIVE"}}
```

### PUT `/contracts/{id}`
Request:
```json
{"endDate":"2027-12-01","rentPrice":3200000,"terms":"Thanh toán trước ngày 05 hằng tháng"}
```
Response:
```json
{"success":true,"message":"Cập nhật hợp đồng thành công","data":{"id":1,"endDate":"2027-12-01","rentPrice":3200000,"status":"ACTIVE"}}
```

### PATCH `/contracts/{id}/terminate`
Request:
```json
{"terminationDate":"2027-10-01","reason":"Hai bên thống nhất kết thúc hợp đồng"}
```
Response:
```json
{"success":true,"message":"Chấm dứt hợp đồng thành công","data":{"id":1,"status":"TERMINATED","terminationDate":"2027-10-01"}}
```

### GET `/rooms/{id}/contracts`
Response:
```json
{"success":true,"message":"Lấy hợp đồng theo phòng thành công","data":[{"id":1,"contractCode":"HD-P101-001","tenantId":1,"startDate":"2026-10-01","endDate":"2027-10-01","status":"ACTIVE"}]}
```

### GET `/tenants/{id}/contracts`
Response:
```json
{"success":true,"message":"Lấy hợp đồng theo người thuê thành công","data":[{"id":1,"contractCode":"HD-P101-001","roomId":101,"startDate":"2026-10-01","endDate":"2027-10-01","status":"ACTIVE"}]}
```

## Yêu cầu xử lý
- Không tạo hợp đồng trùng thời gian cho cùng phòng nếu không hỗ trợ ở ghép.
- Ngày kết thúc sau ngày bắt đầu; giá thuê và tiền cọc không âm.
- Khi chấm dứt hợp đồng, cập nhật trạng thái phòng và giữ lịch sử hợp đồng.
