# USER STORIES -- HỆ THỐNG QUẢN LÝ PHÒNG TRỌ / NHÀ CHO THUÊ

> **Nguồn phân tích:** Tài liệu Actors & Use Cases của hệ thống.\
> **Mục đích:** Chuyển yêu cầu nghiệp vụ thành User Stories có thể đưa
> vào Sprint và dùng làm cơ sở thiết kế API, database, giao diện và kiểm
> thử.\
> **Vai trò BA:** Phân rã yêu cầu theo Actor → Epic → User Story →
> Acceptance Criteria.

------------------------------------------------------------------------

# 1. Quy ước User Story

Cấu trúc chuẩn:

> **Là một \[Actor\], tôi muốn \[chức năng\], để \[giá trị/mục tiêu\].**

Mỗi User Story có:

-   **ID:** Mã duy nhất.
-   **Epic:** Nhóm nghiệp vụ.
-   **Priority:** `Must` / `Should` / `Could`.
-   **Story Point:** Ước lượng tương đối `1, 2, 3, 5, 8`.
-   **User Story:** Nhu cầu của người dùng.
-   **Acceptance Criteria:** Điều kiện để Story được xem là hoàn thành.
-   **Dependencies:** Phụ thuộc vào Story khác nếu có.
-   **Gợi ý code:** Thành phần Frontend/Backend/Database cần chuẩn bị.

------------------------------------------------------------------------

# 2. Actors

  -----------------------------------------------------------------------
  Mã                      Actor                   Vai trò
  ----------------------- ----------------------- -----------------------
  A01                     Chủ nhà                 Quản lý nhà, phòng,
                                                  khách thuê, hợp đồng,
                                                  hóa đơn, thanh toán,
                                                  sửa chữa và báo cáo

  A02                     Nhân viên               Thực hiện nghiệp vụ
                                                  được chủ nhà phân quyền

  A03                     Khách thuê              Xem thông tin thuê, hóa
                                                  đơn, thanh toán và gửi
                                                  yêu cầu sửa chữa

  A04                     Quản trị viên           Quản lý tài khoản, vai
                                                  trò và cấu hình hệ
                                                  thống

  A05                     Cổng thanh toán         Xử lý giao dịch thanh
                                                  toán trực tuyến

  A06                     Email/SMS/Push Service  Gửi thông báo cho người
                                                  dùng
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 3. Product Backlog tổng quan

  ID       Epic              User Story                       Priority     SP
  -------- ----------------- -------------------------------- ---------- ----
  US-001   Authentication    Đăng nhập                        Must          3
  US-002   Authentication    Đăng xuất                        Must          1
  US-003   Authentication    Đăng ký tài khoản khách thuê     Must          3
  US-004   Profile           Quản lý hồ sơ cá nhân            Must          3
  US-005   User Management   Quản lý tài khoản                Should        5
  US-006   Authorization     Phân quyền                       Must          5
  US-007   Property          Thêm nhà/khu trọ                 Must          3
  US-008   Property          Cập nhật nhà/khu trọ             Must          2
  US-009   Property          Xem danh sách nhà/khu trọ        Must          2
  US-010   Property          Ngừng hoạt động nhà/khu trọ      Should        2
  US-011   Room              Thêm phòng                       Must          3
  US-012   Room              Cập nhật phòng                   Must          3
  US-013   Room              Xem danh sách phòng              Must          3
  US-014   Room              Xem chi tiết phòng               Must          2
  US-015   Room              Cập nhật trạng thái phòng        Must          3
  US-016   Room              Tìm kiếm/lọc phòng               Must          3
  US-017   Tenant            Thêm khách thuê                  Must          3
  US-018   Tenant            Cập nhật khách thuê              Must          3
  US-019   Tenant            Xem hồ sơ khách thuê             Must          2
  US-020   Tenant            Tìm kiếm khách thuê              Should        2
  US-021   Tenant            Xem lịch sử thuê                 Should        3
  US-022   Contract          Tạo hợp đồng                     Must          5
  US-023   Contract          Xem hợp đồng                     Must          2
  US-024   Contract          Cập nhật hợp đồng                Must          3
  US-025   Contract          Gia hạn hợp đồng                 Should        3
  US-026   Contract          Chấm dứt hợp đồng                Must          5
  US-027   Contract          Theo dõi hợp đồng sắp hết hạn    Should        3
  US-028   Utility           Khai báo dịch vụ                 Should        3
  US-029   Utility           Cấu hình đơn giá điện            Must          3
  US-030   Utility           Cấu hình đơn giá nước            Must          3
  US-031   Utility           Nhập chỉ số điện                 Must          3
  US-032   Utility           Nhập chỉ số nước                 Must          3
  US-033   Utility           Tính tiền điện                   Must          3
  US-034   Utility           Tính tiền nước                   Must          3
  US-035   Invoice           Tạo hóa đơn                      Must          5
  US-036   Invoice           Tính tổng hóa đơn                Must          3
  US-037   Invoice           Xem hóa đơn                      Must          2
  US-038   Invoice           Cập nhật hóa đơn                 Should        3
  US-039   Notification      Gửi thông báo hóa đơn            Should        3
  US-040   Payment           Ghi nhận thanh toán              Must          3
  US-041   Payment           Thanh toán trực tuyến            Could         8
  US-042   Payment           Cập nhật trạng thái thanh toán   Must          3
  US-043   Payment           Xem lịch sử thanh toán           Must          2
  US-044   Maintenance       Gửi yêu cầu sửa chữa             Must          3
  US-045   Maintenance       Tiếp nhận yêu cầu                Must          2
  US-046   Maintenance       Phân công sửa chữa               Should        3
  US-047   Maintenance       Cập nhật trạng thái sửa chữa     Must          3
  US-048   Maintenance       Theo dõi yêu cầu sửa chữa        Must          2
  US-049   Notification      Tạo thông báo                    Should        3
  US-050   Notification      Xem thông báo                    Must          2
  US-051   Notification      Đánh dấu đã đọc                  Should        1
  US-052   Dashboard         Xem dashboard                    Must          5
  US-053   Report            Báo cáo doanh thu                Should        5
  US-054   Report            Báo cáo công nợ                  Should        5
  US-055   Report            Báo cáo tình trạng phòng         Should        3
  US-056   Report            Báo cáo khách thuê               Could         3

