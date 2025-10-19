---
title: "JavaScript Cơ Bản #1: Giới Thiệu và Thiết Lập Môi Trường"
date: 2024-01-30
draft: false
description: "Tìm hiểu JavaScript là gì và cách thiết lập môi trường để bắt đầu học JavaScript"
tags: ["javascript", "cơ bản", "giới thiệu", "thiết lập"]
categories: ["JavaScript"]
series: ["JavaScript Cơ Bản"]
series_order: 1
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## JavaScript là gì?

**JavaScript** (viết tắt là JS) là ngôn ngữ lập trình được sử dụng chủ yếu để tạo ra các trang web tương tác. Ban đầu JavaScript chỉ chạy trên trình duyệt web, nhưng hiện nay nó có thể chạy ở nhiều môi trường khác nhau.

### Tại sao nên học JavaScript?

1. **Ngôn ngữ của web**: JavaScript là ngôn ngữ duy nhất chạy trực tiếp trên trình duyệt
2. **Dễ học**: Cú pháp đơn giản, thân thiện với người mới
3. **Đa năng**: Có thể làm frontend, backend, mobile app, desktop app
4. **Cộng đồng lớn**: Rất nhiều tài liệu, thư viện và framework
5. **Cơ hội việc làm**: Nhu cầu tuyển dụng JavaScript developer rất cao

### JavaScript có thể làm gì?

- **Frontend**: Tạo giao diện web tương tác (React, Vue, Angular)
- **Backend**: Xây dựng server và API (Node.js)
- **Mobile**: Phát triển ứng dụng di động (React Native, Ionic)
- **Desktop**: Tạo ứng dụng desktop (Electron)
- **Game**: Phát triển game 2D/3D
- **AI/ML**: Machine Learning với TensorFlow.js

## Thiết lập môi trường học JavaScript

### 1. Trình duyệt web (Cách đơn giản nhất)

Mọi trình duyệt hiện đại đều có JavaScript engine tích hợp:

**Chrome/Edge/Firefox:**
1. Mở trình duyệt
2. Nhấn `F12` hoặc chuột phải → "Inspect" → "Console"
3. Bạn có thể viết JavaScript trực tiếp trong Console

**Thử ngay:**
```javascript
console.log("Xin chào JavaScript!");
alert("Đây là thông báo từ JavaScript");
```

### 2. Visual Studio Code (Khuyến nghị)

**Cài đặt VS Code:**
1. Truy cập: https://code.visualstudio.com/
2. Tải và cài đặt phiên bản phù hợp với hệ điều hành
3. Cài đặt các extension hữu ích:
   - **Live Server**: Chạy web server local
   - **JavaScript (ES6) code snippets**: Gợi ý code
   - **Prettier**: Format code đẹp
   - **Bracket Pair Colorizer**: Tô màu dấu ngoặc

### 3. Node.js (Cho backend)

**Cài đặt Node.js:**
1. Truy cập: https://nodejs.org/
2. Tải phiên bản LTS (Long Term Support)
3. Cài đặt theo hướng dẫn
4. Kiểm tra cài đặt:

```bash
node --version
npm --version
```

## Chương trình JavaScript đầu tiên

### 1. JavaScript trong HTML

Tạo file `index.html`:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Đầu Tiên</title>
</head>
<body>
    <h1>Chào mừng đến với JavaScript!</h1>
    <button onclick="chaoHoi()">Nhấn vào đây</button>
    
    <script>
        // JavaScript viết trong thẻ script
        console.log("Trang web đã tải xong!");
        
        function chaoHoi() {
            alert("Xin chào! Bạn đã nhấn nút thành công!");
        }
        
        // Thay đổi nội dung trang
        document.querySelector('h1').style.color = 'blue';
    </script>
</body>
</html>
```

### 2. JavaScript trong file riêng

**File `index.html`:**
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript External</title>
</head>
<body>
    <h1 id="tieu-de">Học JavaScript</h1>
    <p id="noi-dung">Đây là đoạn văn ban đầu</p>
    <button onclick="thayDoiNoiDung()">Thay đổi nội dung</button>
    
    <!-- Liên kết file JavaScript -->
    <script src="script.js"></script>
</body>
</html>
```

**File `script.js`:**
```javascript
// Đây là file JavaScript riêng biệt
console.log("File JavaScript đã được tải!");

// Hàm thay đổi nội dung
function thayDoiNoiDung() {
    // Lấy phần tử theo ID
    const tieuDe = document.getElementById('tieu-de');
    const noiDung = document.getElementById('noi-dung');
    
    // Thay đổi nội dung
    tieuDe.textContent = 'JavaScript thật tuyệt vời!';
    tieuDe.style.color = 'green';
    
    noiDung.innerHTML = '<strong>Nội dung đã được thay đổi bằng JavaScript!</strong>';
    noiDung.style.backgroundColor = 'yellow';
    noiDung.style.padding = '10px';
}

// Thực hiện khi trang web tải xong
document.addEventListener('DOMContentLoaded', function() {
    console.log('Trang web đã sẵn sàng!');
    
    // Thêm thời gian hiện tại
    const now = new Date();
    const thoiGian = now.toLocaleString('vi-VN');
    
    const pThoiGian = document.createElement('p');
    pThoiGian.textContent = 'Thời gian hiện tại: ' + thoiGian;
    pThoiGian.style.fontStyle = 'italic';
    
    document.body.appendChild(pThoiGian);
});
```

