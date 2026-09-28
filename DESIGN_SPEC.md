# VieNeu Mobile Player (PWA) — UI/UX Design Specification
**Version:** 1.1.0-MULTI-MODEL-PROD  
**Author:** Antigravity (Creative Director & Senior Consumer Media Architect)  
**Aesthetic Lineage:** YouTube Media Architecture × Spotify Sensory Restraint × Arc Browser Tactile Focus  
**Platform Target:** Mobile-First Progressive Web App (iOS 16+ Safari / Android 12+ Chrome) — Standalone Display Mode  

---

## 1. DESIGN PHILOSOPHY & PALETTE SPECIFICATION

### 1.1 The Single Unifying Design Principle
> **"Pure Glass on Glass: The phone is an invisible lens; the engine adapts to the user's intent."**
> 
> Whether the user demands cinematic emotional realism from their personal GPU (**VieNeu**), instantaneous zero-friction playback (**Miễn Phí / Edge Cloud**), or bulletproof broadcast-grade cloud delivery (**Azure Neural**), the interface remains pure, dark, and tactile. We clarify latency, we never hide it behind deceptive spinners.

### 1.2 Tri-Model TTS Engine Architecture

| Engine Tier | Processing Core | Latency & Warm-up | Voice Catalog | Primary Use-Case |
| :--- | :--- | :--- | :--- | :--- |
| **VieNeu Local GPU** | Local GTX 1660 SUPER (CUDA FP16, port 8000) | **60s Countdown Ritual** (or **0s instant** if cached) | Anh Khôi, Mỹ Duyên, Minh Đức, Kim Thanh, Thu Trang | Maximum vocal emotion, documentary & film dubbing |
| **Miễn Phí (Edge Cloud)** | Microsoft Edge TTS Cloud API | **2.5s Quick Sync** (Instant start, 0s GPU wait) | Hoài My (Nữ · Bắc), Nam Minh (Nam · Bắc) | 100% Free, quick news, tutorials, no PC GPU load |
| **Azure TTS Cloud** | Microsoft Azure Cognitive Speech Neural | **1.8s Quick Sync** (Studio-grade cloud stream) | Hoài My Neural, Nam Minh Neural | Professional broadcast quality, high stability |

---

### 1.3 Typography System: *Be Vietnam Pro*
Selected for native Vietnamese diacritical rendering (proper accent mark clearances preventing line-height clipping on mobile) paired with geometric grotesque clarity.

| Token | Size | Weight | Line Height | Letter Spacing | Role / Usage |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `type-display` | 32px | 700 Bold | 38px | -0.03em | Hero Countdown Numbers, Major State Indicators |
| `type-title-lg` | 20px | 600 SemiBold | 26px | -0.02em | Video Titles, Screen Headers |
| `type-title-md` | 17px | 600 SemiBold | 22px | -0.015em | Active Dubbing Subtitle (Line 2), Modal Headers |
| `type-body` | 15px | 400 Regular | 20px | 0.00em | Standard Form Inputs, List Item Descriptions |
| `type-caption` | 13px | 500 Medium | 18px | +0.01em | Original Language Subtitle (Line 1), Timestamps, Chips |
| `type-micro` | 11px | 600 SemiBold | 14px | +0.04em | Badge Statuses, Model Tags, GPU Telemetry |

---

### 1.4 Color Palette (OLED High-Contrast Token Architecture)

```
Surface Tokens:
  --bg-canvas:       #0A0A0C  (True Obsidian OLED base)
  --bg-surface:      #121216  (Card background, 10% lightness)
  --bg-elevated:     #1A1A22  (Floating sheets, active chips)
  --bg-glass:        rgba(18, 18, 22, 0.85) (Backdrop blur: 24px)
  --border-subtle:   rgba(255, 255, 255, 0.08)
  --border-active:   rgba(99, 102, 241, 0.40)

Model Accent Tokens:
  --accent-vieneu:   #6366F1  (Electric Indigo — VieNeu Local GPU)
  --accent-free:     #38BDF8  (Sky Blue — Edge Cloud Miễn Phí)
  --accent-azure:    #A78BFA  (Lavender Crystal — Azure Neural Cloud)
  --accent-teal:     #14B8A6  (GPU / Cache Hit Status: 0s Sẵn sàng)
  --accent-amber:    #F59E0B  (Buffer Warming / Lookahead Active)
  --accent-rose:     #F43F5E  (Audio Ducking / Cancel State)

Content Tokens:
  --text-primary:    #FFFFFF  (100% — Active Vietnamese subtitles, main titles)
  --text-secondary:  #A1A1AA  (70% — Original subtitles, labels, metadata)
  --text-tertiary:   #71717A  (40% — Timestamps, inactive states)
  --text-disabled:   #3F3F46  (25% — Disabled states)
```