------------------------------------------------------------------------

# 4. Epic E01 -- Authentication & Profile

## US-001 -- Đăng nhập

**As:** Chủ nhà / Nhân viên / Khách thuê / Admin\
**I want:** Đăng nhập bằng tài khoản và mật khẩu\
**So that:** Tôi có thể truy cập các chức năng phù hợp với quyền của
mình.

**Priority:** Must\
**Story Point:** 3

### Acceptance Criteria

-   [ ] Người dùng nhập username/email và password.
-   [ ] Hệ thống kiểm tra tài khoản tồn tại.
-   [ ] Hệ thống kiểm tra mật khẩu hợp lệ.
-   [ ] Tài khoản bị khóa không được đăng nhập.
-   [ ] Đăng nhập thành công trả về thông tin người dùng và role.
-   [ ] Người dùng được chuyển đến dashboard phù hợp.
-   [ ] Sai thông tin đăng nhập phải có thông báo lỗi.

**Gợi ý code:** - Frontend: `LoginPage`, `AuthContext`, protected
route. - Backend: `POST /api/auth/login`. - Database: `users`, `roles`.

------------------------------------------------------------------------

## US-002 -- Đăng xuất

**As:** Người dùng đã đăng nhập\
**I want:** Đăng xuất\
**So that:** Phiên làm việc được kết thúc an toàn.

**Priority:** Must\
**SP:** 1

### Acceptance Criteria

-   [ ] Click Logout sẽ xóa token/session phía client.
-   [ ] Không thể truy cập route yêu cầu đăng nhập sau khi logout.
-   [ ] Chuyển về trang Login.

**API đề xuất:** `POST /api/auth/logout`.

------------------------------------------------------------------------

## US-003 -- Đăng ký tài khoản khách thuê

**As:** Khách thuê\
**I want:** Đăng ký tài khoản\
**So that:** Tôi có thể sử dụng hệ thống.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Nhập họ tên, email/số điện thoại, mật khẩu.
-   [ ] Email/số điện thoại không được trùng.
-   [ ] Password phải đáp ứng chính sách bảo mật.
-   [ ] Đăng ký thành công tạo user với role Tenant.
-   [ ] Không cho phép người dùng tự đăng ký role Owner/Admin.

------------------------------------------------------------------------

## US-004 -- Quản lý hồ sơ cá nhân

**As:** Người dùng\
**I want:** Xem và cập nhật hồ sơ cá nhân\
**So that:** Thông tin của tôi luôn chính xác.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Xem thông tin hiện tại.
-   [ ] Sửa họ tên, điện thoại, email theo quyền.
-   [ ] Đổi mật khẩu.
-   [ ] Validate dữ liệu đầu vào.
-   [ ] Lưu thành công hiển thị thông tin mới.

------------------------------------------------------------------------

# 5. Epic E02 -- User Management & Authorization

## US-005 -- Quản lý tài khoản

**As:** Admin\
**I want:** Xem, tạo, sửa, khóa/mở khóa tài khoản\
**So that:** Tôi có thể quản lý người dùng hệ thống.

**Priority:** Should\
**SP:** 5

### Acceptance Criteria

-   [ ] Xem danh sách tài khoản.
-   [ ] Tìm kiếm tài khoản.
-   [ ] Tạo tài khoản.
-   [ ] Cập nhật tài khoản.
-   [ ] Khóa/mở khóa.
-   [ ] Không cho phép thao tác nếu không có quyền Admin.

------------------------------------------------------------------------

## US-006 -- Phân quyền

**As:** Admin\
**I want:** Gán role/quyền cho người dùng\
**So that:** Mỗi người chỉ sử dụng được chức năng được phép.

