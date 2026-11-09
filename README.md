# MINOO Eyewear

MINOO Eyewear là website thương mại điện tử dành cho cửa hàng kính mắt, được xây dựng bằng Django. Hệ thống hỗ trợ khách hàng xem và tìm kiếm sản phẩm, lọc gọng kính theo nhiều tiêu chí, tìm sản phẩm tương tự bằng hình ảnh, quản lý giỏ hàng, đặt hàng và thanh toán. Bên cạnh đó, hệ thống còn cung cấp khu vực quản trị để quản lý sản phẩm, đơn hàng, khuyến mãi và dữ liệu liên quan.

## 1. Mục tiêu dự án

Dự án được xây dựng nhằm hỗ trợ MINOO Eyewear giải quyết một số vấn đề trong hoạt động kinh doanh:

- Xây dựng kênh bán hàng trực tuyến chính thức cho cửa hàng.
- Hỗ trợ khách hàng tìm kiếm và lựa chọn sản phẩm thuận tiện hơn.
- Giảm việc kiểm tra sản phẩm tương tự bằng phương pháp thủ công.
- Hỗ trợ quản lý sản phẩm, đơn hàng và tồn kho tập trung.
- Tạo nền tảng để cửa hàng mở rộng hoạt động thương mại điện tử.

## 2. Chức năng chính

### Khách hàng

- Xem danh sách sản phẩm kính mắt.
- Tìm kiếm sản phẩm.
- Lọc sản phẩm theo giới tính, kiểu dáng và khoảng giá.
- Xem chi tiết sản phẩm và các biến thể.
- Tìm kiếm sản phẩm tương tự bằng hình ảnh.
- Hiển thị Top-5 sản phẩm có độ tương đồng cao.
- Thêm sản phẩm vào giỏ hàng.
- Cập nhật và xóa sản phẩm trong giỏ hàng.
- Tiến hành đặt hàng và thanh toán.
- Xem các chương trình khuyến mãi và mã giảm giá.
- Gửi đánh giá và liên hệ với cửa hàng.

### Quản trị viên

- Quản lý danh mục sản phẩm.
- Quản lý sản phẩm và biến thể sản phẩm.
- Quản lý hình ảnh sản phẩm.
- Quản lý tồn kho.
- Quản lý đơn hàng.
- Quản lý khách hàng và chương trình khuyến mãi.
- Quản lý mã giảm giá.
- Theo dõi các giao dịch thanh toán.
- Hỗ trợ kiểm tra sản phẩm tương tự bằng hình ảnh.

## 3. Visual Search

Hệ thống sử dụng kỹ thuật Image Similarity để hỗ trợ tìm kiếm sản phẩm tương tự bằng hình ảnh.

Quy trình xử lý:

1. Người dùng tải ảnh kính lên hệ thống.
2. Hệ thống xử lý ảnh bằng thư viện Pillow.
3. Perceptual Hash (pHash) được sử dụng để tạo mã đặc trưng cho ảnh.
4. Ảnh tải lên được so sánh với ảnh chính, ảnh thư viện và ảnh biến thể của các sản phẩm.
5. Hệ thống tính khoảng cách giữa các mã hash.
6. Các sản phẩm có độ tương đồng cao nhất được sắp xếp và trả về.
7. Hiển thị tối đa 5 sản phẩm tương tự.

Ngưỡng so sánh hiện tại:

```text
pHash threshold: 12
Maximum results: 5
```

## 4. Công nghệ sử dụng

### Backend

- Python
- Django 4.2.30
- Django ORM

### Database

- SQLite

### Frontend

- HTML
- CSS
- JavaScript
- Django Templates

### Image Processing

- Pillow
- ImageHash
- Perceptual Hash (pHash)

### Thanh toán

- SePay
- Webhook xử lý giao dịch thanh toán

## 5. Kiến trúc hệ thống

