### System Info
## Thông tin hệ thống Linux

Sử dụng lệnh cat /etc/*release để xem thông tin HĐH đang sử dụng
```
[root@localhost ~]# cat /etc/*release
CentOS Linux release 7.7.1908 (Core)
NAME="CentOS Linux"
VERSION="7 (Core)"
ID="centos"
ID_LIKE="rhel fedora"
VERSION_ID="7"
PRETTY_NAME="CentOS Linux 7 (Core)"
ANSI_COLOR="0;31"
CPE_NAME="cpe:/o:centos:centos:7"
HOME_URL="https://www.centos.org/"
BUG_REPORT_URL="https://bugs.centos.org/"

CENTOS_MANTISBT_PROJECT="CentOS-7"
CENTOS_MANTISBT_PROJECT_VERSION="7"
REDHAT_SUPPORT_PRODUCT="centos"
REDHAT_SUPPORT_PRODUCT_VERSION="7"

CentOS Linux release 7.7.1908 (Core)
CentOS Linux release 7.7.1908 (Core)

kernel version

[root@localhost ~]# uname -r
3.10.0-1062.el7.x86_64
```
Thông tin bộ nhớ (Memory Info)

- head /proc/meminfo  
```
    MemTotal:         995776 kB (Tổng bộ nhớ)  
    MemFree:          568132 kB (Bộ nhớ trống)  
    MemAvailable:     661624 kB (Bộ nhớ có thể dùng)  
    Buffers:            2108 kB (Bộ đếm)  
    Cached:           214220 kB (Lưu trữ)  
    SwapCached:            0 kB (Trao đổi bộ nhớ)  
    Active:           172768 kB ()  
    Inactive:         123824 kB (không hoạt động)  
    Active(anon):      80828 kB  
    Inactive(anon):     7332 kB
```
- File system (Tập tin hệ thống)
 ```
df -h
```
    Filesystem               Size  Used Avail Use% Mounted on
    devtmpfs                 475M     0  475M   0% /dev
    tmpfs                    487M     0  487M   0% /dev/shm
    tmpfs                    487M  7.8M  479M   2% /run
    tmpfs                    487M     0  487M   0% /sys/fs/cgroup
    /dev/mapper/centos-root   27G  1.3G   26G   5% /
    /dev/sda1               1014M  150M  865M  15% /boot
    tmpfs                     98M     0   98M   0% /run/user/0

Đếm số lượng CPU (Count the number of CPU)
```
cat /proc/cpuinfo | grep model | uniq -c
````

1 model           : 61
1 model name      : Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
1 model           : 61
1 model name      : Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz

The proc Filesystem (Hệ thống tập tin Proc)

- Tên máy chủ  

```
cat /etc/hostname
```

- Đổi tên hostname:  
```
    hostname NEW_NAME
```