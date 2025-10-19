---
title: "Java Cơ Bản #2: Biến và Kiểu Dữ Liệu"
date: 2024-01-22
draft: false
description: "Tìm hiểu về biến và các kiểu dữ liệu cơ bản trong Java với ví dụ thực tế"
tags: ["java", "biến", "kiểu dữ liệu", "cơ bản"]
categories: ["Java"]
series: ["Java Cơ Bản"]
series_order: 2
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## Biến là gì?

**Biến** (Variable) là một "hộp" để lưu trữ dữ liệu trong chương trình. Mỗi biến có một tên và một kiểu dữ liệu cụ thể.

Ví dụ đơn giản:
```java
int tuoi = 25;        // Biến lưu số tuổi
String ten = "Nam";   // Biến lưu tên
```

## Cách khai báo biến

### Cú pháp cơ bản:
```java
kieuDuLieu tenBien = giaTriKhoiTao;
```

### Ví dụ:
```java
public class BienVaKieuDuLieu {
    public static void main(String[] args) {
        // Khai báo và gán giá trị
        int soHoc = 10;
        double diemTrungBinh = 8.5;
        String hoTen = "Nguyễn Văn A";
        boolean daHoc = true;
        
        // In ra màn hình
        System.out.println("Số học: " + soHoc);
        System.out.println("Điểm TB: " + diemTrungBinh);
        System.out.println("Họ tên: " + hoTen);
        System.out.println("Đã học: " + daHoc);
    }
}
```

## Các kiểu dữ liệu cơ bản

### 1. Kiểu số nguyên

| Kiểu | Kích thước | Phạm vi | Ví dụ |
|------|------------|---------|-------|
| `byte` | 1 byte | -128 đến 127 | `byte tuoi = 25;` |
| `short` | 2 byte | -32,768 đến 32,767 | `short nam = 2024;` |
| `int` | 4 byte | -2 tỷ đến 2 tỷ | `int luong = 15000000;` |
| `long` | 8 byte | Rất lớn | `long danSo = 97000000L;` |

```java
public class KieuSoNguyen {
    public static void main(String[] args) {
        byte tuoi = 25;
        short namSinh = 1999;
        int luong = 15000000;
        long danSoVietNam = 97000000L; // Chú ý chữ L ở cuối
        
        System.out.println("Tuổi: " + tuoi);
        System.out.println("Năm sinh: " + namSinh);
        System.out.println("Lương: " + luong + " VND");
        System.out.println("Dân số VN: " + danSoVietNam);
    }
}
```

### 2. Kiểu số thực

| Kiểu | Kích thước | Độ chính xác | Ví dụ |
|------|------------|--------------|-------|
| `float` | 4 byte | 7 chữ số | `float diem = 8.5f;` |
| `double` | 8 byte | 15 chữ số | `double pi = 3.14159;` |

```java
public class KieuSoThuc {
    public static void main(String[] args) {
        float chieuCao = 1.75f; // Chú ý chữ f ở cuối
        double canNang = 65.5;
        double bmi = canNang / (chieuCao * chieuCao);
        
        System.out.println("Chiều cao: " + chieuCao + "m");
        System.out.println("Cân nặng: " + canNang + "kg");
        System.out.println("BMI: " + bmi);
    }
}
```

### 3. Kiểu ký tự và chuỗi

```java
public class KieuKyTu {
    public static void main(String[] args) {
        char kyTu = 'A';           // Một ký tự, dùng dấu nháy đơn
        String chuoi = "Xin chào"; // Chuỗi ký tự, dùng dấu nháy kép
        
        System.out.println("Ký tự: " + kyTu);
        System.out.println("Chuỗi: " + chuoi);
        
        // Một số thao tác với chuỗi
        System.out.println("Độ dài chuỗi: " + chuoi.length());
        System.out.println("Chữ hoa: " + chuoi.toUpperCase());
        System.out.println("Chữ thường: " + chuoi.toLowerCase());
    }
}
```

### 4. Kiểu logic

```java
public class KieuLogic {
    public static void main(String[] args) {
        boolean daKetHon = false;
        boolean coConEm = true;
        
        System.out.println("Đã kết hôn: " + daKetHon);
        System.out.println("Có con em: " + coConEm);
        
        // Sử dụng trong điều kiện
        if (daKetHon) {
            System.out.println("Bạn đã có gia đình");
        } else {
            System.out.println("Bạn còn độc thân");
        }
    }
}
```

## Quy tắc đặt tên biến

### ✅ Đúng:
```java
int tuoi;
String hoTen;
double diemTrungBinh;
boolean daHoc;
final int MAX_STUDENTS = 50; // Hằng số
```

### ❌ Sai:
```java
int 2tuoi;        // Không được bắt đầu bằng số
String ho ten;    // Không được có khoảng trắng
double điểm;      // Không nên dùng tiếng Việt có dấu
int class;        // Không được dùng từ khóa của Java
```

## Hằng số (Constants)

Hằng số là biến không thể thay đổi giá trị sau khi khởi tạo:

```java
public class HangSo {
    public static void main(String[] args) {
        final double PI = 3.14159;
        final int NGAY_TRONG_TUAN = 7;
        final String TRUONG_HOC = "Đại học Bách Khoa";
        
        // PI = 3.14; // Lỗi! Không thể thay đổi giá trị hằng số
        
        double banKinh = 5.0;
        double dienTich = PI * banKinh * banKinh;
        
        System.out.println("Diện tích hình tròn: " + dienTich);
        System.out.println("Số ngày trong tuần: " + NGAY_TRONG_TUAN);
        System.out.println("Trường: " + TRUONG_HOC);
    }
}
```