### 3. JavaScript với Node.js

Tạo file `hello.js`:

```javascript
// Chạy JavaScript với Node.js
console.log("Xin chào từ Node.js!");

// Biến và hàm
const ten = "Nguyễn Văn A";
const tuoi = 25;

function gioisThieu(ten, tuoi) {
    return `Tôi tên là ${ten}, năm nay ${tuoi} tuổi.`;
}

console.log(gioisThieu(ten, tuoi));

// Làm việc với thời gian
const now = new Date();
console.log("Hôm nay là:", now.toLocaleDateString('vi-VN'));

// Tính toán đơn giản
function tinhTong(a, b) {
    return a + b;
}

console.log("5 + 3 =", tinhTong(5, 3));

// Làm việc với mảng
const danhSachMon = ['Phở', 'Bún bò', 'Cơm tấm', 'Bánh mì'];
console.log("Các món ăn Việt Nam:");
danhSachMon.forEach((mon, index) => {
    console.log(`${index + 1}. ${mon}`);
});
```

Chạy file:
```bash
node hello.js
```

## Cú pháp cơ bản JavaScript

### 1. Comments (Ghi chú)
```javascript
// Đây là comment một dòng

/*
Đây là comment
nhiều dòng
*/

/**
 * Đây là JSDoc comment
 * Dùng để mô tả hàm, class
 */
```

### 2. Biến (Variables)
```javascript
// Khai báo biến
var ten = "JavaScript";     // Cách cũ (không khuyến nghị)
let tuoi = 25;             // Biến có thể thay đổi
const PI = 3.14159;        // Hằng số (không thể thay đổi)

console.log(ten, tuoi, PI);

// Thay đổi giá trị
tuoi = 26;  // OK
// PI = 3.14;  // Lỗi! Không thể thay đổi const
```

### 3. Kiểu dữ liệu cơ bản
```javascript
// Number (Số)
let soNguyen = 42;
let soThuc = 3.14;
let soAm = -10;

// String (Chuỗi)
let chuoi1 = "Xin chào";
let chuoi2 = 'JavaScript';
let chuoi3 = `Template string: ${soNguyen}`;

// Boolean (Logic)
let dung = true;
let sai = false;

// Undefined và Null
let chuaGan;           // undefined
let rong = null;       // null

// Array (Mảng)
let mang = [1, 2, 3, "hello", true];

// Object (Đối tượng)
let nguoi = {
    ten: "An",
    tuoi: 25,
    diaChi: "Hà Nội"
};

console.log(typeof soNguyen);  // "number"
console.log(typeof chuoi1);    // "string"
console.log(typeof dung);      // "boolean"
console.log(typeof mang);      // "object"
console.log(typeof nguoi);     // "object"
```

## Công cụ hỗ trợ học JavaScript

### 1. Online Code Editor
- **CodePen**: https://codepen.io/
- **JSFiddle**: https://jsfiddle.net/
- **Repl.it**: https://replit.com/
- **CodeSandbox**: https://codesandbox.io/

### 2. Tài liệu tham khảo
- **MDN Web Docs**: https://developer.mozilla.org/vi/docs/Web/JavaScript
- **W3Schools**: https://www.w3schools.com/js/
- **JavaScript.info**: https://javascript.info/

### 3. Công cụ debug
```javascript
// Console methods
console.log("Thông tin thường");
console.warn("Cảnh báo");
console.error("Lỗi");
console.table([{ten: "An", tuoi: 25}, {ten: "Bình", tuoi: 30}]);

// Debugger
function tinhToan(a, b) {
    debugger; // Dừng tại đây khi debug
    return a + b;
}
```

## Bài tập thực hành

### Bài 1: Trang web cá nhân đơn giản

**File `profile.html`:**
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang cá nhân</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .profile { max-width: 600px; margin: 0 auto; }
        button { padding: 10px 20px; margin: 5px; cursor: pointer; }
        .hidden { display: none; }
    </style>
</head>
<body>
    <div class="profile">
        <h1 id="ten">Tên của bạn</h1>
        <p id="gioi-thieu">Giới thiệu về bản thân...</p>
        
        <div id="thong-tin" class="hidden">
            <h3>Thông tin chi tiết:</h3>
            <p id="tuoi"></p>
            <p id="nghe-nghiep"></p>
            <p id="so-thich"></p>
        </div>
        
        <button onclick="hienThiThongTin()">Hiển thị thông tin</button>
        <button onclick="anThongTin()">Ẩn thông tin</button>
        <button onclick="thayDoiMau()">Đổi màu</button>
    </div>
    
    <script src="profile.js"></script>
