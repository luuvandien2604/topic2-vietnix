# 1. Ping đến domain vietnix.vn sau đó giải thích?
```sh
luuvandien@LVD-mint:~$ ping vietnix.vn
PING vietnix.vn (14.225.253.240) 56(84) bytes of data.
64 bytes from 14.225.253.240: icmp_seq=1 ttl=53 time=4.85 ms
64 bytes from 14.225.253.240: icmp_seq=2 ttl=53 time=4.61 ms
64 bytes from 14.225.253.240: icmp_seq=3 ttl=53 time=3.91 ms
64 bytes from 14.225.253.240: icmp_seq=4 ttl=53 time=3.65 ms
64 bytes from 14.225.253.240: icmp_seq=5 ttl=53 time=6.18 ms
^C
--- vietnix.vn ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 3.646/4.638/6.178/0.887 ms
```
  **TTL (Time To Live):** Trong Ping chính là chỉ số Hop (Router, Gateway) biểu thị các thông tin liên quan đến khả năng truyền dữ liệu và phản hồi. Ngoài ra, nó còn giúp ngăn chặn sự trùng lặp các gói ICMP giữa các Host trên Internet khi truyền dẫn. Chỉ số TTL càng cao, chỉ số Hop khi truyền tín hiệu càng bé.  
  
  **Time:** Là thời gian truyền nhận tín hiệu. Tốc độ truyền mạng sẽ giảm đi khi con số càng lớn.  

  ---

# 2. ssh command 
## Dùng pasword.
```sh
ssh user@host
```
Ví dụ:
```sh
ssh root@192.168.1.100
```

## Dùng Key
```sh
ssh -i /path/to/private_key user@host
```
Ví dụ:
```sh
ssh -i ~/.ssh/id_rsa root@192.168.1.100
```

## Dùng port custom
```sh
ssh -p <port> user@host
```
Ví dụ:
```sh
ssh -p 2222 root@192.168.1.100
```

**Kết hợp với SSH key:**
```sh
ssh -i ~/.ssh/id_rsa -p 2222 user@host
```

---

# 3.Scp command

## SCP 1 file

```sh
scp /path/to/local/file user@host:/path/to/remote/
```

Ví dụ:

```sh
scp /home/user/test.txt root@192.168.1.100:/root/
```

## SCP 1 folder

```sh
scp -r /path/to/local/folder user@host:/path/to/remote/
```

Ví dụ:

```sh
scp -r /home/user/myfolder root@192.168.1.100:/root/
```

  ---
  
# 4.Rsync command

## Rsync 1 file

```sh
rsync -av /path/to/file user@host:/path/to/remote/
```

Ví dụ:

```sh
rsync -av /home/user/test.txt root@192.168.1.100:/root/
```

## Rsync 1 folder

```sh
rsync -av /path/to/folder/ user@host:/path/to/remote/
```

Ví dụ:

```sh
rsync -av /home/user/myfolder/ root@192.168.1.100:/root/myfolder/
```

## Rsync incremental (sao lưu tăng dần)

```sh
rsync -av --delete /home/user/data/ /backup/data/
```

  ---
  
# 5.cat command

## Cat nội dung 1 file
```sh
cat filename
```

Ví dụ:

```sh
cat /etc/hostname
```

## Cat dòng thứ <n> trong file

```sh
sed -n '5p' filename
```

Ví dụ:

```sh
sed -n '10p' /etc/passwd
```

## Cat nhiều dòng vào 1 file bằng EOF

```sh
cat <<EOF > filename
Dòng 1
Dòng 2
Dòng 3
EOF
```

Ví dụ:

```sh
cat <<EOF > /tmp/test.txt
Dong 1
Dong 2
```

  ---
  
# 6. Echo command

## Chèn thêm 1 dòng vào cuối file

echo "Dòng mới" >> filename.txt

Ví dụ:

```sh
echo "Đây là dòng mới" >> test.txt
```

## Ghi đè toàn bộ nội dung file bằng dòng mới

```sh
echo "Nội dung muốn ghi đè" > filename.txt
```

Ví dụ:

```sh
echo "Dòng mới ghi đè" > test.txt
EOF
```

  ---
  
# 7.Tail/head command
## tail — xem các dòng cuối cùng của file

```sh
tail filename.txt
```
  Mặc định hiển thị 10 dòng cuối cùng của file.

  Dùng tùy chọn -n để chỉ định số dòng:
```sh
    tail -n 20 filename.txt  # Hiển thị 20 dòng cuối
```

## tail -f — theo dõi file theo thời gian thực

```sh
tail -f filename.txt
```

  Hiển thị 10 dòng cuối và tiếp tục theo dõi những dòng mới được ghi thêm vào file.

```sh
tail -f /var/log/syslog
```
  
  ---
  
