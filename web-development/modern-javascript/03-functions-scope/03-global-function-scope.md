# Global & Function Scope

**Scope** คือ ขอบเขตหรือพื้นที่ของส่วนของโค้ด โดยมันมีกฎสำหรับการเข้าถึงภายในขอบเขตด้วย

![[function-scope.png | center | 400]]

### Global Scope

ใน JavaScript เมื่อเราเขียนโค้ดอยู่ใน `global scope` โค้ดนั้นสามารถถูกเข้าถึงได้จากทุกที่, รวมถึงจากภายใน function ด้วย โดยถ้าเรา**ไม่ได้**เขียนโค้ดภายใน function หรือ block ต่าง ๆ เช่น if-else, loop นั่นแปลว่าโค้ดนั้นอยู่ใน `global scope`

#### The `window` object

browser สร้าง global object ที่เรียกว่า `window`  โดย `window` object ก็มี methods และ properties มากมายอยู่ภายในที่พร้อมให้ใช้งาน

`alert` method ของ window object
```javascript
window.alert("Hello World");
```
เนื่องจาก window object เป็น most top-level object ใน browser environment, เราจึงไม่จำเป็นต้องใช้ **window** ในการที่จะเข้าถึง method และ property ของมัน
```javascript
alert("Hello World");
```

ใน window object มี `innerWidth` property ที่เราก็สามารถนำมาใช้ได้ทุกที่เช่นกัน
```javascript
console.log(window.innerWidth);
console.log(innerWidth);
```
สามารถนำไปใช้ใน function ได้เช่นเดียวกันเพราะ window object มันคือ global object
```javascript
function run() {
	console.log(window.innerWidth);
}
```

#### Creating globally scoped variables

การสร้าง global variable สามารถทำได้ง่าย ๆ ด้วยการสร้างตัวแปรที่ด้านบนของไฟล์ JavaScript แล้วมันสามารถถูกเข้าถึงได้จากทุกที่
```javascript
const x = 100;
console.log(x); // 100
```
สามารถเข้าถึงตัวแปร x จากภายใน function ได้เช่นกันเพราะมันคือ global variable
```javascript
function run() {
	console.log(x); // 100
}
```

### Function Scope

**Function Scope** คือ scope ที่สามารถใช้งานโค้ดทั้งหมดที่อยู่ภายใน function ได้ และ ตัวแปรใดก็ตามที่ถูกกำหนดภายใน function จะสามารถใช้งานได้ภายใน function เท่านั้น
```javascript
function add() {
	const y = 50;
}

console.log(y); // ReferenceError: y is not defined
```
error จากการอ้างถึงตัวแปร y เพราะ JavaScript ไม่รู้จักตัวแปร y เนื่องจาก y มีชีวิตอยู่เฉพาะภายใน add() function เท่านั้น

ถ้ามี global variable ก็สามารถนำมาใช้ใน function ได้
```javascript
const x = 100;

function add() {
	const y = 50;
	console.log(x + y); // 150
}
```

สมมติเรามีตัวแปร x ที่เป็น global variable แล้วถ้าเราทำการสร้างตัวแปรที่ชื่อว่า x ภายใน function, มันจะทำการ overwrite หรือแทนที่ global variable นั้นทำให้ไม่สามารถเข้าถึงค่า x ที่เป็น global variable ภายใน function scope ได้อีกต่อไป ซึ่งนี่เรียกว่า **variable shadowing**
```javascript
const x = 100;

function add() {
	const x = 1;
	const y = 50;
	console.log(x + y); // 51
	console.log(x); // 1
}

console.log(x); // 100
```

**Variable Shadowing** คือ การที่มีตัวแปรถูกประกาศอยู่ภายใน scope แล้วตัวแปรนั้นมีชื่อเดียวกันกับตัวแปรที่อยู่นอก scope สิ่งที่เกิดขึ้นภายใน scope ใน คือมันจะทำการ overwrite หรือ แทนที่ ตัวแปรที่อยู่ scope นอก ด้วยตัวแปรที่ในอยู่ scope ใน ทำให้เมื่อมีการเรียกใช้งานตัวแปรที่ชื่อเดียวกันจาก scope ใน มันจะใช้ตัวแปรของ scope ในนั่นเอง แต่เมื่อมีการเรียกใช้งานตัวแปรที่ชื่อเดียวกันจาก scope นอก มันก็จะใช้ตัวแปรของ scope นอก

### Local Scope

local scope คือ scope อะไรก็ตามที่ถูกสร้างขึ้นมา เช่น function หรือ block ต่าง ๆ อย่าง if-else, loop เป็นต้น โดยตัวแปรที่ประกาศภายใน scope จะเป็น local variable และสามารถเข้าถึงหรือใช้งานได้เฉพาะใน scope เท่านั้น

