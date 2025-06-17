# 1. SSL là gì?

**SSL** (Secure Sockets Layer) là một tiêu chuẩn của công nghệ bảo mật, giúp **mã hóa truyền thông giữa trình duyệt và máy chủ web**.  
SSL đảm bảo rằng dữ liệu truyền giữa hai bên luôn **toàn vẹn, riêng tư và bảo mật**.

---

# 2. Các cách xác thực SSL

Có 3 loại xác thực chính:

- **DV (Domain Validation)**:  
  Xác thực tên miền – loại đơn giản và nhanh nhất.

- **OV (Organization Validation)**:  
  Xác thực tổ chức – cần xác minh thông tin doanh nghiệp.

- **EV (Extended Validation)**:  
  Xác thực mở rộng – kiểm tra kỹ lưỡng, hiển thị tên tổ chức trên thanh địa chỉ trình duyệt.

---

# 3. CSR File dùng để làm gì?

**CSR** (Certificate Signing Request) là một file chứa:

- Khóa công khai
- Thông tin về tên miền hoặc tổ chức

File này được gửi đến **CA (Certificate Authority)** để họ tạo ra chứng chỉ SSL cho bạn.

---

# 4. Sử dụng OpenSSL để tạo file CSR cho `tech.training.vietnix.tech`

### Bước 1: Tạo khóa riêng tư (`.key`)
```sh
openssl genrsa -out tech.training.vietnix.tech.key 2048
```

### Bước 2: Tạo file CSR (`.csr`)
```sh
openssl req -new -key tech.training.vietnix.tech.key -out tech.training.vietnix.tech.csr
```
(Hệ thống sẽ yêu cầu nhập thông tin về domain, tổ chức, v.v.)

---

# 5. PEM file là gì?

**PEM** (Privacy-Enhanced Mail) là định dạng file văn bản thuần túy phổ biến để lưu trữ các chứng chỉ SSL, khóa riêng tư, và chuỗi chứng chỉ.  
Nội dung bên trong được mã hóa base64 và có các dòng bắt đầu/kết thúc như:  
`-----BEGIN CERTIFICATE-----`

---

# 6. Private Key SSL là gì?

**Private Key** là một file bí mật nằm trên máy chủ.  
Nó là chìa khóa để giải mã dữ liệu được mã hóa bằng chứng chỉ SSL và chứng minh danh tính của máy chủ.  
**Khóa này tuyệt đối không được tiết lộ.**

---

# 7. PFX file là gì? Cách chuyển từ CRT sang PFX

**PFX** (Personal Information Exchange) là một file nhị phân chứa toàn bộ chuỗi chứng chỉ và khóa riêng tư trong một file duy nhất, được bảo vệ bằng mật khẩu.  
Thường được sử dụng trong môi trường Windows Server (IIS).

### Cách chuyển từ CRT sang PFX bằng OpenSSL:

Cần có các file:

- `.crt`: Chứng chỉ chính
- `.key`: Khóa riêng tư
- `ca-bundle.crt`: (tùy chọn) chứng chỉ trung gian

```sh
openssl pkcs12 -export -out your_domain.pfx -inkey your_domain.key -in your_domain.crt -certfile ca-bundle.crt
```

Lệnh này sẽ yêu cầu tạo một mật khẩu để bảo vệ file `.pfx`.
