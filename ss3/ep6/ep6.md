## 📝 Diễn Đạt Mô Tả Chi Tiết Use Case: Đặt Hàng

| Thuộc tính | Chi tiết |
| :--- | :--- |
| **Tên** | Đặt Hàng (Place Order) |
| **Actor** | **Primary:** Khách hàng. **Secondary:** Hệ thống Thanh toán, Hệ thống Quản lý Kho. |
| **Mục tiêu** | Khách hàng hoàn tất việc lựa chọn món ăn, xác nhận thông tin giao hàng, thanh toán và gửi đơn hàng thành công đến nhà hàng. |

---

### Luồng Chính (Basic Flow / Successful Scenario)

1.  **Khách hàng** truy cập vào mục "Giỏ hàng" hoặc chọn "Thanh toán" từ trang chi tiết món ăn/cửa hàng.
2.  **Hệ thống** hiển thị màn hình Tổng quan Đơn hàng (bao gồm danh sách món, tổng tiền tạm tính, phí vận chuyển, và các lựa chọn khuyến mãi).
3.  **Khách hàng** xác nhận hoặc chọn/nhập **Địa chỉ giao hàng** và **Thông tin liên hệ**.
4.  **Khách hàng** chọn **Phương thức thanh toán** (ví dụ: Thẻ/Ví điện tử/Tiền mặt).
5.  **Khách hàng** nhấn nút **"Đặt Hàng"**.
6.  *Nếu chọn thanh toán trực tuyến:*
    * **Hệ thống** chuyển hướng đến cổng **Hệ thống Thanh toán**.
    * **Khách hàng** hoàn tất xác thực thanh toán.
    * **Hệ thống Thanh toán** gửi xác nhận giao dịch thành công về cho **Hệ thống**.
7.  *Nếu chọn thanh toán tiền mặt:*
    * **Hệ thống** bỏ qua bước 6.
8.  **Hệ thống** trừ đi số lượng món hàng khỏi **Hệ thống Quản lý Kho** (nếu có).
9.  **Hệ thống** tạo mới một bản ghi **Đơn hàng** với trạng thái "Chờ xác nhận".
10. **Hệ thống** hiển thị màn hình **Xác nhận Đơn hàng Thành công** cho **Khách hàng** và gửi thông báo (email/SMS/push notification).

---

### Luồng Lỗi (Alternate/Exception Flows)

| Số | Tình huống Lỗi | Mô tả Xử lý Lỗi |
| :--- | :--- | :--- |
| **E1** | **Địa chỉ giao hàng không hợp lệ/không nằm trong khu vực phục vụ.** | **Hệ thống** thông báo lỗi ngay khi Khách hàng nhập địa chỉ và yêu cầu Khách hàng chọn địa chỉ khác hoặc điều chỉnh. Quá trình đặt hàng bị tạm dừng. |
| **E2** | **Hết hàng (Stock Out) khi xác nhận đơn.** | Ngay sau bước 5, **Hệ thống** kiểm tra lại kho. Nếu một hoặc nhiều món đã hết, **Hệ thống** thông báo món nào đã hết và hỏi Khách hàng muốn *Bỏ món đó*, *Chờ cập nhật*, hoặc *Hủy toàn bộ đơn hàng*. |
| **E3** | **Thanh toán trực tuyến thất bại.** | Sau bước 6, **Hệ thống Thanh toán** báo giao dịch lỗi. **Hệ thống** thông báo lỗi cho **Khách hàng** và đề nghị thử lại thanh toán, hoặc chuyển sang phương thức thanh toán khác (ví dụ: đổi sang Tiền mặt). Đơn hàng chưa được tạo chính thức. |
| **E4** | **Khách hàng hủy đơn trong lúc thanh toán.** | **Hệ thống** ghi nhận việc hủy bỏ. Nếu đơn hàng chưa được tạo (ví dụ: lỗi thanh toán), không có hành động gì thêm. Nếu đơn đã được tạo nhưng thanh toán thất bại, trạng thái đơn hàng được cập nhật là "Đã Hủy" (do lỗi thanh toán). |