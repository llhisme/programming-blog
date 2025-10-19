---
title: "JavaScript Cơ Bản #2: Biến, Kiểu Dữ Liệu và Toán Tử"
date: 2024-02-01
draft: false
description: "Tìm hiểu chi tiết về biến, các kiểu dữ liệu và toán tử trong JavaScript"
tags: ["javascript", "biến", "kiểu dữ liệu", "toán tử", "cơ bản"]
categories: ["JavaScript"]
series: ["JavaScript Cơ Bản"]
series_order: 2
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## Biến trong JavaScript

**Biến** (Variable) là nơi lưu trữ dữ liệu trong chương trình. JavaScript có 3 cách khai báo biến: `var`, `let`, và `const`.

### 1. Cách khai báo biến

```javascript
// var - cách cũ (không khuyến nghị)
var ten = "JavaScript";

// let - biến có thể thay đổi (khuyến nghị)
let tuoi = 25;

// const - hằng số (không thể thay đổi)
const PI = 3.14159;

console.log(ten, tuoi, PI);
```

### 2. Sự khác biệt giữa var, let và const

```javascript
// Ví dụ về scope (phạm vi)
function viDuScope() {
    if (true) {
        var a = 1;    // Function scope
        let b = 2;    // Block scope
        const c = 3;  // Block scope
    }
    
    console.log(a); // 1 - OK
    // console.log(b); // Lỗi! b không tồn tại ngoài block
    // console.log(c); // Lỗi! c không tồn tại ngoài block
}

// Ví dụ về hoisting
console.log(x); // undefined (không lỗi)
var x = 5;

// console.log(y); // Lỗi! Cannot access 'y' before initialization
let y = 10;

// Ví dụ về const
const mang = [1, 2, 3];
mang.push(4); // OK - có thể thay đổi nội dung
console.log(mang); // [1, 2, 3, 4]

// mang = [5, 6, 7]; // Lỗi! Không thể gán lại
```

### 3. Quy tắc đặt tên biến

```javascript
// ✅ Đúng
let tenHocSinh = "An";        // camelCase (khuyến nghị)
let _private = "riêng tư";    // Bắt đầu bằng _
let $element = "phần tử";     // Bắt đầu bằng $
let age2 = 25;                // Có số ở cuối

// ❌ Sai
// let 2age = 25;             // Không bắt đầu bằng số
// let ten-hoc-sinh = "An";   // Không có dấu gạch ngang
// let class = "lớp";         // Không dùng từ khóa
// let tên = "An";            // Tránh tiếng Việt có dấu

// Quy ước đặt tên
const MAX_SIZE = 100;         // Hằng số: UPPER_CASE
let isActive = true;          // Boolean: is/has/can + tính từ
let getUserName = function(){}; // Hàm: động từ + danh từ
```

## Kiểu dữ liệu trong JavaScript

JavaScript có 2 nhóm kiểu dữ liệu chính:

### 1. Primitive Types (Kiểu nguyên thủy)

#### Number (Số)
```javascript
// Số nguyên và số thực
let soNguyen = 42;
let soThuc = 3.14159;
let soAm = -10;
let soLon = 1e6; // 1,000,000

// Số đặc biệt
let voCuc = Infinity;
let voHan = -Infinity;
let khongPhaiSo = NaN; // Not a Number

console.log(typeof soNguyen); // "number"
console.log(5 / 0); // Infinity
console.log("abc" * 2); // NaN

// Kiểm tra số
console.log(Number.isInteger(42)); // true
console.log(Number.isNaN(NaN)); // true
console.log(Number.isFinite(100)); // true
```

#### String (Chuỗi)
```javascript
// Các cách tạo chuỗi
let chuoi1 = "Dấu nháy kép";
let chuoi2 = 'Dấu nháy đơn';
let chuoi3 = `Template string`;

// Template string (ES6)
let ten = "An";
let tuoi = 25;
let gioisThieu = `Tôi tên là ${ten}, năm nay ${tuoi} tuổi.`;
console.log(gioisThieu);

// Chuỗi nhiều dòng
let thongDiep = `
Đây là chuỗi
nhiều dòng
rất tiện lợi!
`;

// Escape characters
let chuoiDacBiet = "Dòng 1\nDòng 2\tTab\t\"Nháy kép\"";
console.log(chuoiDacBiet);

// Thuộc tính và phương thức của string
let text = "JavaScript";
console.log(text.length); // 10
console.log(text.toUpperCase()); // "JAVASCRIPT"
console.log(text.toLowerCase()); // "javascript"
console.log(text.charAt(0)); // "J"
console.log(text.indexOf("Script")); // 4
console.log(text.slice(0, 4)); // "Java"
```

