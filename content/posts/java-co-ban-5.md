---
title: "Java Cơ Bản #5: Vòng Lặp - For, While và Do-While"
date: 2024-01-28
draft: false
description: "Tìm hiểu các loại vòng lặp trong Java và cách sử dụng chúng hiệu quả"
tags: ["java", "vòng lặp", "for", "while", "do-while", "cơ bản"]
categories: ["Java"]
series: ["Java Cơ Bản"]
series_order: 5
showTableOfContents: true
---

## Vòng lặp là gì?

**Vòng lặp** (Loop) cho phép chúng ta thực hiện một đoạn code nhiều lần mà không cần viết lại. Giống như khi bạn cần in 100 số từ 1 đến 100, thay vì viết 100 dòng `System.out.println()`, bạn chỉ cần dùng vòng lặp.

Java có 3 loại vòng lặp chính:
- **For loop**: Biết trước số lần lặp
- **While loop**: Lặp khi điều kiện còn đúng
- **Do-while loop**: Thực hiện ít nhất 1 lần, sau đó kiểm tra điều kiện

## 1. Vòng lặp For

### Cú pháp cơ bản:
```java
for (khởi_tạo; điều_kiện; cập_nhật) {
    // Code thực hiện trong mỗi lần lặp
}
```

### Ví dụ đơn giản:
```java
public class VongLapFor {
    public static void main(String[] args) {
        // In số từ 1 đến 5
        System.out.println("Đếm từ 1 đến 5:");
        for (int i = 1; i <= 5; i++) {
            System.out.println("Số: " + i);
        }
        
        // In số chẵn từ 2 đến 10
        System.out.println("\nSố chẵn từ 2 đến 10:");
        for (int i = 2; i <= 10; i += 2) {
            System.out.println(i);
        }
        
        // Đếm ngược từ 10 về 1
        System.out.println("\nĐếm ngược từ 10 về 1:");
        for (int i = 10; i >= 1; i--) {
            System.out.println(i);
        }
    }
}
```

### Ví dụ thực tế - Tính tổng:
```java
public class TinhTong {
    public static void main(String[] args) {
        // Tính tổng từ 1 đến 100
        int tong = 0;
        for (int i = 1; i <= 100; i++) {
            tong += i; // tong = tong + i
        }
        System.out.println("Tổng từ 1 đến 100: " + tong);
        
        // Tính tổng số chẵn từ 2 đến 50
        int tongChan = 0;
        for (int i = 2; i <= 50; i += 2) {
            tongChan += i;
        }
        System.out.println("Tổng số chẵn từ 2 đến 50: " + tongChan);
        
        // Tính giai thừa của 5 (5! = 5 × 4 × 3 × 2 × 1)
        int n = 5;
        long giaiThua = 1;
        for (int i = 1; i <= n; i++) {
            giaiThua *= i;
        }
        System.out.println(n + "! = " + giaiThua);
    }
}
```

## 2. Vòng lặp While

### Cú pháp:
```java
while (điều_kiện) {
    // Code thực hiện khi điều kiện đúng
    // Cần có code để thay đổi điều kiện, tránh vòng lặp vô hạn
}
```

### Ví dụ cơ bản:
```java
public class VongLapWhile {
    public static void main(String[] args) {
        // Đếm từ 1 đến 5
        int i = 1;
        while (i <= 5) {
            System.out.println("Số: " + i);
            i++; // Quan trọng: tăng i để tránh vòng lặp vô hạn
        }
        
        // Tìm số đầu tiên chia hết cho 7 và lớn hơn 50
        int so = 51;
        while (so % 7 != 0) {
            so++;
        }
        System.out.println("Số đầu tiên > 50 và chia hết cho 7: " + so);
        
        // Nhập số cho đến khi nhập đúng (giả lập)
        int soCanTim = 42;
        int doanSo = 30; // Giả sử người dùng đoán
        int lanDoan = 1;
        
        while (doanSo != soCanTim) {
            System.out.println("Lần " + lanDoan + ": Đoán " + doanSo);
            if (doanSo < soCanTim) {
                System.out.println("Số cần tìm lớn hơn!");
                doanSo += 5; // Giả lập tăng đoán
            } else {
                System.out.println("Số cần tìm nhỏ hơn!");
                doanSo -= 3; // Giả lập giảm đoán
            }
            lanDoan++;
        }
        System.out.println("Chúc mừng! Bạn đã đoán đúng số " + soCanTim);
    }
}
```

## 3. Vòng lặp Do-While

### Cú pháp:
```java
do {
    // Code thực hiện ít nhất 1 lần
} while (điều_kiện);
```

