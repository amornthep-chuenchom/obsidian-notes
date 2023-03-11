# Block Scope

**Block Scope** คือ scope ที่สามารถใช้งานโค้ดทั้งหมดที่อยู่ภายใน block ได้, block คือ อะไรแบบ if statement หรือ loop ต่าง ๆ 
```javascript
const x = 100;

if (true) {
	console.log(x); // 100
	const y = 200;
	console.log(x + y); // 300
}

console.log(y) // ReferenceError: y is not defined
```
จากตัวอย่าง เราไม่สามารถเข้าถึงตัวแปร y จากใน global scope ได้ เพราะ y เป็นของ if statement block

### Loop Example

```javascript
for (let i = 0, i < 10; i++) {
	console.log(i);
}
console.log(i) // ReferenceError: i is not defined
```
จากตัวอย่าง ตัวแปร i สามารถใช้งานได้จากภายใน loop เท่านั้น

### let & const vs var

ทั้ง `const` และ `let` เป็น block scope แต่ `var` ไม่มี block scope
```javascript
if (true) {
	const a = 500;
	let b = 600;
	var c = 700;
}

console.log(a); // ReferenceError: a is not defined
console.log(b); // ReferenceError: b is not defined
console.log(c); // 700
```
ถ้าเราใช้ `var` กับพวก block scope อย่าง if, loop ต่าง ๆ ตัวแปรแบบ var ก็ยังสามารถถูกเข้าถึงจากนอก block ได้, ซึ่งเป็นสิ่งที่ไม่เราไม่ต้องการให้มันเป็น
```javascript
for (var i = 0; i <= 10; i++) {
	console.log(i);
}

console.log(i); // 11
```

สิ่งหนึ่งที่ควรรู้ไว้เกี่ยวกับ `var` ก็คือ อย่างน้อยมันก็เป็น **function-scoped** หมายความว่าถ้าเราสร้างตัวแปรแบบ `var` ใน function ตัวแปรนี้จะไม่สามารถถูกเข้าถึงได้จากนอก function
```javascript
function run() {
	var d = 100;
	console.log(d); // 100
}

run();

console.log(d) // ReferenceError: d is not defined
```

ในการประกาศตัวแปรควรใช้ `let` หรือ `const` ยกเว้นแต่ว่าจะมีเหตุผลที่ดีพอในการใช้ `var` เพราะการที่ตัวแปรไม่สามารถถูกเข้าถึงจากนอก scope ของมันได้ถือว่าเป็นเรื่องดี

อีกข้อแตกต่างจาก `var` คือเมื่อเราสร้างตัวแปรแบบ `var` เป็น global variable, ตัวแปรนั้นจะถูกนำไปใส่ใน `window` object ด้วย
```javascript
const foo = 1;
var bar = 2;

window
```

![[global-variable-var.png | center | 400]]