**Priority:** Must\
**SP:** 5

### Acceptance Criteria

-   [ ] Có các role cơ bản: Admin, Owner, Staff, Tenant.
-   [ ] API kiểm tra authorization, không chỉ ẩn nút trên frontend.
-   [ ] Owner/Staff/Tenant không thể truy cập API Admin.
-   [ ] Staff chỉ được thực hiện chức năng được cấp.

------------------------------------------------------------------------

# 6. Epic E03 -- Property Management

## US-007 -- Thêm nhà/khu trọ

**As:** Chủ nhà\
**I want:** Thêm một nhà/khu trọ\
**So that:** Tôi có thể quản lý các bất động sản cho thuê.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Nhập tên, địa chỉ, mô tả, thông tin liên hệ.
-   [ ] Validate trường bắt buộc.
-   [ ] Nhà được gắn với Owner hiện tại.
-   [ ] Lưu thành công hiển thị trong danh sách.

------------------------------------------------------------------------

## US-008 -- Cập nhật nhà/khu trọ

**As:** Chủ nhà\
**I want:** Chỉnh sửa thông tin nhà\
**So that:** Dữ liệu quản lý luôn chính xác.

**Priority:** Must\
**SP:** 2

### Acceptance Criteria

-   [ ] Chỉ Owner có quyền quản lý nhà đó mới được sửa.
-   [ ] Validate dữ liệu.
-   [ ] Lưu và hiển thị dữ liệu mới.

------------------------------------------------------------------------

## US-009 -- Xem danh sách nhà/khu trọ

**As:** Chủ nhà/Nhân viên\
**I want:** Xem danh sách nhà\
**So that:** Tôi có thể quản lý nhiều địa điểm.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

## US-010 -- Ngừng hoạt động nhà/khu trọ

**As:** Chủ nhà\
**I want:** Ngừng quản lý một nhà\
**So that:** Tôi giữ được lịch sử dữ liệu nhưng không cho phát sinh
nghiệp vụ mới.

**Priority:** Should\
**SP:** 2

### Acceptance Criteria

-   [ ] Không xóa vật lý nhà đã có dữ liệu nghiệp vụ.
-   [ ] Chuyển trạng thái sang Inactive.
-   [ ] Không tạo phòng/hợp đồng mới cho nhà inactive.
-   [ ] Lịch sử hợp đồng/hóa đơn vẫn được giữ.

------------------------------------------------------------------------

# 7. Epic E04 -- Room Management

## US-011 -- Thêm phòng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Thêm phòng vào nhà\
**So that:** Hệ thống có thể quản lý phòng cho thuê.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Chọn nhà/khu trọ.
-   [ ] Nhập mã/số phòng.
-   [ ] Nhập diện tích.
-   [ ] Nhập giá thuê.
-   [ ] Trạng thái mặc định là Trống.
-   [ ] Không cho phép trùng mã phòng trong cùng nhà.

------------------------------------------------------------------------

## US-012 -- Cập nhật phòng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Sửa thông tin phòng\
**So that:** Thông tin phòng chính xác.

**Priority:** Must\
**SP:** 3

------------------------------------------------------------------------

## US-013 -- Xem danh sách phòng

**As:** Chủ nhà/Nhân viên/Khách thuê\
**I want:** Xem danh sách phòng\
**So that:** Tôi biết tình trạng phòng.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Hiển thị số phòng, giá, diện tích, trạng thái.
-   [ ] Owner/Staff xem phòng thuộc phạm vi được cấp quyền.
-   [ ] Tenant chỉ xem thông tin được phép.

------------------------------------------------------------------------

## US-014 -- Xem chi tiết phòng

**As:** Người dùng có quyền\
**I want:** Xem chi tiết phòng\
**So that:** Tôi có đầy đủ thông tin trước khi thực hiện nghiệp vụ.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

## US-015 -- Cập nhật trạng thái phòng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Thay đổi trạng thái phòng\
**So that:** Trạng thái phòng phản ánh đúng thực tế.

**Priority:** Must\
**SP:** 3

### Trạng thái

`AVAILABLE → RESERVED → RENTED → MAINTENANCE → AVAILABLE`

Ngoài ra có `INACTIVE`.

### Acceptance Criteria

-   [ ] Không cho chuyển trạng thái trái quy tắc nghiệp vụ.
-   [ ] Phòng có hợp đồng đang hiệu lực không được chuyển thành
    Available tùy ý.
-   [ ] Khi hợp đồng kết thúc và hoàn tất trả phòng, phòng có thể chuyển
    Available.

------------------------------------------------------------------------

## US-016 -- Tìm kiếm/lọc phòng

**As:** Người dùng\
**I want:** Tìm kiếm và lọc phòng\
**So that:** Tôi nhanh chóng tìm được phòng phù hợp.

**Priority:** Must\
**SP:** 3

**Bộ lọc:** số phòng, giá, diện tích, trạng thái, nhà/khu trọ.