## Chuyển đổi kiểu dữ liệu

### 1. Chuyển đổi tự động (Implicit)
```java
public class ChuyenDoiTuDong {
    public static void main(String[] args) {
        int soNguyen = 10;
        double soThuc = soNguyen; // int -> double (tự động)
        
        System.out.println("Số nguyên: " + soNguyen);
        System.out.println("Số thực: " + soThuc);
    }
}
```

### 2. Chuyển đổi tường minh (Explicit)
```java
public class ChuyenDoiTuongMinh {
    public static void main(String[] args) {
        double soThuc = 9.8;
        int soNguyen = (int) soThuc; // Ép kiểu double -> int
        
        System.out.println("Số thực: " + soThuc);
        System.out.println("Số nguyên: " + soNguyen); // Kết quả: 9 (mất phần thập phân)
        
        // Chuyển String thành số
        String chuoiSo = "123";
        int so = Integer.parseInt(chuoiSo);
        System.out.println("Chuỗi: " + chuoiSo);
        System.out.println("Số: " + so);
    }
}
```

## Bài tập thực hành

### Bài 1: Thông tin cá nhân
```java
public class ThongTinCaNhan {
    public static void main(String[] args) {
        // Khai báo các biến thông tin cá nhân
        String hoTen = "Nguyễn Văn Nam";
        int tuoi = 22;
        double chieuCao = 1.75;
        double canNang = 65.5;
        boolean daHoc = true;
        char xepLoai = 'A';
        
        // In thông tin
        System.out.println("=== THÔNG TIN CÁ NHÂN ===");
        System.out.println("Họ tên: " + hoTen);
        System.out.println("Tuổi: " + tuoi);
        System.out.println("Chiều cao: " + chieuCao + "m");
        System.out.println("Cân nặng: " + canNang + "kg");
        System.out.println("Đã học đại học: " + daHoc);
        System.out.println("Xếp loại: " + xepLoai);
        
        // Tính BMI
        double bmi = canNang / (chieuCao * chieuCao);
        System.out.println("BMI: " + bmi);
    }
}
```

### Bài 2: Tính toán điểm số
```java
public class TinhDiem {
    public static void main(String[] args) {
        // Điểm các môn học
        double diemToan = 8.5;
        double diemLy = 7.0;
        double diemHoa = 9.0;
        
        // Tính điểm trung bình
        double diemTB = (diemToan + diemLy + diemHoa) / 3;
        
        // In kết quả
        System.out.println("Điểm Toán: " + diemToan);
        System.out.println("Điểm Lý: " + diemLy);
        System.out.println("Điểm Hóa: " + diemHoa);
        System.out.println("Điểm trung bình: " + diemTB);
        
        // Xếp loại
        if (diemTB >= 8.0) {
            System.out.println("Xếp loại: Giỏi");
        } else if (diemTB >= 6.5) {
            System.out.println("Xếp loại: Khá");
        } else {
            System.out.println("Xếp loại: Trung bình");
        }
    }
}
```

### Bài 3: Chuyển đổi đơn vị
```java
public class ChuyenDoiDonVi {
    public static void main(String[] args) {
        // Chuyển đổi nhiệt độ
        double celsius = 25.0;
        double fahrenheit = (celsius * 9/5) + 32;
        
        System.out.println(celsius + "°C = " + fahrenheit + "°F");
        
        // Chuyển đổi tiền tệ (giả sử 1 USD = 24,000 VND)
        final double TY_GIA = 24000;
        double usd = 100;
        double vnd = usd * TY_GIA;
        
        System.out.println(usd + " USD = " + vnd + " VND");
        
        // Chuyển đổi thời gian
        int giay = 3665;
        int gio = giay / 3600;
        int phut = (giay % 3600) / 60;
        int giayConLai = giay % 60;
        
        System.out.println(giay + " giây = " + gio + " giờ " + phut + " phút " + giayConLai + " giây");
    }
}
```

## Lỗi thường gặp và cách khắc phục

### 1. Quên khởi tạo biến
```java
// ❌ Sai
int tuoi;
System.out.println(tuoi); // Lỗi: biến chưa được khởi tạo

// ✅ Đúng
int tuoi = 0;
System.out.println(tuoi);
```

### 2. Nhầm lẫn kiểu dữ liệu
```java
// ❌ Sai
int soThuc = 3.14; // Lỗi: không thể gán số thực cho int

// ✅ Đúng
double soThuc = 3.14;
// hoặc
int soNguyen = (int) 3.14; // Ép kiểu
```

### 3. Quên dấu nháy với String
```java
// ❌ Sai
String ten = Nguyen Van A; // Lỗi: thiếu dấu nháy

// ✅ Đúng
String ten = "Nguyen Van A";
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Khái niệm về biến và cách khai báo
- Các kiểu dữ liệu cơ bản: int, double, String, boolean, char
- Quy tắc đặt tên biến
- Hằng số và cách sử dụng
- Chuyển đổi kiểu dữ liệu
- Các lỗi thường gặp

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **toán tử và biểu thức** trong Java. Hãy thực hành các bài tập để nắm vững kiến thức nhé!