### Ví dụ:
```java
public class VongLapDoWhile {
    public static void main(String[] args) {
        // Menu chương trình
        int luaChon;
        
        do {
            System.out.println("\n=== MENU CHÍNH ===");
            System.out.println("1. Xem thông tin");
            System.out.println("2. Thêm dữ liệu");
            System.out.println("3. Cập nhật");
            System.out.println("0. Thoát");
            
            // Giả lập người dùng chọn
            luaChon = 1; // Trong thực tế sẽ nhập từ bàn phím
            
            switch (luaChon) {
                case 1:
                    System.out.println("Đang xem thông tin...");
                    break;
                case 2:
                    System.out.println("Đang thêm dữ liệu...");
                    break;
                case 3:
                    System.out.println("Đang cập nhật...");
                    break;
                case 0:
                    System.out.println("Tạm biệt!");
                    break;
                default:
                    System.out.println("Lựa chọn không hợp lệ!");
            }
            
            // Để tránh vòng lặp vô hạn trong ví dụ này
            if (luaChon != 0) luaChon = 0;
            
        } while (luaChon != 0);
        
        // Ví dụ khác: Kiểm tra mật khẩu
        String matKhauDung = "123456";
        String matKhauNhap;
        int soLanThu = 0;
        
        do {
            soLanThu++;
            matKhauNhap = "123457"; // Giả lập nhập sai lần đầu
            if (soLanThu == 2) matKhauNhap = "123456"; // Lần 2 nhập đúng
            
            System.out.println("Lần thử " + soLanThu + ": Nhập mật khẩu");
            
            if (!matKhauNhap.equals(matKhauDung)) {
                System.out.println("Mật khẩu sai!");
            }
        } while (!matKhauNhap.equals(matKhauDung) && soLanThu < 3);
        
        if (matKhauNhap.equals(matKhauDung)) {
            System.out.println("Đăng nhập thành công!");
        } else {
            System.out.println("Tài khoản bị khóa do nhập sai quá 3 lần!");
        }
    }
}
```

## 4. Vòng lặp For-Each (Enhanced For)

Dùng để duyệt qua các phần tử trong mảng hoặc collection:

```java
public class VongLapForEach {
    public static void main(String[] args) {
        // Mảng các số
        int[] mang = {10, 20, 30, 40, 50};
        
        // Cách thông thường
        System.out.println("Cách thông thường:");
        for (int i = 0; i < mang.length; i++) {
            System.out.println("Phần tử " + i + ": " + mang[i]);
        }
        
        // Cách dùng for-each
        System.out.println("\nCách dùng for-each:");
        for (int phanTu : mang) {
            System.out.println("Giá trị: " + phanTu);
        }
        
        // Mảng chuỗi
        String[] tenHocSinh = {"An", "Bình", "Cường", "Dũng"};
        System.out.println("\nDanh sách học sinh:");
        int stt = 1;
        for (String ten : tenHocSinh) {
            System.out.println(stt + ". " + ten);
            stt++;
        }
    }
}
```

## 5. Vòng lặp lồng nhau (Nested Loop)

```java
public class VongLapLongNhau {
    public static void main(String[] args) {
        // In bảng cửu chương
        System.out.println("BẢNG CỬU CHƯƠNG:");
        for (int i = 2; i <= 9; i++) {
            System.out.println("\nBảng cửu chương " + i + ":");
            for (int j = 1; j <= 10; j++) {
                System.out.println(i + " x " + j + " = " + (i * j));
            }
        }
        
        // In hình tam giác sao
        System.out.println("\nHình tam giác sao:");
        for (int hang = 1; hang <= 5; hang++) {
            for (int sao = 1; sao <= hang; sao++) {
                System.out.print("* ");
            }
            System.out.println(); // Xuống dòng
        }
        
        // In hình chữ nhật số
        System.out.println("\nHình chữ nhật số:");
        for (int hang = 1; hang <= 4; hang++) {
            for (int cot = 1; cot <= 6; cot++) {
                System.out.print(hang + " ");
            }
            System.out.println();
        }
    }
}
```

## 6. Break và Continue

### Break - Thoát khỏi vòng lặp:
```java
public class SuDungBreak {
    public static void main(String[] args) {
        // Tìm số đầu tiên chia hết cho cả 3 và 5
        System.out.println("Tìm số đầu tiên chia hết cho cả 3 và 5:");
        for (int i = 1; i <= 100; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                System.out.println("Số cần tìm: " + i);
                break; // Thoát khỏi vòng lặp
            }
        }
        
        // Kiểm tra số nguyên tố
        int so = 17;
        boolean laSoNguyenTo = true;
        
        for (int i = 2; i <= so / 2; i++) {
            if (so % i == 0) {
                laSoNguyenTo = false;
                break; // Không cần kiểm tra tiếp
            }
        }
        
        if (laSoNguyenTo && so > 1) {
            System.out.println(so + " là số nguyên tố");
        } else {
            System.out.println(so + " không là số nguyên tố");
        }
    }
}
```

