# Kệ Truyện

Trình đọc truyện chạy trên web cho các folder ảnh trong app **Files** trên iPhone. Khi mở ảnh trong Files, iPhone chỉ hiện từng ảnh một. Kệ Truyện cho bạn lướt cả folder như một app đọc truyện.

Chỉ có một file `index.html`, không cần build và không có backend. Ảnh được mở ngay trên máy bạn và không bị tải lên đâu cả.

## Tính năng

- Chọn nhiều ảnh trong Files, hoặc chọn một file `.zip` / `.cbz` (giải nén ngay trên trình duyệt bằng JSZip).
- Xếp trang theo số: `1, 2, … 9, 10, 11`, không bị kiểu `1, 10, 11, 2`.
- Hai kiểu đọc: **Cuộn dọc** (webtoon) và **Lật trang** (chạm cạnh hoặc vuốt). Có tùy chọn lật kiểu manga, từ phải sang trái.
- Thanh trượt để nhảy trang, nhớ trang đang đọc (lưu trong `localStorage`), giữ màn hình sáng khi đọc (Wake Lock).
- Có truyện mẫu để thử ngay.
- **Kệ truyện (menu ☰):** mỗi file .zip hoặc bộ ảnh đã mở được lưu một bản sao trong IndexedDB. Lần sau bấm vào là đọc tiếp, không cần chọn lại file. Mỗi truyện có các nút Đọc, Lưu ra Files (qua bảng Chia sẻ), Ẩn và Xoá.
- **Truyện ẩn:** truyện ẩn được mã hoá AES-GCM bằng khoá tạo từ mật khẩu của bạn (PBKDF2), cả tên lẫn ảnh. Nếu quên mật khẩu thì không mở lại được truyện ẩn.

Lưu ý: trang web không đọc được đường dẫn file gốc trong Files (iOS không cho phép), nên kệ lưu một bản sao. Bản sao này chiếm thêm dung lượng máy. Safari có thể tự xoá dữ liệu của trang nếu lâu không mở. Thêm trang ra màn hình chính thì sẽ không bị xoá.

## Dùng trên iPhone

1. Bấm **Chọn ảnh hoặc file .zip**, rồi chọn **Chọn tệp** (Choose File).
2. Vào folder truyện, bấm **Chọn** (Select), rồi **Chọn tất cả** (Select All), rồi **Mở** (Open).
3. Mẹo: trong Files, nhấn giữ folder và chọn **Nén** (Compress) để có file `.zip`. Chọn đúng file đó là mở được cả bộ.

Sau khi host trang lên mạng, mở bằng Safari rồi bấm Chia sẻ → **Thêm vào MH chính** (Add to Home Screen) để dùng như một app.

## Chạy ở máy

```bash
npx serve .
```

Hoặc dùng `python3 -m http.server`. Để test trên iPhone, máy tính và iPhone phải chung mạng Wi‑Fi.

## Host

Dùng được trên mọi chỗ host trang tĩnh. Với GitHub Pages: vào Settings → Pages → Deploy from branch → `main` / root.

## Ý tưởng làm tiếp

- Lưu bộ truyện vào IndexedDB để không phải chọn lại file.
- Chọn chương khi folder có nhiều thư mục con.
- Phóng to trong chế độ lật trang, chế độ hai trang cho iPad.
- Thêm manifest cho PWA, thêm icon.