---

## 2. SCREEN 1: HOME / PASTE SCREEN

### 2.1 Layout Hierarchy & Spatial Architecture
- **Safe Area Top (0 to 48px):** Status bar displaying clock `9:41` and real-time engine telemetry pill:
  - VieNeu Mode: `● GTX 1660 SUPER (Online)`
  - Free Mode: `☁️ Edge Cloud Free`
  - Azure Mode: `💎 Azure Speech Pro`
- **Header (48px to 110px):** Minimal brand logotype `VieNeu Player` with subtitle *"Biến PC thành máy chủ lồng tiếng riêng cho điện thoại"*.
- **Model Engine Switcher Rail (110px to 164px):**
  - Segmented 3-way control: `[ ⚡ VieNeu GPU ]` · `[ ☁️ Miễn Phí (Edge) ]` · `[ 💎 Azure Cloud ]`.
  - Tactile sliding background with distinctive accent borders on active selection.
  - Sub-caption explaining model characteristics (e.g., *"VieNeu Local: Giọng tự nhiên AI · Cần 60s nạp GPU"* vs *"Miễn Phí Edge Cloud: Phát tức thì · Không tốn GPU"*).
- **Hero Paste Box (164px to 234px):**
  - Spans `calc(100vw - 32px)`, height: 56px, radius: 18px.
  - Left YouTube icon, center high-contrast URL input, right gradient button `[ Dán & Phát ]`.
- **Dynamic Voice Chips Carousel (234px to 286px):**
  - Smooth horizontal scrolling chip bar adapting directly to the selected model:
    - VieNeu: `⚡ Anh Khôi` · `🎙️ Mỹ Duyên` · `🎙️ Minh Đức` · `🎙️ Kim Thanh` · `🎙️ Thu Trang`
    - Free: `☁️ Hoài My (Nữ · Bắc)` · `☁️ Nam Minh (Nam · Bắc)`
    - Azure: `💎 Hoài My Neural` · `💎 Nam Minh Neural`
- **Recent Feed Section (286px to bottom):**
  - Media list displaying recently watched and cached videos.
  - Differentiated status badges:
    - `⚡ 0s Chờ` (Audio cache hit on PC)
    - `☁️ Nhanh` (Free/Azure cloud video)
    - `60s Nạp` (Uncached VieNeu video)
- **Bottom Navigation Bar (Fixed 68px):** Translucent glassmorphism tabs: `Trang chủ`, `Trình phát`, `Cài đặt`.

### 2.2 Typography Specs
- **Brand Title:** `type-display` (25px / 700 Bold / `#FFFFFF`), tracking -0.03em.
- **Model Tabs:** `type-caption` (11.5px / 600 SemiBold / Active `#FFFFFF`, Inactive `#A1A1AA`).
- **Input Text:** `type-body` (14px / 400 Regular / `#FFFFFF`).
- **Voice Chips:** `type-caption` (12px / 600 SemiBold / Active `#FFFFFF`, Inactive `#A1A1AA`).
- **Card Titles:** `type-body` (13px / 600 SemiBold / `#FFFFFF`), line-height 1.35.

### 2.3 Color Application
- Background: Strict `--bg-canvas` (`#0A0A0C`).
- Model Tab (VieNeu): `#C7D2FE` border `rgba(99, 102, 241, 0.35)`.
- Model Tab (Free): `#BAE6FD` border `rgba(56, 189, 248, 0.35)`.
- Model Tab (Azure): `#DDD6FE` border `rgba(167, 139, 250, 0.35)`.
- Paste CTA Button: `linear-gradient(135deg, #6366F1, #8B5CF6)`.