------------------------------------------------------------------------

# 8. Epic E05 -- Tenant Management

## US-017 -- Thêm khách thuê

**As:** Chủ nhà/Nhân viên\
**I want:** Tạo hồ sơ khách thuê\
**So that:** Tôi có thể lập hợp đồng và quản lý người thuê.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Nhập họ tên, điện thoại, email, giấy tờ tùy thân.
-   [ ] Kiểm tra dữ liệu bắt buộc.
-   [ ] Có thể liên kết khách thuê với tài khoản Tenant.
-   [ ] Không tạo hồ sơ trùng theo quy tắc định danh được thống nhất.

------------------------------------------------------------------------

## US-018 -- Cập nhật khách thuê

**As:** Chủ nhà/Nhân viên\
**I want:** Cập nhật hồ sơ khách thuê\
**So that:** Thông tin luôn chính xác.

**Priority:** Must\
**SP:** 3

------------------------------------------------------------------------

## US-019 -- Xem hồ sơ khách thuê

**As:** Chủ nhà/Nhân viên\
**I want:** Xem hồ sơ khách thuê\
**So that:** Tôi có thông tin phục vụ quản lý.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

## US-020 -- Tìm kiếm khách thuê

**As:** Chủ nhà/Nhân viên\
**I want:** Tìm khách thuê theo thông tin\
**So that:** Tôi nhanh chóng tìm được hồ sơ.

**Priority:** Should\
**SP:** 2

------------------------------------------------------------------------

## US-021 -- Xem lịch sử thuê

**As:** Chủ nhà/Nhân viên\
**I want:** Xem lịch sử thuê của khách\
**So that:** Tôi biết các lần thuê trước đây.

**Priority:** Should\
**SP:** 3

------------------------------------------------------------------------

# 9. Epic E06 -- Contract Management

## US-022 -- Tạo hợp đồng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Tạo hợp đồng cho khách thuê\
**So that:** Việc thuê phòng được quản lý chính thức.

**Priority:** Must\
**SP:** 5

### Acceptance Criteria

-   [ ] Chọn phòng.
-   [ ] Chọn khách thuê.
-   [ ] Nhập ngày bắt đầu/kết thúc.
-   [ ] Nhập giá thuê.
-   [ ] Nhập tiền cọc.
-   [ ] Chọn dịch vụ.
-   [ ] Kiểm tra phòng còn khả dụng.
-   [ ] Không tạo hai hợp đồng active cho cùng một phòng.
-   [ ] Tạo thành công cập nhật phòng thành RENTED.

------------------------------------------------------------------------

## US-023 -- Xem hợp đồng

**As:** Owner/Staff/Tenant\
**I want:** Xem hợp đồng\
**So that:** Tôi có thể kiểm tra thông tin thuê.

**Priority:** Must\
**SP:** 2

### Acceptance Criteria

-   [ ] Owner/Staff xem hợp đồng thuộc phạm vi được cấp.
-   [ ] Tenant chỉ xem hợp đồng của chính mình.
-   [ ] Không được xem dữ liệu người thuê khác.

------------------------------------------------------------------------

## US-024 -- Cập nhật hợp đồng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Cập nhật hợp đồng\
**So that:** Các thông tin được điều chỉnh đúng thực tế.

**Priority:** Must\
**SP:** 3

------------------------------------------------------------------------

## US-025 -- Gia hạn hợp đồng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Gia hạn hợp đồng\
**So that:** Khách có thể tiếp tục thuê mà không tạo lại toàn bộ hồ sơ.

**Priority:** Should\
**SP:** 3

------------------------------------------------------------------------

## US-026 -- Chấm dứt hợp đồng

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Chấm dứt hợp đồng\
**So that:** Hệ thống ghi nhận việc kết thúc thuê.

**Priority:** Must\
**SP:** 5

### Acceptance Criteria

-   [ ] Nhập ngày chấm dứt và lý do.
-   [ ] Kiểm tra các khoản còn nợ.
-   [ ] Ghi nhận trạng thái TERMINATED.
-   [ ] Không xóa lịch sử hợp đồng.
-   [ ] Phòng có thể chuyển AVAILABLE sau khi hoàn tất quy trình trả
    phòng.

------------------------------------------------------------------------

## US-027 -- Theo dõi hợp đồng sắp hết hạn

**As:** Chủ nhà/Nhân viên\
**I want:** Xem danh sách hợp đồng sắp hết hạn\
**So that:** Tôi chủ động liên hệ khách thuê.

**Priority:** Should\
**SP:** 3

------------------------------------------------------------------------

# 10. Epic E07 -- Utilities

## US-028 -- Khai báo dịch vụ

**As:** Chủ nhà\
**I want:** Tạo các loại dịch vụ\
**So that:** Hệ thống có thể tính phí dịch vụ.

**Priority:** Should\
**SP:** 3

**Ví dụ:** Internet, rác, gửi xe, phí quản lý.

------------------------------------------------------------------------