### Continue - Bỏ qua lần lặp hiện tại:
```java
public class SuDungContinue {
    public static void main(String[] args) {
        // In số từ 1 đến 10, bỏ qua số 5
        System.out.println("Số từ 1 đến 10 (bỏ qua số 5):");
        for (int i = 1; i <= 10; i++) {
            if (i == 5) {
                continue; // Bỏ qua lần lặp này
            }
            System.out.println(i);
        }
        
        // Tính tổng số lẻ từ 1 đến 20
        int tongSoLe = 0;
        for (int i = 1; i <= 20; i++) {
            if (i % 2 == 0) {
                continue; // Bỏ qua số chẵn
            }
            tongSoLe += i;
        }
        System.out.println("Tổng số lẻ từ 1 đến 20: " + tongSoLe);
    }
}
```

## Bài tập thực hành

### Bài 1: Chương trình quản lý điểm
```java
public class QuanLyDiem {
    public static void main(String[] args) {
        double[] diem = {8.5, 7.0, 9.0, 6.5, 8.0, 7.5, 9.5, 6.0, 8.5, 7.0};
        String[] tenHocSinh = {"An", "Bình", "Cường", "Dũng", "Em", 
                              "Phương", "Giang", "Hà", "Inh", "Khánh"};
        
        System.out.println("=== BẢNG ĐIỂM LỚP ===");
        double tongDiem = 0;
        int soHocSinhGioi = 0;
        int soHocSinhYeu = 0;
        
        for (int i = 0; i < diem.length; i++) {
            System.out.printf("%-10s: %.1f điểm", tenHocSinh[i], diem[i]);
            
            // Xếp loại
            if (diem[i] >= 8.0) {
                System.out.println(" (Giỏi)");
                soHocSinhGioi++;
            } else if (diem[i] >= 6.5) {
                System.out.println(" (Khá)");
            } else if (diem[i] >= 5.0) {
                System.out.println(" (Trung bình)");
            } else {
                System.out.println(" (Yếu)");
                soHocSinhYeu++;
            }
            
            tongDiem += diem[i];
        }
        
        double diemTrungBinh = tongDiem / diem.length;
        System.out.println("\n=== THỐNG KÊ ===");
        System.out.println("Điểm trung bình lớp: " + Math.round(diemTrungBinh * 100.0) / 100.0);
        System.out.println("Số học sinh giỏi: " + soHocSinhGioi);
        System.out.println("Số học sinh yếu: " + soHocSinhYeu);
        
        // Tìm điểm cao nhất và thấp nhất
        double diemCaoNhat = diem[0];
        double diemThapNhat = diem[0];
        String tenCaoNhat = tenHocSinh[0];
        String tenThapNhat = tenHocSinh[0];
        
        for (int i = 1; i < diem.length; i++) {
            if (diem[i] > diemCaoNhat) {
                diemCaoNhat = diem[i];
                tenCaoNhat = tenHocSinh[i];
            }
            if (diem[i] < diemThapNhat) {
                diemThapNhat = diem[i];
                tenThapNhat = tenHocSinh[i];
            }
        }
        
        System.out.println("Điểm cao nhất: " + tenCaoNhat + " (" + diemCaoNhat + ")");
        System.out.println("Điểm thấp nhất: " + tenThapNhat + " (" + diemThapNhat + ")");
    }
}
```

### Bài 2: Trò chơi đoán số
```java
public class TroChoiDoanSo {
    public static void main(String[] args) {
        int soCanTim = 73; // Số cần đoán
        int min = 1, max = 100;
        int lanDoan = 0;
        int maxLanDoan = 7;
        boolean daThang = false;
        
        System.out.println("=== TRÒ CHƠI ĐOÁN SỐ ===");
        System.out.println("Tôi đã nghĩ ra một số từ 1 đến 100.");
        System.out.println("Bạn có " + maxLanDoan + " lần đoán!");
        
        // Giả lập người chơi đoán (trong thực tế sẽ nhập từ bàn phím)
        int[] cacLanDoan = {50, 75, 62, 68, 71, 73}; // Mô phỏng các lần đoán
        
        while (lanDoan < maxLanDoan && !daThang) {
            lanDoan++;
            int doanSo = cacLanDoan[lanDoan - 1]; // Lấy số đoán
            
            System.out.println("\nLần " + lanDoan + ": Bạn đoán số " + doanSo);
            
            if (doanSo == soCanTim) {
                daThang = true;
                System.out.println("🎉 Chúc mừng! Bạn đã đoán đúng!");
                System.out.println("Bạn đã thắng sau " + lanDoan + " lần đoán.");
            } else if (doanSo < soCanTim) {
                System.out.println("📈 Số cần tìm LỚN HƠN " + doanSo);
                min = doanSo + 1;
            } else {
                System.out.println("📉 Số cần tìm NHỎ HƠN " + doanSo);
                max = doanSo - 1;
            }
            
            if (!daThang) {
                System.out.println("Gợi ý: Số nằm trong khoảng [" + min + ", " + max + "]");
                System.out.println("Còn lại " + (maxLanDoan - lanDoan) + " lần đoán.");
            }
        }
        
        if (!daThang) {
            System.out.println("\n😞 Rất tiếc! Bạn đã hết lượt đoán.");
            System.out.println("Số tôi nghĩ là: " + soCanTim);
        }
    }
}
```

