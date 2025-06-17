1.DNS là gì ?
  DNS viết tắt của Domain Name System có nghĩa là hệ thống phân giải tên miền. DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền trên Internet.

2.Các loại recored DNS
  Hiện nay, DNS có bảy loại bản ghi, bao gồm:
    - CNAME Record: Là một bản ghi tên quy chuẩn (Canonical Name Record). Đây là một dạng bản ghi tài nguyên trong hệ thống tên miền.
    - A Record: Dùng để trỏ tên miền website tới một địa chỉ IP cụ thể. Đây được xem là bản ghi DNS đơn giản nhất.
    - MX Record: Bản ghi này bạn có thể sử dụng để trỏ tên miền đến mail server. MX Record chỉ định server nào quản lý các dịch vụ Email của tên miền đó.
    - AAAA Record: Dùng để trỏ tên miền đến địa chỉ IPv6 và cho phép thêm host mới, TTL và IPv6.
    - TXT Record: Ngoài ra, có thể thêm giá trị TXT, Host mới, TTL và Point To để chứa các thông tin định dạng văn bản domain.
    - SRV Record: Đây là bản ghi DNS đặc biệt, dùng để xác định chính xác dịch vụ nào đang chạy Port nào. Và thông qua bản ghi này bạn có thể thêm Priority, Port, Weight, TTL, Point to Point.
    - NS Record: Bản ghi này có thể chỉ định Name Server cho từng tên miền phụ và bên cạnh đó có thể tạo tên Name Server, TTL hay host mới.

3.Nguyên tắc làm việc của DNS
    - Khi người dùng truy cập một website, máy tính sẽ gửi yêu cầu đến máy chủ DNS cục bộ để tìm địa chỉ IP của website đó. Máy chủ DNS cục bộ sẽ kiểm tra cơ sở dữ liệu của mình xem có chứa địa chỉ IP của website hay không. Nếu có, sẽ trả về địa chỉ IP cho máy tính của người dùng.
    - Quá trình phân giải DNS bao gồm chuyển đổi tên máy chủ thành địa chỉ IP. Một địa chỉ IP được cung cấp cho mỗi thiết bị trên Internet và địa chỉ đó là cần thiết để tìm thiết bị Internet phù hợp. 
    - Khi người dùng muốn tải một trang web, một bản dịch phải xảy ra giữa những gì người dùng nhập vào trình duyệt web của họ và địa chỉ thân thiện với máy cần thiết để định vị trang web.
    - Nếu máy chủ DNS cục bộ không có địa chỉ IP của website, nó sẽ hỏi máy chủ DNS gốc. Máy chủ DNS gốc sẽ trả về địa chỉ IP của máy chủ DNS cấp cao nhất cho website.
    - Máy chủ DNS cấp cao nhất sẽ trả về địa chỉ IP của máy chủ DNS quản lý website. Máy chủ DNS quản lý sẽ trả về địa chỉ IP của trang web cho máy chủ DNS cục bộ.
    - Cuối cùng, máy chủ DNS cục bộ sẽ trả về địa chỉ IP của trang web cho máy tính của người dùng. Máy tính của người dùng sẽ sử dụng địa chỉ IP này để kết nối với website.

4.Cách phân giải địa chỉ DNS:
  Bước 1: Trình duyệt kiểm tra cache cục bộ (Local DNS cache): Nếu tên miền đã truy cập trước đó, hệ thống có thể đã lưu IP → không cần phân giải lại.
  Bước 2: Hệ điều hành hỏi DNS Resolver (thường là DNS của nhà mạng hoặc 8.8.8.8 – Google): Nếu không có trong cache, máy sẽ hỏi DNS Resolver được cấu hình.
  Bước 3: DNS Resolver thực hiện truy vấn phân cấp:
    - Đầu tiên, DNS Resolver sẽ gửi truy vấn đến Root DNS Server để hỏi thông tin về tên miền. Root Server không trả về IP đích, mà sẽ chỉ đến máy chủ quản lý tên miền cấp cao nhất (TLD), ví dụ như     .com, .net, .org, v.v.
    - Sau đó, Resolver tiếp tục truy vấn đến TLD DNS Server (ví dụ .com) để hỏi. Máy chủ TLD sẽ trả lời bằng cách chỉ định địa chỉ của Authoritative DNS Server cho tên miền đó.
    - Cuối cùng, Resolver gửi truy vấn đến Authoritative DNS Server – đây là nơi lưu trữ bản ghi DNS thực sự của domain. Máy chủ này sẽ trả về địa chỉ IP chính xác của www.example.com.
  Bước 4: DNS Resolver trả IP lại cho hệ điều hành & trình duyệt: Trình duyệt dùng IP đó để kết nối đến server.
