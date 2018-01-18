# Các yếu tố ảnh hưởng đến hiệu suất của ổ cứng HDD

![Imgur](https://i.imgur.com/8p0LRfy.png)

Hiệu suất của ổ cứng rất quan trọng đối với tốc độ chung của cả hệ thống, một ổ cứng chậm 
sẽ làm hạn chế đi rất nhiều tốc độ của bộ vi xử lý (cpu). Hiệu suất của ổ cứng bị ảnh 
hưởng bởi những yếu tố dưới đây.

## 1. Tốc độ của quay của tấm đĩa ( rotation speed of the platters )

- Tốc độ quay của ổ đĩa tính theo đơn vị vòng/phút ( round per min - RPM) là yếu tố quan 
trọng nhất ảnh hưởng đến tốc độ ổ cứng vì nó tác động trực tiếp đến **độ trễ** (latency) 
và **tốc độ đọc/ghi dữ liệu** ( disk transfer rate ).

- Tốc độ quay càng cao, càng nhiều dữ liệu được truyền qua đầu từ.

	- Tốc độ phổ biến của chuẩn ổ cứng **EIDE** là 7200rpm, **SCSI** là 7200rpm, 15000rpm.

- Để cải thiện tốc độ ổ cứng, số vòng quay tăng lên cũng làm tăng nhiệt lượng tỏa ra, 
	dễ gây mất ổn định và giảm tuổi thọ ổ cứng. Để hạn chế việc này, các nhà sản xuất đã 
	**làm nhỏ đi kích thước tấm đĩa**. Kích thước càng *nhỏ* càng *giảm độ ma sát* giữa mặt đĩa 
	với không khí.
	
	- Kích thước chuẩn của tấm đĩa (platter) là 3 inch với ổ cứng kích thước 3.5 inch, 
	2.5 inch với ổ có kích thước 3 inch.
	
## 2. Độ trễ ( Latency)

- Độ trễ tính theo đơn vị **miliseconds** bao gồm cả **thời gian tìm thông tin** (seek time) 
và độ trễ của trục quay ( rotational latency). 

	- Seak Time : thời gian mà đầu từ đọc/ghi của ổ cứng tìm đến nơi chứa dữ liệu trên mặt đĩa. 

- Độ trễ là thời gian trung bình để đầu từ tìm đến đúng vị trí của sector chứa dữ liệu sau khi 
hoàn thành việc tìm kiếm. 

	- Công thức tính độ trễ ổ đĩa:
	
	`(1/(spindle speed/60))*0.5*1000`
	
	Trong đó: 
	- Spindle speed là tốc độ trục quay của ổ đĩa ( rpm)
	- 60 giây, 0.5 là tính theo nửa vòng quay của ổ đĩa, 1000 để quy chuẩn giây ra mili giây.
	
	**Ví dụ**: Với ổ đĩa có rpm là 7200 rpm, latency là: `(1/(7200/60))*0.5*1000= 4.17 ms
	
- Thời gian truy cập trung bình của ổ đĩa bao gồm thời gian hệ thống yêu cầu dữ liệu và thời gian 
mà dữ liệu được trích xuất ra từ ổ đĩa. Thời gian truy cập gồm thời gian thời tìm kiếm dữ liệu, độ 
trễ của trục quay và thời gian thực thi dòng lệnh từ hệ thống.

## 3. Tốc độ truy xuất dữ liệu ( the disk transfer rate )

- Tốc độ truy xuất dữ liệu ( hay còn gọi là tỷ lệ truyền thông ) là tốc độ dữ liệu được đọc/ghi từ 
ổ đĩa, đơn vị là **Megabyte per second (MBps)**. 

- Các đĩa cứng hiện đại có tỷ lệ truyền đĩa tăng lên từ đường kính bên trong tới đường kính ngoài của đĩa. 
Đây được gọi là kỹ thuật ghi âm theo vùng. Tấm đĩa càng có nhiều track thì càng có tốc độ cao.

	- Tốc độ ghi dữ liệu dựa trên độ dầy của Track ( Track per inch) và Bits per inch.
	- Track là một đường tròn xung quanh đĩa, mật độ track trong một khu vực 1 inch từ tâm đĩa càng lớn
		thì tốc độ đọc/ghi càng cao.
	- BPI xác định bao nhiêu bits được ghi vào 1 inch track của bề mặt đĩa.
	
- Host transfer rate là tốc độ mà máy tính có thể truyền dữ liệu qua các cổng kết nối 
IDE/EIDE hoặc SCSI đến CPU.

- Tốc độ trung bình của HDD là 200 MBps.

### IOPS ( Input/output per second )

- IOPS viết tắt từ Input – output per second (Nôm na là 1 truy cập đọc hoặc viết mỗi giây). 
Ở các thiết bị lưu trữ file thì băng thông (MBps) là thông số quan trọng nhất. 
Còn đối với các thiết bị lưu trữ cho đám mây CLOUD thì IOPS quyết định độ “nhạy” và độ “NHANH” của máy ảo.

- Ổ HDD truyền thống có 1 cần đọc và ổ dĩa tròn chứa dữ liệu. 
Khi mặt dĩa xoay, đầu đọc ở mũi cần sẽ đọc được 1 IO (đọc hoặc viết). 
Vậy trong trường hợp xấu nhất, cứ 1 vòng xoay thì ổ HDD sẽ cung cấp được 1 IO.

=> Vậy 1 ổ SAS 15,000 vòng sẽ cung cấp trung bình 15,000 / 60 ~ 220 IOPS.


##### Random IO và Sequential IO:

![Imgur](https://i.imgur.com/24f9HjO.png)

- IO được gọi là **sequential** khi dữ liệu được đọc và ghi liên tiếp lên các bit gần nhau 
của các sector liên tiếp nhau trên dĩa tròn. Sequential IO rất phù hợp với HDD. 
Và chỉ có 2 dạng sequential IO: đọc – đọc – đọc – … -đọc và viết – viết – viết- …-viết

- IO được gọi là **random** khi khi dữ liệu được đọc, tìm kiếm và ghi ngẫu nhiên 
lên các ô lộn xộn trên các sector phân bố ngẫu nhiên trên dĩa tròn. 
Nôm na, Random IO sẽ có dạng đọc – tìm kiếm – viết – tìm kiếm – viết – tìm kiếm …

*Lưu ý là mỗi lệnh đọc / viết / tìm kiếm sẽ mất 1 vòng xoay ổ dĩa*.

- Kiểu copy file có dung lượng lớn gọi là kiểu READ/WRITE tuần tự, gọi là sequential, viết tắt seq READ/WRITE.

- Kiểu copy nhiều file có dung lượng nhỏ gọi là kiểu READ/WRITE ngẫu nhiên, gọi là ramdom READ/WRITE, một thuật ngữ thường dùng khác nữa là 4k READ/WRITE.

Tại sao là 4k?

4k ở đây chính là nói đến những file hệ thống có dung lượng rất nhỏ , chỉ khoảng 4kB (~0.004MB), những file có dung lượng này được cho là ảnh hưởng lớn nhất đến tốc độ truy xuất của ổ cứng, chính vì thế người ta sử dụng thuật ngữ 4k để nói đến tốc độ truy xuất ngẫu nhiên

=> Do đó Random IO là “kẻ thù của ổ cứng”, máy ảo Cloud chạy HDD sẽ giật và lác do tốc độ rất thấp.