# 8.Dùng sed để find and replace một string trong file

```sh
sed -i 's/chuỗi_cũ/chuỗi_mới/' filename.txt
```

Ví dụ:

```sh
sed -i 's/hello/xin chào/' test.txt
```

  ---
  
# 9.Traceroute Command 

```sh
traceroute vietnix.vn
```

```sh
traceroute vietnix.vn
```
| Hop | IP/Hostname                       | Giải thích                                                               |
|-----|----------------------------------|--------------------------------------------------------------------------|
| 1   | `_gateway (192.168.0.1)`         | Router nội bộ.                                     |
| 2   | `localhost (27.71.251.149)`      | Gateway của nhà cung cấp dịch vụ (ISP)                                   |
| 3   | `10.255.x.x`                     | Mạng nội bộ của nhà mạng  |
| 4   | `* * *`                          | Không nhận được phản hồi (timeout hoặc bị chặn ICMP)                     |
| 5   | `localhost (27.68.236.x)`        | Tiếp tục route trong hạ tầng nhà mạng                                    |
| 6   | `203.113.187.98`, `113.171.7.205`| Các node thuộc hệ thống mạng (ISP)                          |
| 7-9 | `static.vnpt.vn (113.171.x.x)`   | Các hop trung gian trước khi đến server đích                    |
| 10  | `14.225.253.240`                 | Địa chỉ IP của **vietnix.vn** (đích đến cuối)                            |

  ---

# 10. Netstat command

## Hiển thị các socket đang LISTEN

```sh
ss -l
```

## Không resolve hostname/portname

```sh
ss -ln
```

## Hiển thị process name/PID

```sh
ss -lpn
```

## Chỉ hiển thị TCP socket

```sh
ss -ltnp
```

## Chỉ hiển thị UDP socket

```sh
ss -lunp
```

---

# 11. Sort command

## Sort theo thứ tự tăng dần

```sh
sort filename.txt
```

## Sort theo thứ tự giảm dần

```sh
sort -r filename.txt
```

## Sort theo cột (column)

## Giả sử file data.txt có nội dung dạng bảng với các cột cách nhau bằng khoảng trắng hoặc tab:
| Name  | Age |
|-------|-----|
| Alice | 30  |
| Bob   | 25  |
| Tom   | 35  |


  ### Sort theo cột thứ 2 (tuổi):

```sh
sort -k2 data.txt
```

  ### Sort theo cột thứ 2 giảm dần:

```sh
sort -k2 -r data.txt
```

  ### Bạn có thể thêm -n nếu muốn sort theo số thay vì chữ:

  ```sh
sort -k2 -n data.txt       # Tăng dần theo số
sort -k2 -n -r data.txt    # Giảm dần theo số
```

---

# 12. Uniq command

## Lọc ra các dòng lặp lại trong một file:

```sh
sort filename.txt | uniq -d
```

##Lọc và đếm số dòng lặp lại:

```sh
sort filename.txt | uniq -c
```

---

# 13. chmod, chown, chattr command

## Phân quyền bằng số (Octal)

```sh
chmod 755 file.txt
```

## Phân quyền bằng chữ:

```sh
chmod u+x file.txt      # Thêm quyền thực thi cho owner
chmod g-w file.txt      # Gỡ quyền ghi cho group
chmod o=r file.txt      # Chỉ cho others quyền đọc
```

## chown – Thay đổi chủ sở hữu và nhóm

### Đổi user sở hữu:

```sh
chown username file.txt
```

### Đổi user và group:

```sh
chown username:groupname file.txt
```

## chattr – Thiết lập thuộc tính không thể thay đổi

### Đặt thuộc tính immutable (không cho sửa/xóa file):

```sh
sudo chattr +i file.txt
```

###Gỡ bỏ thuộc tính immutable:

```sh
sudo chattr -i file.txt
```

---

# 14. Find command

## Tìm các file có đuôi .log:

```sh
find . -type f -name "*.log"
```

## Tìm các thư mục tên abc:

```
find . -type d -name "abc"
```
## Tìm các file tên abc:

```
find . -type f -name "abc"
```
## Tìm file tên abc và set read-only:

```
find . -type f -name "abc" -exec chmod 444 {} \;
```

---

# 15. cp command

## Copy file:

```
cp file1.txt file2.txt
```
## Copy thư mục:

```
cp -r folder1/ folder2/
```

---

# 16. mv command

## Move file hoặc thư mục:

```
mv file.txt /path/to/destination/
mv folder/ /path/to/destination/
```

---

# 17. cut command

## Cắt ký tự thứ <n> trong string:

```
echo "abcdef" | cut -c 3       # → c
```
## Cắt từ ký tự thứ <n> trở về sau:

```
echo "abcdef" | cut -c 3-      # → cdef
```
## Cắt từ ký tự thứ <n> trở về trước:

