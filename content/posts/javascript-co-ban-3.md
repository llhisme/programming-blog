---
title: "JavaScript Cơ Bản #3: Hàm (Functions) và Scope"
date: 2024-02-03
draft: false
description: "Tìm hiểu về hàm trong JavaScript, các cách định nghĩa hàm và khái niệm scope"
tags: ["javascript", "hàm", "function", "scope", "cơ bản"]
categories: ["JavaScript"]
series: ["JavaScript Cơ Bản"]
series_order: 3
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## Hàm là gì?

**Hàm** (Function) là một khối code có thể tái sử dụng, thực hiện một nhiệm vụ cụ thể. Hàm giúp code trở nên có tổ chức, dễ đọc và dễ bảo trì.

### Tại sao cần sử dụng hàm?

1. **Tái sử dụng code**: Viết một lần, dùng nhiều lần
2. **Tổ chức code**: Chia nhỏ chương trình thành các phần dễ quản lý
3. **Dễ debug**: Dễ tìm và sửa lỗi
4. **Dễ test**: Có thể test từng hàm riêng biệt

## Các cách định nghĩa hàm

### 1. Function Declaration (Khai báo hàm)

```javascript
// Cú pháp cơ bản
function tenHam(thamSo1, thamSo2) {
    // Code thực hiện
    return ketQua; // Tùy chọn
}

// Ví dụ đơn giản
function chaoHoi() {
    console.log("Xin chào!");
}

// Gọi hàm
chaoHoi(); // "Xin chào!"

// Hàm có tham số
function chaoHoiCaNhan(ten) {
    console.log("Xin chào " + ten + "!");
}

chaoHoiCaNhan("An"); // "Xin chào An!"

// Hàm có return
function tinhTong(a, b) {
    return a + b;
}

let ketQua = tinhTong(5, 3);
console.log(ketQua); // 8
```

### 2. Function Expression (Biểu thức hàm)

```javascript
// Gán hàm vào biến
const chaoHoi = function() {
    console.log("Xin chào từ function expression!");
};

chaoHoi(); // "Xin chào từ function expression!"

// Hàm có tên (Named function expression)
const tinhTich = function nhan(a, b) {
    return a * b;
};

console.log(tinhTich(4, 5)); // 20

// Anonymous function (hàm ẩn danh)
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(function(num) {
    return num * 2;
});
console.log(doubled); // [2, 4, 6, 8, 10]
```

### 3. Arrow Function (Hàm mũi tên - ES6)

```javascript
// Cú pháp cơ bản
const tenHam = (thamSo) => {
    return ketQua;
};

// Ví dụ đơn giản
const chaoHoi = () => {
    console.log("Xin chào từ arrow function!");
};

// Hàm một tham số (có thể bỏ dấu ngoặc)
const binhPhuong = x => x * x;
console.log(binhPhuong(5)); // 25

// Hàm nhiều tham số
const tinhTong = (a, b) => a + b;
console.log(tinhTong(3, 7)); // 10

// Hàm phức tạp hơn
const kiemTraChanLe = (so) => {
    if (so % 2 === 0) {
        return "chẵn";
    } else {
        return "lẻ";
    }
};

console.log(kiemTraChanLe(4)); // "chẵn"

// Arrow function với array methods
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);
const squared = numbers.map(num => num ** 2);

console.log(evenNumbers); // [2, 4]
console.log(squared); // [1, 4, 9, 16, 25]
```

## Tham số và đối số

### 1. Tham số cơ bản

```javascript
// Hàm với nhiều tham số
function gioisThieu(ten, tuoi, ngheNghiep) {
    return `Tôi tên là ${ten}, ${tuoi} tuổi, làm ${ngheNghiep}.`;
}

console.log(gioisThieu("An", 25, "lập trình viên"));
// "Tôi tên là An, 25 tuổi, làm lập trình viên."

// Thiếu tham số
console.log(gioisThieu("Bình", 30));
// "Tôi tên là Bình, 30 tuổi, làm undefined."
```

### 2. Tham số mặc định (Default Parameters - ES6)

