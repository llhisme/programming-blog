# Blog Lập Trình Mạng

Blog cá nhân chia sẻ kiến thức về lập trình Java và JavaScript, được xây dựng bằng Hugo và theme Blowfish.

## 🚀 Tính năng

- **🎨 Responsive Design**: Tối ưu cho mọi thiết bị
- **🐠 Theme Blowfish**: Giao diện hiện đại và chuyên nghiệp  
- **📚 Series Bài Viết**: Tổ chức bài viết theo chuỗi học tập
- **🔍 Tìm kiếm**: Tìm kiếm nội dung dễ dàng
- **🌙 Dark/Light Mode**: Chuyển đổi chế độ sáng/tối
- **⚡ SEO Optimized**: Tối ưu cho công cụ tìm kiếm
- **🚀 Fast Loading**: Tốc độ tải trang nhanh
- **💫 Shortcodes**: Alert, button, timeline, badge components
- **🎯 Hero Background**: Hình nền gradient đẹp mắt
- **📱 Mobile First**: Thiết kế ưu tiên mobile

## 📚 Nội dung

### Java Cơ Bản (5 bài)
1. **Giới Thiệu Về Java và Cài Đặt Môi Trường**
   - Tổng quan về Java
   - Cài đặt JDK và IDE
   - Chương trình Hello World đầu tiên

2. **Biến và Kiểu Dữ Liệu**
   - Các kiểu dữ liệu cơ bản
   - Khai báo và sử dụng biến
   - Chuyển đổi kiểu dữ liệu

3. **Toán Tử và Biểu Thức**
   - Toán tử số học, logic, so sánh
   - Thứ tự ưu tiên
   - Bài tập thực hành

4. **Cấu Trúc Điều Khiển - If/Else và Switch**
   - Câu lệnh điều kiện
   - Switch-case
   - Toán tử ba ngôi

5. **Vòng Lặp - For, While và Do-While**
   - Các loại vòng lặp
   - Break và continue
   - Vòng lặp lồng nhau

### JavaScript Cơ Bản (4 bài)
1. **Giới Thiệu và Thiết Lập Môi Trường**
   - JavaScript là gì?
   - Thiết lập môi trường phát triển
   - Chương trình đầu tiên

2. **Biến, Kiểu Dữ Liệu và Toán Tử**
   - Var, let, const
   - Primitive và non-primitive types
   - Toán tử và chuyển đổi kiểu

3. **Hàm (Functions) và Scope**
   - Function declaration vs expression
   - Arrow functions
   - Scope và closure

4. **DOM Manipulation và Events**
   - Tương tác với HTML DOM
   - Event handling
   - Bài tập thực hành

## 🛠️ Công nghệ sử dụng

- **Hugo**: Static Site Generator
- **Blowfish Theme**: Hugo theme hiện đại
- **GitHub Pages**: Hosting miễn phí
- **GitHub Actions**: CI/CD tự động

## 🚀 Cài đặt và chạy local

### Yêu cầu
- Hugo Extended (v0.121.0+)
- Git

### Các bước cài đặt

1. **Clone repository**
```bash
git clone https://github.com/yourusername/programming-blog.git
cd programming-blog
```

2. **Cài đặt theme (đã có sẵn)**
```bash
git submodule update --init --recursive
```

3. **Chạy development server**
```bash
hugo server -D
```

4. **Truy cập blog**
Mở trình duyệt và vào: `http://localhost:1313/programming-blog/`
(Nếu port 1313 bị chiếm, thử: `hugo server -p 1314`)

## 📝 Thêm bài viết mới

### Tạo bài viết Java
```bash
hugo new posts/java-ten-bai-viet.md
```

### Tạo bài viết JavaScript
```bash
hugo new posts/javascript-ten-bai-viet.md
```

### Template bài viết
```markdown
---
title: "Tiêu đề bài viết"
date: 2024-02-01
draft: false
description: "Mô tả ngắn về bài viết"
tags: ["java", "javascript", "cơ bản"]
categories: ["Java"] # hoặc ["JavaScript"]
series: ["Java Cơ Bản"] # nếu thuộc series
series_order: 1 # thứ tự trong series
showTableOfContents: true
---

Nội dung bài viết ở đây...
```

## 🎨 Tùy chỉnh

### Thay đổi thông tin cá nhân
Chỉnh sửa file `hugo.toml`:
```toml
[languages.vi.author]
  name = "Tên của bạn"
  image = "img/author.jpg"
  headline = "Lập trình viên Java & JavaScript"
  bio = "Mô tả về bản thân"
  links = [
    { email = "mailto:your-email@example.com" },
    { github = "https://github.com/yourusername" },
    { linkedin = "https://linkedin.com/in/yourusername" },
  ]
```

### Thêm ảnh avatar
1. Thêm ảnh vào thư mục `static/img/`
2. Cập nhật đường dẫn trong `hugo.toml`

### Thay đổi màu sắc theme
Tạo file `assets/css/custom.css` và thêm CSS tùy chỉnh.

## 🚀 Deploy lên GitHub Pages

### Tự động (khuyến nghị)
1. Push code lên GitHub repository
2. GitHub Actions sẽ tự động build và deploy
3. Truy cập blog tại: `https://yourusername.github.io/programming-blog`

### Thủ công
```bash
# Build site
hugo --gc --minify

# Deploy (nếu có setup GitHub Pages)
# Files trong thư mục public/ sẽ được deploy
```

## 📊 Analytics và SEO

### Google Analytics
Thêm vào `hugo.toml`:
```toml
[params.analytics]
  google = "G-XXXXXXXXXX"
```

### Search Console
Thêm verification meta tag vào `hugo.toml`:
```toml
[params.verification]
  google = "your-verification-code"
```

## 🤝 Đóng góp

Mọi đóng góp đều được chào đón! Bạn có thể:

1. **Báo lỗi**: Tạo issue mô tả lỗi
2. **Đề xuất tính năng**: Tạo issue với nhãn "enhancement"
3. **Sửa lỗi**: Tạo pull request
4. **Thêm nội dung**: Đề xuất bài viết mới

### Quy trình đóng góp
1. Fork repository
2. Tạo branch mới: `git checkout -b feature/ten-tinh-nang`
3. Commit changes: `git commit -m 'Thêm tính năng mới'`
4. Push to branch: `git push origin feature/ten-tinh-nang`
5. Tạo Pull Request

## 📞 Liên hệ

- **Email**: your-email@example.com
- **GitHub**: [@yourusername](https://github.com/yourusername)
- **LinkedIn**: [Your Name](https://linkedin.com/in/yourusername)

## 📄 License

Dự án này được phân phối dưới giấy phép MIT. Xem file `LICENSE` để biết thêm chi tiết.

## 🙏 Cảm ơn

- [Hugo](https://gohugo.io/) - Static Site Generator tuyệt vời
- [Blowfish Theme](https://blowfish.page/) - Theme Hugo đẹp và mạnh mẽ
- [GitHub Pages](https://pages.github.com/) - Hosting miễn phí
- Cộng đồng lập trình viên Việt Nam

---

**Happy Coding! 🚀**