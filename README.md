# VieNeu Mobile Player (PWA) v1.2.0

> **Trình phát lồng tiếng AI đa Model cho điện thoại di động (Mobile-First PWA)**  
> Biến PC thành máy chủ lồng tiếng riêng — Xem video YouTube có lồng tiếng tiếng Việt mượt mà ngay trên điện thoại iPhone & Android.

---

## 📱 Tính Năng Mới trong v1.2.0

- **Trimodal Engine Architecture (3 dòng Model):**
  - **⚡ VieNeu AI (Local GPU):** Giọng clone cảm xúc tự nhiên nhất (GTX 1660 SUPER, nạp đón đầu 60s hoặc phát ngay 0s nếu có cache).
  - **☁️ Miễn Phí (Edge Cloud):** Kết nối trực tiếp Microsoft Edge Cloud, tốc độ nạp nhanh 2.5s, không tốn GPU máy tính.
  - **💎 Azure TTS (Cloud Pro):** Chuẩn phát thanh viên Microsoft Azure Cognitive Speech Service.
- **Vuốt để xoá lịch sử (Swipe-to-Delete History):** Vuốt thẻ video sang trái để xoá nhanh, hỗ trợ rung haptic feedback và thanh hoàn tác (Undo toast) trong 4 giây.
- **Trình chuyển đổi 3 chế độ phụ đề (Trimodal Subtitle HUD):**
  - `[ 双 ]` **Song ngữ:** Hiển thị đồng thời dòng phụ đề gốc (tiếng Anh) và phụ đề dịch tiếng Việt.
  - `[ VI ]` **Chỉ dịch:** Ẩn phụ đề gốc, phóng to dòng phụ đề tiếng Việt lên 17px dễ đọc.
  - `[ CC ]` **Tắt phụ đề:** Thu gọn HUD về 0px, hiện nút CC nổi để bật lại khi cần.
  - Tự động đồng bộ 2 chiều với Cài đặt và lưu vào `localStorage`.
- **Quản lý bộ nhớ đệm âm thanh (Audio Cache Management):**
  - Hiển thị trực tiếp: số files, dung lượng MB và file cũ nhất.
  - **Xoá cache tạm:** Giải phóng dung lượng đệm, giữ lại audio đã lưu.
  - **Xoá toàn bộ:** Bottom sheet xác nhận kèm hiệu ứng đếm ngược odometer mượt mà (600ms).
- **Hỗ trợ Đa Thiết Bị (Adaptive Responsive Layout):** Tự động thích ứng mượt mà trên Điện thoại (Phone), Máy tính bảng (Tablet 2 cột), và Máy tính (Desktop 3 cột / Navigation Rail).
- **Giao diện Kép Sáng / Tối (Dark & Light Mode):** Hỗ trợ Dark Cinema (`#0A0A0C`) và Light Editorial (`#F5F4F2`) chuẩn tương phản WCAG AA.
- **Dual-Audio Mixing Console:** Hai thanh trượt điều khiển độc lập tỷ lệ âm lượng video gốc và âm thanh lồng tiếng AI.

---

## 🚀 Hướng Dẫn Cài Đặt & Sử Dụng Trên Điện Thoại

### Cách 1: Sử dụng qua GitHub Pages (Trực tiếp trên điện thoại)
1. Truy cập liên kết: **[https://duytan1411.github.io/LongTiengVideoYTB/](https://duytan1411.github.io/LongTiengVideoYTB/)**
2. **Trên iPhone (Safari):** Nhấn nút **Chia sẻ (Share)** ở thanh công cụ dưới ➔ Chọn **"Thêm vào Màn hình chính" (Add to Home Screen)**.
3. **Trên Android (Chrome):** Nhấn menu 3 chấm ở góc trên ➔ Chọn **"Cài đặt ứng dụng"** hoặc **"Thêm vào màn hình chính"**.
4. Mở ứng dụng từ icon trên màn hình chính: Ứng dụng chạy toàn màn hình (Standalone PWA) không có thanh địa chỉ trình duyệt.

### Cách 2: Kết nối máy chủ PC cá nhân qua Wi-Fi nội bộ
1. Đảm bảo điện thoại và máy tính kết nối chung mạng Wi-Fi gia đình.
2. Khởi động server máy tính:
   ```bash
   cd TransDuck/backend-server
   node server.js
   ```
   *(Server lắng nghe trên cổng 3000)*
3. Trên điện thoại, mở trình duyệt và truy cập:
   ```
   http://<IP_MÁY_TÍNH>:3000/m/
   ```
   *(Ví dụ: `http://192.168.1.15:3000/m/`)*
4. Thêm vào màn hình chính để sử dụng như app native.

---

## 🛠️ Cấu Trúc Mã Nguồn PWA

- `index.html`: Ứng dụng PWA đầy đủ gồm 4 màn hình (Home, Warmup, Player, Settings) tích hợp CSS design system và JS tương tác.
- `manifest.json`: Khai báo metadata PWA (tên app, màu sắc, chế độ standalone).
- `sw.js`: Service Worker quản lý offline caching và tài nguyên PWA.
- `DESIGN_SPEC.md`: Tài liệu đặc tả thiết kế UI/UX và animation choreographies chi tiết chuẩn v1.2.0.

