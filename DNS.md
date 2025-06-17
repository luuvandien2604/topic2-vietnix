# 1. DNS là gì?

**DNS** (Domain Name System) là hệ thống phân giải tên miền. Nó cho phép ánh xạ giữa tên miền và địa chỉ IP trên Internet.

---

# 2. Các loại bản ghi DNS

DNS bao gồm 7 loại bản ghi chính:

- **A Record**: Trỏ tên miền đến địa chỉ IPv4.
- **AAAA Record**: Trỏ tên miền đến địa chỉ IPv6.
- **CNAME Record**: Trỏ một tên miền đến một tên miền khác (Canonical Name).
- **MX Record**: Xác định máy chủ email cho tên miền.
- **TXT Record**: Chứa thông tin dạng văn bản như SPF, DKIM, v.v.
- **SRV Record**: Xác định dịch vụ nào chạy trên cổng nào (Port, Priority, Weight).
- **NS Record**: Chỉ định Name Server cho tên miền hoặc tên miền phụ.

---

# 3. Nguyên tắc hoạt động của DNS

1. Khi người dùng truy cập một website, máy tính gửi yêu cầu đến DNS resolver (thường là DNS của nhà mạng).
2. Nếu resolver đã có bản ghi IP tương ứng, nó sẽ trả về ngay.
3. Nếu không, resolver sẽ hỏi các máy chủ DNS theo thứ tự:
   - Root DNS Server
   - TLD DNS Server (ví dụ: `.com`, `.vn`)
   - Authoritative DNS Server (máy chủ quản lý bản ghi chính xác của domain)
4. Resolver nhận IP và trả về cho trình duyệt.
5. Trình duyệt kết nối đến địa chỉ IP để truy cập website.

---

# 4. Quá trình phân giải địa chỉ DNS

- **Bước 1**: Trình duyệt kiểm tra cache cục bộ. Nếu có IP tương ứng thì dùng luôn.
- **Bước 2**: Nếu không, hệ điều hành gửi truy vấn đến DNS Resolver.
- **Bước 3**: DNS Resolver thực hiện truy vấn phân cấp:
  - Gửi yêu cầu đến **Root Server** → trả về TLD Server.
  - Gửi yêu cầu đến **TLD Server** → trả về Authoritative DNS Server.
  - Gửi yêu cầu đến **Authoritative Server** → trả về địa chỉ IP chính xác.
- **Bước 4**: DNS Resolver trả IP về cho hệ điều hành và trình duyệt sử dụng để kết nối.

---

> **Ghi chú**: DNS rất quan trọng cho việc duyệt web, gửi email và nhiều dịch vụ mạng khác.