```javascript
function chaoHoi(ten = "Bạn", tuoi = 18) {
    return `Xin chào ${ten}, ${tuoi} tuổi!`;
}

console.log(chaoHoi()); // "Xin chào Bạn, 18 tuổi!"
console.log(chaoHoi("An")); // "Xin chào An, 18 tuổi!"
console.log(chaoHoi("Bình", 25)); // "Xin chào Bình, 25 tuổi!"

// Tham số mặc định với biểu thức
function tinhDienTich(dai = 1, rong = dai) {
    return dai * rong;
}

console.log(tinhDienTich()); // 1 (1 * 1)
console.log(tinhDienTich(5)); // 25 (5 * 5)
console.log(tinhDienTich(4, 3)); // 12 (4 * 3)
```

### 3. Rest Parameters (Tham số còn lại - ES6)

```javascript
// Nhận số lượng tham số không xác định
function tinhTong(...numbers) {
    let tong = 0;
    for (let num of numbers) {
        tong += num;
    }
    return tong;
}

console.log(tinhTong(1, 2, 3)); // 6
console.log(tinhTong(1, 2, 3, 4, 5)); // 15
console.log(tinhTong()); // 0

// Kết hợp với tham số thường
function gioisThieuNhom(leader, ...members) {
    console.log(`Trưởng nhóm: ${leader}`);
    console.log(`Thành viên: ${members.join(", ")}`);
}

gioisThieuNhom("An", "Bình", "Cường", "Dũng");
// Trưởng nhóm: An
// Thành viên: Bình, Cường, Dũng
```

### 4. Arguments Object (Cách cũ)

```javascript
// Chỉ hoạt động với function declaration/expression
function tinhTongCu() {
    let tong = 0;
    for (let i = 0; i < arguments.length; i++) {
        tong += arguments[i];
    }
    return tong;
}

console.log(tinhTongCu(1, 2, 3, 4)); // 10

// Lưu ý: arguments không hoạt động với arrow function
const arrowFunc = () => {
    // console.log(arguments); // Lỗi!
};
```

## Scope (Phạm vi)

### 1. Global Scope (Phạm vi toàn cục)

```javascript
// Biến global
let globalVar = "Tôi là biến global";

function testGlobal() {
    console.log(globalVar); // Có thể truy cập
}

testGlobal(); // "Tôi là biến global"
console.log(globalVar); // "Tôi là biến global"
```

### 2. Function Scope (Phạm vi hàm)

```javascript
function testFunctionScope() {
    let functionVar = "Tôi là biến function scope";
    
    function innerFunction() {
        console.log(functionVar); // Có thể truy cập
    }
    
    innerFunction(); // "Tôi là biến function scope"
}

testFunctionScope();
// console.log(functionVar); // Lỗi! Không thể truy cập từ bên ngoài
```

### 3. Block Scope (Phạm vi khối - ES6)

```javascript
function testBlockScope() {
    if (true) {
        let blockVar = "Tôi là biến block scope";
        const blockConst = "Tôi là hằng block scope";
        var functionVar = "Tôi là biến function scope";
        
        console.log(blockVar); // OK
        console.log(blockConst); // OK
        console.log(functionVar); // OK
    }
    
    // console.log(blockVar); // Lỗi! let có block scope
    // console.log(blockConst); // Lỗi! const có block scope
    console.log(functionVar); // OK - var có function scope
}

testBlockScope();
```

### 4. Lexical Scope (Phạm vi từ vựng)

```javascript
function ngoai() {
    let x = 10;
    
    function trong() {
        console.log(x); // Có thể truy cập biến của hàm cha
    }
    
    return trong;
}

const hamTrong = ngoai();
hamTrong(); // 10

// Closure example
function taoCounter() {
    let count = 0;
    
    return function() {
        count++;
        return count;
    };
}

const counter1 = taoCounter();
const counter2 = taoCounter();

console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter2()); // 1 (counter riêng biệt)
```

## Hoisting (Kéo lên)

