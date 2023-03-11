# Introduction

## The Web

**World Wide Web** หรือ Web คือ ระบบข้อมูลที่มี document คอยให้บริการอยู่บน internet 
โดย document เหล่านี้ส่งหากันระหว่าง client และ web server ผ่าน protocol ที่เรียกว่า HTTP (HyperText Transfer Protocol)

## HTTP

**Protocol** คือ ข้อกำหนดหรือภาษากลางในการสื่อสารระหว่างคอมพิวเตอร์

**HTTP (HyperText Transfer Protocol)** คือ กฎสำหรับการสื่อสารระหว่าง client (requester) และ  server (responder)

## Web Browser

**Web Browser** หรือ โปรแกรมท่องเว็บ ใช้ในการ *request* เพื่อเรียกดู web page โดยจะนำ *response* ที่ได้มาจาก web server (ไฟล์ HTML, CSS, JS) มาทำการ render และแสดง web page ออกมาที่คนทั่วไปสามารถอ่านและเข้าใจได้

## Clients

**Clients** หรือ ผู้ขอใช้บริการ ก็คือ เครื่องคอมพิวเตอร์, แท็บเล็ต, สมาร์ทโฟน หรือ อุปกรณ์ใด ๆ ที่ *request* web page จาก web server ผ่านโปรแกรมที่เรียกว่า *web browsers*  

## Web Server

**Web Server** คือ คอมพิวเตอร์ที่ต้องออนไลน์ตลอด 24/7 เพื่อเตรียมพร้อมให้บริการ request ที่เข้ามาจากฝั่ง client (โดยผ่านทาง browser) แล้วส่ง response ของ web page ที่ถูก request มากลับไปยัง client (ซึ่ง Web server จะเก็บไฟล์ที่ใช้ในการสร้าง web application เอาไว้)

# How The Web Works

![[how-the-web-work.png | center | 700]]

เมื่อมีการเข้าเว็บ ไม่ว่าจะเป็นการคลิก link, พิมพ์ชื่อเว็บใน browser หรือ refresh page มันคือการสร้าง HTTP request ไปยัง web server เพื่อขอ document ของเว็บ จากนั้น web server ทำการค้นหา document ของ web page แล้วส่งเป็น HTTP response กลับไปที่ client จากนั้น browser ก็ทำการ render และแสดง web page ออกมา

## Web Server's Response Analogy

![[web-server-response-analogy.png | center | 700]]

Response ของ Web Server เปรียบได้กับการซื้อ furniture ที่ IKEA สิ่งที่เราได้กลับบ้านคือชิ้นส่วนประกอบต่าง ๆ ที่ต้องนำมาประกอบเองที่บ้าน

![[http-response.png | center | 500]]

โดยสิ่งที่ Web Server ส่งกลับไป (HTTP Response) จริง ๆ แล้วคือ code ที่ browser ของเรานำมา render ให้กลายเป็นเว็บเพจที่สวยงาม

## Another Way to Make a Request 

เราสามารถสร้าง request ด้วย Tools อีกอันที่ไม่ใช่ Web Browser ได้ก็คือ โปรแกรม Postman ส่วนใหญ่คนใช้คือ Developer เพื่อทดสอบ website's api ว่าใช้งานได้หรือไม่

![[postman-logo.png | center | 300]]

![[postman-example.png | center | 500]]


