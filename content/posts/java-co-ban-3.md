---
title: "Java Cơ Bản #3: Toán Tử và Biểu Thức"
date: 2024-01-24
draft: false
description: "Tìm hiểu các loại toán tử trong Java và cách sử dụng chúng trong biểu thức"
tags: ["java", "toán tử", "biểu thức", "cơ bản"]
categories: ["Java"]
series: ["Java Cơ Bản"]
series_order: 3
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## Toán tử là gì?

**Toán tử** (Operator) là các ký hiệu đặc biệt được sử dụng để thực hiện các phép toán trên dữ liệu. **Biểu thức** (Expression) là sự kết hợp của các biến, hằng số và toán tử.

Ví dụ:
```java
int a = 5;
int b = 3;
int ketQua = a + b; // "a + b" là một biểu thức, "+" là toán tử
```

## 1. Toán tử số học (Arithmetic Operators)

### Các toán tử cơ bản:

| Toán tử | Ý nghĩa | Ví dụ | Kết quả |
|---------|---------|-------|---------|
| `+` | Cộng | `5 + 3` | `8` |
| `-` | Trừ | `5 - 3` | `2` |
| `*` | Nhân | `5 * 3` | `15` |
| `/` | Chia | `10 / 3` | `3` (chia nguyên) |
| `%` | Chia lấy dư | `10 % 3` | `1` |

### Ví dụ thực tế:
```java
public class ToanTuSoHoc {
    public static void main(String[] args) {
        int a = 15;
        int b = 4;
        
        System.out.println("a = " + a + ", b = " + b);
        System.out.println("a + b = " + (a + b)); // 19
        System.out.println("a - b = " + (a - b)); // 11
        System.out.println("a * b = " + (a * b)); // 60
        System.out.println("a / b = " + (a / b)); // 3 (chia nguyên)
        System.out.println("a % b = " + (a % b)); // 3 (15 chia 4 dư 3)
        
        // Chia thực
        double c = 15.0;
        double d = 4.0;
        System.out.println("c / d = " + (c / d)); // 3.75
    }
}
```

### Ứng dụng thực tế:
```java
public class UngDungToanTu {
    public static void main(String[] args) {
        // Tính tiền điện
        int soDien = 150; // kWh
        int giaDien = 2500; // VND/kWh
        int tienDien = soDien * giaDien;
        
        System.out.println("Số điện sử dụng: " + soDien + " kWh");
        System.out.println("Tiền điện: " + tienDien + " VND");
        
        // Kiểm tra số chẵn/lẻ
        int so = 17;
        if (so % 2 == 0) {
            System.out.println(so + " là số chẵn");
        } else {
            System.out.println(so + " là số lẻ");
        }
        
        // Tính thời gian
        int tongGiay = 3725;
        int gio = tongGiay / 3600;
        int phut = (tongGiay % 3600) / 60;
        int giay = tongGiay % 60;
        
        System.out.println(tongGiay + " giây = " + gio + ":" + phut + ":" + giay);
    }
}
```

## 2. Toán tử gán (Assignment Operators)

### Toán tử gán cơ bản:
```java
public class ToanTuGan {
    public static void main(String[] args) {
        int a = 10; // Gán giá trị 10 cho a
        
        a += 5;  // Tương đương: a = a + 5;  (a = 15)
        System.out.println("a += 5: " + a);
        
        a -= 3;  // Tương đương: a = a - 3;  (a = 12)
        System.out.println("a -= 3: " + a);
        
        a *= 2;  // Tương đương: a = a * 2;  (a = 24)
        System.out.println("a *= 2: " + a);
        
        a /= 4;  // Tương đương: a = a / 4;  (a = 6)
        System.out.println("a /= 4: " + a);
        
        a %= 4;  // Tương đương: a = a % 4;  (a = 2)
        System.out.println("a %= 4: " + a);
    }
}
```

## 3. Toán tử tăng/giảm (Increment/Decrement)

```java
public class ToanTuTangGiam {
    public static void main(String[] args) {
        int a = 5;
        
        // Tăng trước (Pre-increment)
        System.out.println("a = " + a);        // 5
        System.out.println("++a = " + (++a));  // 6 (tăng a lên 1, rồi trả về giá trị)
        System.out.println("a = " + a);        // 6
        
        // Tăng sau (Post-increment)
        System.out.println("a++ = " + (a++));  // 6 (trả về giá trị hiện tại, rồi tăng a)
        System.out.println("a = " + a);        // 7
        
        // Giảm trước (Pre-decrement)
        System.out.println("--a = " + (--a));  // 6
        
        // Giảm sau (Post-decrement)
        System.out.println("a-- = " + (a--));  // 6
        System.out.println("a = " + a);        // 5
    }
}
```

### Ví dụ thực tế với vòng lặp:
```java
public class DemSo {
    public static void main(String[] args) {
        System.out.println("Đếm từ 1 đến 5:");
        for (int i = 1; i <= 5; i++) { // i++ tăng i sau mỗi lần lặp
            System.out.println("Lần " + i);
        }
        
        System.out.println("\nĐếm ngược từ 5 về 1:");
        for (int i = 5; i >= 1; i--) { // i-- giảm i sau mỗi lần lặp
            System.out.println("Lần " + i);
        }
    }
}
```

