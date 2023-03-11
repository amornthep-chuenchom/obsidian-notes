# Variables

Variables คือ ภาชนะสำหรับใส่ข้อมูล โดยข้อมูลนั้นมีหลายชนิดแตกต่างกันไป

## Declaring a Variable

ใน JavaScript, เราต้องประกาศตัวแปรโดยเริ่มด้วย 1 ใน 3 keywords นี้
- var
- let
- const

ใน modern JavaScript เราคงจะไม่เห็น `var` บ่อยนัก, `var` เคยเป็นการประกาศตัวแปรแบบดั้งเดิม แต่ใน `ES2015` หรือ `ES6` ที่มีการอัปเดตครั้งใหญ่ของภาษามีการนำการประกาศตัวแปรด้วย `let` และ `const` เข้ามาซึ่งมันมี `block scope` (ขอบเขตของตัวแปร) ที่ช่วยให้เราเขียนโค้ดได้ clean และเข้าใจง่ายยิ่งขึ้นจึงเป็นทางเลือกที่ดีกว่าในการประกาศตัวแปร 

> var ไม่มี concept ของ block scope ไม่ควรใช้อีกต่อไป
> โดยมันมีขอบเขตภายในฟังก์ชันที่มันอยู่ และเพิกเฉยต่อขอบเขตของบล็อค เช่น if for หรือคำสั่งอื่นๆ

```javascript
if (true) {
    var name = "Metin";
}
console.log(name);  // Metin
```


`var` และ `let` มีการหลักทำงานที่เหมือนกัน ส่วน `const` นั้นแตกต่างออกไปนิดหน่อย

%%`global scope` หมายถึง ไม่ได้อยู่ใน function หรือ control structure (block `{...}`)%%

example: 
```javascript
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
```javascript
let firstName = "Kenny";
```
เราอาจจะเจอการตั้งชื่อด้วย underscores แบบนี้
```javascript
let first_name = "Chirs";
```
นอกจากนี้ยังมี `PascalCase` ที่คำแรกเริ่มต้นด้วยตัวพิมพ์ใหญ่ โดยเรามักจะเจอการตั้งชื่อแบบนี้สำหรับ class ใน OOP 
```javascript
let FirstName = "Lalo";
```
แล้วอาจจะเจอการตั้งชื่อแบบตัวพิมพ์เล็กทั้งหมด ซึ่งไม่แนะนำ
```javascript
let firstname = "Okada";
```

## Reassigning Values

การกำหนดค่าใหม่ให้กับตัวแปรสามารถทำได้กับตัวแปรแบบ `var` และ `let` เท่านั้น 

> ไม่สามารถทำได้กับตัวแปรแบบ `const` เนื่องจาก const ย่อมาจาก **constant** ที่แปลว่าคงที่ซึ่งหมายถึงค่าของตัวแปรที่ประกาศเป็น constant นี้เป็นค่าคงที่ไม่มีการเปลี่ยนแปลงตลอดการทำงานของโปรแกรม 

```javascript
let worldChamp = "Kenny Omega";

// Kenny Omega lose match against Adam Page, let's reassign worldChamp variable

worldChamp = "Adam Page";
```

ในบางกรณี เราอาจต้องการแค่ประกาศตัวแปรไว้แต่ไม่ต้องการกำหนดค่าลงไป
```javascript
let score;
```
ในกรณีนี้, `score` จะเท่ากับ **undefined**, ซึ่งจริง ๆ แล้ว undefined คือ 1 ใน 7 primitive data types
ถ้าเราต้องการกำหนดค่าให้ตัวแปร เราสามารถทำได้ทุกเมื่อ
```javascript
score = 99;
```

## Constants

`const` มีหลักการทำงานแตกต่างจาก `let` หรือ `var` เล็กน้อย 

โดยเราไม่สามารถกำหนดค่าใหม่ลงไปในตัวแปรแบบ `const` ตรง ๆ ได้ 
```javascript
const x = 100;
// and then I try re-assign that value
x = 200; // Results in error
```

และก็ไม่สามารถประกาศตัวแปรแบบ const โดยที่ไม่กำหนดค่าเริ่มต้นให้มันได้ เพราะ `const` จำเป็นต้องถูกประกาศโดยกำหนดค่าเริ่มต้นให้เสมอ
```javascript
const score; // Results in error
```

แต่เมื่อเราใช้ตัวแปรแบบ `const` กับค่าที่ไม่ใช่ primitive types แต่เป็น reference types เช่น `arrays` และ `object literals` ในกรณีนี้เราก็ไม่สามารถกำหนดค่าใหม่ลงไปตรง ๆ ให้กับตัวแปรได้เช่นกัน
```javascript
const arr = [1, 2, 3, 4];
// What I can't do is re-assign
arr = [1, 2, 3, 4, 5]; // Results in error
```

แต่เราสามารถเปลี่ยนค่ามันได้ เช่น  เพิ่มค่าลงไปใน array ด้วย push method และ เปลี่ยนค่าของอาเรย์ใน index ที่ต้องการได้
```javascript
const arr = [1, 2, 3, 4];
arr.push[5]; // [1, 2, 3, 4, 5];
arr[0] = 200; // [200, 2, 3, 4, 5];
```

สามารถทำแบบเดียวกันได้กับ object literals
```javascript
const person = {
	name: "Brad";
}

person.name = "John";
person.email = "john@gmail.com";

console.log(person);

/*
	Results in...
	{
		name: "John",
		email: "john@gmail.com"
	}
*/
```

## Declaring multiple values at once

หากต้องการประกาศตัวแปรหลายตัว เราไม่จำเป็นต้องประกาศตัวแปรทีละบรรทัด, เราสามารถประกาศตัวแปรหลาย ๆ ตัวพร้อมกันทีเดียว ในบรรทัดเดียวกันได้เลย

```javascript
let a, b, c;
const d = 10, e = 20, f = 30;
```

## Let or Const - Which to Use?

ที่แนะนำคือให้ใช้ `const` เสมอ ยกเว้นแต่ว่าเรารู้ว่าตัวแปรต้องกำหนดค่าเริ่มต้นเป็น undefined หรือ มีค่าเป็น primitive value ที่อาจต้องกำหนดค่าใหม่ให้มันในภายหลังจึงใช้ `let`

> ไม่แนะนำให้ใช้ตัวแปรแบบ `var` เลยเพราะไม่มี concept ของ block scope

