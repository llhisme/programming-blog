---
title: "Java Cơ Bản #4: Cấu Trúc Điều Khiển - If/Else và Switch"
date: 2024-01-26
draft: false
description: "Học cách sử dụng câu lệnh điều kiện if-else và switch-case trong Java"
tags: ["java", "if-else", "switch", "điều kiện", "cơ bản"]
categories: ["Java"]
series: ["Java Cơ Bản"]
series_order: 4
showTableOfContents: true
---

## Cấu trúc điều khiển là gì?

**Cấu trúc điều khiển** cho phép chương trình đưa ra quyết định và thực hiện các hành động khác nhau dựa trên điều kiện. Giống như trong cuộc sống, chúng ta thường phải đưa ra quyết định: "Nếu trời mưa thì mang ô, nếu không thì không cần".

## 1. Câu lệnh If

### Cú pháp cơ bản:
```java
if (điều_kiện) {
    // Code thực hiện khi điều kiện đúng
}
```

### Ví dụ đơn giản:
```java
public class CauLenhIf {
    public static void main(String[] args) {
        int tuoi = 18;
        
        if (tuoi >= 18) {
            System.out.println("Bạn đã đủ tuổi bầu cử!");
        }
        
        // Kiểm tra số chẵn
        int so = 10;
        if (so % 2 == 0) {
            System.out.println(so + " là số chẵn");
        }
        
        // Kiểm tra điểm số
        double diem = 8.5;
        if (diem >= 8.0) {
            System.out.println("Bạn đạt loại giỏi!");
        }
    }
}
```

## 2. Câu lệnh If-Else

### Cú pháp:
```java
if (điều_kiện) {
    // Code khi điều kiện đúng
} else {
    // Code khi điều kiện sai
}
```

### Ví dụ thực tế:
```java
public class IfElse {
    public static void main(String[] args) {
        // Kiểm tra tuổi
        int tuoi = 16;
        if (tuoi >= 18) {
            System.out.println("Bạn đã trưởng thành");
        } else {
            System.out.println("Bạn còn nhỏ tuổi");
        }
        
        // Kiểm tra điểm thi
        double diem = 6.5;
        if (diem >= 5.0) {
            System.out.println("Chúc mừng! Bạn đã đậu");
        } else {
            System.out.println("Rất tiếc! Bạn bị rớt");
        }
        
        // Kiểm tra số dương/âm
        int so = -5;
        if (so > 0) {
            System.out.println(so + " là số dương");
        } else {
            System.out.println(so + " là số âm hoặc bằng 0");
        }
    }
}
```

## 3. Câu lệnh If-Else If-Else

### Cú pháp:
```java
if (điều_kiện_1) {
    // Code khi điều kiện 1 đúng
} else if (điều_kiện_2) {
    // Code khi điều kiện 2 đúng
} else if (điều_kiện_3) {
    // Code khi điều kiện 3 đúng
} else {
    // Code khi tất cả điều kiện đều sai
}
```

### Ví dụ xếp loại học lực:
```java
public class XepLoaiHocLuc {
    public static void main(String[] args) {
        double diemTB = 7.8;
        String xepLoai;
        
        if (diemTB >= 9.0) {
            xepLoai = "Xuất sắc";
        } else if (diemTB >= 8.0) {
            xepLoai = "Giỏi";
        } else if (diemTB >= 6.5) {
            xepLoai = "Khá";
        } else if (diemTB >= 5.0) {
            xepLoai = "Trung bình";
        } else {
            xepLoai = "Yếu";
        }
        
        System.out.println("Điểm trung bình: " + diemTB);
        System.out.println("Xếp loại: " + xepLoai);
    }
}
```

### Ví dụ tính tiền điện:
```java
public class TinhTienDien {
    public static void main(String[] args) {
        int soDien = 250; // kWh
        int tienDien = 0;
        
        if (soDien <= 50) {
            // Bậc 1: 0-50 kWh = 1,678 VND/kWh
            tienDien = soDien * 1678;
        } else if (soDien <= 100) {
            // Bậc 2: 51-100 kWh = 1,734 VND/kWh
            tienDien = 50 * 1678 + (soDien - 50) * 1734;
        } else if (soDien <= 200) {
            // Bậc 3: 101-200 kWh = 2,014 VND/kWh
            tienDien = 50 * 1678 + 50 * 1734 + (soDien - 100) * 2014;
        } else {
            // Bậc 4: > 200 kWh = 2,536 VND/kWh
            tienDien = 50 * 1678 + 50 * 1734 + 100 * 2014 + (soDien - 200) * 2536;
        }
        
        System.out.println("Số điện sử dụng: " + soDien + " kWh");
        System.out.println("Tiền điện phải trả: " + tienDien + " VND");
    }
}
```

## 4. If lồng nhau (Nested If)