## 4. Toán tử so sánh (Comparison Operators)

| Toán tử | Ý nghĩa | Ví dụ | Kết quả |
|---------|---------|-------|---------|
| `==` | Bằng | `5 == 3` | `false` |
| `!=` | Khác | `5 != 3` | `true` |
| `>` | Lớn hơn | `5 > 3` | `true` |
| `<` | Nhỏ hơn | `5 < 3` | `false` |
| `>=` | Lớn hơn hoặc bằng | `5 >= 5` | `true` |
| `<=` | Nhỏ hơn hoặc bằng | `3 <= 5` | `true` |

```java
public class ToanTuSoSanh {
    public static void main(String[] args) {
        int diem = 85;
        int diemChuan = 80;
        
        System.out.println("Điểm của bạn: " + diem);
        System.out.println("Điểm chuẩn: " + diemChuan);
        
        System.out.println("Điểm >= điểm chuẩn: " + (diem >= diemChuan)); // true
        System.out.println("Điểm == điểm chuẩn: " + (diem == diemChuan)); // false
        System.out.println("Điểm > điểm chuẩn: " + (diem > diemChuan));   // true
        
        // Ứng dụng trong điều kiện
        if (diem >= diemChuan) {
            System.out.println("Chúc mừng! Bạn đã đậu.");
        } else {
            System.out.println("Rất tiếc! Bạn chưa đậu.");
        }
    }
}
```

## 5. Toán tử logic (Logical Operators)

| Toán tử | Ý nghĩa | Ví dụ | Kết quả |
|---------|---------|-------|---------|
| `&&` | VÀ (AND) | `true && false` | `false` |
| `\|\|` | HOẶC (OR) | `true \|\| false` | `true` |
| `!` | PHỦ ĐỊNH (NOT) | `!true` | `false` |

```java
public class ToanTuLogic {
    public static void main(String[] args) {
        int tuoi = 20;
        boolean coGiayPhep = true;
        boolean coTien = false;
        
        // Điều kiện lái xe: >= 18 tuổi VÀ có giấy phép
        boolean coTheLaiXe = (tuoi >= 18) && coGiayPhep;
        System.out.println("Có thể lái xe: " + coTheLaiXe); // true
        
        // Điều kiện mua xe: có giấy phép HOẶC có tiền
        boolean coTheMuaXe = coGiayPhep || coTien;
        System.out.println("Có thể mua xe: " + coTheMuaXe); // true
        
        // Phủ định
        System.out.println("Không có tiền: " + !coTien); // true
        
        // Ví dụ phức tạp hơn
        int diem = 75;
        boolean diHocDayDu = true;
        boolean coChungChi = false;
        
        // Điều kiện tốt nghiệp: (điểm >= 70 VÀ đi học đầy đủ) HOẶC có chứng chỉ
        boolean totNghiep = ((diem >= 70) && diHocDayDu) || coChungChi;
        System.out.println("Được tốt nghiệp: " + totNghiep); // true
    }
}
```

## 6. Thứ tự ưu tiên của toán tử

Khi có nhiều toán tử trong một biểu thức, Java sẽ thực hiện theo thứ tự ưu tiên:

1. `()` - Dấu ngoặc (cao nhất)
2. `++`, `--`, `!` - Tăng/giảm, phủ định
3. `*`, `/`, `%` - Nhân, chia, chia dư
4. `+`, `-` - Cộng, trừ
5. `<`, `<=`, `>`, `>=` - So sánh
6. `==`, `!=` - Bằng, khác
7. `&&` - VÀ logic
8. `||` - HOẶC logic
9. `=`, `+=`, `-=`, ... - Gán (thấp nhất)

```java
public class ThuTuUuTien {
    public static void main(String[] args) {
        int a = 2, b = 3, c = 4;
        
        // Không có dấu ngoặc
        int ketQua1 = a + b * c; // b * c trước, rồi + a
        System.out.println("a + b * c = " + ketQua1); // 2 + 12 = 14
        
        // Có dấu ngoặc
        int ketQua2 = (a + b) * c; // (a + b) trước, rồi * c
        System.out.println("(a + b) * c = " + ketQua2); // 5 * 4 = 20
        
        // Biểu thức phức tạp
        boolean ketQua3 = a > 1 && b < 5 || c == 4;
        // Thứ tự: a > 1 (true), b < 5 (true), true && true (true), c == 4 (true), true || true (true)
        System.out.println("a > 1 && b < 5 || c == 4 = " + ketQua3); // true
    }
}
```

## Bài tập thực hành

