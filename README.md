# VieNeu Mobile Player (PWA)

> **Trình phát lồng tiếng AI đa Model cho điện thoại di động (Mobile-First PWA)**  
> Biến PC thành máy chủ lồng tiếng riêng — Xem video YouTube có lồng tiếng tiếng Việt mượt mà ngay trên điện thoại iPhone & Android.

---

## 📱 Tính Năng Chính

- **Tri-Model Engine:**
  - **⚡ VieNeu AI (Local GPU):** Giọng clone cảm xúc tự nhiên nhất (GTX 1660 SUPER, nạp đón đầu 60s hoặc phát ngay 0s nếu có cache).
  - **☁️ Miễn Phí (Edge Cloud):** Kết nối trực tiếp Microsoft Edge Cloud, tốc độ nạp nhanh 2.5s, không tốn GPU máy tính.
  - **💎 Azure TTS (Cloud Pro):** Chuẩn phát thanh viên Microsoft Azure Cognitive Speech Service.
- **Standalone PWA:** Cài đặt trực tiếp lên màn hình chính điện thoại (Add to Home Screen) — Trải nghiệm toàn màn hình như ứng dụng gốc, không có thanh địa chỉ trình duyệt.
- **Dual-Audio Mixing Console:** Hai thanh trượt điều khiển độc lập:
  - Âm lượng video gốc (ducked xuống 20%).
  - Âm lượng lồng tiếng AI (90% - 100%).
- **Subtitle HUD Song Ngữ:** Hiển thị đồng thời dòng phụ đề gốc (tiếng Anh) và phụ đề dịch tiếng Việt độ tương phản cao.
- **Hot-swapping Giọng Đọc:** Chuyển đổi giọng nói giữa chừng mà không cần dừng video.

---

## 🚀 Hướng Dẫn Cài Đặt Lên Điện Thoại

### Cách 1: Chạy qua GitHub Pages
1. Mở liên kết: [https://duytan1411.github.io/LongTiengVideoYTB/](https://duytan1411.github.io/LongTiengVideoYTB/) trên trình duyệt Safari (iOS) hoặc Chrome (Android).
2. Nhấn nút **Chia sẻ (Share)** trên Safari hoặc menu 3 chấm trên Chrome.
3. Chọn **"Thêm vào Màn hình chính" (Add to Home Screen)**.
4. Mở ứng dụng từ màn hình chính để tận hưởng giao diện không viền.

### Cách 2: Kết nối trực tiếp máy tính qua Wi-Fi
1. Đảm bảo điện thoại và máy tính kết nối chung mạng Wi-Fi.
2. Khởi động server Node.js trên máy tính: `node server.js` (Cổng 3000).
3. Trên điện thoại, truy cập: `http://<IP_MÁY_TÍNH>:3000/m/` (ví dụ: `http://192.168.1.15:3000/m/`).
4. Thêm vào màn hình chính để dùng app.