```javascript
// Function declaration được hoisted
console.log(sayHello()); // "Hello!" - Hoạt động bình thường

function sayHello() {
    return "Hello!";
}

// Function expression không được hoisted
// console.log(sayHi()); // Lỗi! Cannot access 'sayHi' before initialization

const sayHi = function() {
    return "Hi!";
};

// Var được hoisted nhưng giá trị thì không
console.log(myVar); // undefined (không lỗi)
var myVar = "Hello World";

// Let và const không được hoisted
// console.log(myLet); // Lỗi! Cannot access 'myLet' before initialization
let myLet = "Hello";
```

## Callback Functions

```javascript
// Hàm callback đơn giản
function processData(data, callback) {
    console.log("Đang xử lý dữ liệu...");
    const result = data.toUpperCase();
    callback(result);
}

function displayResult(result) {
    console.log("Kết quả:", result);
}

processData("hello world", displayResult);
// Đang xử lý dữ liệu...
// Kết quả: HELLO WORLD

// Callback với array methods
const numbers = [1, 2, 3, 4, 5];

// forEach
numbers.forEach(function(num, index) {
    console.log(`Phần tử ${index}: ${num}`);
});

// map
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4]

// reduce
const sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 15
```

## Higher-Order Functions

```javascript
// Hàm trả về hàm khác
function createMultiplier(multiplier) {
    return function(number) {
        return number * multiplier;
    };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5)); // 10
console.log(triple(4)); // 12

// Hàm nhận hàm khác làm tham số
function calculate(operation, a, b) {
    return operation(a, b);
}

const add = (x, y) => x + y;
const multiply = (x, y) => x * y;

console.log(calculate(add, 5, 3)); // 8
console.log(calculate(multiply, 4, 6)); // 24

// Practical example: Event handling
function createEventHandler(message) {
    return function(event) {
        console.log(message, event.type);
    };
}

// const button = document.querySelector('button');
// button.addEventListener('click', createEventHandler('Button clicked:'));
```

## Bài tập thực hành

### Bài 1: Thư viện toán học

```javascript
// Thư viện các hàm toán học
const MathUtils = {
    // Hàm cơ bản
    add: (a, b) => a + b,
    subtract: (a, b) => a - b,
    multiply: (a, b) => a * b,
    divide: (a, b) => b !== 0 ? a / b : null,
    
    // Hàm nâng cao
    power: (base, exponent) => Math.pow(base, exponent),
    sqrt: (number) => number >= 0 ? Math.sqrt(number) : null,
    
    // Kiểm tra số nguyên tố
    isPrime(num) {
        if (num < 2) return false;
        for (let i = 2; i <= Math.sqrt(num); i++) {
            if (num % i === 0) return false;
        }
        return true;
    },
    
    // Tính giai thừa
    factorial(n) {
        if (n < 0) return null;
        if (n === 0 || n === 1) return 1;
        return n * this.factorial(n - 1);
    },
    
    // Tìm ước chung lớn nhất
    gcd(a, b) {
        while (b !== 0) {
            let temp = b;
            b = a % b;
            a = temp;
        }
        return Math.abs(a);
    },
    
    // Tìm bội chung nhỏ nhất
    lcm(a, b) {
        return Math.abs(a * b) / this.gcd(a, b);
    },
    
    // Kiểm tra số hoàn hảo
    isPerfectNumber(num) {
        if (num <= 1) return false;
        let sum = 1;
        for (let i = 2; i <= Math.sqrt(num); i++) {
            if (num % i === 0) {
                sum += i;
                if (i !== num / i) {
                    sum += num / i;
                }
            }
        }
        return sum === num;
    },
    
    // Tạo dãy Fibonacci
    fibonacci(n) {
        if (n <= 0) return [];
        if (n === 1) return [0];
        if (n === 2) return [0, 1];
        
        const fib = [0, 1];
        for (let i = 2; i < n; i++) {
            fib[i] = fib[i - 1] + fib[i - 2];
        }
        return fib;
    },
    
    // Tính trung bình
    average(...numbers) {
        if (numbers.length === 0) return 0;
        const sum = numbers.reduce((total, num) => total + num, 0);
        return sum / numbers.length;
    },
    
    // Tìm min/max
    min: (...numbers) => Math.min(...numbers),
    max: (...numbers) => Math.max(...numbers),
    
    // Làm tròn đến n chữ số thập phân
    round(number, decimals = 0) {
        const factor = Math.pow(10, decimals);
        return Math.round(number * factor) / factor;
    }
};

// Test thư viện
console.log("=== THỰC HÀNH THƯVIỆN TOÁN HỌC ===");
console.log("5 + 3 =", MathUtils.add(5, 3));
console.log("10 - 4 =", MathUtils.subtract(10, 4));
console.log("6 × 7 =", MathUtils.multiply(6, 7));
console.log("15 ÷ 3 =", MathUtils.divide(15, 3));
console.log("2^8 =", MathUtils.power(2, 8));
console.log("√16 =", MathUtils.sqrt(16));

console.log("\n=== KIỂM TRA SỐ NGUYÊN TỐ ===");
[2, 3, 4, 17, 25, 29].forEach(num => {
    console.log(`${num} là số nguyên tố:`, MathUtils.isPrime(num));
});

console.log("\n=== TÍNH GIAI THỪA ===");
[0, 1, 5, 7].forEach(num => {
    console.log(`${num}! =`, MathUtils.factorial(num));
});

console.log("\n=== ƯỚC CHUNG LỚN NHẤT VÀ BỘI CHUNG NHỎ NHẤT ===");
console.log("GCD(12, 18) =", MathUtils.gcd(12, 18));
console.log("LCM(12, 18) =", MathUtils.lcm(12, 18));

console.log("\n=== SỐ HOÀN HẢO ===");
[6, 28, 12, 496].forEach(num => {
    console.log(`${num} là số hoàn hảo:`, MathUtils.isPerfectNumber(num));
});

console.log("\n=== DÃY FIBONACCI ===");
console.log("10 số Fibonacci đầu tiên:", MathUtils.fibonacci(10));

console.log("\n=== THỐNG KÊ ===");
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
console.log("Dãy số:", numbers);
console.log("Trung bình:", MathUtils.average(...numbers));
console.log("Nhỏ nhất:", MathUtils.min(...numbers));
console.log("Lớn nhất:", MathUtils.max(...numbers));
console.log("Pi làm tròn 3 chữ số:", MathUtils.round(Math.PI, 3));
```

