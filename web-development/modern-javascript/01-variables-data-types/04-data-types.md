# Data Types

เมื่อเราสร้างตัวแปร, ข้อมูลที่กำหนดให้ตัวแปรก็มีประเภทของมัน โดยมีด้วยกัน 2 ประเภท คือ `primitive types` และ `reference types` ซึ่งความแตกต่างใหญ่ ๆ อยู่ที่การทำงานภายในเกี่ยวกับวิธีการเก็บและเข้าถึงข้อมูลจาก memory

1. **Primitive Types** - เก็บค่าข้อมูลลงไปตรง ๆ ในตัวแปร (stack memory) และเข้าถึงค่าข้อมูลตรง ๆ จากตัวแปรเช่นเดียวกัน (stack memory)
2. **Reference Types (Objects)** - เก็บ reference หรือ heap address ในตัวแปร (stack memory) แล้วเข้าถึงค่าข้อมูลโดยใช้ reference ที่เก็บไว้อ้างไปยังค่าของข้อมูลที่เก็บอยู่อีกที่หนึ่ง (heap memory)

## Primitive Data Types 

primitive data types ของ JavaScript มี 7 ชนิดดังต่อไปนี้

- `String` - ลำดับของตัวอักษร หรือ ข้อความ โดยใน JavaScript นั้น strings ต้องล้อมรอบด้วยเครื่องหมาย single หรือ double quotes หรือ backticks ก็ได้
- `Number` - ตัวเลข เป็นได้ทั้งจำนวนเต็มและเลขทศนิยม
- `Boolean` - ค่าความจริงสามารถเป็นได้ 2 ค่า เท่านั้นคือ `true` หรือ `false`
- `Null` - เป็นค่าว่าง โดยเป็นการตั้งใจให้มีค่าแบบนี้ (มีค่าแต่ค่าคือ `null` หรือ ค่าว่าง)
- `Undefined` - ตัวแปรที่ไม่ได้กำหนดค่า
- `Symbol` - คือ built-in object ของ constructor ซึ่ง return unique symbol
- `BigInt` - ตัวเลขจำนวนเต็มขนาดใหญ่ คือ ชนิดข้อมูลใหม่ที่ใช้สำหรับตัวเลขที่มีขนาดใหญ่เกินกว่าชนิดข้อมูล Number จะรับมือได้

## Dynamic vs Static Types

JavaScript คือ "dynamically-typed" language หมายความว่าในตอนที่เราสร้าง variable หรือ function เราไม่กำหนด data type อย่างชัดเจนให้มัน เพราะว่า JavaScript จะทำการกำหนด data type จาก value ของมันให้แบบ dynamic หรือจะพูดอีกอย่างว่า data type มีความเกี่ยวข้องกับ **value**, ไม่ใช่ **variable** ดังนั้นเราสามารถกำหนดค่าของตัวแปรเป็น string แล้วหลังจากนั้นเปลี่ยนค่าของตัวแปรเป็น number ได้ เราอาจจะไม่ได้ทำแบบนี้บ่อยนักแต่ว่ามันทำได้

มันมีภาษาอื่นที่เป็นแบบ "statically-typed" คือเราจะกำหนด data type ให้ variable หรือ function อย่างชัดเจน เช่น Java, C# เป็นต้น มันยังมีอีกภาษาที่เรียกว่า TypeScript ซึ่งโดยหลักการแล้วมันก็คือ JavaScript ที่มีคุณสมบัติพิเศษเพิ่มเติม, รวมไปถึงมี data types ดังนั้นใน TypeScript เราสามารถทำแบบนี้ได้
```typescript
const y:number = 100
```
จากตัวอย่างเรากำหนดให้ตัวแปร y เป็น **number** ดังนั้นตั้งแต่นี้ไปค่าของตัวแปร y **ต้องเป็น** number เสมอ

ซึ่งนี่ไม่ใช่สิ่งที่เราสามารถทำได้ด้วย Vanilla JavaScript (Pure JavaScript) โดยประโยชน์ของ static types คือ มันทำให้โค้ดมีประสิทธิภาพมากยิ่งขึ้นและมีแนวโน้มจะเกิด error น้อยลง ส่วนข้อเสียก็คือเราต้องเขียนโค้ดเยอะขึ้น

## Assigning Variables

### String

String คือ สายของตัวอักษรต้องล้อมรอบด้วยเครื่องหมาย single หรือ double quotes หรือ backticks โดย string สามารถประกอบด้วย ตัวเลข, ตัวอักษร และ เครื่องหมาย
```javascript
const firstName = "Kenny";
```

