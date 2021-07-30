# pymap
Pymap cung cấp một cách dễ dàng để sử dụng Nmap. Với Pymap, bạn có thể quên các cờ khác nhau mà bạn cần cung cấp cho Nmap mỗi khi bạn chơi CTF. Pymap bắt đầu bằng cách quét các cổng đang mở. Sau đó, Pymap cung cấp các cổng đang mở cho Nmap để quét phiên bản dịch vụ, chạy tập lệnh vuln, v.v. Điều này làm cho Pymap nhanh hơn so với cách chạy Nmap thông thường.

Pymap cũng cung cấp:

Ip quét,
Quét SMB
Quét NFS
sử dụng tập lệnh Nmap

**PS**:  nên học cách sử dụng Nmap trước khi sử dụng công cụ này

## UPDATED v 1.0
Pymap is using threading when performing a service scan. It reduces the time taken for service scans by more than 50% (Upon scanning a target with more than 5 open ports). I tested by scanning `beep.htb` which has 12 open ports. Pymap last version would take 350 sec, **V 1.0 takes only 150 sec!!!**

# requriments
- subprocess
- argparse

# Q&A
Tại sao sử dụng sudo?
đọc điều này thì bạn sẽ biết tại sao sudo. Hơn nữa, một cái gì đó quét bằng ping với sudo không thể phát hiện ra một số máy chủ ... không hiểu tại sao. Nếu bạn biết, xin vui lòng cho tôi biết

# usage
```console
$ python3 pymap.py -h # man page
$ sudo python3 pymap.py -t $IP # scan top 10k port
$ sudo python3 pymap.py -t $IP -A # scan every port
$ sudo python3 pymap.py -t $IP -smb # samba scan
$ sudo python3 pymap.py -t $IP -nfs # nfs scan
$ sudo python3 pymap.py -t 192.168.1.0/24 -pS # ping sweep on network, looking for alive hosts
```

# todo:
- [x] samba: `nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse <ip>`
- [x] rpcbind: `nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount <ip>`
- [x] ping sweep
- [x] created cool banner
- [x] Only perfrom SYN scan!!, (sudo = alway -sS)
- [x] improve speed (using thread?)
- [x] add -sC
- [x] remove `Service detection performed. Please report any incorrect results at https://nmap.org/submit/Nmap done: 1 IP address (1 host up) scanned in 2.10 seconds Starting Nmap 7.80 ( https://nmap.org ) at 2020-11-02 15:10 EST Nmap scan report for 10.200.11.232 Host is up (0.046s latency).`
- [ ] script=smb-brute?
