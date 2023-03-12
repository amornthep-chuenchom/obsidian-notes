# Stack vs Heap Memory Allocation

ชนิดข้อมูลแบบ `primitive` และ `reference` เก็บข้อมูลลง memory อย่างไร?

## Garbage Collection

JavaScript ใช้ **garbage collection** ในการจัดการ memory แบบอัตโนมัติ

ใน low-level programming languages อย่าง ภาษา `c` และ `c++`, ผู้เขียนโปรแกรมต้องจัดการ memory ด้วยตัวเอง อย่างตอนสร้างตัวแปรขึ้นมาใช้ก็ต้องจัดสรร memory ของตัวแปรนั้นด้วยตัวเองและเมื่อใช้งานตัวแปรนั้นเสร็จเราก็ต้องเคลียร์พื้นที่นั้นให้ว่างด้วย แต่ในภาษาสมัยใหม่อย่าง `JavaScript` และ `python` เราไม่จำเป็นต้องทำเรื่องพวกนี้ เพราะมันมีสิ่งที่จัดการเรื่องนี้ให้โดยอัตโนมัติซึ่งเรียกว่า garbage collection

## Memory Allocation

เมื่อมีการสร้างตัวแปร, JavaScript engine จะจัดสรรตัวแปรไปใน memory 2 แห่งที่แตกต่างกัน ซึ่งเรียกว่า `stack` และ `heap` 

**Primitive values** อย่าง strings, numbers และค่าอื่น ๆ เป็นข้อมูลที่คงที่และไม่สามารถเปลี่ยนแปลงได้  ด้วยเหตุนี้ขนาดของข้อมูลจึงไม่มีการเปลี่ยนแปลงเด็ดขาด ดังนั้นขนาดพื้นที่ที่ถูกจัดสรรให้ตัวแปรแบบ primitive จะมีขนาดตายตัวและถูกเก็บไว้ใน stack memory

```javascript
const name = "John";
const age = "30";
```

เพื่อให้มองเห็นภาพนี่คือตัวอย่างรูปของ memory stack ที่เกิดขึ้นจากโค้ดด้านบน

![[stack1.png | center | 250]]

สังเกตุได้ว่า memory ถูกจัดสรรเป็นกอง stack ทับ ๆ กันสำหรับตัวแปรและค่าของ name และ age เนื่องจากพวกมันคือ static primitive value 

ลองสร้าง **person** object
```javascript
const person = {
	name: "Brad",
	age: 40
}
```
เนื่องจาก object คือ reference type ซึ่งไม่คงที่เราสามารถเพิ่มหรือลบค่าจาก object ได้, object จะถูกเก็บภายใน heap memory

![[stack2.png | center | 680]]

ลองสร้างตัวแปรใหม่ที่มีชื่อว่า **newName** เพื่ออ้างถึงตัวแปร **name** ที่เก็บค่า primitive value ไว้ว่าจะเกิดอะไรขึ้น?
```javascript
const newName = name;
```
สิ่งที่เกิดขึ้นภายในการทำงานคือ JavaScript จะทำการ copy ค่า 'John' แล้วกำหนดให้กับตัวแปร **newName**

![[stack3.png | center | 680]]

ลองเปลี่ยนค่าของ **newName** เป็น **Jonathan**

```javascript
newName = "Jonathan";
```

![[stack4.png | center | 680]]
ค่าของตัวแปร **name** ยังคงเหมือนเดิมมีแค่ของตัวแปร **newName** เท่านั้นที่เปลี่ยนไป เพราะตอนคำสั่ง `const newName = name;` มันเป็น passed by value
> pass by value คือ การที่เรา copy ค่าของตัวแปรใน memory ออกมาเพื่อใช้งาน

ลองสร้างตัวแปรใหม่ที่ชื่อว่า **newPerson** แล้วกำหนด **person** ให้กับมัน
```javascript
const newPerson = person;
```

ตอนนี้ตัวแปร **newPerson** เก็บ reference ที่อ้างถึงค่าเดียวกันตัวแปร **person** ที่อยู่ใน heap

![[stack5.png | center | 680]]

ถ้าเราแก้ไขค่า name ของ newPerson object
```javascript
newPerson.name = "Bradly";
```
มันก็จะเปลี่ยนค่า name ของ object ที่ถูกอ้างถึงใน heap ทำให้ทั้ง **person** และ **newPerson** object มีค่าของ name ว่า Bradley เนื่องจาก `const newPerson = person;` คือการ passed by reference
> pass by reference (pass by address) คือ การที่เรา copy address ของค่าจริงที่เก็บไว้กับตัวแปรออกมาเพื่อใช้งาน

![[stack6.png | center | 680]]


