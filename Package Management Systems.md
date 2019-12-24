### Package Management Systems
- PMS là một tập hợp các phần mềm dùng để quản lý và tự động hóa việc cài đặt, nâng cấp, gỡ bỏ các phần mềm/thư viện
- Các phần cốt lõi của bản phân phối Linux và hầu hết các phần mềm hỗ trợ của nó được cài đặt thông qua Package Management Sys. Mỗi gói chứa các tệp và các hướng dẫn khác cần thiết để làm cho một thành phần phần mềm hoạt động trên hệ thống. Các gói có thể phụ thuộc lẫn nhau. Có hai họ quản lý gói: những người dựa trên dpkg và những người sử dụng rpm làm trình quản lý gói cấp thấp của họ. Hai hệ thống không tương thích, nhưng cung cấp các tính năng giống nhau ở mức độ rộng.
## Hệ thống quản lý gói(Package Management Systems)
| High Level Tool | Low Level Tool | Family |
| ----- | ----- | ----- |
| zypper | rpm | SUSE |
| yum | rpm | Red Hat |

Cả hai hệ thống quản lý gói đều cung cấp 2 công cụ   
    - Công cụ cấp thấp(như là dpkg hoặc rpm) chăm sóc các chi tiết của việc giải nén gói riêng lẻ, chạy lệnh, cài đặt phần mềm chính xác
    - Công cụ cấp cao (apt-get,yum hoặc zyppper) hoạt động với các nhóm gói, tải các gói từ nhà cung cấp và tìm ra các phụ thuộc

Hầu hết người dùng chỉ làm việc với các công cụ cấp cao, công cụ này sẽ gọi các công cụ cấp thấp khi cần thiết. Theo dõi phụ thuộc là tính năng đặc biệt trong công cụ cấp cao, nó xử lý các chi tiết tìm kiếm và cài đặt từng phụ thuộc.

| Operation | RPM | Debian |
| ----- | ----- | ----- |
| Cài đặt một gói | rpm –i foo.rpm | dpkg --install foo.deb|
| Cài đặt một gói với các phụ thuộc từ kho lưu trữ | yum install foo |  apt-get install foo |
| Xóa một gói | rpm –e foo.rpm | dpkg --remove foo.deb |
| Xóa gói và phụ thuộc bằng kho lưu trữ | yum remove foo | apt-get remove foo |
| Cập nhật gói lên phiên bản mới | rpm –U foo.rpm | dpkg --install foo.deb |
| Cập nhật gói sử dụng kho lưu trữ và giải quyết các phụ thuộc | yum update foo | apt-get upgrade foo |
| Cập nhật toàn bộ hệ thống | yum update | apt-get dist-upgrade |
| Hiển thị các gói đã cài đặt | yum list installed |dpkg --list |
| Nhận thông tin về một gói được cài đặt bao gồm các tệp | rpm –qil foo | dpkg --listfiles foo |
| Hiển thị gói có sẵn có tên 'foo' | yum list foo | apt-cache search foo | 
| Hiện thị tất cả các gói có sẵn | yum list | apt-cache dumpavail |
| Hiển thị các gói một tập tin thuộc về | rpm –qf file | dpkg --search file |S
