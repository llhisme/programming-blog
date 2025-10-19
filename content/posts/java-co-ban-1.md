---
title: "Java Cơ Bản #1: Giới Thiệu Về Java và Cài Đặt Môi Trường"
date: 2024-01-20
draft: false
description: "Hướng dẫn chi tiết về Java cho người mới bắt đầu - Phần 1: Giới thiệu và cài đặt"
tags: ["java", "cơ bản", "hướng dẫn", "cài đặt"]
categories: ["Java"]
series: ["Java Cơ Bản"]
series_order: 1
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## Java là gì?

Java là một ngôn ngữ lập trình hướng đối tượng được phát triển bởi Sun Microsystems (hiện thuộc Oracle) vào năm 1995. Java nổi tiếng với slogan **"Write Once, Run Anywhere"** (Viết một lần, chạy mọi nơi).

### Tại sao nên học Java?

1. **Phổ biến**: Java là một trong những ngôn ngữ được sử dụng nhiều nhất thế giới
2. **Đa nền tảng**: Code Java có thể chạy trên Windows, Mac, Linux
3. **Cộng đồng lớn**: Có rất nhiều tài liệu và hỗ trợ từ cộng đồng
4. **Cơ hội việc làm**: Nhiều công ty tuyển dụng lập trình viên Java

## Cài đặt môi trường Java

### Bước 1: Tải và cài đặt JDK

**JDK** (Java Development Kit) là bộ công cụ phát triển Java.

1. Truy cập trang web chính thức của Oracle: https://www.oracle.com/java/technologies/downloads/
2. Chọn phiên bản JDK mới nhất (khuyến nghị JDK 17 hoặc 21)
3. Tải file cài đặt phù hợp với hệ điều hành của bạn
4. Chạy file cài đặt và làm theo hướng dẫn

### Bước 2: Kiểm tra cài đặt

Mở Command Prompt (Windows) hoặc Terminal (Mac/Linux) và gõ:

```bash
java -version
```

Nếu thấy thông tin phiên bản Java hiển thị, bạn đã cài đặt thành công!

### Bước 3: Cài đặt IDE (Môi trường phát triển)

IDE giúp bạn viết code dễ dàng hơn. Tôi khuyến nghị:

#### IntelliJ IDEA Community (Miễn phí)
1. Truy cập: https://www.jetbrains.com/idea/download/
2. Tải phiên bản Community (miễn phí)
3. Cài đặt và khởi động

#### Eclipse (Miễn phí)
1. Truy cập: https://www.eclipse.org/downloads/
2. Tải Eclipse IDE for Java Developers
3. Giải nén và chạy

## Chương trình Java đầu tiên

Hãy tạo chương trình "Hello World" đầu tiên:

### Bước 1: Tạo file Java

Tạo file mới tên `HelloWorld.java`:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào, đây là chương trình Java đầu tiên của tôi!");
    }
}
```

### Bước 2: Giải thích code

- `public class HelloWorld`: Khai báo một class công khai tên HelloWorld
- `public static void main(String[] args)`: Phương thức main - điểm bắt đầu của chương trình
- `System.out.println()`: In ra màn hình và xuống dòng

### Bước 3: Biên dịch và chạy

```bash
# Biên dịch
javac HelloWorld.java

# Chạy
java HelloWorld
```

Kết quả:
```
Xin chào, đây là chương trình Java đầu tiên của tôi!
```

## Cấu trúc cơ bản của chương trình Java

```java
// 1. Import các thư viện cần thiết
import java.util.Scanner;

// 2. Khai báo class
public class TenClass {
    
    // 3. Phương thức main
    public static void main(String[] args) {
        // Code của bạn ở đây
    }
    
    // 4. Các phương thức khác (nếu có)
}
```

## Quy tắc đặt tên trong Java

### Quy tắc bắt buộc:
- Tên class phải trùng với tên file
- Không được bắt đầu bằng số
- Không được chứa khoảng trắng
- Phân biệt chữ hoa/thường

### Quy ước (nên tuân theo):
- **Class**: PascalCase (VD: `HelloWorld`, `StudentManager`)
- **Method/Variable**: camelCase (VD: `getName`, `studentAge`)
- **Constant**: UPPER_CASE (VD: `MAX_SIZE`, `PI_VALUE`)

## Bài tập thực hành

### Bài 1: Chương trình chào hỏi
Tạo chương trình in ra tên và tuổi của bạn:

```java
public class Greeting {
    public static void main(String[] args) {
        System.out.println("Tên tôi là: [Tên của bạn]");
        System.out.println("Tuổi tôi là: [Tuổi của bạn]");
        System.out.println("Tôi đang học Java!");
    }
}
```

### Bài 2: Tính toán đơn giản
```java
public class Calculator {
    public static void main(String[] args) {
        int a = 10;
        int b = 5;
        
        System.out.println("a + b = " + (a + b));
        System.out.println("a - b = " + (a - b));
        System.out.println("a * b = " + (a * b));
        System.out.println("a / b = " + (a / b));
    }
}
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Java là gì và tại sao nên học Java
- Cách cài đặt JDK và IDE
- Tạo chương trình Java đầu tiên
- Cấu trúc cơ bản của chương trình Java
- Quy tắc đặt tên

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **biến và kiểu dữ liệu** trong Java. Hãy thực hành các bài tập trên để làm quen với việc viết code Java nhé!

## Câu hỏi thường gặp

**Q: Tôi có thể học Java mà không cần biết ngôn ngữ lập trình nào khác không?**
A: Có! Java là ngôn ngữ tốt cho người mới bắt đầu lập trình.

**Q: JDK và JRE khác nhau như thế nào?**
A: JDK (Java Development Kit) dùng để phát triển, JRE (Java Runtime Environment) chỉ dùng để chạy chương trình Java.

**Q: Tôi nên chọn IDE nào?**
A: IntelliJ IDEA Community rất tốt cho người mới, giao diện thân thiện và có nhiều tính năng hỗ trợ.