### Number

ชนิดข้อมูล Number คือ ตัวเลขใดก็ตามใน JavaScript, รวมถึง floats และ decimals ในบางภาษาจะแยกประเภทข้อมูลของเลขทศนิยมกับเลขจำนวนเต็มออกจากกัน แต่ว่า JavaScript ไม่ได้แยก โดย Number ไม่ล้อมรอบด้วยเครื่องหมายคำพูด
```javascript
const age = 27;
const size = 52.5;
```

### Boolean

Boolean คือ ค่าความจริงโดยมีค่าเป็น true หรือ false เท่านั้น
```javascript
const hasKids = false;
```

### Null

Null คือ ค่าว่าง โดยเป็นการตั้งใจให้มีค่าแบบนี้ (มีค่าแต่ค่าคือ `null` หรือ ค่าว่าง)
```javascript
const loyalGirl = null
```

### Undefined

Undefined หมายถึง ตัวแปรที่ไม่มีการกำหนดค่าให้
```javascript
let score;
const score = undefined;
```

### Symbol

Symbol หมายถึง unique identifier
```javascript
const id = Symbol('id');
```

### BigInt

BigInt คือ ชนิดข้อมูลใหม่แบบ primitive ซึ่งหมายถึง เลขจำนวนเต็มที่มีขนาดใหญ่เกินกว่าขอบเขตของชนิดข้อมูล Number
```javascript
const n = 9007199254740991n;
```

### typeof Operator

ตัวดำเนินการ typeof ใช้ในการตรวจสอบชนิดข้อมูลของตัวแปรใน JavaScript
```javascript
const name = "Eric";
console.log(typeof name); // string
```

**Tip:** ถ้าเราใช้ typeof กับตัวแปรที่เก็บค่า `null` เอาไว้ ผลลัพธ์ที่ได้จะเป็น `object` ซึ่งนี่ถือว่าเป็นข้อผิดพลาด More Info [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#typeof_null)
```javascript
const loyalGirl = null;
console.log(typeof loyalGirl); // object
```

## Reference Data Types (Objects)

Reference Data Types มีด้วยกัน 3 ประเภท

- `Arrays`
- `Functions`
- `Objects`

โดยทางเทคนิคแล้วพวกมันเป็น "objects" ทั้งหมด, หมายความว่ามันมี properties และ methods

Reference types หรือ "objects" เป็นค่าที่ไม่ใช่ค่าแบบ primitive แล้วเมื่อทำการกำหนดค่าให้กับตัวแปร, ตัวแปรนั้นจะได้รับ **reference** ที่อ้างไปยังค่าจริง ๆ ของมันโดย reference จะชี้ไปที่ตำแหน่งของ object ใน memory (heap) ไม่เหมือนกับ primitive ที่ตัวแปรจะเก็บค่าจริง ๆ ของมันไว้ที่ตัวแปรเลย

### Arrays

Arrays โดยพื้นฐานแล้วมันคือโครงสร้างข้อมูลที่สามารถเก็บค่าได้หลาย ๆ ค่า ไว้ในตัวแปรเดียว
```javascript
const numbers = [1, 2, 3, 4, 5];
```
เราได้ทำการสร้าง array ใน heap memory และ ตัวแปรใน stack memory ที่เก็บ reference ซึ่งชี้ไปยังตำแหน่งของ array นี้

### Object Literals

Objects คือ ลิสต์ที่เก็บข้อมูลในรูปแบบของคู่ `name:value` โดยแบ่งข้อมูลแต่ละตัวด้วยเครื่องหมาย comma 
```javascript
{
	firstName: "Pedro",
	lastName: "Pascal",
	age: 47
}
```

### Functions

Functions ก็คือ objects ใน JavaScript มันสามารถมี `properties` และ `methods` โดยสิ่งที่ทำให้มันแตกต่างจาก object อื่น ๆ คือมันสามารถถูกเรียกใช้งานได้
```javascript
const sayHello = function() {
	return "Hello";
}

sayHello();
```

ถ้าเราทำการตรวจสอบประเภทข้อมูลของ arrays และ object literals ด้วย typeof จะได้ผลลัพธ์ออกมาเป็น "object" แต่สำหรับ function จะได้ผลลัพธ์เป็น "function" ซึ่งมันก็ยังคงเป็น object เพียงแต่ถูกระบุเป็น function object