#### Boolean (Logic)
```javascript
let dung = true;
let sai = false;

// Chuyển đổi sang boolean
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean("hello")); // true
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false

// Truthy và Falsy values
// Falsy: false, 0, "", null, undefined, NaN
// Tất cả các giá trị khác là truthy

if ("") {
    console.log("Không chạy"); // Chuỗi rỗng là falsy
}

if ("hello") {
    console.log("Sẽ chạy"); // Chuỗi có nội dung là truthy
}
```

#### Undefined và Null
```javascript
let chuaKhoiTao; // undefined
let rong = null; // null

console.log(typeof chuaKhoiTao); // "undefined"
console.log(typeof rong); // "object" (đây là bug lịch sử của JS)

// So sánh
console.log(null == undefined); // true (loose equality)
console.log(null === undefined); // false (strict equality)
```

#### Symbol (ES6)
```javascript
// Symbol tạo ra giá trị duy nhất
let sym1 = Symbol("mô tả");
let sym2 = Symbol("mô tả");

console.log(sym1 === sym2); // false - mỗi symbol là duy nhất
console.log(typeof sym1); // "symbol"
```

### 2. Non-Primitive Types (Kiểu tham chiếu)

#### Object (Đối tượng)
```javascript
// Tạo object
let nguoi = {
    ten: "Nguyễn Văn An",
    tuoi: 25,
    diaChi: "Hà Nội",
    soThich: ["đọc sách", "nghe nhạc", "lập trình"]
};

// Truy cập thuộc tính
console.log(nguoi.ten); // "Nguyễn Văn An"
console.log(nguoi["tuoi"]); // 25

// Thêm/sửa thuộc tính
nguoi.email = "an@example.com";
nguoi.tuoi = 26;

// Xóa thuộc tính
delete nguoi.diaChi;

console.log(nguoi);

// Object methods
let mayTinh = {
    hang: "Dell",
    gia: 15000000,
    
    thongTin: function() {
        return `${this.hang} - ${this.gia} VND`;
    },
    
    // ES6 method syntax
    giamGia(phanTram) {
        this.gia = this.gia * (1 - phanTram / 100);
        return this.gia;
    }
};

console.log(mayTinh.thongTin());
console.log(mayTinh.giamGia(10)); // Giảm 10%
```

#### Array (Mảng)
```javascript
// Tạo mảng
let mang1 = [1, 2, 3, 4, 5];
let mang2 = new Array("a", "b", "c");
let mangHonHop = [1, "hello", true, {ten: "An"}, [1, 2, 3]];

console.log(mang1.length); // 5
console.log(mang1[0]); // 1 (index bắt đầu từ 0)

// Phương thức mảng cơ bản
let fruits = ["táo", "chuối", "cam"];

// Thêm phần tử
fruits.push("xoài"); // Thêm cuối
fruits.unshift("dưa hấu"); // Thêm đầu
console.log(fruits); // ["dưa hấu", "táo", "chuối", "cam", "xoài"]

// Xóa phần tử
let cuoi = fruits.pop(); // Xóa cuối, trả về phần tử đã xóa
let dau = fruits.shift(); // Xóa đầu, trả về phần tử đã xóa
console.log(cuoi, dau); // "xoài", "dưa hấu"

// Tìm kiếm
console.log(fruits.indexOf("cam")); // 2
console.log(fruits.includes("táo")); // true

// Cắt mảng
let catMang = fruits.slice(1, 3); // Từ index 1 đến 2
console.log(catMang); // ["chuối", "cam"]

// Nối mảng
let mang3 = [1, 2];
let mang4 = [3, 4];
let mangNoi = mang3.concat(mang4);
console.log(mangNoi); // [1, 2, 3, 4]
```

## Toán tử trong JavaScript

