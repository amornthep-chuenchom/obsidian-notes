# Nested Scope

### Nested Functions

ใน JavaScript, เราสามารถกำหนด function ใน function ได้ ซึ่งมันเรียกว่า `nested function` นี่เกี่ยวข้องกับสิ่งที่เรียกว่า `closures` 

เมื่อพูดถึง scope ตัวแปรใดก็ตามที่กำหนดภายใน parent function ก็สามารถถูกเข้าถึงหรือใช้งานได้จากใน nested/child function แต่ไม่ใช่ในทางกลับกัน
```javascript
function first() {
	const x = 500;
	function second() {
		const y = 600;
		console.log(x); // 500
	}
	console.log(y); // ReferenceError: y is not defined

	second();
}

first();
```
จากตัวอย่างตัวแปร x ถูกกำหนดใน `first()`, ดังนั้น child function หรือ `second()` สามารถเข้าถึงตัวแปร x ได้ แต่ในทางกลับกันตัวแปร y ที่ถูกประกาศภายใน `second()` นั้นไม่สามารถถูกเข้าถึงจาก parent function หรือ `first()` ได้

สรุปก็คือเราสามารถเข้าถึงตัวแปรจาก parent function ได้ แต่ไม่สามารถเข้าถึงตัวแปรจาก child function ได้

### Nested If

เช่นเดียวกันกับ function, ตัวแปรที่ถูกประกาศใน parent block scope สามารถถูกเข้าถึงหรือใช้งานได้จากใน nested/child block scope แต่ไม่ใช่ในทางกลับกัน
```javascript
// Parent if
if (true) {
	const x = 100;
	// Nested/Child if
	if (x === 100) {
		const y = 200;
		console.log(x + y); // 300
	}
	// console.log(y) // ReferenceError: y is not defined
}
// console.log(x) // ReferenceError: x is not defined
// console.log(y) // ReferenceError: y is not defined
```