```
echo "abcdef" | cut -c -3      # → abc
```

---

# 18. dig command

## Kiểm tra record A, MX, NS:

```
dig example.com A
dig example.com MX
dig example.com NS
``` 
## Kiểm tra với custom DNS (VD: 8.8.8.8):

dig @8.8.8.8 example.com A
dig @8.8.8.8 example.com MX
dig @8.8.8.8 example.com NS

---

# 19. tar, zip, unzip command

## Nén file/thư mục thành .tar.gz:

```
tar -czvf archive.tar.gz folder/
```

## Giải nén .tar.gz:

```
tar -xzvf archive.tar.gz
```

## Nén file/thư mục thành .zip:

```
zip -r archive.zip folder/
```

## Giải nén .zip:

```
unzip archive.zip
```

---

# 20. mount / umount command

## Xem danh sách ổ đĩa (kể cả sdb):

```
lsblk
```

## Tạo thư mục mount:

```
sudo mkdir -p /mnt/test
```
   
## Mount ổ cứng /dev/sdb vào /mnt/test:

```
sudo mount /dev/sdb /mnt/test
```

## Umount thư mục /mnt/test:
```
sudo umount /mnt/test
```

---

# 21. Symbolic Links & Hard Links

## Định nghĩa Symbolic Link (Symlink):

* Là **liên kết tượng trưng** đến một file hoặc thư mục.
* Hoạt động giống như **shortcut**.
* Nếu file gốc bị xóa → symlink sẽ bị "gãy".

## ▸ Định nghĩa Hard Link:

* Là **liên kết thực sự** đến cùng 1 inode với file gốc.
* Nếu file gốc bị xóa → hard link vẫn hoạt động bình thường.

## ▸ Ví dụ:


### Tạo file test.txt
```
echo "Hello" > test.txt
```
### Tạo symlink:
```
ln -s test.txt symlink.txt
```
### Tạo hard link:
```
ln test.txt hardlink.txt
```

---

# 22. ls command

## Liệt kê danh sách file/thư mục:

```bash
ls
```

## Hiện thuộc tính file (quyền, chủ sở hữu, thời gian):

```bash
ls -l
```

## Hiện cả file ẩn:

```bash
ls -la
```

---

# 23. `ps` command

## Hiển thị các tiến trình đang chạy:

```bash
ps aux
```

## Kill tiến trình theo PID:

```bash
kill <PID>
```

---

# 24. `top` command

## Hiển thị tiến trình và tài nguyên sử dụng real-time:

```bash
top
```

# 25. Ý nghĩa thông số:

| Thông số     | Giải thích                                               |
| ------------ | -------------------------------------------------------- |
| Load average | Tải hệ thống trong 1, 5, 15 phút. < 1 là ổn (với 1 CPU). |
| us           | % CPU user sử dụng                                       |
| sy           | % CPU kernel sử dụng                                     |
| ni           | % CPU dành cho process `nice`                            |
| id           | % CPU rảnh                                               |
| wa           | % CPU chờ I/O                                            |
| hi           | % CPU xử lý ngắt phần cứng                               |
| si           | % CPU xử lý ngắt phần mềm                                |
| st           | % CPU bị VM khác lấy mất (trên máy ảo)                   |

## Trạng thái process:

* **Sleeping**: Đang chờ event 
* **Zombie**: Đã kết thúc nhưng chưa bị parent thu dọn
* **Running**: Đang chạy CPU

---

# 26. Free command – Kiểm tra bộ nhớ RAM

```
free -h
```

## Giải thích các cột:
|Cột	|Giải thích|
|------|-------------|
|total|	Tổng dung lượng RAM|
|used|	RAM đã sử dụng (bao gồm cache + buffer)|
|free|	RAM còn trống chưa dùng tới|
|shared	|RAM dùng để chia sẻ giữa các tiến trình|
|buff/cache|	RAM dùng làm buffer (I/O) & cache (page cache)|
|available|	RAM còn thực sự có thể dùng được cho ứng dụng mới (tính luôn RAM có thể giải phóng từ cache/buffer)|

---

# 27. df command – Kiểm tra dung lượng đĩa

```
df -h
```

## Giải thích:
|Cột|	Giải thích|
|---|---|
|Filesystem|	Thiết bị/partition|
|Size	|Tổng dung lượng|
|Used|	Đã sử dụng|
|Avail	|Dung lượng còn trống|
|Use%|	% đã dùng|
|Mounted on	|Mount point (gắn vào thư mục nào)|

---

# 28. Phân vùng / là gì?

  * / gọi là root partition – phân vùng gốc.

  * Là gốc của toàn bộ hệ thống file Linux (nơi chứa tất cả thư mục như /home, /etc, /bin, /var, ...)

  * Mọi thư mục khác đều là con của /.