## US-029 -- Cấu hình đơn giá điện

**As:** Chủ nhà\
**I want:** Thiết lập đơn giá điện\
**So that:** Hệ thống tính tiền điện chính xác.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Có đơn giá và thời điểm áp dụng.
-   [ ] Không áp dụng nhầm đơn giá cho kỳ cũ.
-   [ ] Lưu lịch sử thay đổi đơn giá.

------------------------------------------------------------------------

## US-030 -- Cấu hình đơn giá nước

Tương tự US-029 cho tiền nước.

**Priority:** Must\
**SP:** 3

------------------------------------------------------------------------

## US-031 -- Nhập chỉ số điện

**As:** Chủ nhà/Nhân viên\
**I want:** Nhập chỉ số điện theo kỳ\
**So that:** Hệ thống xác định lượng điện tiêu thụ.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Chọn phòng và kỳ ghi.
-   [ ] Nhập chỉ số mới.
-   [ ] Chỉ số mới không nhỏ hơn chỉ số kỳ trước.
-   [ ] Không tạo trùng bản ghi cho cùng phòng/kỳ.
-   [ ] Tính được sản lượng tiêu thụ.

------------------------------------------------------------------------

## US-032 -- Nhập chỉ số nước

Tương tự US-031 cho nước.

**Priority:** Must\
**SP:** 3

------------------------------------------------------------------------

## US-033 -- Tính tiền điện

**As:** Hệ thống\
**I want:** Tính tiền điện dựa trên chỉ số và đơn giá\
**So that:** Hóa đơn có tiền điện chính xác.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

`Sản lượng = Chỉ số mới - Chỉ số cũ`

`Tiền điện = Sản lượng × Đơn giá`

-   [ ] Không cho kết quả sản lượng âm.
-   [ ] Dùng đúng đơn giá có hiệu lực tại kỳ tính.

------------------------------------------------------------------------

## US-034 -- Tính tiền nước

**As:** Hệ thống\
**I want:** Tính tiền nước\
**So that:** Hóa đơn có tiền nước chính xác.

**Priority:** Must\
**SP:** 3

------------------------------------------------------------------------

# 11. Epic E08 -- Invoice

## US-035 -- Tạo hóa đơn

**As:** Chủ nhà/Nhân viên\
**I want:** Tạo hóa đơn theo kỳ\
**So that:** Khách thuê biết số tiền phải thanh toán.

**Priority:** Must\
**SP:** 5

### Acceptance Criteria

-   [ ] Chọn phòng/hợp đồng.
-   [ ] Chọn kỳ hóa đơn.
-   [ ] Lấy tiền phòng.
-   [ ] Lấy tiền điện.
-   [ ] Lấy tiền nước.
-   [ ] Lấy phí dịch vụ.
-   [ ] Có thể thêm phát sinh/giảm trừ theo quyền.
-   [ ] Không tạo trùng hóa đơn cho cùng hợp đồng/kỳ.

------------------------------------------------------------------------

## US-036 -- Tính tổng hóa đơn

**As:** Hệ thống\
**I want:** Tự động tính tổng hóa đơn\
**So that:** Giảm sai sót khi tính tiền.

**Priority:** Must\
**SP:** 3

**Công thức:**

`Tổng = Tiền phòng + Điện + Nước + Dịch vụ + Phát sinh - Giảm trừ`

------------------------------------------------------------------------

## US-037 -- Xem hóa đơn

**As:** Owner/Staff/Tenant\
**I want:** Xem hóa đơn\
**So that:** Tôi biết chi tiết khoản phải trả.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

## US-038 -- Cập nhật hóa đơn

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Điều chỉnh hóa đơn trước khi khóa\
**So that:** Sai sót có thể được sửa.

**Priority:** Should\
**SP:** 3

### Acceptance Criteria

-   [ ] Không sửa tùy ý hóa đơn đã thanh toán.
-   [ ] Lưu người sửa và thời gian sửa.
-   [ ] Tính lại tổng tiền sau khi thay đổi.

------------------------------------------------------------------------

# 12. Epic E09 -- Payment

## US-040 -- Ghi nhận thanh toán

**As:** Chủ nhà/Nhân viên\
**I want:** Ghi nhận khách đã thanh toán\
**So that:** Công nợ được cập nhật.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Chọn hóa đơn.
-   [ ] Nhập số tiền.
-   [ ] Chọn phương thức.
-   [ ] Ghi nhận ngày thanh toán.
-   [ ] Không cho thanh toán vượt số tiền còn phải trả nếu không có quy
    tắc cho phép.
-   [ ] Cập nhật trạng thái hóa đơn.

------------------------------------------------------------------------

## US-041 -- Thanh toán trực tuyến

**As:** Khách thuê\
**I want:** Thanh toán hóa đơn trực tuyến\
**So that:** Tôi có thể thanh toán mà không cần trả tiền trực tiếp.

**Priority:** Could\
**SP:** 8

### Acceptance Criteria

