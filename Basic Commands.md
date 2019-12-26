# Basic Commands
Các chương trình và các gói cài đặt sẽ được lưu ở /bin /urs/bin /sbin /usr/sbin /opt.  
Xác định vị trí chương trình đang ở đâu dùng lệnh: Which <gói>.  
Xác định vị trí chương trình đang ở đâu mở rộng hơn ta dùng lệnh: Whereis <gói>.

## Truy cập thư mục

    | Lệnh | Kết quả |
    | -----| ----- |
    | cd X | Di chuyển tới thư mục X |
    | cd.. | Di chuyển tới thư mục cha |
    | cd - | Quay về thư mục cũ (vừa thoát đi) |
    | cd ~ | Quay trở về thư root |

## Exploring the Filesystem (Xem hệ thống tập tin)  

    | Lệnh | Kết quả | 
    | ----- | ----- |
    | ls | Liệt kê các nội dung ở thưc mục hiện tại |  
    | ls -a | Liệt kê toàn bộ tệp và thư mục ẩn |
    | ls -l | Hiển thị nội dung theo danh sách,chi tiết hơn |
    | tree | Liệt kê các tệp tin theo dạng hình cây |
    | tree -d | Chỉ liệt kê các thư mục mà không liệt kê file |

## Hard and Symbolic Links (Liệt kê cứng và tượng trưng)
### Liên kết cứng (hard link)
+ Là 1 *liên kết* (link) trỏ đến vị trí lưu 1 file trên ổ cứng.
+ Nếu đổi tên, xóa hoặc di chuyển file gốc sang thư  mục khác, hard link vẫn mở được file đó vì nó vẫn trỏ đến vị trí lưu file cố định trên ổ cứng.
+ Tên *hard link* có thể khác tên file gốc, *hard link*  có thể nằm trong một thư mục khác với thư mục file gốc. Vì vậy, 1 file có thể có nhiều tên file nằm ở các thư mục khác nhau.Khi truy cập vào *hard link*(VD: click chuột) sẽ truy cập thẳng đến file( mở file hoặc thực thi file).
+ Nếu đồng thời mở 1 file từ các *hard link* và tên file gốc, khi sửa ở 1 bản, các bản khác cũng thay đổi theo sau khi refresh hoặc reload vì thực chất là sửa trên cùng 1 file.
+ Nếu muốn xóa 1 *hard link* hoặc xóa tên file gốc nhưng còn 1 *hard link*, file vẫn không bị xóa. File chỉ bị xóa khi không còn gì trỏ đến vị trí lưu của nó => Muốn xóa file thì phải xóa tất cả tên file và toàn bộ các *hard link* của nó.
 - Lệnh tạo liên kết cứng là ln:  
 ```
     ln <file nguồn><file đích>
```
### Liên kết mềm (soft link)
+ Còn được gọi là Symbolic Link hoặc symlink.
+ là 1 liên kết tạo ra 1 đường dẫn khác đến thư mục hoặc file gốc.
+ VD: file gốc là test1 có đường dẫn là /usr/test1. Trong đó thư mục /home/huydx tạo ra 1 soft lnk đặt tên là test11 trỏ đến file đó. Khi truy cập 1 trong 2 đường dẫn đều là truy cập đến file test1.
+ Nếu đổi tên, hoặc xóa hay di chuyện file gốc sang thư mục khác thì soft link bị mất tác dụng, không truy cập được đến file đó nữa. Khác với hard link, khi xóa file có soft link, file bị xóa thật.
+ Có thể tạo *soft link với thư mục và file nằm trên partition(phân vùng) khác.
+ Soft link  được tạo bởi lệnh ln – s:
 ```
 ln –s <path/file_name> <soft-link_name>
 ```
