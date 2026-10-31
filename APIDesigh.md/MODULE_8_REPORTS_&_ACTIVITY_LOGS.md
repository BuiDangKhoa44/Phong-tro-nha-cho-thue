# MODULE 8: REPORTS & ACTIVITY LOGS – BÁO CÁO VÀ NHẬT KÝ

# 8.1 REPORTS – BÁO CÁO, THỐNG KÊ

| Chức năng | Method | Endpoint |
|---|---|---|
| Dashboard tổng quan | GET | `/reports/dashboard` |
| Doanh thu | GET | `/reports/revenue` |
| Tình trạng phòng | GET | `/reports/occupancy` |
| Công nợ | GET | `/reports/debts` |
| Hóa đơn | GET | `/reports/invoices` |
| Điện nước | GET | `/reports/utilities` |

### GET `/reports/dashboard?month=10&year=2026`
Response:
```json
{"success":true,"message":"Lấy thống kê tổng quan thành công","data":{"totalRooms":20,"availableRooms":5,"occupiedRooms":13,"maintenanceRooms":2,"totalTenants":15,"monthlyRevenue":39000000,"unpaidAmount":8500000,"totalInvoices":13,"paidInvoices":10,"unpaidInvoices":3}}
```

### GET `/reports/revenue?fromDate=2026-01-01&toDate=2026-10-31`
Response:
```json
{"success":true,"message":"Lấy báo cáo doanh thu thành công","data":{"totalRevenue":39000000,"fromDate":"2026-01-01","toDate":"2026-10-31","monthlyData":[{"month":"2026-09","revenue":35000000},{"month":"2026-10","revenue":39000000}]}}
```

### GET `/reports/occupancy`
Response:
```json
{"success":true,"message":"Lấy tình trạng phòng thành công","data":{"totalRooms":20,"availableRooms":5,"occupiedRooms":13,"maintenanceRooms":2,"occupancyRate":65}}
```

### GET `/reports/debts?month=10&year=2026`
Response:
```json
{"success":true,"message":"Lấy báo cáo công nợ thành công","data":{"totalDebt":8500000,"totalUnpaidInvoices":3,"items":[{"invoiceId":1,"invoiceCode":"HD202610101","roomCode":"P101","tenantName":"Nguyen Van C","totalAmount":3385000,"paidAmount":2000000,"remainingAmount":1385000,"status":"PARTIAL"}]}}
```

### GET `/reports/invoices?month=10&year=2026`
Response:
```json
{"success":true,"message":"Lấy báo cáo hóa đơn thành công","data":{"totalInvoices":13,"paidInvoices":10,"partialInvoices":1,"unpaidInvoices":2,"totalAmount":45000000,"paidAmount":36500000,"remainingAmount":8500000}}
```

### GET `/reports/utilities?month=10&year=2026`
Response:
```json
{"success":true,"message":"Lấy báo cáo điện nước thành công","data":{"period":"2026-10","totalElectricityUsed":2500,"totalWaterUsed":300,"totalElectricityAmount":6500000,"totalWaterAmount":1800000,"rooms":[{"roomCode":"P101","electricityUsed":120,"waterUsed":15,"electricityAmount":285000,"waterAmount":0}]}}
```

## Yêu cầu xử lý
- Hỗ trợ lọc theo tháng/năm hoặc khoảng ngày.
- Phân biệt doanh thu thực thu với tổng tiền hóa đơn đã lập.
- Không tính tiền cọc vào doanh thu tiền thuê.
- Công nợ bằng số tiền còn phải thanh toán.

# 8.2 ACTIVITY LOGS – NHẬT KÝ HOẠT ĐỘNG

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách nhật ký | GET | `/activity-logs` |
| Chi tiết nhật ký | GET | `/activity-logs/{id}` |
| Nhật ký theo người dùng | GET | `/users/{id}/activity-logs` |

### GET `/activity-logs?page=1&limit=10`
Response:
```json
{"success":true,"message":"Lấy danh sách nhật ký thành công","data":{"items":[{"id":1,"userId":1,"username":"admin","action":"CREATE","module":"ROOM","description":"Thêm phòng P103","createdAt":"2026-10-31T08:00:00Z"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/activity-logs/{id}`
Response:
```json
{"success":true,"message":"Lấy chi tiết nhật ký thành công","data":{"id":1,"userId":1,"username":"admin","action":"UPDATE","module":"ROOM","recordId":101,"description":"Cập nhật giá thuê phòng P101","oldValue":{"price":3000000},"newValue":{"price":3500000},"createdAt":"2026-10-31T08:00:00Z"}}
```

### GET `/users/{id}/activity-logs`
Response:
```json
{"success":true,"message":"Lấy nhật ký theo người dùng thành công","data":[{"id":1,"action":"CREATE","module":"ROOM","description":"Thêm phòng P103","createdAt":"2026-10-31T08:00:00Z"}]}
```

## Yêu cầu xử lý
- Tự động ghi lại người thực hiện, thời gian, module, hành động và bản ghi liên quan.
- Có thể lưu giá trị trước/sau khi cập nhật.
- Không cho phép người dùng thông thường sửa hoặc xóa nhật ký.
- Không ghi mật khẩu hoặc token vào log.