### Bài 2: Hệ thống quản lý sinh viên

```javascript
// Hệ thống quản lý sinh viên
const StudentManager = {
    students: [],
    
    // Thêm sinh viên
    addStudent(id, name, age, grades = []) {
        const student = {
            id,
            name,
            age,
            grades,
            createdAt: new Date()
        };
        this.students.push(student);
        console.log(`✅ Đã thêm sinh viên: ${name}`);
        return student;
    },
    
    // Tìm sinh viên theo ID
    findStudentById(id) {
        return this.students.find(student => student.id === id);
    },
    
    // Tìm sinh viên theo tên
    findStudentsByName(name) {
        return this.students.filter(student => 
            student.name.toLowerCase().includes(name.toLowerCase())
        );
    },
    
    // Cập nhật thông tin sinh viên
    updateStudent(id, updates) {
        const student = this.findStudentById(id);
        if (student) {
            Object.assign(student, updates);
            console.log(`✅ Đã cập nhật sinh viên ID: ${id}`);
            return student;
        } else {
            console.log(`❌ Không tìm thấy sinh viên ID: ${id}`);
            return null;
        }
    },
    
    // Xóa sinh viên
    removeStudent(id) {
        const index = this.students.findIndex(student => student.id === id);
        if (index !== -1) {
            const removed = this.students.splice(index, 1)[0];
            console.log(`✅ Đã xóa sinh viên: ${removed.name}`);
            return removed;
        } else {
            console.log(`❌ Không tìm thấy sinh viên ID: ${id}`);
            return null;
        }
    },
    
    // Thêm điểm cho sinh viên
    addGrade(studentId, subject, score) {
        const student = this.findStudentById(studentId);
        if (student) {
            student.grades.push({ subject, score, date: new Date() });
            console.log(`✅ Đã thêm điểm ${subject}: ${score} cho ${student.name}`);
            return true;
        }
        return false;
    },
    
    // Tính điểm trung bình của sinh viên
    calculateAverage(studentId) {
        const student = this.findStudentById(studentId);
        if (student && student.grades.length > 0) {
            const total = student.grades.reduce((sum, grade) => sum + grade.score, 0);
            return Math.round((total / student.grades.length) * 100) / 100;
        }
        return 0;
    },
    
    // Xếp loại học lực
    getGradeLevel(average) {
        if (average >= 9) return "Xuất sắc";
        if (average >= 8) return "Giỏi";
        if (average >= 7) return "Khá";
        if (average >= 5) return "Trung bình";
        return "Yếu";
    },
    
    // Hiển thị thông tin sinh viên
    displayStudent(studentId) {
        const student = this.findStudentById(studentId);
        if (!student) {
            console.log(`❌ Không tìm thấy sinh viên ID: ${studentId}`);
            return;
        }
        
        const average = this.calculateAverage(studentId);
        const gradeLevel = this.getGradeLevel(average);
        
        console.log("\n" + "=".repeat(40));
        console.log(`📋 THÔNG TIN SINH VIÊN`);
        console.log("=".repeat(40));
        console.log(`ID: ${student.id}`);
        console.log(`Họ tên: ${student.name}`);
        console.log(`Tuổi: ${student.tuoi}`);
        console.log(`Điểm trung bình: ${average}`);
        console.log(`Xếp loại: ${gradeLevel}`);
        
        if (student.grades.length > 0) {
            console.log("\n📊 BẢNG ĐIỂM:");
            student.grades.forEach((grade, index) => {
                console.log(`${index + 1}. ${grade.subject}: ${grade.score}`);
            });
        } else {
            console.log("\n📊 Chưa có điểm nào.");
        }
        console.log("=".repeat(40));
    },
    
    // Hiển thị tất cả sinh viên
    displayAllStudents() {
        if (this.students.length === 0) {
            console.log("📝 Danh sách sinh viên trống.");
            return;
        }
        
        console.log("\n" + "=".repeat(60));
        console.log("📚 DANH SÁCH TẤT CẢ SINH VIÊN");
        console.log("=".repeat(60));
        
        this.students.forEach((student, index) => {
            const average = this.calculateAverage(student.id);
            const gradeLevel = this.getGradeLevel(average);
            
            console.log(`${index + 1}. ${student.name} (ID: ${student.id})`);
            console.log(`   Tuổi: ${student.age} | Điểm TB: ${average} | Xếp loại: ${gradeLevel}`);
        });
        console.log("=".repeat(60));
    },
    
    // Thống kê lớp
    getClassStatistics() {
        if (this.students.length === 0) {
            return { message: "Không có sinh viên nào." };
        }
        
        const averages = this.students.map(student => this.calculateAverage(student.id));
        const classAverage = averages.reduce((sum, avg) => sum + avg, 0) / averages.length;
        
        const gradeLevels = {
            "Xuất sắc": 0,
            "Giỏi": 0,
            "Khá": 0,
            "Trung bình": 0,
            "Yếu": 0
        };
        
        averages.forEach(avg => {
            const level = this.getGradeLevel(avg);
            gradeLevels[level]++;
        });
        
        return {
            totalStudents: this.students.length,
            classAverage: Math.round(classAverage * 100) / 100,
            gradeLevels,
            highestAverage: Math.max(...averages),
            lowestAverage: Math.min(...averages)
        };
    },
    
    // Hiển thị thống kê
    displayStatistics() {
        const stats = this.getClassStatistics();
        
        if (stats.message) {
            console.log(stats.message);
            return;
        }
        
        console.log("\n" + "=".repeat(50));
        console.log("📊 THỐNG KÊ LỚP HỌC");
        console.log("=".repeat(50));
        console.log(`Tổng số sinh viên: ${stats.totalStudents}`);
        console.log(`Điểm trung bình lớp: ${stats.classAverage}`);
        console.log(`Điểm cao nhất: ${stats.highestAverage}`);
        console.log(`Điểm thấp nhất: ${stats.lowestAverage}`);
        
        console.log("\n📈 PHÂN BỐ XẾP LOẠI:");
        Object.entries(stats.gradeLevels).forEach(([level, count]) => {
            const percentage = Math.round((count / stats.totalStudents) * 100);
            console.log(`${level}: ${count} sinh viên (${percentage}%)`);
        });
        console.log("=".repeat(50));
    }
};

// Test hệ thống
console.log("🎓 HỆ THỐNG QUẢN LÝ SINH VIÊN");

// Thêm sinh viên
StudentManager.addStudent("SV001", "Nguyễn Văn An", 20);
StudentManager.addStudent("SV002", "Trần Thị Bình", 19);
StudentManager.addStudent("SV003", "Lê Văn Cường", 21);

// Thêm điểm
StudentManager.addGrade("SV001", "Toán", 8.5);
StudentManager.addGrade("SV001", "Lý", 7.5);
StudentManager.addGrade("SV001", "Hóa", 9.0);

StudentManager.addGrade("SV002", "Toán", 9.5);
StudentManager.addGrade("SV002", "Lý", 8.0);
StudentManager.addGrade("SV002", "Hóa", 8.5);

StudentManager.addGrade("SV003", "Toán", 6.5);
StudentManager.addGrade("SV003", "Lý", 7.0);

// Hiển thị thông tin
StudentManager.displayStudent("SV001");
StudentManager.displayAllStudents();
StudentManager.displayStatistics();
```

