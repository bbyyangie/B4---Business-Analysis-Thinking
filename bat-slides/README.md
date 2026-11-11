# Business Analysis Thinking — Slide Web

Trang web trình chiếu 15 slide (ảnh PNG) — thay thế cho Canva link.

## Xem locally

Mở `index.html` trực tiếp bằng trình duyệt, hoặc chạy:

```bash
python -m http.server 8000
# rồi mở http://localhost:8000
```

## Phím tắt

| Phím | Chức năng |
|---|---|
| `←` `→` / `Space` | Chuyển slide |
| `G` | Mở/đóng lưới slide |
| `F` | Toàn màn hình |
| `Home` / `End` | Về đầu / cuối |
| Swipe (mobile) | Chuyển slide |

Slide hiện tại cũng lưu vào URL (`#3`) — refresh không mất vị trí.

## Deploy lên Vercel qua GitHub

### 1. Đẩy code lên GitHub

Tạo repo mới trên [github.com/new](https://github.com/new) (để trống, không tick README), rồi chạy trong thư mục này:

```bash
cd "bat-slides"
git init
git add .
git commit -m "Slide web: Business Analysis Thinking"
git branch -M main
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

> Quan trọng: repo phải chứa `index.html` **ở gốc repo** (thư mục `bat-slides` chính là gốc), kèm folder `slides/`.

### 2. Kết nối Vercel

1. Vào [vercel.com/new](https://vercel.com/new), đăng nhập bằng GitHub
2. Chọn **Import** repo vừa tạo
3. **Framework Preset**: chọn **Other** (site tĩnh, không cần build)
4. Bấm **Deploy**
5. Xong — Vercel cấp domain dạng `<repo-name>.vercel.app`

### 3. Cập nhật slide sau này

Chỉ cần thay ảnh trong `slides/` rồi:

```bash
git add . && git commit -m "Update slides" && git push
```

Vercel tự deploy lại.

## Cấu trúc

```
bat-slides/
├── index.html    # trang trình chiếu (1 file duy nhất, không cần build)
└── slides/       # 1.png → 15.png
```

Thêm/bớt slide: kéo thả ảnh vào `slides/` theo thứ tự tên, rồi sửa biến `TOTAL` trong `index.html`.
