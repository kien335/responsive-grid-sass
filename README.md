# Bài tập CodeGym: Tái cấu trúc CSS thành SASS

**Mã nguồn tham khảo:** https://github.com/codegym-vn/responsive-grid (nhánh `master`, file `responsive_grid.htm`).

## Phân tích CSS gốc

Bản gốc chỉ có một file HTML. CSS viết trong thẻ `<style>` gồm `*`, `.gridwrapper`, `.gridcontent`; nhiều kiểu khác được khai báo trực tiếp qua thuộc tính `style`. Bố cục có thanh header tím, sidebar bên trái với bốn thanh xanh, sidebar bên phải, footer xanh và lớp 12 cột mờ.

## Những thay đổi trong phiên bản SCSS

- `index.html`: giữ nguyên cấu trúc mô phỏng grid, thay inline styles bằng class; nạp `styles.css`.
- `scss/abstracts/_variables.scss`: tập trung màu sắc, chiều cao, khoảng cách, độ mờ và độ rộng cột.
- `scss/abstracts/_mixins.scss`: định nghĩa `grid-cell` và `blue-placeholder` để tránh lặp.
- `scss/base/_reset.scss`: `box-sizing: border-box` như bản gốc.
- `scss/layout/_grid.scss`: các khối `.gridwrapper`, `.gridcontent` dùng nesting `&--...`.
- `scss/components/_mockup.scss`: cấu trúc ví dụ, các thanh sidebar và lưới mờ; dùng nesting cho `:last-child` và `:first-child`.
- `scss/main.scss`: tải các module bằng `@use` (không dùng `@import` đã deprecated).
- `styles.css`: CSS đầu ra cho trình duyệt.
- `original/responsive_grid.htm`: lưu bản gốc để so sánh trước/sau.

## Chạy bài (Windows PowerShell)

Trước hết cần cài SASS nếu máy chưa có: `npm.cmd install -g sass`.

```powershell
sass.cmd -v
sass.cmd scss/main.scss styles.css --no-source-map
sass.cmd scss/main.scss styles.css --watch
```

Giữ Terminal ở chế độ watch; sửa màu `$header-color` trong `scss/abstracts/_variables.scss`, lưu file để kiểm tra CSS cập nhật, sau đó `Ctrl + C` để dừng.

Mở `index.html` trên Chrome hoặc Live Server. Mở thêm `original/responsive_grid.htm` để đối chiếu bố cục và thử đổi độ rộng cửa sổ.

## Nộp bài

Đưa toàn bộ file lên GitHub, dán URL repository vào ô nộp CodeGym. Không cần thay đổi bản gốc trong thư mục `original/`.