### 1. Toán tử số học
```javascript
let a = 10, b = 3;

console.log(a + b); // 13 - Cộng
console.log(a - b); // 7  - Trừ
console.log(a * b); // 30 - Nhân
console.log(a / b); // 3.333... - Chia
console.log(a % b); // 1  - Chia lấy dư
console.log(a ** b); // 1000 - Lũy thừa (ES2016)

// Toán tử tăng/giảm
let x = 5;
console.log(x++); // 5 (trả về rồi mới tăng)
console.log(x);   // 6
console.log(++x); // 7 (tăng rồi mới trả về)
console.log(x--); // 7 (trả về rồi mới giảm)
console.log(--x); // 5 (giảm rồi mới trả về)
```

### 2. Toán tử gán
```javascript
let num = 10;

num += 5;  // num = num + 5;  (15)
num -= 3;  // num = num - 3;  (12)
num *= 2;  // num = num * 2;  (24)
num /= 4;  // num = num / 4;  (6)
num %= 4;  // num = num % 4;  (2)
num **= 3; // num = num ** 3; (8)

console.log(num); // 8
```

### 3. Toán tử so sánh
```javascript
let a = 5, b = "5", c = 10;

// So sánh lỏng lẻo (==, !=)
console.log(a == b);  // true (tự động chuyển đổi kiểu)
console.log(a != c);  // true

// So sánh nghiêm ngặt (===, !==)
console.log(a === b); // false (khác kiểu dữ liệu)
console.log(a !== b); // true

// So sánh kích thước
console.log(a > 3);   // true
console.log(a < c);   // true
console.log(a >= 5);  // true
console.log(c <= 10); // true

// So sánh chuỗi
console.log("apple" < "banana"); // true (theo thứ tự alphabet)
console.log("10" < "2"); // true (so sánh chuỗi, không phải số)
console.log("10" < 2);   // false (chuyển đổi thành số)
```

### 4. Toán tử logic
```javascript
let x = true, y = false, z = true;

// AND (&&) - tất cả phải đúng
console.log(x && z); // true
console.log(x && y); // false

// OR (||) - chỉ cần 1 cái đúng
console.log(x || y); // true
console.log(y || false); // false

// NOT (!) - đảo ngược
console.log(!x); // false
console.log(!y); // true

// Short-circuit evaluation
let name = null;
let displayName = name || "Khách"; // Nếu name falsy thì dùng "Khách"
console.log(displayName); // "Khách"

// Nullish coalescing operator (??) - ES2020
let value = null;
let defaultValue = value ?? "mặc định";
console.log(defaultValue); // "mặc định"

// Khác với ||
let zero = 0;
console.log(zero || "default"); // "default" (0 là falsy)
console.log(zero ?? "default"); // 0 (0 không phải null/undefined)
```

### 5. Toán tử điều kiện (Ternary)
```javascript
let tuoi = 18;

// Cú pháp: điều_kiện ? giá_trị_nếu_đúng : giá_trị_nếu_sai
let thongBao = tuoi >= 18 ? "Đã trưởng thành" : "Còn nhỏ tuổi";
console.log(thongBao); // "Đã trưởng thành"

// Có thể lồng nhau
let diem = 85;
let xepLoai = diem >= 90 ? "Xuất sắc" : 
              diem >= 80 ? "Giỏi" : 
              diem >= 70 ? "Khá" : "Trung bình";
console.log(xepLoai); // "Giỏi"

// Sử dụng trong JSX (React)
let isLoggedIn = true;
let greeting = isLoggedIn ? "Chào mừng trở lại!" : "Vui lòng đăng nhập";
```

### 6. Toán tử typeof và instanceof
```javascript
// typeof - kiểm tra kiểu dữ liệu
console.log(typeof 42);        // "number"
console.log(typeof "hello");   // "string"
console.log(typeof true);      // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null);      // "object" (bug lịch sử)
console.log(typeof [1, 2, 3]); // "object"
console.log(typeof {a: 1});    // "object"

// instanceof - kiểm tra instance
let arr = [1, 2, 3];
let obj = {a: 1};
let date = new Date();

console.log(arr instanceof Array);  // true
console.log(obj instanceof Object); // true
console.log(date instanceof Date);  // true
console.log(arr instanceof Object); // true (Array kế thừa từ Object)
```