-   [ ] Tạo payment request.
-   [ ] Chuyển đến payment gateway.
-   [ ] Nhận callback/webhook.
-   [ ] Xác thực kết quả giao dịch.
-   [ ] Chỉ cập nhật thành công khi gateway trả kết quả hợp lệ.
-   [ ] Giao dịch thất bại không được đánh dấu đã thanh toán.

> **MVP:** Có thể bỏ qua Story này và chỉ làm ghi nhận tiền mặt/chuyển
> khoản.

------------------------------------------------------------------------

## US-042 -- Cập nhật trạng thái thanh toán

**As:** Hệ thống\
**I want:** Cập nhật trạng thái thanh toán\
**So that:** Công nợ và hóa đơn phản ánh đúng.

**Priority:** Must\
**SP:** 3

**Trạng thái:** `UNPAID → PARTIAL → PAID`

Có thể có `OVERDUE`, `FAILED`.

------------------------------------------------------------------------

## US-043 -- Xem lịch sử thanh toán

**As:** Owner/Staff/Tenant\
**I want:** Xem lịch sử thanh toán\
**So that:** Tôi kiểm tra được các giao dịch đã thực hiện.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

# 13. Epic E10 -- Maintenance

## US-044 -- Gửi yêu cầu sửa chữa

**As:** Khách thuê\
**I want:** Gửi yêu cầu sửa chữa\
**So that:** Chủ nhà biết vấn đề cần xử lý.

**Priority:** Must\
**SP:** 3

### Acceptance Criteria

-   [ ] Chọn loại sự cố.
-   [ ] Nhập mô tả.
-   [ ] Có thể đính kèm hình ảnh.
-   [ ] Hệ thống tự xác định phòng của khách thuê.
-   [ ] Tạo request trạng thái NEW.
-   [ ] Chủ nhà/nhân viên có thể xem request.

------------------------------------------------------------------------

## US-045 -- Tiếp nhận yêu cầu

**As:** Chủ nhà/Nhân viên\
**I want:** Tiếp nhận yêu cầu sửa chữa\
**So that:** Yêu cầu được đưa vào quy trình xử lý.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

## US-046 -- Phân công sửa chữa

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Phân công người xử lý\
**So that:** Mỗi yêu cầu có người chịu trách nhiệm.

**Priority:** Should\
**SP:** 3

------------------------------------------------------------------------

## US-047 -- Cập nhật trạng thái sửa chữa

**As:** Chủ nhà/Nhân viên\
**I want:** Cập nhật trạng thái xử lý\
**So that:** Khách thuê biết tiến độ.

**Priority:** Must\
**SP:** 3

**Trạng thái:**

`NEW → ACCEPTED → IN_PROGRESS → COMPLETED → CLOSED`

Có thể có `WAITING`.

------------------------------------------------------------------------

## US-048 -- Theo dõi yêu cầu sửa chữa

**As:** Khách thuê\
**I want:** Theo dõi yêu cầu của mình\
**So that:** Tôi biết tình trạng xử lý.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

# 14. Epic E11 -- Notification

## US-039 -- Gửi thông báo hóa đơn

**As:** Chủ nhà/Nhân viên\
**I want:** Gửi thông báo khi hóa đơn được tạo\
**So that:** Khách thuê biết hóa đơn mới.

**Priority:** Should\
**SP:** 3

**Kênh:** Notification nội bộ trước; Email/SMS/Push là mở rộng.

------------------------------------------------------------------------

## US-049 -- Tạo thông báo

**As:** Chủ nhà/Nhân viên\
**I want:** Tạo thông báo\
**So that:** Tôi có thể thông báo thông tin đến khách thuê.

**Priority:** Should\
**SP:** 3

------------------------------------------------------------------------

## US-050 -- Xem thông báo

**As:** Người dùng\
**I want:** Xem thông báo\
**So that:** Tôi biết các thông tin mới.

**Priority:** Must\
**SP:** 2

------------------------------------------------------------------------

## US-051 -- Đánh dấu đã đọc

**As:** Người dùng\
**I want:** Đánh dấu thông báo đã đọc\
**So that:** Tôi phân biệt được thông báo mới và cũ.

**Priority:** Should\
**SP:** 1

------------------------------------------------------------------------

# 15. Epic E12 -- Dashboard & Reports

## US-052 -- Dashboard

**As:** Chủ nhà\
**I want:** Xem dashboard tổng quan\
**So that:** Tôi nắm được tình hình kinh doanh nhanh chóng.

**Priority:** Must\
**SP:** 5

### Dashboard đề xuất

-   Tổng số nhà.
-   Tổng số phòng.
-   Phòng trống.
-   Phòng đang thuê.
-   Phòng đang sửa.
-   Hợp đồng sắp hết hạn.
-   Hóa đơn chưa thanh toán.
-   Doanh thu.
-   Yêu cầu sửa chữa đang mở.

------------------------------------------------------------------------

## US-053 -- Báo cáo doanh thu