### 2.4 Motion Notes
- **Model Tab Switch:** 180ms ease-out cross-fade and smooth scale. Dynamic voice chips slide in from right with subtle stagger.
- **Card Tap Compression:** Scale down to `0.98` on touchstart (80ms linear).

### 2.5 Interaction Details
- Tapping **"Dán & Phát"**:
  - If **VieNeu** model is active: transitions into **Screen 2: 60s Preparation Ritual** (or instant player if cache hit).
  - If **Free (Edge)** or **Azure** model is active: transitions into **Screen 2B: Quick Cloud Warmup (2.5s)** then starts playback immediately.

### 2.6 The Inevitable Design Decision (Not in the brief)
> **"Smart Model Routing on History Tap"**  
> History cards remember which model synthesized them. Tapping a card generated on Free mode immediately sets the model to Free and launches the cloud player; tapping a VieNeu card checks local cache and offers 0s playback.

---

## 3. SCREEN 2: WARM-UP & PREPARATION SCREENS

### 3A. VieNeu Mode: The 60s Countdown Preparation Ritual
- **Visual Staging:** Top 58% blurred video thumbnail (40px blur, desaturated 20%) layered with a 3-stop vertical gradient.
- **The Countdown Ring:**
  - 176px circular SVG with dual stroke: background track (`rgba(255,255,255,0.08)`), active arc with electric indigo gradient (`#6366F1` ➔ `#8B5CF6`).
  - Giant tabular digits `59` counting down smoothly every second.
- **Buffer Ticks Gauge:** 12 glowing physical blocks showing lookahead queue segments being forged on GPU (Filled: Emerald Teal, Cooking: Amber Pulse, Empty: Translucent).
- **Progressive Stage Messaging:**
  - *59s–45s:* "Đang tải & dịch phụ đề qua Groq AI..."
  - *45s–10s:* "VieNeu GPU đang tổng hợp giọng Anh Khôi trên GTX 1660 SUPER..."
  - *10s–00s:* "Sắp hoàn tất bộ đệm đón đầu — Chuẩn bị phát mượt mà..."
- **Escape Hatch Button:** *"Xem gấp? Chuyển sang Miễn Phí Edge Cloud (Bỏ chờ 60s)"* — Tapping instantly switches to Free mode and starts in 2 seconds.

### 3B. Free / Azure Mode: Quick Cloud Warm-Up (2.5s)
- **Visual Staging:** Centered minimal cloud wave animation with pulsating radial rings.
- **Cloud Wave Pulse:**
  - Free Mode: Sky Blue `#38BDF8` cloud glyph with concentric ripple waves.
  - Azure Mode: Lavender Crystal `#A78BFA` studio glyph with concentric ripple waves.
- **Fast Linear Progress Track:** Fills from 0% to 100% in 2.5 seconds with live micro-steps:
  - *Step 1 (0.6s):* "Đang dịch phụ đề qua Groq AI..."
  - *Step 2 (1.5s):* "Đang nạp âm thanh Cloud (Hoài My)..."
  - *Step 3 (2.5s):* "Đã nạp 3 câu — Sẵn sàng phát!"
- **No 60s Wait:** Cleanly communicates that Cloud API does not require local GPU allocation.

---

## 4. SCREEN 3: PLAYER SCREEN (Main Experience)

### 4.1 Layout Hierarchy & Spatial Architecture
- **Video Viewport (Top 0 to 50%):** 16:9 YouTube frame with native controls hidden, audio ducked. Floating pill badge indicates active engine:
  - `● VieNeu: Anh Khôi` (Teal)
  - `☁️ Free: Hoài My` (Sky Blue)
  - `💎 Azure: Nam Minh Neural` (Lavender)
- **Subtitle HUD (50% to 62%):** Pinned directly below video with zero gap:
  - Line 1: Original Language Subtitle (`type-caption`, 12px, muted `#71717A`).
  - Line 2: Vietnamese Dubbed Subtitle (`type-title-md`, 15.5px, bold white `#FFFFFF`, drop shadow).
- **Dual-Audio Acoustic Mixing Console (62% to 74%):**
  - Row 1: **Âm Gốc (Original Track)** slider at 20% (muted white fill).
  - Row 2: **Lồng Tiếng (AI Dub Track)** slider at 90% (gradient indigo fill with glow).
