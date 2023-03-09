# Variables

Variables คือ ภาชนะสำหรับใส่ข้อมูล โดยข้อมูลนั้นมีหลายชนิดแตกต่างกันไป

## Declaring a Variable

ใน JavaScript, เราต้องประกาศตัวแปรก่อนด้วย 1 ใน 3 keywords นี้
- var
- let
- const

ใน modern JavaScript เราคงจะไม่เห็น `var` บ่อยนัก, `var` เคยเป็นต้นแบบในการประกาศตัวแปร แต่ใน `ES2015` หรือ `ES6` ที่มีการอัปเดตครั้งใหญ่ของภาษามีการนำการประกาศตัวแปรด้วย `let` และ `const` เข้ามาซึ่งมันมี `block scope` ที่ช่วยให้เราเขียนโค้ดได้ clean และเข้าใจง่ายยิ่งขึ้นจึงเป็นทางเลือกที่ดีกว่าในการประกาศตัวแปร 
> var ไม่มี concept ของ block scope ไม่ควรใช้อีกต่อไป

`var` และ `let` มีการหลักทำงานที่เหมือนกัน ส่วน `const` นั้นแตกต่างออกไปนิดหน่อย

%%`global scope` หมายถึง ไม่ได้อยู่ใน function หรือ control structure (block `{...}`)%%

example: 
```
let firstName = "Tsubaki";
let lastName = "Sannomiya";

console.log(firstName, lastName); // Tsubaki Sannomiya
```

## Variable Naming Conventions

- การตั้งชื่อสามารถใช้ได้แค่ ตัวอักษร, underscore (`_`), ตัวเลข และ dollar sign (`$`) เท่านั้น
- การตั้งชื่อไม่สามารถขึ้นต้นด้วยตัวเลขได้

ไม่ควรตั้งชื่อตัวแปรโดยเริ่มต้นด้วยทั้ง dollar sign หรือ underscore

### Multi-Word Variables

ในการตั้งชื่อ ตัวแปร, ฟังก์ชัน และ คลาส ที่ประกอบด้วยหลาย ๆ คำ ใน JavaScript จะ**นิยม**เขียนในรูปแบบ `camelCase` โดยคำแรกที่เริ่มต้นจะเป็นตัวพิมพ์เล็ก แต่คำอื่น ๆ หลังจากนั้นจะเริ่มต้นตัวอักษรแรกด้วยตัวพิมพ์ใหญ่
```
let firstName = "Kenny";
```
เราอาจจะเจอการตั้งชื่อด้วย underscores แบบนี้
```
let first_name = "Chirs";
```
นอกจากนี้ยังมี `PascalCase` ที่คำแรกเริ่มต้นด้วยตัวพิมพ์ใหญ่ โดยเรามักจะเจอการตั้งชื่อแบบนี้สำหรับ class ใน OOP 
```
let FirstName = "Lalo";
```
แล้วอาจจะเจอการตั้งชื่อแบบตัวพิมพ์เล็กทั้งหมด ซึ่งไม่แนะนำ
```
let firstname = "Okada";
```

## Reassigning Values

การกำหนดค่าใหม่ให้กับตัวแปรสามารถทำได้กับตัวแปรแบบ `var` และ `let` เท่านั้น 

> ไม่สามารถทำได้กับตัวแปรแบบ `const` เนื่องจาก const ย่อมาจาก **constant** ที่แปลว่าคงที่ซึ่งหมายถึงค่าของตัวแปรนี้เป็นค่าคงที่ไม่มีการเปลี่ยนแปลงตลอดการทำงานของโปรแกรม 

```
let worldChamp = "Kenny Omega";

// Kenny Omega lose match against Adam Page, let's reassign worldChamp variable

worldChamp = "Adam Page";
```

ในบางกรณี เราอาจต้องการแค่ประกาศตัวแปรไว้แต่ไม่ต้องการกำหนดค่าลงไป
```
let score;
```
ในกรณีนี้, `score` จะเท่ากับ **undefined**, ซึ่งจริง ๆ แล้ว undefined คือ 1 ใน 7 primitive data types
ถ้าเราต้องการกำหนดค่าให้ตัวแปร เราสามารถทำได้ทุกเมื่อ
```
score = 99;
```

## Constants

`const` มีหลักการทำงานแตกต่างจาก `let` หรือ `var` เล็กน้อย