Hệ thống được xây dựng theo kiến trúc Django MVT:

```text
User
  |
  v
Django Templates
  |
  v
Views
  |
  v
Django ORM
  |
  v
SQLite Database
```

Các thành phần chính của hệ thống bao gồm:

```text
User
Category
Product
ProductVariant
ProductImage
Order
OrderItem
PromotionCustomer
DiscountCoupon
SePayTransaction
ContactMessage
ProductReview
```

## 6. Cấu trúc dữ liệu chính

### Product

Lưu thông tin chính của sản phẩm như:

- Tên sản phẩm
- SKU
- Danh mục
- Giá bán
- Giá khuyến mãi
- Kiểu dáng
- Chất liệu
- Màu sắc
- Kích thước
- Giới tính
- Số lượng tồn kho

### ProductVariant

Quản lý các biến thể khác nhau của sản phẩm.

### ProductImage

Quản lý ảnh chính và các ảnh liên quan của sản phẩm.

### Order

Lưu thông tin đơn hàng của khách hàng.

### OrderItem

Lưu các sản phẩm thuộc từng đơn hàng.

### SePayTransaction

Lưu và xử lý thông tin giao dịch thanh toán từ SePay.

## 7. Cài đặt và chạy dự án

### Bước 1. Clone repository

```bash
git clone <repository-url>
```

### Bước 2. Di chuyển vào thư mục project

```bash
cd minoo-eyewear
```

### Bước 3. Tạo virtual environment

Windows:

```bash
python -m venv venv
```

Kích hoạt:

```bash
venv\Scripts\activate
```

### Bước 4. Cài thư viện

```bash
pip install -r requirements.txt
```

### Bước 5. Migration database

```bash
python manage.py migrate
```

### Bước 6. Chạy server

```bash
python manage.py runserver
```

Sau đó truy cập:

```text
http://127.0.0.1:8000
```

## 8. Quy trình sử dụng cơ bản

### Khách hàng

```text
Trang chủ
→ Danh sách sản phẩm
→ Tìm kiếm / Lọc sản phẩm
→ Xem chi tiết sản phẩm
→ Thêm vào giỏ hàng
→ Checkout
→ Tạo đơn hàng
→ Thanh toán
```

### Visual Search

```text
Tải ảnh lên
→ Xử lý ảnh
→ Tạo pHash
→ So sánh với dữ liệu sản phẩm
→ Xếp hạng độ tương đồng
→ Trả về Top-5 sản phẩm
```

### Quản trị viên

```text
Đăng nhập Admin
→ Quản lý sản phẩm
→ Quản lý tồn kho
→ Quản lý đơn hàng
→ Kiểm tra giao dịch
→ Theo dõi hoạt động hệ thống
```

## 9. Kết quả kiểm thử

Hệ thống đã thực hiện kiểm thử các chức năng chính.

- Functional Testing: 40/40 test case Pass.
- User Acceptance Testing: 15/15 test case Accepted.
- Số người tham gia UAT: 3.
- Không còn lỗi Critical hoặc Major tại thời điểm nghiệm thu.
- Kết quả Business Decision: Accepted for Release.

## 10. Demo

Video giới thiệu và demo hệ thống sẽ được cập nhật tại:

```text
YouTube Demo:
https://www.youtube.com/watch?v=9e1GuB0rVSw&t=164s
```
## 11. Lưu ý

Repository được sử dụng cho mục đích học tập trong học phần Quản trị dự án Thương mại điện tử.

Một số thông tin cấu hình nhạy cảm như:

- Secret key
- API key
- Payment token
- Cloudflare Tunnel token
- Thông tin tài khoản

không nên được upload công khai lên GitHub.

## 12. Project

**Project:** MINOO Eyewear  
**Platform:** Django Web Application  
**Database:** SQLite  
**Course:** Quản trị dự án Thương mại điện tử  
**Purpose:** Academic project / E-commerce system demonstration