## Chuyển đổi kiểu dữ liệu

### 1. Chuyển đổi tự động (Implicit)
```javascript
// String + Number = String
console.log("5" + 3); // "53"
console.log(5 + "3"); // "53"

// String - Number = Number
console.log("10" - 5); // 5
console.log("10" * "2"); // 20
console.log("10" / "2"); // 5

// Boolean trong phép toán
console.log(true + 1);  // 2
console.log(false + 1); // 1
console.log(true * 5);  // 5
```

### 2. Chuyển đổi tường minh (Explicit)
```javascript
// Chuyển sang Number
console.log(Number("123"));    // 123
console.log(Number("123.45")); // 123.45
console.log(Number("abc"));    // NaN
console.log(Number(true));     // 1
console.log(Number(false));    // 0

console.log(parseInt("123"));     // 123
console.log(parseInt("123.45"));  // 123 (chỉ lấy phần nguyên)
console.log(parseFloat("123.45")); // 123.45

// Chuyển sang String
console.log(String(123));    // "123"
console.log(String(true));   // "true"
console.log((123).toString()); // "123"

// Chuyển sang Boolean
console.log(Boolean(1));     // true
console.log(Boolean(0));     // false
console.log(Boolean(""));    // false
console.log(Boolean("hi"));  // true
```

## Bài tập thực hành

### Bài 1: Quản lý thông tin sinh viên
```javascript
// Tạo object sinh viên
const sinhVien = {
    maSV: "SV001",
    hoTen: "Nguyễn Văn An",
    tuoi: 20,
    diemTB: 8.5,
    monHoc: ["Toán", "Lý", "Hóa", "Anh văn"],
    diaChi: {
        tinh: "Hà Nội",
        quan: "Cầu Giấy",
        duong: "Duy Tân"
    }
};

// Hiển thị thông tin
console.log("=== THÔNG TIN SINH VIÊN ===");
console.log(`Mã SV: ${sinhVien.maSV}`);
console.log(`Họ tên: ${sinhVien.hoTen}`);
console.log(`Tuổi: ${sinhVien.tuoi}`);
console.log(`Điểm TB: ${sinhVien.diemTB}`);
console.log(`Địa chỉ: ${sinhVien.diaChi.duong}, ${sinhVien.diaChi.quan}, ${sinhVien.diaChi.tinh}`);

// Xếp loại học lực
let xepLoai = sinhVien.diemTB >= 9 ? "Xuất sắc" :
              sinhVien.diemTB >= 8 ? "Giỏi" :
              sinhVien.diemTB >= 7 ? "Khá" :
              sinhVien.diemTB >= 5 ? "Trung bình" : "Yếu";

console.log(`Xếp loại: ${xepLoai}`);

// Kiểm tra tuổi
let trangThai = sinhVien.tuoi >= 18 ? "Đã trưởng thành" : "Chưa trưởng thành";
console.log(`Trạng thái: ${trangThai}`);

// Danh sách môn học
console.log("Môn học đang theo học:");
sinhVien.monHoc.forEach((mon, index) => {
    console.log(`${index + 1}. ${mon}`);
});
```

