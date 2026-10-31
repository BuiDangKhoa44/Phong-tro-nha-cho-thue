# MODULE 5: RENTAL SERVICES & BILLING – DỊCH VỤ VÀ THANH TOÁN

Module gồm Service, Utility, Invoice và Deposit. Các ví dụ giá chỉ để minh họa.

# 5.1 SERVICE – QUẢN LÝ DỊCH VỤ

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách dịch vụ | GET | `/services` |
| Chi tiết dịch vụ | GET | `/services/{id}` |
| Thêm dịch vụ | POST | `/services` |
| Cập nhật dịch vụ | PUT | `/services/{id}` |
| Xóa dịch vụ | DELETE | `/services/{id}` |
| Dịch vụ theo phòng | GET | `/rooms/{id}/services` |
| Gán dịch vụ cho phòng | POST | `/rooms/{id}/services` |
| Cập nhật dịch vụ phòng | PUT | `/rooms/{id}/services/{serviceId}` |
| Gỡ dịch vụ khỏi phòng | DELETE | `/rooms/{id}/services/{serviceId}` |

### GET `/services?page=1&limit=10`
Response:
```json
{"success":true,"message":"OK","data":{"items":[{"id":1,"serviceName":"Internet","unit":"Tháng","price":100000,"billingType":"FIXED","status":"ACTIVE"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/services/{id}`
Response:
```json
{"success":true,"message":"OK","data":{"id":1,"serviceName":"Internet","unit":"Tháng","price":100000,"billingType":"FIXED","description":"Phí Internet","status":"ACTIVE"}}
```

### POST `/services`
Request:
```json
{"serviceName":"Internet","unit":"Tháng","price":100000,"billingType":"FIXED","description":"Phí Internet"}
```
Response:
```json
{"success":true,"message":"Thêm dịch vụ thành công","data":{"id":1,"serviceName":"Internet","price":100000,"status":"ACTIVE"}}
```

### PUT `/services/{id}`
Request:
```json
{"serviceName":"Internet","unit":"Tháng","price":120000,"billingType":"FIXED"}
```
Response:
```json
{"success":true,"message":"Cập nhật dịch vụ thành công","data":{"id":1,"serviceName":"Internet","price":120000,"status":"ACTIVE"}}
```

### DELETE `/services/{id}`
Response:
```json
{"success":true,"message":"Xóa dịch vụ thành công","data":null}
```

### GET `/rooms/{id}/services`
Response:
```json
{"success":true,"message":"OK","data":[{"serviceId":1,"serviceName":"Internet","price":100000,"unit":"Tháng","quantity":1}]}
```

### POST `/rooms/{id}/services`
Request:
```json
{"services":[{"serviceId":1,"quantity":1,"price":100000},{"serviceId":2,"quantity":2,"price":50000}]}
```
Response:
```json
{"success":true,"message":"Gán dịch vụ thành công","data":{"roomId":101,"services":[{"serviceId":1,"quantity":1,"price":100000},{"serviceId":2,"quantity":2,"price":50000}]}}
```

### PUT `/rooms/{id}/services/{serviceId}`
Request:
```json
{"quantity":2,"price":120000}
```
Response:
```json
{"success":true,"message":"Cập nhật dịch vụ phòng thành công","data":{"roomId":101,"serviceId":1,"quantity":2,"price":120000}}
```

### DELETE `/rooms/{id}/services/{serviceId}`
Response:
```json
{"success":true,"message":"Gỡ dịch vụ thành công","data":null}
```

# 5.2 UTILITY – QUẢN LÝ ĐIỆN NƯỚC

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách chỉ số | GET | `/meter-readings` |
| Chi tiết chỉ số | GET | `/meter-readings/{id}` |
| Nhập chỉ số | POST | `/meter-readings` |
| Cập nhật chỉ số | PUT | `/meter-readings/{id}` |
| Chỉ số theo phòng | GET | `/rooms/{id}/meter-readings` |
| Bảng giá điện nước | GET | `/utility-rates` |
| Thêm bảng giá | POST | `/utility-rates` |
| Cập nhật bảng giá | PUT | `/utility-rates/{id}` |

### GET `/meter-readings?roomId=101&period=2026-10`
Response:
```json
{"success":true,"message":"OK","data":[{"id":1,"roomId":101,"period":"2026-10","electricityOld":1000,"electricityNew":1150,"electricityUsed":150,"waterOld":200,"waterNew":215,"waterUsed":15}]}
```

### GET `/meter-readings/{id}`
Response:
```json
{"success":true,"message":"OK","data":{"id":1,"roomId":101,"period":"2026-10","electricityOld":1000,"electricityNew":1150,"electricityUsed":150,"waterOld":200,"waterNew":215,"waterUsed":15}}
```

### POST `/meter-readings`
Request:
```json
{"roomId":101,"period":"2026-10","electricityOld":1000,"electricityNew":1150,"waterOld":200,"waterNew":215}
```
Response:
```json
{"success":true,"message":"Nhập chỉ số thành công","data":{"id":1,"roomId":101,"period":"2026-10","electricityUsed":150,"waterUsed":15}}
```