### Bài 1: Máy tính đơn giản
```java
public class MayTinhDonGian {
    public static void main(String[] args) {
        double so1 = 15.5;
        double so2 = 4.2;
        
        System.out.println("Số thứ nhất: " + so1);
        System.out.println("Số thứ hai: " + so2);
        System.out.println();
        
        System.out.println("Cộng: " + (so1 + so2));
        System.out.println("Trừ: " + (so1 - so2));
        System.out.println("Nhân: " + (so1 * so2));
        System.out.println("Chia: " + (so1 / so2));
        System.out.println("Chia lấy dư: " + (so1 % so2));
    }
}
```

### Bài 2: Kiểm tra điều kiện học bổng
```java
public class HocBong {
    public static void main(String[] args) {
        double diemTB = 8.5;
        boolean tinhThanh = true; // true = thành phố, false = nông thôn
        int soMonDau = 8;
        boolean coHoatDongXaHoi = true;
        
        System.out.println("=== THÔNG TIN SINH VIÊN ===");
        System.out.println("Điểm TB: " + diemTB);
        System.out.println("Ở thành thành: " + tinhThanh);
        System.out.println("Số môn đậu: " + soMonDau);
        System.out.println("Có hoạt động xã hội: " + coHoatDongXaHoi);
        
        // Điều kiện học bổng:
        // - Điểm TB >= 8.0 VÀ số môn đậu >= 7
        // - HOẶC (điểm TB >= 7.5 VÀ có hoạt động xã hội VÀ không ở thành phố)
        
        boolean hocBongLoai1 = (diemTB >= 8.0) && (soMonDau >= 7);
        boolean hocBongLoai2 = (diemTB >= 7.5) && coHoatDongXaHoi && !tinhThanh;
        boolean duocHocBong = hocBongLoai1 || hocBongLoai2;
        
        System.out.println("\n=== KẾT QUẢ ===");
        System.out.println("Đủ điều kiện học bổng loại 1: " + hocBongLoai1);
        System.out.println("Đủ điều kiện học bổng loại 2: " + hocBongLoai2);
        System.out.println("Được học bổng: " + duocHocBong);
    }
}
```

### Bài 3: Tính lương nhân viên
```java
public class TinhLuong {
    public static void main(String[] args) {
        int soGioLam = 45;
        int luongCoBan = 50000; // VND/giờ
        boolean laQuanLy = false;
        int soNamKinhNghiem = 3;
        
        // Tính lương cơ bản
        int luongGio = soGioLam * luongCoBan;
        
        // Tính lương làm thêm (> 40 giờ)
        int gioLamThem = 0;
        int luongLamThem = 0;
        if (soGioLam > 40) {
            gioLamThem = soGioLam - 40;
            luongLamThem = gioLamThem * luongCoBan * 150 / 100; // 1.5 lần lương
        }
        
        // Phụ cấp quản lý
        int phuCapQuanLy = laQuanLy ? 2000000 : 0;
        
        // Phụ cấp kinh nghiệm
        int phuCapKinhNghiem = soNamKinhNghiem * 500000;
        
        // Tổng lương
        int tongLuong = luongGio + luongLamThem + phuCapQuanLy + phuCapKinhNghiem;
        
        System.out.println("=== BẢNG LƯƠNG ===");
        System.out.println("Số giờ làm: " + soGioLam);
        System.out.println("Lương cơ bản: " + luongGio + " VND");
        System.out.println("Giờ làm thêm: " + gioLamThem);
        System.out.println("Lương làm thêm: " + luongLamThem + " VND");
        System.out.println("Phụ cấp quản lý: " + phuCapQuanLy + " VND");
        System.out.println("Phụ cấp kinh nghiệm: " + phuCapKinhNghiem + " VND");
        System.out.println("TỔNG LƯƠNG: " + tongLuong + " VND");
    }
}
```

## Lỗi thường gặp

### 1. Nhầm lẫn `=` và `==`
```java
// ❌ Sai
int a = 5;
if (a = 10) { // Lỗi: dùng = thay vì ==
    System.out.println("a bằng 10");
}

// ✅ Đúng
int a = 5;
if (a == 10) { // So sánh
    System.out.println("a bằng 10");
}
```

### 2. Chia nguyên không mong muốn
```java
// ❌ Có thể không như mong muốn
int a = 5, b = 2;
double ketQua = a / b; // Kết quả: 2.0 (không phải 2.5)

// ✅ Đúng
int a = 5, b = 2;
double ketQua = (double) a / b; // Kết quả: 2.5
// hoặc
double ketQua = 5.0 / 2; // Kết quả: 2.5
```

### 3. Thứ tự toán tử
```java
// ❌ Có thể gây nhầm lẫn
int ketQua = 2 + 3 * 4; // Kết quả: 14 (không phải 20)

// ✅ Rõ ràng hơn
int ketQua = 2 + (3 * 4); // Kết quả: 14
// hoặc
int ketQua = (2 + 3) * 4; // Kết quả: 20
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Các loại toán tử: số học, gán, tăng/giảm, so sánh, logic
- Cách sử dụng từng loại toán tử
- Thứ tự ưu tiên của toán tử
- Các lỗi thường gặp và cách khắc phục

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **cấu trúc điều khiển** (if-else, switch-case) trong Java. Hãy thực hành các bài tập để nắm vững kiến thức nhé!