### Bài 2: Máy tính nâng cao
```javascript
// Object máy tính
const calculator = {
    // Thuộc tính
    result: 0,
    history: [],
    
    // Phương thức cơ bản
    add(a, b = 0) {
        const result = a + b;
        this.saveHistory('add', a, b, result);
        return result;
    },
    
    subtract(a, b = 0) {
        const result = a - b;
        this.saveHistory('subtract', a, b, result);
        return result;
    },
    
    multiply(a, b = 1) {
        const result = a * b;
        this.saveHistory('multiply', a, b, result);
        return result;
    },
    
    divide(a, b = 1) {
        if (b === 0) {
            console.log("Lỗi: Không thể chia cho 0!");
            return null;
        }
        const result = a / b;
        this.saveHistory('divide', a, b, result);
        return result;
    },
    
    power(a, b = 2) {
        const result = a ** b;
        this.saveHistory('power', a, b, result);
        return result;
    },
    
    sqrt(a) {
        if (a < 0) {
            console.log("Lỗi: Không thể tính căn bậc hai của số âm!");
            return null;
        }
        const result = Math.sqrt(a);
        this.saveHistory('sqrt', a, null, result);
        return result;
    },
    
    // Lưu lịch sử
    saveHistory(operation, a, b, result) {
        this.history.push({
            operation,
            operands: b !== null ? [a, b] : [a],
            result,
            timestamp: new Date().toLocaleString('vi-VN')
        });
    },
    
    // Hiển thị lịch sử
    showHistory() {
        console.log("\n=== LỊCH SỬ TÍNH TOÁN ===");
        if (this.history.length === 0) {
            console.log("Chưa có phép tính nào.");
            return;
        }
        
        this.history.forEach((item, index) => {
            let expression = '';
            switch (item.operation) {
                case 'add':
                    expression = `${item.operands[0]} + ${item.operands[1]} = ${item.result}`;
                    break;
                case 'subtract':
                    expression = `${item.operands[0]} - ${item.operands[1]} = ${item.result}`;
                    break;
                case 'multiply':
                    expression = `${item.operands[0]} × ${item.operands[1]} = ${item.result}`;
                    break;
                case 'divide':
                    expression = `${item.operands[0]} ÷ ${item.operands[1]} = ${item.result}`;
                    break;
                case 'power':
                    expression = `${item.operands[0]} ^ ${item.operands[1]} = ${item.result}`;
                    break;
                case 'sqrt':
                    expression = `√${item.operands[0]} = ${item.result}`;
                    break;
            }
            console.log(`${index + 1}. ${expression} (${item.timestamp})`);
        });
    },
    
    // Xóa lịch sử
    clearHistory() {
        this.history = [];
        console.log("Đã xóa lịch sử tính toán.");
    }
};

// Sử dụng máy tính
console.log("=== MÁY TÍNH JAVASCRIPT ===");
console.log("Cộng 10 + 5 =", calculator.add(10, 5));
console.log("Trừ 20 - 8 =", calculator.subtract(20, 8));
console.log("Nhân 6 × 7 =", calculator.multiply(6, 7));
console.log("Chia 15 ÷ 3 =", calculator.divide(15, 3));
console.log("Lũy thừa 2^8 =", calculator.power(2, 8));
console.log("Căn bậc hai √16 =", calculator.sqrt(16));

// Thử các trường hợp lỗi
calculator.divide(10, 0);
calculator.sqrt(-4);

// Hiển thị lịch sử
calculator.showHistory();
```

