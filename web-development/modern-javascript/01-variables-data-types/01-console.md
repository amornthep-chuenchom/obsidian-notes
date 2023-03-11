# The JavaScript Console

ในการสร้าง front-end web applications เราจะทำงานใน browser, เราสามารถใช้ JavaScript ในการจัดการ DOM (Document Object Model) และแสดงค่าผลลัพธ์ (values) และ element ต่าง ๆ แต่บ่อยครั้งเราต้องการวิธีที่รวดเร็วในการดูค่าผลลัพธ์และ errors หรือ warnings ต่าง ๆ ใน scripts ที่ run อยู่ด้วย นี่คือเหตุผลว่าทำไมต้องมี JavaScript Console

Console คือ ส่วนหนึ่งของ **Developer Tools** ใน Web Browser 

Open DevTools from Chrome menus
1. Menu (Kebab Menu)
2. More Tools
3. Developer Tools

Open DevTools with shortcuts on Windows
- `CTRL+SHIFT+I`
- `F12`

Directly Open to Console with shortcuts on Windows
- `CTRL+SHIFT+J`

## Console methods

`console` คือ `global object` ที่มี method ที่มีประโยชน์มากมายที่เราสามารถนำไปใช้ใน JavaScript file ได้เลยเพื่อโต้ตอบกับ console
> method ก็คือ function ที่เป็นของ object

### console.log()
`log()` method แสดงค่าอะไรก็ตามที่ได้รับเข้ามาเป็น argument ออกทางหน้า console โดยค่า argument ดังกล่าวสามารถเป็นได้ทั้ง string, number, boolead, object, array หรือแม้แต่ function

Log a number
```javascript
console.log(123); // 123
```

Log a string
```javascript
console.log("Hello World"); // Hello World
```

Log multiple values

ใช้ comma ในการแยกแต่ละค่าออกจากกัน
```javascript
console.log(123, "Hello", true) // 123 'Hello' true
```

Log a variable

โดยส่วนใหญ่ เราจะใช้ console ในการ debug และ แสดงค่าของ variables หรือ ผลลัพธ์ของ function หรือ network request 
```javascript
x = 100;
console.log(x); // 100
```

### console.error()
`error()` method จะแสดงข้อความเป็นสีแดงออกทางหน้า console
```javascript
console.error("This is an error!"); // This is an error!
```

### console.warn()
`warn()` method จะแสดงข้อความเป็นสีเหลืองออกทางหน้า console
```javascript
console.warn("This is a warning!"); // This is a warning!
```

### console.clear()
`clear()` method เคลียร์หน้าจอ console
```javascript
console.clear();
```

### console.table()
`table()` method แสดง object ออกมาในรูปแบบของตารางออกทางหน้า console
```javascript
console.table({ name: "Maxwell Jacob Friedman", finisher: "Salt of the Earth"});
```
![[console-table-method-result.png]]

### console.group()
`group()` method สร้างกลุ่มใน console
```javascript
console.group("group-name");
console.log(x);
console.error("This is an error!");
console.warn("This is a warning!");
console.groupEnd();
```
![[console-group-result.png]]

### Log with style
ใส่ CSS style ใน `console.log()`
```javascript
const styles = "padding: 10px; background-color: aqua; color: white;";
console.log("%cHello", styles);
```
![[log-with-style.png]]

There are even more methods. See all of them [here](https://developer.mozilla.org/en-US/docs/Web/API/console)
