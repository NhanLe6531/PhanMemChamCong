# Gói Đóng Gói Ứng Dụng: Chấm Công Làm Thêm Sinh Viên

Gói mã nguồn này đã được cấu hình sẵn chế độ **Full-screen / Standalone (Ẩn thanh địa chỉ trình duyệt)** và **Ẩn nút cài đặt Kiếm tiền QC** đối với người dùng cuối.

## 1. Các file trong gói đóng gói
- `index.html`: Giao diện và toàn bộ tính năng chấm công sinh viên (đã thêm thẻ `<meta name="mobile-web-app-capable" content="yes">`, `<meta name="apple-mobile-web-app-capable" content="yes">` và ẩn nút `💰 Kiếm tiền QC`).
- `manifest.json`: Cấu hình PWA `display: "standalone"` & `display_override: ["fullscreen", "standalone"]` kèm đủ icon `192x192` và `512x512` để điện thoại mở toàn màn hình không hiện thanh địa chỉ.
- `sw.js`: Service Worker lưu bộ nhớ đệm offline và tự động cập nhật mượt mà không hiện hộp thoại `confirm()` có tên miền.

## 2. Cách dán Link Quảng Cáo Kiếm Tiền vào `index.html`
Mở file `index.html` bằng trình soạn thảo (hoặc sửa trực tiếp trên GitHub), tìm từ khóa `const sampleAds = [` (khoảng dòng 552) và thay thuộc tính `url:` bằng link rút gọn của bạn:
- Bạn có thể dán **không giới hạn số lượng link** và kết hợp **4 loại link kiếm tiền** khác nhau trong mảng `sampleAds`:
  1. **Link Sản phẩm Shopee Affiliate** (`https://s.shopee.vn/...` từ mục *Hoa hồng Sản phẩm* hoặc *Custom Link*).
  2. **Link Chiến dịch / Trang Ưu đãi Shopee** (`https://s.shopee.vn/...` từ mục *Hoa hồng Shopee* / *Ưu đãi độc quyền*).
  3. **Link Chiến dịch CPA / Mở thẻ ngân hàng / Khóa học** (từ Accesstrade, MasOffer...).
  4. **Link Kênh cá nhân / Nhóm săn sale của bạn** (Zalo nhóm săn sale, kênh TikTok/YouTube gắn giỏ hàng).

## 3. Cách khắc phục triệt để lỗi hiện thanh địa chỉ trên điện thoại
- **Nếu cài trực tiếp từ trình duyệt Chrome/Safari:** Sau khi cập nhật `index.html`, `manifest.json` và `sw.js` lên GitHub Pages, hãy xóa shortcut cũ trên màn hình chính điện thoại, mở lại link web trong Chrome và chọn **Cài đặt ứng dụng (Install App / Thêm vào màn hình chính)** — ứng dụng sẽ mở toàn màn hình 100% không còn thanh địa chỉ.
- **Nếu đóng gói thành file `.apk` bằng PWABuilder (Trusted Web Activity - TWA):** Khi dùng PWABuilder, Android yêu cầu file `.well-known/assetlinks.json` trên GitHub Pages khớp mã SHA-256 của file APK thì mới ẩn thanh địa chỉ. Nếu không muốn cấu hình `assetlinks.json`, hãy đóng gói file ZIP này bằng công cụ **WebView APK** (như **WebIntoApp.com** hoặc **Website 2 APK**) — file APK tạo ra dùng Native WebView nên sẽ **không bao giờ hiện thanh địa chỉ**.