```java
public class IfLongNhau {
    public static void main(String[] args) {
        int tuoi = 20;
        boolean coGiayPhep = true;
        boolean coXe = false;
        
        if (tuoi >= 18) {
            System.out.println("Bạn đủ tuổi lái xe");
            
            if (coGiayPhep) {
                System.out.println("Bạn có giấy phép lái xe");
                
                if (coXe) {
                    System.out.println("Bạn có thể lái xe ngay!");
                } else {
                    System.out.println("Bạn cần mua hoặc mượn xe");
                }
            } else {
                System.out.println("Bạn cần thi lấy giấy phép");
            }
        } else {
            System.out.println("Bạn chưa đủ tuổi lái xe");
        }
    }
}
```

## 5. Toán tử ba ngôi (Ternary Operator)

Cú pháp ngắn gọn cho if-else đơn giản:

```java
biến = (điều_kiện) ? giá_trị_nếu_đúng : giá_trị_nếu_sai;
```

### Ví dụ:
```java
public class ToanTuBaNgoi {
    public static void main(String[] args) {
        int a = 10, b = 5;
        
        // Cách viết thông thường
        int max1;
        if (a > b) {
            max1 = a;
        } else {
            max1 = b;
        }
        
        // Cách viết với toán tử ba ngôi
        int max2 = (a > b) ? a : b;
        
        System.out.println("Số lớn nhất: " + max2);
        
        // Ví dụ khác
        int tuoi = 17;
        String thongBao = (tuoi >= 18) ? "Đã trưởng thành" : "Còn nhỏ tuổi";
        System.out.println(thongBao);
        
        // Kiểm tra số chẵn/lẻ
        int so = 15;
        String loaiSo = (so % 2 == 0) ? "chẵn" : "lẻ";
        System.out.println(so + " là số " + loaiSo);
    }
}
```

## 6. Câu lệnh Switch-Case

Switch-case được sử dụng khi cần so sánh một biến với nhiều giá trị cụ thể.

### Cú pháp:
```java
switch (biến) {
    case giá_trị_1:
        // Code khi biến == giá_trị_1
        break;
    case giá_trị_2:
        // Code khi biến == giá_trị_2
        break;
    default:
        // Code khi không khớp case nào
        break;
}
```

### Ví dụ menu chọn:
```java
public class MenuChon {
    public static void main(String[] args) {
        int luaChon = 2;
        
        switch (luaChon) {
            case 1:
                System.out.println("Bạn chọn: Xem thông tin");
                break;
            case 2:
                System.out.println("Bạn chọn: Thêm mới");
                break;
            case 3:
                System.out.println("Bạn chọn: Cập nhật");
                break;
            case 4:
                System.out.println("Bạn chọn: Xóa");
                break;
            case 0:
                System.out.println("Thoát chương trình");
                break;
            default:
                System.out.println("Lựa chọn không hợp lệ!");
                break;
        }
    }
}
```

### Ví dụ với String (Java 7+):
```java
public class SwitchString {
    public static void main(String[] args) {
        String thang = "Tháng 3";
        int soNgay;
        
        switch (thang) {
            case "Tháng 1":
            case "Tháng 3":
            case "Tháng 5":
            case "Tháng 7":
            case "Tháng 8":
            case "Tháng 10":
            case "Tháng 12":
                soNgay = 31;
                break;
            case "Tháng 4":
            case "Tháng 6":
            case "Tháng 9":
            case "Tháng 11":
                soNgay = 30;
                break;
            case "Tháng 2":
                soNgay = 28; // Không tính năm nhuận
                break;
            default:
                soNgay = 0;
                System.out.println("Tháng không hợp lệ!");
                break;
        }
        
        if (soNgay > 0) {
            System.out.println(thang + " có " + soNgay + " ngày");
        }
    }
}
```

### Switch Expression (Java 14+):
```java
public class SwitchExpression {
    public static void main(String[] args) {
        int thu = 3;
        
        String tenThu = switch (thu) {
            case 2 -> "Thứ Hai";
            case 3 -> "Thứ Ba";
            case 4 -> "Thứ Tư";
            case 5 -> "Thứ Năm";
            case 6 -> "Thứ Sáu";
            case 7 -> "Thứ Bảy";
            case 8 -> "Chủ Nhật";
            default -> "Không hợp lệ";
        };
        
        System.out.println("Hôm nay là: " + tenThu);
    }
}
```

## Bài tập thực hành

### Bài 1: Máy tính đơn giản
```java
public class MayTinh {
    public static void main(String[] args) {
        double so1 = 10;
        double so2 = 3;
        char phepToan = '/';
        double ketQua = 0;
        boolean hopLe = true;
        
        switch (phepToan) {
            case '+':
                ketQua = so1 + so2;
                break;
            case '-':
                ketQua = so1 - so2;
                break;
            case '*':
                ketQua = so1 * so2;
                break;
            case '/':
                if (so2 != 0) {
                    ketQua = so1 / so2;
                } else {
                    System.out.println("Lỗi: Không thể chia cho 0!");
                    hopLe = false;
                }
                break;
            default:
                System.out.println("Phép toán không hợp lệ!");
                hopLe = false;
                break;
        }
        
        if (hopLe) {
            System.out.println(so1 + " " + phepToan + " " + so2 + " = " + ketQua);
        }
    }
}
```