- **Playback Transport (74% to 88%):**
  - High-density seekbar with buffered lookahead bar, played progress, and glowing thumb.
  - Centered 56px circular white Play/Pause button, flanked by ±10s skip triggers.
- **In-Player Voice & Model Switcher (88% to bottom):**
  - Horizontal chip row allowing hot-swapping voices mid-video. Changing voice takes effect seamlessly on the next sentence boundary.

---

## 5. SCREEN 4: SETTINGS SCREEN

### 5.1 Layout Hierarchy & Spatial Architecture
- **Header:** "Cài Đặt Hệ Thống" (`type-title-lg`, 22px).
- **Group 0 — Bộ Máy Lồng Tiếng (TTS Engine Architecture):**
  - 3 selectable cards with radio checkmark:
    1. **VieNeu AI (Local GPU):** Khuyên dùng · Giọng tự nhiên nhất · GTX 1660 SUPER.
    2. **Miễn Phí (Edge Cloud):** 100% Miễn phí · Không tốn GPU · Phát tức thì.
    3. **Azure TTS (Microsoft Cloud):** Giọng chuẩn phòng thu Neural · Độ ổn định cao.
  - **Azure Configuration Form** (expands when Azure is chosen):
    - Azure API Key input field (masked).
    - Azure Service Region (`southeastasia`, `eastasia`, `centralus`).
    - Test connection button with live ping response (`● 42ms OK`).
- **Group 1 — Trải Nghiệm & Hiển Thị:**
  - Default voice preference display.
  - Subtitle display mode segmented switch (`Song ngữ` vs `Chỉ TV`).
- **Group 2 — Bộ Nhớ Đệm Âm Thanh (PC):**
  - Real-time disk cache metric: `143 files (~42.5 MB) trên GTX 1660 SUPER`.
  - Button: `🧹 Dọn dẹp cache tạm (Giữ file audio)`.
- **Group 3 — Kết Nối Máy Chủ PC:**
  - Local PC IP input: `http://192.168.1.15:3000` (Latency: `12ms`).
  - QR Code Scanner button: `📷 Quét mã QR từ TransDuck Studio`.

---

## 6. DESIGN SYSTEM SUMMARY & TOKENS

### 6.1 Spacing Scale (Base 4px Grid)
```
--space-1:   4px
--space-2:   8px
--space-3:   12px
--space-4:   16px   (Standard mobile gutter)
--space-5:   20px
--space-6:   24px   (Section separation)
--space-8:   32px
--space-12:  48px   (Minimum touch target height)
--space-16:  64px   (Hero inputs / Large controls)
```

### 6.2 Radii Scale
```
--radius-sm:  8px    (Badges, chips)
--radius-md:  12px   (Buttons, audio controls)
--radius-lg:  18px   (List cards, input fields)
--radius-xl:  24px   (Modal sheets, hero panels)
--radius-full: 9999px (Pills, circular buttons)
```

### 6.3 Component Inventory
1. **`AppHeader`**: Minimal top bar with real-time model and hardware telemetry.
2. **`ModelSelectorRail`**: 3-state segmented pill control with distinct model accent theming.
3. **`SmartPasteInput`**: 56px input with clipboard auto-sniffing and gradient submit CTA.
4. **`VoiceChipCarousel`**: Dynamic horizontal voice chips filterable by engine model.
5. **`CountdownRing` (VieNeu)**: 176px circular SVG countdown with lookahead buffer tick gauge.
6. **`CloudPulseLoader` (Free / Azure)**: Wave ripple pulse loader for 2.5s rapid cloud initialization.
7. **`SubtitleDisplayHUD`**: High-contrast pinned bilingual subtitle box.
8. **`DualAudioConsole`**: Independent sliders for ducked original and synthesized voice.
9. **`PlaybackTransport`**: Full touch scrubber with ±10s skip and tactile play/pause trigger.
10. **`BottomNavBar`**: 68px frosted glass navigation dock with iOS safe-area support.

---
*VieNeu Mobile Player Design System — Unified across Local GPU, Free Cloud, and Azure Neural.*