</body>
</html>
```

**File `profile.js`:**
```javascript
// Thông tin cá nhân
const thongTinCaNhan = {
    ten: "Nguyễn Văn An",
    tuoi: 25,
    ngheNghiep: "Lập trình viên",
    soThich: "Đọc sách, nghe nhạc, lập trình"
};

// Cập nhật thông tin khi trang tải
document.addEventListener('DOMContentLoaded', function() {
    capNhatThongTin();
});

function capNhatThongTin() {
    document.getElementById('ten').textContent = thongTinCaNhan.ten;
    document.getElementById('gioi-thieu').textContent = 
        `Xin chào! Tôi là ${thongTinCaNhan.ten}, một ${thongTinCaNhan.ngheNghiep}.`;
    
    document.getElementById('tuoi').textContent = `Tuổi: ${thongTinCaNhan.tuoi}`;
    document.getElementById('nghe-nghiep').textContent = `Nghề nghiệp: ${thongTinCaNhan.ngheNghiep}`;
    document.getElementById('so-thich').textContent = `Sở thích: ${thongTinCaNhan.soThich}`;
}

function hienThiThongTin() {
    const thongTin = document.getElementById('thong-tin');
    thongTin.classList.remove('hidden');
}

function anThongTin() {
    const thongTin = document.getElementById('thong-tin');
    thongTin.classList.add('hidden');
}

function thayDoiMau() {
    const mauNgauNhien = '#' + Math.floor(Math.random()*16777215).toString(16);
    document.body.style.backgroundColor = mauNgauNhien;
}
```

### Bài 2: Máy tính đơn giản

**File `calculator.html`:**
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Máy tính JavaScript</title>
    <style>
        .calculator {
            max-width: 300px;
            margin: 50px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
        }
        input, button {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            font-size: 16px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 5px;
        }
        button {
            width: auto;
            cursor: pointer;
        }
        #result {
            background-color: #f0f0f0;
            text-align: right;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <h2>Máy tính JavaScript</h2>
        <input type="text" id="result" readonly>
        
        <div class="buttons">
            <button onclick="clearResult()">C</button>
            <button onclick="deleteLast()">⌫</button>
            <button onclick="appendToResult('/')">/</button>
            <button onclick="appendToResult('*')">×</button>
            
            <button onclick="appendToResult('7')">7</button>
            <button onclick="appendToResult('8')">8</button>
            <button onclick="appendToResult('9')">9</button>
            <button onclick="appendToResult('-')">-</button>
            
            <button onclick="appendToResult('4')">4</button>
            <button onclick="appendToResult('5')">5</button>
            <button onclick="appendToResult('6')">6</button>
            <button onclick="appendToResult('+')">+</button>
            
            <button onclick="appendToResult('1')">1</button>
            <button onclick="appendToResult('2')">2</button>
            <button onclick="appendToResult('3')">3</button>
            <button onclick="calculate()" rowspan="2">=</button>
            
            <button onclick="appendToResult('0')" colspan="2">0</button>
            <button onclick="appendToResult('.')">.</button>
        </div>
    </div>
    
    <script src="calculator.js"></script>
</body>
</html>
```

**File `calculator.js`:**
```javascript
let currentInput = '';
let operator = '';
let previousInput = '';

function appendToResult(value) {
    const result = document.getElementById('result');
    result.value += value;
}

function clearResult() {
    document.getElementById('result').value = '';
    currentInput = '';
    operator = '';
    previousInput = '';
}

function deleteLast() {
    const result = document.getElementById('result');
    result.value = result.value.slice(0, -1);
}

function calculate() {
    const result = document.getElementById('result');
    try {
        // Thay thế × bằng * để tính toán
        const expression = result.value.replace(/×/g, '*');
        const answer = eval(expression);
        result.value = answer;
    } catch (error) {
        result.value = 'Lỗi';
        setTimeout(() => {
            clearResult();
        }, 1500);
    }
}

// Hỗ trợ bàn phím
document.addEventListener('keydown', function(event) {
    const key = event.key;
    
    if (key >= '0' && key <= '9' || key === '.') {
        appendToResult(key);
    } else if (key === '+' || key === '-' || key === '*' || key === '/') {
        appendToResult(key);
    } else if (key === 'Enter' || key === '=') {
        calculate();
    } else if (key === 'Escape' || key === 'c' || key === 'C') {
        clearResult();
    } else if (key === 'Backspace') {
        deleteLast();
    }
});
```

## Tổng kết

Trong bài này, chúng ta đã học:
- JavaScript là gì và tại sao nên học
- Cách thiết lập môi trường phát triển
- Tạo chương trình JavaScript đầu tiên
- Cú pháp cơ bản và kiểu dữ liệu
- Các công cụ hỗ trợ học JavaScript

JavaScript là ngôn ngữ rất mạnh mẽ và linh hoạt. Với nền tảng này, bạn đã sẵn sàng để tìm hiểu sâu hơn về các khái niệm JavaScript.

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **biến, kiểu dữ liệu và toán tử** trong JavaScript chi tiết hơn. Hãy thực hành các bài tập để làm quen với JavaScript nhé!