**So sánh Hard link và Soft link**
+ Tên file giống như tên khai sinh và các hard link giống như các bí danh, Chúng đều tham chiếu trực tiếp đến 1 số inode cụ thể và từ đó trỏ tới các block đang lưu file trên ổ cứng. Đi từ tên file hay hard link đều thông quá số inode để đến cùng 1 vị trí trên ổ cứng.
+ *Soft link*  thì không tham chiếu trực tiếp đến số inode mà tham chiếu đến “cấp trung gian” là tên file(kèm theo 1 đường dẫn ở 1 thư mục cụ thể); từ tên file mới đến số inode rồi dùng inode để truy cập vào file. Vì vậy nếu tên file bị thay đổi, file bị di chuyển hoặc xóa là soft link "bơ vơ" không truy cập được vào nội dung file nữa .
+ *Hard link* chỉ tạo được với file nằm cùng một partition , không tạo được với thư mục hoặc file nằm trên partition khác .
+ *Soft link* tạo được với cả thư mục và thư mục / file nằm trên partition khác .
+ *Hard link* có thể làm việc với mọi ứng dụng . Soft link không được cho phép với 1 số ứng dụng .
+ *Hard link* , *Soft link* không làm tăng dung lượng ổ cứng .


## Lệnh tìm kiếm thư mục  

Để có danh sách theo đúng ý ta sử dụng grep làm bộ lọc. Nó sẽ chỉ in các dòng có chứa một hoặc nhiều chuỗi được chỉ định. Ví dụ:

![Imgur](https://i.imgur.com/ijdnPei.png)
 

- Ở đây nó đã liệt kê hết các tệp và thư mục có cả “zip” và “bin” trong tên của nó.
- Ký tự đại diện có thể sử dụng để tìm kiếm tên tệp chứa các ký tự cụ thể
| Ký tự đại diện | Kết quả |
| ----- | ----- |
| ?  | Phù hợp với bất kỳ ký tự đơn nào |
| * | Phù hợp với bất kỳ chuỗi ký tự nào |


-	Lệnh find vô cùng hữu ích và được sử dụng trong cuộc
```
find /var -name *.log
```

Sẽ có kết quả :  

![Imgur](https://i.imgur.com/LS4t3YB.png)

- Tìm kiếm tệp và thư mục có tên là “gcc”:

     $ find /usr -name gcc

- Chỉ tìm kiếm các thư mục có tên là “gcc”;

     $find /usr –type d –name gcc

- Chỉ tìm kiếm các tệp thông thường có tên là “test1”:

     $ find /usr -type f -name test1

- Tìm kiếm dựa trên kích thước

	$ find / -size +10M

Tìm kiếm file có kích thước lớn hơn 10 MB

Quản lý tập tin

Sử dụng các lệnh sau để xem tệp:

| Lệnh | Sử dụng |
| ----- | ----- |
| cat | Được dùng để xem các tệp ngắn |
| tac | Được dùng để xem một tập tin ngược, bắt đầu với dòng cuối cùng |
| less | Được dùng để xem các tệp lớn hơn vì đây là chương trình phân trang. Nó dùng ở mỗi màn hình văn bản và cho phép tìm kiếm và điều hướng trong tệp |
| tail | Được sử dụng để in ra 10 dòng cuối cùng của tệp theo mặc định |
| head | Được sử dụng để in ra 10 dòng đầu tiên của một tệp tin

Ta có thể sử dụng lệnh touch để tạo một tệp rỗng:
 
![Imgur](https://i.imgur.com/lkcOJaF.png)

Với tùy chọn –t ta có thể đặt dấu ngày giờ của tệp. Để có thể đặt dấu thời gian thành thời gian củ thể ta dùng lệnh:
![Imgur](https://i.imgur.com/xDQOsGF.png)
Ta dùng lệnh mkdir để tạo một thư mục. Xóa một thư mục ta dùng lệnh rmkdir. Thư mục này phải trống bằng không nó sẽ không xóa đc.
![Imgur](https://i.imgur.com/SW0as7i.png)
## So sánh các tệp tin
Ta sử dụng lệnh diff để so sánh các tập tin và thư mục
![Imgur](https://i.imgur.com/uWhNHZt.png)