### Bài 3: Vẽ hình bằng ký tự
```java
public class VeHinh {
    public static void main(String[] args) {
        // Vẽ kim tự tháp
        System.out.println("KIM TỰ THÁP:");
        int chieuCao = 5;
        for (int hang = 1; hang <= chieuCao; hang++) {
            // In khoảng trắng
            for (int khoangTrang = 1; khoangTrang <= chieuCao - hang; khoangTrang++) {
                System.out.print(" ");
            }
            // In dấu sao
            for (int sao = 1; sao <= 2 * hang - 1; sao++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Vẽ hình thoi
        System.out.println("\nHÌNH THOI:");
        int kichThuoc = 5;
        
        // Nửa trên
        for (int hang = 1; hang <= kichThuoc; hang++) {
            for (int khoangTrang = 1; khoangTrang <= kichThuoc - hang; khoangTrang++) {
                System.out.print(" ");
            }
            for (int sao = 1; sao <= 2 * hang - 1; sao++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Nửa dưới
        for (int hang = kichThuoc - 1; hang >= 1; hang--) {
            for (int khoangTrang = 1; khoangTrang <= kichThuoc - hang; khoangTrang++) {
                System.out.print(" ");
            }
            for (int sao = 1; sao <= 2 * hang - 1; sao++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Vẽ bảng số
        System.out.println("\nBẢNG SỐ:");
        for (int hang = 1; hang <= 10; hang++) {
            for (int cot = 1; cot <= 10; cot++) {
                System.out.printf("%4d", hang * cot);
            }
            System.out.println();
        }
    }
}
```

## So sánh các loại vòng lặp

| Loại vòng lặp | Khi nào dùng | Ưu điểm | Nhược điểm |
|---------------|--------------|---------|------------|
| **For** | Biết trước số lần lặp | Gọn gàng, rõ ràng | Kém linh hoạt |
| **While** | Không biết trước số lần lặp | Linh hoạt | Dễ tạo vòng lặp vô hạn |
| **Do-While** | Cần thực hiện ít nhất 1 lần | Đảm bảo chạy ít nhất 1 lần | Ít dùng |
| **For-Each** | Duyệt mảng/collection | Đơn giản, an toàn | Không có chỉ số |

## Lỗi thường gặp

### 1. Vòng lặp vô hạn
```java
// ❌ Sai - quên tăng biến đếm
int i = 1;
while (i <= 5) {
    System.out.println(i);
    // Quên i++; -> vòng lặp vô hạn
}

// ✅ Đúng
int i = 1;
while (i <= 5) {
    System.out.println(i);
    i++; // Quan trọng!
}
```

### 2. Điều kiện sai
```java
// ❌ Sai - điều kiện không bao giờ đúng
for (int i = 1; i >= 5; i++) { // i bắt đầu từ 1, không thể >= 5
    System.out.println(i);
}

// ✅ Đúng
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

### 3. Sử dụng break/continue sai
```java
// ❌ Sai - break ngoài vòng lặp
if (true) {
    break; // Lỗi: break chỉ dùng trong vòng lặp hoặc switch
}

// ✅ Đúng
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // OK
    }
}
```

## Tổng kết

Trong bài này, chúng ta đã học:
- Ba loại vòng lặp: for, while, do-while
- Vòng lặp for-each để duyệt mảng
- Vòng lặp lồng nhau
- Sử dụng break và continue
- So sánh và lựa chọn vòng lặp phù hợp
- Các lỗi thường gặp

Vòng lặp là một trong những khái niệm quan trọng nhất trong lập trình. Hãy thực hành nhiều để thành thạo!

Ở bài tiếp theo, chúng ta sẽ chuyển sang tìm hiểu về **JavaScript** - ngôn ngữ lập trình web phổ biến nhất hiện nay.