### Bài 3: Game Tic-Tac-Toe

```javascript
// Game Tic-Tac-Toe
const TicTacToe = {
    board: Array(9).fill(null),
    currentPlayer: 'X',
    gameActive: true,
    winningConditions: [
        [0, 1, 2], [3, 4, 5], [6, 7, 8], // Hàng ngang
        [0, 3, 6], [1, 4, 7], [2, 5, 8], // Hàng dọc
        [0, 4, 8], [2, 4, 6]             // Đường chéo
    ],
    
    // Khởi tạo game mới
    newGame() {
        this.board = Array(9).fill(null);
        this.currentPlayer = 'X';
        this.gameActive = true;
        console.log("🎮 Game Tic-Tac-Toe mới bắt đầu!");
        this.displayBoard();
        console.log(`Lượt của người chơi: ${this.currentPlayer}`);
    },
    
    // Hiển thị bàn cờ
    displayBoard() {
        console.log("\n📋 BẢNG GAME:");
        console.log("┌───┬───┬───┐");
        for (let i = 0; i < 9; i += 3) {
            const row = this.board.slice(i, i + 3)
                .map((cell, index) => cell || (i + index + 1))
                .map(cell => ` ${cell} `)
                .join('│');
            console.log(`│${row}│`);
            if (i < 6) console.log("├───┼───┼───┤");
        }
        console.log("└───┴───┴───┘");
    },
    
    // Thực hiện nước đi
    makeMove(position) {
        // Kiểm tra game còn hoạt động không
        if (!this.gameActive) {
            console.log("❌ Game đã kết thúc! Gọi newGame() để chơi lại.");
            return false;
        }
        
        // Kiểm tra vị trí hợp lệ
        if (position < 1 || position > 9) {
            console.log("❌ Vị trí không hợp lệ! Chọn từ 1-9.");
            return false;
        }
        
        const index = position - 1;
        
        // Kiểm tra ô đã được đánh chưa
        if (this.board[index] !== null) {
            console.log("❌ Ô này đã được đánh rồi!");
            return false;
        }
        
        // Thực hiện nước đi
        this.board[index] = this.currentPlayer;
        console.log(`\n✅ Người chơi ${this.currentPlayer} đánh vào ô ${position}`);
        
        // Hiển thị bàn cờ
        this.displayBoard();
        
        // Kiểm tra kết quả
        if (this.checkWin()) {
            console.log(`🎉 Chúc mừng! Người chơi ${this.currentPlayer} thắng!`);
            this.gameActive = false;
            return true;
        }
        
        if (this.checkDraw()) {
            console.log("🤝 Hòa! Không ai thắng.");
            this.gameActive = false;
            return true;
        }
        
        // Chuyển lượt
        this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
        console.log(`\nLượt của người chơi: ${this.currentPlayer}`);
        
        return true;
    },
    
    // Kiểm tra thắng
    checkWin() {
        return this.winningConditions.some(condition => {
            const [a, b, c] = condition;
            return this.board[a] && 
                   this.board[a] === this.board[b] && 
                   this.board[a] === this.board[c];
        });
    },
    
    // Kiểm tra hòa
    checkDraw() {
        return this.board.every(cell => cell !== null);
    },
    
    // AI đơn giản (random move)
    aiMove() {
        if (!this.gameActive || this.currentPlayer !== 'O') {
            return false;
        }
        
        const availableMoves = [];
        this.board.forEach((cell, index) => {
            if (cell === null) {
                availableMoves.push(index + 1);
            }
        });
        
        if (availableMoves.length > 0) {
            const randomMove = availableMoves[Math.floor(Math.random() * availableMoves.length)];
            console.log(`🤖 AI chọn ô ${randomMove}`);
            return this.makeMove(randomMove);
        }
        
        return false;
    },
    
    // Chơi với AI
    playWithAI() {
        this.newGame();
        console.log("🤖 Chế độ chơi với AI. Bạn là X, AI là O.");
        
        // Hàm mô phỏng game với AI
        const simulateGame = () => {
            const playerMoves = [5, 1, 9, 3]; // Mô phỏng nước đi của người chơi
            let moveIndex = 0;
            
            const makeNextMove = () => {
                if (!this.gameActive) return;
                
                if (this.currentPlayer === 'X' && moveIndex < playerMoves.length) {
                    // Nước đi của người chơi
                    setTimeout(() => {
                        console.log(`\n👤 Người chơi chọn ô ${playerMoves[moveIndex]}`);
                        this.makeMove(playerMoves[moveIndex]);
                        moveIndex++;
                        
                        // AI đi sau
                        if (this.gameActive) {
                            setTimeout(() => {
                                this.aiMove();
                                makeNextMove();
                            }, 1000);
                        }
                    }, 1000);
                }
            };
            
            makeNextMove();
        };
        
        // Bắt đầu simulation
        simulateGame();
    },
    
    // Hiển thị hướng dẫn
    showInstructions() {
        console.log("\n📖 HƯỚNG DẪN CHƠI TIC-TAC-TOE:");
        console.log("1. Bàn cờ có 9 ô, được đánh số từ 1-9");
        console.log("2. Người chơi X đi trước, sau đó đến O");
        console.log("3. Mục tiêu: Tạo thành 3 ký hiệu liên tiếp (ngang, dọc, chéo)");
        console.log("4. Sử dụng makeMove(số) để đánh vào ô tương ứng");
        console.log("5. Gọi newGame() để bắt đầu game mới");
        console.log("6. Gọi playWithAI() để chơi với máy");
    }
};

// Demo game
console.log("🎯 TIC-TAC-TOE GAME");
TicTacToe.showInstructions();
TicTacToe.newGame();

// Mô phỏng một game
console.log("\n🎮 Mô phỏng một game:");
setTimeout(() => TicTacToe.makeMove(5), 1000);  // X vào giữa
setTimeout(() => TicTacToe.makeMove(1), 2000);  // O vào góc
setTimeout(() => TicTacToe.makeMove(3), 3000);  // X
setTimeout(() => TicTacToe.makeMove(7), 4000);  // O
setTimeout(() => TicTacToe.makeMove(9), 5000);  // X
setTimeout(() => TicTacToe.makeMove(2), 6000);  // O
setTimeout(() => TicTacToe.makeMove(4), 7000);  // X
setTimeout(() => TicTacToe.makeMove(6), 8000);  // O
setTimeout(() => TicTacToe.makeMove(8), 9000);  // X thắng
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Các cách định nghĩa hàm: declaration, expression, arrow function
- Tham số và đối số: default parameters, rest parameters
- Scope và lexical scope
- Hoisting và closure
- Callback functions và higher-order functions
- Thực hành với các dự án thực tế

Hàm là nền tảng của JavaScript và lập trình nói chung. Hiểu rõ về hàm sẽ giúp bạn viết code hiệu quả và có tổ chức tốt hơn.

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **DOM Manipulation** - cách JavaScript tương tác với HTML để tạo ra các trang web động và tương tác!