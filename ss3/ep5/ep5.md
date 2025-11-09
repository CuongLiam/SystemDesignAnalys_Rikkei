## 👥 Phân tích Actor và Use Case cho Ứng dụng Giao đồ ăn

Mục tiêu: Nhận biết Actor, phân loại vai trò (Primary/Secondary) và xác định Use Case tương ứng.

---

### I. Liệt kê và Phân loại Actor

Actor là bất kỳ người, hệ thống hoặc thiết bị nào tương tác với hệ thống (ứng dụng giao đồ ăn).

| Actor | Loại (Vai trò) | Giải thích |
| :--- | :--- | :--- |
| **Khách hàng** | **Primary** | Người dùng chính khởi xướng các Use Case quan trọng để đạt được mục tiêu (ví dụ: đặt món, thanh toán). |
| **Nhà hàng/Cửa hàng** | **Primary** | Cung cấp dịch vụ chính (đồ ăn). Khởi xướng các Use Case để tương tác trực tiếp (ví dụ: cập nhật menu, xác nhận đơn hàng). |
| **Tài xế/Shipper** | **Primary** | Cung cấp dịch vụ vận chuyển. Khởi xướng các Use Case quan trọng để hoàn thành dịch vụ (ví dụ: nhận đơn, giao hàng). |
| **Hệ thống Thanh toán** | **Secondary** | Một hệ thống bên ngoài cung cấp dịch vụ (thanh toán) mà hệ thống của chúng ta phụ thuộc vào. |
| **Hệ thống Quản trị (Admin)** | **Secondary** | Đại diện cho người quản lý hệ thống thực hiện các tác vụ duy trì và giám sát (ví dụ: quản lý tài khoản, xem báo cáo). |

---

### II. Bảng Tổng hợp Actor và Use Case Tương ứng

Đây là bảng tổng hợp mối quan hệ giữa các Actor và các chức năng (Use Case) mà họ tương tác.

| Actor | Loại | Use Case phục vụ |
| :--- | :--- | :--- |
| **Khách hàng** | Primary | Đặt món ăn, Thanh toán trực tuyến, Xem lịch sử đơn hàng, Đánh giá nhà hàng |
| **Nhà hàng/Cửa hàng** | Primary | Xác nhận đơn hàng, Cập nhật menu và giá, Quản lý giờ mở cửa |
| **Tài xế/Shipper** | Primary | Cập nhật trạng thái giao hàng, Nhận đơn hàng, Xem thông tin giao hàng |
| **Hệ thống Thanh toán** | Secondary | Xử lý giao dịch Thanh toán trực tuyến, Xử lý Hoàn tiền |
| **Hệ thống Quản trị** | Secondary | Quản lý tài khoản người dùng, Quản lý khuyến mãi, Xem báo cáo chung của hệ thống |

---

### 📝 Các Use Case Chính được xác định

1.  **Đặt món ăn (Place Order)**
2.  **Xác nhận đơn hàng (Confirm Order)**
3.  **Thanh toán trực tuyến (Process Online Payment)**
4.  **Cập nhật trạng thái giao hàng (Update Delivery Status)**