### PUT `/meter-readings/{id}`
Request:
```json
{"electricityNew":1160,"waterNew":220}
```
Response:
```json
{"success":true,"message":"Cập nhật chỉ số thành công","data":{"id":1,"electricityUsed":160,"waterUsed":20}}
```

### GET `/rooms/{id}/meter-readings`
Response:
```json
{"success":true,"message":"OK","data":[{"period":"2026-10","electricityUsed":160,"waterUsed":20}]}
```

### GET `/utility-rates`
Response:
```json
{"success":true,"message":"OK","data":[{"id":1,"utilityType":"ELECTRICITY","pricingType":"PROGRESSIVE","unit":"kWh","effectiveDate":"2026-10-01","tiers":[{"from":0,"to":50,"price":2000},{"from":51,"to":100,"price":2500},{"from":101,"to":null,"price":3000}]}]}
```

### POST `/utility-rates`
Request:
```json
{"utilityType":"ELECTRICITY","pricingType":"PROGRESSIVE","unit":"kWh","effectiveDate":"2026-11-01","tiers":[{"from":0,"to":50,"price":2000},{"from":51,"to":100,"price":2500},{"from":101,"to":null,"price":3000}]}
```
Response:
```json
{"success":true,"message":"Tạo bảng giá thành công","data":{"id":2,"utilityType":"ELECTRICITY","effectiveDate":"2026-11-01","status":"ACTIVE"}}
```

### PUT `/utility-rates/{id}`
Request:
```json
{"effectiveDate":"2026-11-01","tiers":[{"from":0,"to":50,"price":2200},{"from":51,"to":100,"price":2600},{"from":101,"to":null,"price":3100}]}
```
Response:
```json
{"success":true,"message":"Cập nhật bảng giá thành công","data":{"id":2,"effectiveDate":"2026-11-01","status":"ACTIVE"}}
```

Tính lũy tiến ví dụ 120 kWh: `50×2.000 + 50×2.500 + 20×3.000 = 285.000đ`. Các bậc giá do chủ nhà cấu hình; chỉ số mới không được thấp hơn chỉ số cũ.

# 5.3 INVOICE – QUẢN LÝ HÓA ĐƠN

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách hóa đơn | GET | `/invoices` |
| Chi tiết hóa đơn | GET | `/invoices/{id}` |
| Tạo hóa đơn | POST | `/invoices` |
| Cập nhật hóa đơn | PUT | `/invoices/{id}` |
| Tính trước hóa đơn | POST | `/invoices/calculate` |
| Chi tiết khoản phí | GET | `/invoices/{id}/details` |
| Ghi nhận thanh toán | POST | `/invoices/{id}/payments` |
| Hóa đơn theo phòng | GET | `/rooms/{id}/invoices` |
| Hóa đơn theo người thuê | GET | `/tenants/{id}/invoices` |

### GET `/invoices?page=1&limit=10&status=UNPAID`
Response:
```json
{"success":true,"message":"OK","data":{"items":[{"id":1,"invoiceCode":"HD202610101","roomId":101,"tenantId":1,"period":"2026-10","totalAmount":3385000,"paidAmount":0,"remainingAmount":3385000,"status":"UNPAID","dueDate":"2026-11-05"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/invoices/{id}`
Response:
```json
{"success":true,"message":"OK","data":{"id":1,"invoiceCode":"HD202610101","roomId":101,"tenantId":1,"period":"2026-10","rentAmount":3000000,"electricityAmount":285000,"waterAmount":0,"serviceAmount":100000,"totalAmount":3385000,"paidAmount":0,"remainingAmount":3385000,"status":"UNPAID"}}
```

### POST `/invoices`
Request:
```json
{"roomId":101,"contractId":1,"period":"2026-10","dueDate":"2026-11-05","rentAmount":3000000,"electricityAmount":285000,"waterAmount":0,"serviceAmount":100000,"otherAmount":0}
```
Response:
```json
{"success":true,"message":"Tạo hóa đơn thành công","data":{"id":1,"invoiceCode":"HD202610101","totalAmount":3385000,"paidAmount":0,"remainingAmount":3385000,"status":"UNPAID"}}
```

### PUT `/invoices/{id}`
Request:
```json
{"dueDate":"2026-11-07","otherAmount":50000,"note":"Bổ sung khoản phí"}
```
Response:
```json
{"success":true,"message":"Cập nhật hóa đơn thành công","data":{"id":1,"totalAmount":3435000,"dueDate":"2026-11-07"}}
```

### POST `/invoices/calculate`
Request:
```json
{"roomId":101,"contractId":1,"period":"2026-10","electricityReadingId":1,"waterReadingId":1}
```
Response:
```json
{"success":true,"message":"Tính hóa đơn thành công","data":{"roomId":101,"period":"2026-10","rentAmount":3000000,"electricityAmount":285000,"waterAmount":0,"serviceAmount":100000,"totalAmount":3385000,"details":[{"name":"Tiền thuê phòng","amount":3000000},{"name":"Tiền điện","amount":285000},{"name":"Internet","amount":100000}]}}
```