### Bài 2: Kiểm tra tam giác
```java
public class KiemTraTamGiac {
    public static void main(String[] args) {
        double a = 3, b = 4, c = 5;
        
        // Kiểm tra có tạo thành tam giác không
        if (a + b > c && a + c > b && b + c > a) {
            System.out.println("Ba cạnh tạo thành một tam giác");
            
            // Phân loại tam giác
            if (a == b && b == c) {
                System.out.println("Đây là tam giác đều");
            } else if (a == b || b == c || a == c) {
                System.out.println("Đây là tam giác cân");
            } else {
                System.out.println("Đây là tam giác thường");
            }
            
            // Kiểm tra tam giác vuông
            double max = Math.max(Math.max(a, b), c);
            if (max == a && b*b + c*c == a*a ||
                max == b && a*a + c*c == b*b ||
                max == c && a*a + b*b == c*c) {
                System.out.println("Đây cũng là tam giác vuông");
            }
            
        } else {
            System.out.println("Ba cạnh không tạo thành tam giác");
        }
    }
}
```

### Bài 3: Hệ thống chấm điểm
```java
public class ChamDiem {
    public static void main(String[] args) {
        double diemToan = 8.5;
        double diemLy = 7.0;
        double diemHoa = 9.0;
        double diemTB = (diemToan + diemLy + diemHoa) / 3;
        
        System.out.println("=== BẢNG ĐIỂM ===");
        System.out.println("Toán: " + diemToan);
        System.out.println("Lý: " + diemLy);
        System.out.println("Hóa: " + diemHoa);
        System.out.println("Điểm TB: " + Math.round(diemTB * 100.0) / 100.0);
        
        // Xếp loại
        String xepLoai;
        if (diemTB >= 9.0) {
            xepLoai = "Xuất sắc";
        } else if (diemTB >= 8.0) {
            xepLoai = "Giỏi";
        } else if (diemTB >= 6.5) {
            xepLoai = "Khá";
        } else if (diemTB >= 5.0) {
            xepLoai = "Trung bình";
        } else {
            xepLoai = "Yếu";
        }
        
        System.out.println("Xếp loại: " + xepLoai);
        
        // Kiểm tra điều kiện tốt nghiệp
        boolean totNghiep = diemTB >= 5.0 && diemToan >= 4.0 && diemLy >= 4.0 && diemHoa >= 4.0;
        
        if (totNghiep) {
            System.out.println("Kết quả: ĐẬU");
            
            // Kiểm tra học bổng
            if (diemTB >= 8.5 && diemToan >= 8.0 && diemLy >= 8.0 && diemHoa >= 8.0) {
                System.out.println("Chúc mừng! Bạn được học bổng!");
            }
        } else {
            System.out.println("Kết quả: RỚT");
            System.out.println("Bạn cần học lại các môn có điểm dưới 4.0");
        }
    }
}
```

## So sánh If-Else và Switch-Case

| Tiêu chí | If-Else | Switch-Case |
|----------|---------|-------------|
| **Sử dụng khi** | Điều kiện phức tạp, phạm vi | So sánh với giá trị cụ thể |
| **Hiệu suất** | Chậm hơn với nhiều điều kiện | Nhanh hơn với nhiều case |
| **Linh hoạt** | Cao (có thể dùng &&, \|\|) | Thấp (chỉ so sánh bằng) |
| **Dễ đọc** | Khó đọc khi có nhiều điều kiện | Dễ đọc với nhiều lựa chọn |

## Lỗi thường gặp

### 1. Quên break trong switch
```java
// ❌ Sai - thiếu break
switch (so) {
    case 1:
        System.out.println("Một");
        // Thiếu break, sẽ chạy tiếp case 2
    case 2:
        System.out.println("Hai");
        break;
}

// ✅ Đúng
switch (so) {
    case 1:
        System.out.println("Một");
        break;
    case 2:
        System.out.println("Hai");
        break;
}
```

### 2. Điều kiện luôn đúng/sai
```java
// ❌ Sai - điều kiện luôn đúng
if (5 > 3) { // Luôn đúng
    System.out.println("Điều này luôn được in");
}

// ❌ Sai - gán thay vì so sánh
int a = 5;
if (a = 10) { // Lỗi cú pháp
    System.out.println("...");
}
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Câu lệnh if, if-else, if-else if-else
- If lồng nhau và toán tử ba ngôi
- Câu lệnh switch-case và switch expression
- So sánh giữa if-else và switch-case
- Các lỗi thường gặp

Ở bài tiếp theo, chúng ta sẽ tìm hiểu về **vòng lặp** (for, while, do-while) trong Java. Hãy thực hành các bài tập để nắm vững kiến thức nhé!