**As:** Chủ nhà\
**I want:** Xem doanh thu theo thời gian\
**So that:** Tôi theo dõi kết quả cho thuê.

**Priority:** Should\
**SP:** 5

### Bộ lọc

-   Ngày.
-   Tháng.
-   Quý.
-   Năm.
-   Nhà/khu trọ.

------------------------------------------------------------------------

## US-054 -- Báo cáo công nợ

**As:** Chủ nhà/Nhân viên có quyền\
**I want:** Xem các khoản chưa thanh toán\
**So that:** Tôi biết khách nào còn nợ.

**Priority:** Should\
**SP:** 5

------------------------------------------------------------------------

## US-055 -- Báo cáo tình trạng phòng

**As:** Chủ nhà\
**I want:** Xem thống kê trạng thái phòng\
**So that:** Tôi biết tỷ lệ phòng đang khai thác.

**Priority:** Should\
**SP:** 3

------------------------------------------------------------------------

## US-056 -- Báo cáo khách thuê

**As:** Chủ nhà\
**I want:** Xem báo cáo khách thuê\
**So that:** Tôi quản lý được tình hình người thuê.

**Priority:** Could\
**SP:** 3

------------------------------------------------------------------------

# 16. Definition of Done (DoD)

Một User Story chỉ được xem là **Done** khi:

-   [ ] UI đã hoàn thành.
-   [ ] API đã hoàn thành nếu Story cần backend.
-   [ ] Database đã có bảng/cột cần thiết.
-   [ ] Validation frontend đã có.
-   [ ] Validation backend đã có.
-   [ ] Phân quyền đã kiểm tra.
-   [ ] Xử lý loading/error/empty state.
-   [ ] Test Case đã được thực hiện.
-   [ ] Không còn lỗi Critical/High liên quan.
-   [ ] Code đã được review.
-   [ ] Có thể chạy được trên môi trường phát triển.

------------------------------------------------------------------------

# 17. Definition of Ready (DoR)

Trước khi bắt đầu code một User Story:

-   [ ] Story có Actor rõ ràng.
-   [ ] Business value rõ ràng.
-   [ ] Acceptance Criteria rõ ràng.
-   [ ] UI/API cần thiết đã được xác định.
-   [ ] Dependency đã được xác định.
-   [ ] Database entity liên quan đã được xác định.
-   [ ] Story có thể kiểm thử.
-   [ ] Team đã thống nhất phạm vi Story.

------------------------------------------------------------------------

# 18. MVP đề xuất để bắt đầu code

Để tránh làm dự án quá lớn, phiên bản đầu nên tập trung vào luồng:

**Đăng nhập → Quản lý nhà → Quản lý phòng → Khách thuê → Hợp đồng → Điện
nước → Hóa đơn → Thanh toán thủ công → Sửa chữa → Dashboard**

## Sprint 1 -- Authentication & Foundation

-   US-001 Đăng nhập
-   US-002 Đăng xuất
-   US-003 Đăng ký
-   US-004 Hồ sơ cá nhân
-   US-006 Phân quyền

**Kết quả Sprint:** Có hệ thống user + role + login + protected routes.

------------------------------------------------------------------------

## Sprint 2 -- Nhà & Phòng

-   US-007 Thêm nhà
-   US-008 Cập nhật nhà
-   US-009 Xem nhà
-   US-011 Thêm phòng
-   US-012 Cập nhật phòng
-   US-013 Danh sách phòng
-   US-014 Chi tiết phòng
-   US-015 Trạng thái phòng
-   US-016 Tìm kiếm/lọc

**Kết quả Sprint:** Chủ nhà quản lý được toàn bộ phòng.

------------------------------------------------------------------------

## Sprint 3 -- Khách thuê & Hợp đồng

-   US-017 Thêm khách thuê
-   US-018 Cập nhật khách thuê
-   US-019 Xem khách thuê
-   US-022 Tạo hợp đồng
-   US-023 Xem hợp đồng
-   US-024 Cập nhật hợp đồng
-   US-026 Chấm dứt hợp đồng

**Kết quả Sprint:** Có luồng hoàn chỉnh:

`Phòng trống → Chọn khách → Tạo hợp đồng → Phòng đang thuê`

------------------------------------------------------------------------

## Sprint 4 -- Điện nước & Hóa đơn

-   US-029 Đơn giá điện
-   US-030 Đơn giá nước
-   US-031 Chỉ số điện
-   US-032 Chỉ số nước
-   US-033 Tính tiền điện
-   US-034 Tính tiền nước
-   US-035 Tạo hóa đơn
-   US-036 Tính tổng
-   US-037 Xem hóa đơn

**Kết quả Sprint:** Có luồng:

`Nhập điện/nước → Tính phí → Tạo hóa đơn → Khách xem hóa đơn`

------------------------------------------------------------------------

## Sprint 5 -- Thanh toán & Sửa chữa