### GET `/invoices/{id}/details`
Response:
```json
{"success":true,"message":"OK","data":[{"name":"Tiền thuê phòng","quantity":1,"unitPrice":3000000,"amount":3000000},{"name":"Tiền điện","quantity":120,"unitPrice":null,"amount":285000},{"name":"Internet","quantity":1,"unitPrice":100000,"amount":100000}]}
```

### POST `/invoices/{id}/payments`
Request:
```json
{"amount":2000000,"paymentMethod":"CASH","paymentDate":"2026-11-02","note":"Thanh toán lần 1"}
```
Response:
```json
{"success":true,"message":"Ghi nhận thanh toán thành công","data":{"paymentId":1,"invoiceId":1,"amount":2000000,"paidAmount":2000000,"remainingAmount":1385000,"status":"PARTIAL"}}
```

### GET `/rooms/{id}/invoices`
Response:
```json
{"success":true,"message":"OK","data":[{"id":1,"invoiceCode":"HD202610101","period":"2026-10","totalAmount":3385000,"status":"UNPAID"}]}
```

### GET `/tenants/{id}/invoices`
Response:
```json
{"success":true,"message":"OK","data":[{"id":1,"invoiceCode":"HD202610101","period":"2026-10","totalAmount":3385000,"status":"UNPAID"}]}
```

# 5.4 DEPOSIT – QUẢN LÝ TIỀN CỌC

| Chức năng | Method | Endpoint |
|---|---|---|
| Danh sách tiền cọc | GET | `/deposits` |
| Chi tiết tiền cọc | GET | `/deposits/{id}` |
| Ghi nhận tiền cọc | POST | `/deposits` |
| Cập nhật tiền cọc | PUT | `/deposits/{id}` |
| Hoàn trả tiền cọc | POST | `/deposits/{id}/refund` |
| Khấu trừ tiền cọc | POST | `/deposits/{id}/forfeit` |
| Tiền cọc theo hợp đồng | GET | `/contracts/{id}/deposit` |

### GET `/deposits?page=1&limit=10`
Response:
```json
{"success":true,"message":"OK","data":{"items":[{"id":1,"contractId":1,"tenantId":1,"amount":3000000,"status":"HELD","depositDate":"2026-10-01"}],"pagination":{"page":1,"limit":10,"total":1,"totalPages":1}}}
```

### GET `/deposits/{id}`
Response:
```json
{"success":true,"message":"OK","data":{"id":1,"contractId":1,"amount":3000000,"refundedAmount":0,"deductedAmount":0,"status":"HELD"}}
```

### POST `/deposits`
Request:
```json
{"contractId":1,"amount":3000000,"depositDate":"2026-10-01","paymentMethod":"CASH","note":"Tiền cọc khi ký hợp đồng"}
```
Response:
```json
{"success":true,"message":"Ghi nhận tiền cọc thành công","data":{"id":1,"contractId":1,"amount":3000000,"status":"HELD"}}
```

### PUT `/deposits/{id}`
Request:
```json
{"amount":3500000,"note":"Điều chỉnh theo thỏa thuận"}
```
Response:
```json
{"success":true,"message":"Cập nhật tiền cọc thành công","data":{"id":1,"amount":3500000,"status":"HELD"}}
```

### POST `/deposits/{id}/refund`
Request:
```json
{"amount":2500000,"refundDate":"2027-10-01","paymentMethod":"BANK_TRANSFER","note":"Hoàn cọc khi kết thúc hợp đồng"}
```
Response:
```json
{"success":true,"message":"Hoàn trả tiền cọc thành công","data":{"depositId":1,"originalAmount":3000000,"refundedAmount":2500000,"deductedAmount":500000,"remainingAmount":0,"status":"PARTIALLY_REFUNDED"}}
```

### POST `/deposits/{id}/forfeit`
Request:
```json
{"amount":500000,"reason":"Khấu trừ theo thỏa thuận","deductionDate":"2027-10-01"}
```
Response:
```json
{"success":true,"message":"Ghi nhận khấu trừ thành công","data":{"depositId":1,"amount":500000,"reason":"Khấu trừ theo thỏa thuận"}}
```

### GET `/contracts/{id}/deposit`
Response:
```json
{"success":true,"message":"OK","data":{"id":1,"contractId":1,"amount":3000000,"refundedAmount":0,"deductedAmount":0,"status":"HELD"}}
```

## Quy tắc chung
- Không hoàn hoặc khấu trừ vượt số dư tiền cọc.
- Lưu lịch sử thanh toán, hoàn cọc, khấu trừ và lý do.
- Hóa đơn phải lưu giá trị tại thời điểm lập; không bị thay đổi khi bảng giá hiện tại thay đổi.