### Bài 3: Trò chơi đoán số nâng cao
```javascript
// Game đoán số
const guessingGame = {
    // Cài đặt game
    minNumber: 1,
    maxNumber: 100,
    maxAttempts: 7,
    
    // Trạng thái game
    secretNumber: 0,
    attempts: 0,
    isGameActive: false,
    playerGuesses: [],
    
    // Bắt đầu game mới
    startNewGame() {
        this.secretNumber = Math.floor(Math.random() * (this.maxNumber - this.minNumber + 1)) + this.minNumber;
        this.attempts = 0;
        this.isGameActive = true;
        this.playerGuesses = [];
        
        console.log("🎮 TRÒ CHƠI ĐOÁN SỐ BẮT ĐẦU!");
        console.log(`Tôi đã nghĩ ra một số từ ${this.minNumber} đến ${this.maxNumber}`);
        console.log(`Bạn có ${this.maxAttempts} lần đoán. Chúc may mắn!`);
        console.log("=====================================");
    },
    
    // Đoán số
    makeGuess(guess) {
        // Kiểm tra game có đang hoạt động không
        if (!this.isGameActive) {
            console.log("❌ Game chưa bắt đầu! Gọi startNewGame() để chơi.");
            return;
        }
        
        // Kiểm tra input hợp lệ
        if (typeof guess !== 'number' || !Number.isInteger(guess)) {
            console.log("❌ Vui lòng nhập một số nguyên!");
            return;
        }
        
        if (guess < this.minNumber || guess > this.maxNumber) {
            console.log(`❌ Số phải nằm trong khoảng ${this.minNumber} - ${this.maxNumber}!`);
            return;
        }
        
        // Kiểm tra đã đoán số này chưa
        if (this.playerGuesses.includes(guess)) {
            console.log(`❌ Bạn đã đoán số ${guess} rồi!`);
            return;
        }
        
        // Tăng số lần đoán
        this.attempts++;
        this.playerGuesses.push(guess);
        
        console.log(`\n🎯 Lần ${this.attempts}: Bạn đoán số ${guess}`);
        
        // Kiểm tra kết quả
        if (guess === this.secretNumber) {
            this.winGame();
        } else if (this.attempts >= this.maxAttempts) {
            this.loseGame();
        } else {
            this.giveHint(guess);
        }
    },
    
    // Đưa ra gợi ý
    giveHint(guess) {
        const difference = Math.abs(guess - this.secretNumber);
        let hint = "";
        
        if (guess < this.secretNumber) {
            hint = "📈 Số cần tìm LỚN HƠN";
        } else {
            hint = "📉 Số cần tìm NHỎ HƠN";
        }
        
        // Gợi ý về độ gần
        if (difference <= 5) {
            hint += " (Rất gần rồi! 🔥)";
        } else if (difference <= 10) {
            hint += " (Gần rồi! 👍)";
        } else if (difference <= 20) {
            hint += " (Hơi xa 😐)";
        } else {
            hint += " (Còn xa lắm 😅)";
        }
        
        console.log(hint);
        console.log(`Còn lại ${this.maxAttempts - this.attempts} lần đoán.`);
        
        // Hiển thị các số đã đoán
        console.log(`Đã đoán: [${this.playerGuesses.sort((a, b) => a - b).join(', ')}]`);
    },
    
    // Thắng game
    winGame() {
        this.isGameActive = false;
        console.log("🎉 CHÚC MỪNG! Bạn đã đoán đúng!");
        console.log(`✨ Số bí mật là: ${this.secretNumber}`);
        console.log(`🏆 Bạn đã thắng sau ${this.attempts} lần đoán!`);
        
        // Đánh giá hiệu suất
        let rating = "";
        if (this.attempts <= 3) {
            rating = "Xuất sắc! 🌟🌟🌟";
        } else if (this.attempts <= 5) {
            rating = "Tốt! 🌟🌟";
        } else {
            rating = "Khá! 🌟";
        }
        console.log(`Đánh giá: ${rating}`);
    },
    
    // Thua game
    loseGame() {
        this.isGameActive = false;
        console.log("😞 RẤT TIẾC! Bạn đã hết lượt đoán.");
        console.log(`💡 Số bí mật là: ${this.secretNumber}`);
        console.log("🔄 Thử lại lần nữa nhé!");
    },
    
    // Hiển thị trạng thái game
    showStatus() {
        if (!this.isGameActive) {
            console.log("Game chưa bắt đầu hoặc đã kết thúc.");
            return;
        }
        
        console.log("\n📊 TRẠNG THÁI GAME:");
        console.log(`Phạm vi: ${this.minNumber} - ${this.maxNumber}`);
        console.log(`Lần đoán: ${this.attempts}/${this.maxAttempts}`);
        console.log(`Đã đoán: [${this.playerGuesses.sort((a, b) => a - b).join(', ')}]`);
    }
};

// Chơi game
guessingGame.startNewGame();

// Mô phỏng người chơi đoán
const simulateGame = () => {
    const guesses = [50, 75, 62, 68, 71, 73, 70]; // Ví dụ các lần đoán
    
    guesses.forEach((guess, index) => {
        setTimeout(() => {
            guessingGame.makeGuess(guess);
            if (index === guesses.length - 1 && guessingGame.isGameActive) {
                guessingGame.showStatus();
            }
        }, (index + 1) * 1000); // Delay 1 giây giữa các lần đoán
    });
};

// Chạy simulation (bỏ comment để chạy)
// simulateGame();
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Cách khai báo biến với `var`, `let`, `const`
- Các kiểu dữ liệu nguyên thủy và tham chiếu
- Các loại toán tử và cách sử dụng
- Chuyển đổi kiểu dữ liệu tự động và tường minh
- Thực hành với các bài tập thực tế

JavaScript có hệ thống kiểu dữ liệu linh hoạt nhưng cũng có thể gây nhầm lẫn. Hiểu rõ các khái niệm này sẽ giúp bạn viết code JavaScript hiệu quả hơn.

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **hàm (Functions)** trong JavaScript - một trong những khái niệm quan trọng nhất của ngôn ngữ này!