-   US-040 Ghi nhận thanh toán
-   US-042 Cập nhật trạng thái
-   US-043 Lịch sử thanh toán
-   US-044 Gửi yêu cầu sửa chữa
-   US-045 Tiếp nhận
-   US-047 Cập nhật trạng thái
-   US-048 Theo dõi

**Kết quả Sprint:** Có luồng vận hành hàng tháng.

------------------------------------------------------------------------

## Sprint 6 -- Dashboard & Báo cáo

-   US-052 Dashboard
-   US-053 Doanh thu
-   US-054 Công nợ
-   US-055 Tình trạng phòng

**Kết quả:** Hoàn thiện phiên bản MVP có thể demo.

------------------------------------------------------------------------

# 19. Thứ tự phụ thuộc để code

``` text
AUTH
  ↓
USER / ROLE
  ↓
PROPERTY
  ↓
ROOM
  ↓
TENANT
  ↓
CONTRACT
  ↓
UTILITY CONFIG
  ↓
ELECTRIC / WATER READING
  ↓
INVOICE
  ↓
PAYMENT
  ↓
MAINTENANCE
  ↓
NOTIFICATION
  ↓
DASHBOARD / REPORT
```

Không nên code hóa đơn trước khi có **Contract + Room + Utility
Reading**, vì hóa đơn phụ thuộc dữ liệu của các module đó.

------------------------------------------------------------------------

# 20. Database entity dự kiến từ User Stories

  Entity                   Mục đích
  ------------------------ -------------------
  `users`                  Tài khoản
  `roles`                  Vai trò
  `permissions`            Quyền
  `user_roles`             User -- Role
  `properties`             Nhà/khu trọ
  `rooms`                  Phòng
  `tenants`                Hồ sơ khách thuê
  `contracts`              Hợp đồng
  `services`               Dịch vụ
  `service_prices`         Đơn giá dịch vụ
  `electric_readings`      Chỉ số điện
  `water_readings`         Chỉ số nước
  `invoices`               Hóa đơn
  `invoice_items`          Chi tiết hóa đơn
  `payments`               Thanh toán
  `maintenance_requests`   Yêu cầu sửa chữa
  `notifications`          Thông báo
  `notification_reads`     Trạng thái đã đọc
  `audit_logs`             Nhật ký thao tác

------------------------------------------------------------------------

# 21. API module dự kiến

``` text
/api/auth
/api/users
/api/roles
/api/properties
/api/rooms
/api/tenants
/api/contracts
/api/services
/api/electric-readings
/api/water-readings
/api/invoices
/api/payments
/api/maintenance
/api/notifications
/api/dashboard
/api/reports
```

------------------------------------------------------------------------

# 22. Frontend route dự kiến

``` text
/login
/register

/dashboard

/properties
/properties/:id

/rooms
/rooms/:id

/tenants
/tenants/:id

/contracts
/contracts/:id

/utilities/electric
/utilities/water
/utilities/services

/invoices
/invoices/:id

/payments
/payments/history

/maintenance
/maintenance/:id

/notifications

/reports/revenue
/reports/debt
/reports/rooms

/profile
/admin/users
/admin/roles
```

------------------------------------------------------------------------

# 23. Luồng nghiệp vụ quan trọng nhất để demo

## Flow 1 -- Cho thuê phòng

``` text
Chủ nhà đăng nhập
       ↓
Tạo nhà
       ↓
Tạo phòng
       ↓
Thêm khách thuê
       ↓
Tạo hợp đồng
       ↓
Phòng = ĐANG THUÊ
```

## Flow 2 -- Lập hóa đơn hàng tháng

``` text
Chọn kỳ
   ↓
Nhập chỉ số điện
   ↓
Nhập chỉ số nước
   ↓
Tính điện
   ↓
Tính nước
   ↓
Lấy tiền phòng
   ↓
Lấy phí dịch vụ
   ↓
Tạo hóa đơn
   ↓
Khách thuê xem hóa đơn
```

## Flow 3 -- Thanh toán

``` text
Khách xem hóa đơn
       ↓
Thanh toán
       ↓
Chủ nhà ghi nhận
       ↓
Payment
       ↓
Cập nhật Invoice
       ↓
PAID
```

## Flow 4 -- Sửa chữa

``` text
Khách thuê gửi yêu cầu
       ↓
NEW
       ↓
Chủ nhà/Staff tiếp nhận
       ↓
ACCEPTED
       ↓
Đang xử lý
       ↓
IN_PROGRESS
       ↓
Hoàn thành
       ↓
COMPLETED
       ↓
Đóng
```

------------------------------------------------------------------------

# 24. Backlog sau khi chuyển từ BA sang Developer

``` text
BA Requirement
      ↓
User Story
      ↓
Acceptance Criteria
      ↓
UI Design
      ↓
Database Design
      ↓
API Specification
      ↓
Frontend Implementation
      ↓
Backend Implementation
      ↓
Integration
      ↓
Test Case
      ↓
UAT
      ↓
Done
```

**Tài liệu User Story này là cầu nối giữa phần Phân tích & Thiết kế HTTT
và phần lập trình.**
