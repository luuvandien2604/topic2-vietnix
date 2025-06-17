# 1. Mail Server là gì?

**Mail Server** là hệ thống máy chủ chuyên dụng để **gửi, nhận, lưu trữ và quản lý email**.

Có hai loại chính:

- **SMTP Server**: Dùng để gửi email đi.
- **POP3 / IMAP Server**: Dùng để nhận và quản lý email đến.

---

# 2. MX Record là gì?

**MX Record** (Mail Exchanger Record) là bản ghi DNS chỉ định **máy chủ thư** chịu trách nhiệm nhận email cho một tên miền.

> Khi một email được gửi đến địa chỉ thuộc tên miền, hệ thống sẽ tra cứu bản ghi MX để biết cần gửi thư tới máy chủ nào.

---

# 3. DKIM, SPF, PTR là gì?

Đây là những cơ chế **xác thực email** giúp ngăn chặn thư rác và giả mạo:

## a. DKIM (DomainKeys Identified Mail)

- Cho phép **ký điện tử** vào email bằng domain của người gửi.
- Giúp xác minh email đến từ domain hợp lệ và không bị thay đổi trong quá trình truyền đi.
- *Lợi ích*: Tăng độ tin cậy, giảm nguy cơ bị đánh dấu là spam.

## b. SPF (Sender Policy Framework)

- Là bản ghi DNS loại **TXT** quy định **những máy chủ nào được phép gửi email** thay mặt cho domain đó.
- *Lợi ích*: Ngăn email giả mạo, bảo vệ danh tiếng domain.

## c. PTR (Pointer Record)

- Là bản ghi DNS dùng để **ánh xạ địa chỉ IP ngược lại tên miền** (Reverse DNS Lookup).
- *Lợi ích*: Giúp xác minh danh tính máy chủ gửi email, tăng độ tin cậy và giảm tỷ lệ bị đánh dấu spam.

---

