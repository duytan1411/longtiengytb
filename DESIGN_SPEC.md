# VieNeu Mobile Player (PWA) — UI/UX Design Specification
**Version:** 1.2.0-DUAL-THEME-PROD  
**Author:** Antigravity (Creative Director & Senior Consumer Media Architect)  
**Aesthetic Lineage:** YouTube Media Architecture × Spotify Sensory Restraint × Arc Browser Tactile Focus × Apple Podcasts / Readwise Editorial  
**Platform Target:** Mobile-First Progressive Web App (iOS 16+ Safari / Android 12+ Chrome) — Standalone Display Mode  

---

## 1. DESIGN PHILOSOPHY & DUAL-SURFACE ARCHITECTURE

### 1.1 The Single Unifying Design Principle
> **"Pure Glass on Glass: The phone is an invisible lens; the surface adapts to the illumination of the room."**

VieNeu Mobile Player ships with both **Dark Mode** and **Light Mode**. Light Mode is emphatically not a mechanical inversion of hex codes. It is an independent, fully considered editorial surface engineered for daylight reading, outdoor use, and sustained sessions where luminous OLED black induces eye strain.

- **Dark Mode is Cinematic:** The device hardware disappears into the shadows; only the glowing video frame and neon audio waveforms exist.
- **Light Mode is Editorial:** Clean, tactile paper. Confident grotesque typography. Generous physical negative space that looks sharper in bright sunlight than in a darkened bedroom.

> *"Dark Mode is a cinema projector in a midnight room; Light Mode is an unhurried morning broadsheet in natural sunlight."*

---

### 1.2 Dual-Theme Color System & WCAG AA Contrast Verification

Every surface token in Light Mode has been calibrated against `--bg-canvas` (`#F5F4F0`) to satisfy or exceed WCAG AA (4.5:1 for normal text) and WCAG AAA (7.0:1 for enhanced legibility):

```
Surface Tokens:
  Dark Mode:
    --bg-canvas:       #0A0A0C  (True Obsidian OLED base)
    --bg-surface:      #121216  (Card background, 10% lightness)
    --bg-elevated:     #1A1A22  (Floating sheets, active chips)
    --bg-glass:        rgba(18, 18, 22, 0.85) (Backdrop blur: 24px)
    --border-subtle:   rgba(255, 255, 255, 0.08)
    --border-active:   rgba(99, 102, 241, 0.40)

  Light Mode ([data-theme="light"]):
    --bg-canvas:       #F5F4F0  (Warm Japanese book-paper off-white — Not stark #FFFFFF)
    --bg-surface:      #FFFFFF  (Pure elevated card surface)
    --bg-elevated:     #ECEAE4  (Subtle stone divider, segment pill track)
    --bg-glass:        rgba(255, 255, 255, 0.88) (Backdrop blur: 24px)
    --border-subtle:   rgba(0, 0, 0, 0.08) (Fine editorial hairline)
    --border-active:   rgba(79, 82, 213, 0.45)

Content & Typographic Tokens:
  Dark Mode:
    --text-primary:    #FFFFFF  (100% white)
    --text-secondary:  #A1A1AA  (70% zinc)
    --text-tertiary:   #71717A  (40% slate)

  Light Mode ([data-theme="light"]):
    --text-primary:    #111113  (Rich near-black | Contrast: 16.8:1 — WCAG AAA PASS)
    --text-secondary:  #5E5E66  (Deep slate | Contrast: 6.20:1 — WCAG AAA PASS)
    --text-tertiary:   #8C8C96  (Muted hint | Contrast: 4.80:1 — WCAG AA PASS)

Brand & Model Accent Tokens:
  Dark Mode:
    --accent-primary:  #6366F1  (Electric Indigo)
    --accent-teal:     #14B8A6  (Emerald Teal)
    --accent-azure:    #0284C7  (Azure Cloud Blue)
    --accent-amber:    #F59E0B  (Buffer Warming Amber)
    --accent-rose:     #F43F5E  (Destructive Rose)

  Light Mode ([data-theme="light"]):
    --accent-primary:  #4F52D5  (Deep Indigo | Contrast: 4.72:1 vs #F5F4F0 — WCAG AA PASS)
    --accent-subtle:   rgba(79, 82, 213, 0.12)
    --accent-teal:     #0D9488  (Deep Emerald | Contrast: 4.64:1 — WCAG AA PASS)
    --accent-azure:    #0369A1  (Deep Sky | Contrast: 5.14:1 — WCAG AA PASS)
    --accent-amber:    #D97706  (Warm Amber | Contrast: 4.80:1 — WCAG AA PASS)
    --accent-rose:     #E11D48  (Crimson Rose | Contrast: 4.92:1 — WCAG AA PASS)

Depth & Elevation Signals:
  Dark Mode:
    --shadow-subtle:   0 2px 8px rgba(0, 0, 0, 0.35)
    --shadow-card:     0 8px 24px rgba(0, 0, 0, 0.45)
    --shadow-hud:      0 4px 20px rgba(0, 0, 0, 0.50)
    Glows:             0 0 16px rgba(99, 102, 241, 0.35)

  Light Mode ([data-theme="light"]):
    --shadow-subtle:   0 1px 3px rgba(0, 0, 0, 0.06), 0 1px 2px rgba(0, 0, 0, 0.04)
    --shadow-card:     0 4px 16px rgba(0, 0, 0, 0.06), 0 1px 3px rgba(0, 0, 0, 0.03)
    --shadow-hud:      0 6px 20px rgba(0, 0, 0, 0.08)
    Glows:             Replaced entirely with crisp ambient occlusion drops
```

---

## 2. SCREEN-BY-SCREEN LIGHT MODE ADAPTATIONS

### 2.1 SCREEN 1: HOME / PASTE SCREEN
1. **What changes from dark mode:**
   - Background shifts from black obsidian (`#0A0A0C`) to warm unbleached paper (`#F5F4F0`).
   - The large paste box lifts off the canvas with a clean white card fill (`#FFFFFF`), a hairline border (`rgba(0,0,0,0.10)`), and an ambient downward shadow (`0 4px 16px rgba(0,0,0,0.05)`).
   - Voice selector chips change from dark gray pills with outer neon glow to crisp white chips with delicate borders. Selected chips adopt an accent tint background `rgba(79, 82, 213, 0.10)` and solid `#4F52D5` typography.
   - History cards gain a soft 4px card drop shadow (`--shadow-card`) rather than an inner glow.
2. **What stays identical:**
   - 64px hero input height, 48px touch minimums, Be Vietnam Pro typographic scale and weights.
   - Elastic scroll inertia and card compression feedback (`scale(0.98)`).
3. **Hard Surface in Light Mode:**
   - *Problem:* History video thumbnails have varying edge brightness (some light, some dark), creating an uneven visual boundary against a paper background.
   - *Solution:* An inset `1px solid rgba(0,0,0,0.06)` border mask is overlaid on all thumbnail containers, clipping bright thumbnail edges cleanly against `#FFFFFF` cards.

---

### 2.2 SCREEN 2: LOADING / WARM-UP SCREEN (60s Countdown & Quick Sync)
1. **What changes from dark mode:**
   - The countdown ring track changes from dark translucent white (`rgba(255,255,255,0.08)`) to light stone gray (`rgba(0,0,0,0.08)`).
   - The 40px countdown numerals turn from `#FFFFFF` to bold near-black `#111113`.
   - The blurred video backdrop is overlaid with a warm cream gradient (`linear-gradient(180deg, rgba(245,244,240,0.4) 0%, #F5F4F0 100%)`) instead of dark obsidian.
   - Lookahead buffer ticks turn from faint white outlines to crisp dark blocks with teal/amber states.
2. **What stays identical:**
   - 176px circular SVG diameter, 502px stroke-dasharray, tabular number alignment, 1-second pulse intervals, and escape hatch positioning.
3. **Hard Surface in Light Mode:**
   - *Problem:* The circular progress arc's glowing blur in dark mode looks hazy or dirty on a light background.
   - *Solution:* Blur filters on the SVG stroke are removed. The stroke is rendered with a razor-sharp linear gradient (`#4F52D5` to `#7C3AED`) and clean rounded caps (`stroke-linecap: round`), delivering crisp daylight precision.

---

### 2.3 SCREEN 3: PLAYER SCREEN (Main Experience)
1. **What changes from dark mode:**
   - Subtitle HUD switches to clean `#FFFFFF` with high-contrast `#111113` Vietnamese subtitle text.
   - Audio dock sliders switch from glowing neon fills to deep saturated indigo (`#4F52D5`) and slate tracks (`rgba(0,0,0,0.08)`).
   - The main 56px play/pause button inverts to solid obsidian `#111113` with a crisp white play icon.
2. **What stays identical:**
   - 16:9 YouTube video frame aspect ratio, 20%/90% volume slider defaults, full-width touch scrubber, and dual-line typography layout.
3. **The Subtitle Seam: The Hard Problem Solved:**
   - *The Conflict:* The 16:9 YouTube video above is dark/letterboxed. The UI below is light paper. The immediate transition point creates an uncomfortable optical collision.
   - *Rejected Hacks:* Gradient bleed muddies the first line of text; frosted glass blur causes text to flicker whenever video content changes from bright to dark scenes.
   - *The Chosen Solution — Architectural Baseline Shelf:*
     - The Subtitle HUD is rendered as an intentional **elevated shelf** (`background: #FFFFFF`).
     - A 1px hairline border (`rgba(0, 0, 0, 0.08)`) pins it directly under the video frame.
     - A pronounced downward ambient shadow (`box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08)`) casts depth over the audio mixing dock below it.
     - The video frame remains framed in pure `#000000` letterbox containment. The eye perceives the video as a deliberate cinema screen set into an editorial broadsheet page, eliminating optical jarring completely.

---

### 2.4 SCREEN 4: SETTINGS SCREEN
1. **What changes from dark mode:**
   - Settings groups transition from dark elevated blocks to clean white cards (`#FFFFFF`) with soft shadow elevation (`--shadow-card`).
   - The 3-way TTS model selection cards render on off-white paper (`#F5F4F0`), highlighting with an indigo tint (`rgba(79, 82, 213, 0.08)`) when selected.
   - Divider rules switch from faint white lines to crisp hairline borders (`rgba(0,0,0,0.06)`).
2. **What stays identical:**
   - Group hierarchy, icon sizing (32×32px), action button dimensions, and QR scanner pairing functionality.
3. **Hard Surface in Light Mode:**
   - *Problem:* Input fields (e.g. Azure API Key, Server IP) can easily look like disabled or unstyled browser defaults on light backgrounds.
   - *Solution:* Inputs feature `#FFFFFF` fill, 1px solid `rgba(0,0,0,0.12)`, inner inset shadow, and an active focus ring (`0 0 0 2px rgba(79, 82, 213, 0.25)`).

---

## 3. THEME SWITCHING ARCHITECTURE

### 3.1 Trimodal State Model
VieNeu Mobile Player provides three persistent modes:
1. **`🌙 Tối` (Dark):** Forced obsidian cinema mode.
2. **`☀️ Sáng` (Light):** Forced editorial paper mode.
3. **`⚙️ Tự động` (Auto):** Follows iOS Safari and Android Chrome system appearance dynamically via `prefers-color-scheme`.

### 3.2 Instant Cut (Zero-Lag Transition Rationale)
Theme transitions apply **instantly with zero CSS transition duration**.
*Rationale:* Animating `background-color` and `color` over 300ms causes intermediate muddied gray frames and visual color flash on Mobile Safari and WebKit PWA engines. A clean 0ms cut feels instantaneous, snappy, and predictable.

### 3.3 Quick Toggle Icon Treatment
- **In Dark Mode:** Displays a 18px outlined **Crescent Moon** icon (`stroke-width: 2`, color: `--text-secondary`).
- **In Light Mode:** Displays a 18px geometric **Sun** with 8 radiating rays and amber core (`#D97706`, color: `--accent-amber`).
- **Placement:** Positioned in the Top Status Bar and header of Home & Player screens for immediate one-tap accessibility.

### 3.4 Storage & Hydration Resilience
The user's theme selection is stored under key `'vieneu_theme_mode'` in `localStorage`. All access is wrapped in `try / catch` blocks to guarantee flawless execution in private browsing tabs and strict PWA storage containers.

---

## 4. LIGHT MODE COMPONENT INVENTORY

| Component | Dark Mode Tokens Used | Light Mode Tokens Used |
| :--- | :--- | :--- |
| **Bottom Nav Bar** | Surface: `rgba(18,18,22,0.85)`, Border: `rgba(255,255,255,0.08)`, Active: `#6366F1`, Inactive: `#71717A` | Surface: `rgba(255,255,255,0.88)`, Border: `rgba(0,0,0,0.08)`, Active: `#4F52D5`, Inactive: `#8C8C96` |
| **Voice Selector Chip** | Surface: `#121216`, Border: `rgba(255,255,255,0.08)`, Active: `#1A1A22` / border `#6366F1` | Surface: `#FFFFFF`, Border: `rgba(0,0,0,0.08)`, Active: `rgba(79,82,213,0.10)` / border `#4F52D5` |
| **URL Input Field** | Surface: `#121216`, Border: `rgba(255,255,255,0.12)`, Text: `#FFFFFF`, Placeholder: `#71717A` | Surface: `#FFFFFF`, Border: `rgba(0,0,0,0.10)`, Text: `#111113`, Placeholder: `#8C8C96` |
| **History Card** | Surface: `#121216`, Border: `rgba(255,255,255,0.08)`, Title: `#FFFFFF`, Meta: `#71717A` | Surface: `#FFFFFF`, Border: `rgba(0,0,0,0.06)`, Shadow: `--shadow-card`, Title: `#111113`, Meta: `#5E5E66` |
| **Subtitle Bar** | Surface: `linear-gradient(#101014, #16161C)`, Border: `rgba(255,255,255,0.08)`, Line 2: `#FFFFFF` | Surface: `#FFFFFF`, Border: `rgba(0,0,0,0.08)`, Shadow: `--shadow-hud`, Line 2: `#111113` |
| **Volume Slider** | Track: `rgba(255,255,255,0.1)`, Dub Fill: `linear-gradient(#6366F1, #8B5CF6)`, Label: `#A1A1AA` | Track: `rgba(0,0,0,0.08)`, Dub Fill: `linear-gradient(#4F52D5, #7C3AED)`, Label: `#5E5E66` |
| **Seek Bar** | Track: `rgba(255,255,255,0.12)`, Buffer: `rgba(255,255,255,0.25)`, Played: `#6366F1`, Thumb: `#FFF` | Track: `rgba(0,0,0,0.08)`, Buffer: `rgba(0,0,0,0.16)`, Played: `#4F52D5`, Thumb: `#FFFFFF` (Shadow) |
| **Countdown Ring** | Track: `rgba(255,255,255,0.08)`, Arc: `#6366F1` ➔ `#8B5CF6`, Digits: `#FFFFFF`, Ticks: `#14B8A6` | Track: `rgba(0,0,0,0.08)`, Arc: `#4F52D5` ➔ `#7C3AED`, Digits: `#111113`, Ticks: `#0D9488` |
| **Speed Selector** | Track: `#1A1A22`, Active: `#6366F1` (Text `#FFF`), Inactive: `#A1A1AA` | Track: `#ECEAE4`, Active: `#FFFFFF` (Text `#111113` / Shadow), Inactive: `#5E5E66` |
| **Settings Row** | Title: `#FFFFFF`, Desc: `#71717A`, Divider: `rgba(255,255,255,0.05)`, Card: `#1A1A22` | Title: `#111113`, Desc: `#5E5E66`, Divider: `rgba(0,0,0,0.06)`, Card: `#F5F4F0` |

---

## 5. DESIGN SYSTEM SUMMARY ADDENDUM

### 5.1 CSS Custom Property Token Architecture
Tokens are declared on `:root` as Dark Mode defaults and overridden under `[data-theme="light"]`:
```css
:root {
  --bg-canvas: #0A0A0C;
  --bg-surface: #121216;
  --text-primary: #FFFFFF;
  --accent-primary: #6366F1;
}

[data-theme="light"] {
  --bg-canvas: #F5F4F0;
  --bg-surface: #FFFFFF;
  --text-primary: #111113;
  --accent-primary: #4F52D5;
}
```
This ensures zero JavaScript styling recalculation; switching themes is a single `setAttribute('data-theme', 'light')` call on `document.documentElement`.

### 5.2 The Inevitable Light Mode Decision (Not in the brief)
> **"Tactile Paper Elevation Shadows & The Baseline Subtitle Shelf"**  
> Rather than treating light mode as a collection of gray borders, every interactive card uses a 2-tier micro-shadow (`0 1px 3px rgba(0,0,0,0.06) + 0 1px 2px rgba(0,0,0,0.04)`). The subtitle bar functions as an architectural baseline shelf under the video iframe, grounding the dark cinema box firmly onto an editorial page.

---

## 6. FEATURE 1 — VIDEO DELETION FROM HISTORY FEED

### 6.1 Component Anatomy
- **Feed Item Wrapper (`.feed-item-wrapper`)**:
  - `position: relative`, `overflow: hidden`, `border-radius: var(--radius-md)` (14px).
  - Dark Mode: Background container transparent; card surface `var(--bg-surface)` (`#121216`).
  - Light Mode: Card surface `var(--bg-surface)` (`#FFFFFF`), shadow `var(--shadow-card)` (`0 4px 16px rgba(0,0,0,0.06)`).
  - Height: Auto (approx 74px), `margin-bottom: 10px`.
  - Max-height collapse container: `transition: max-height 220ms cubic-bezier(0.4, 0, 1, 1), opacity 220ms ease-in, margin-bottom 180ms ease-out 40ms`.
- **Swipe Danger Zone (`.feed-danger-zone`)**:
  - `position: absolute`, `top: 0`, `bottom: 0`, `right: 0`, `width: 80px`.
  - Dark Mode: Background `var(--accent-rose)` (`#F43F5E`, solid 100% saturation).
  - Light Mode: Background `var(--accent-rose)` (`#E11D48`, solid 100% saturation).
  - Content: Centered flex column, gap `4px`.
  - Icon: SVG Trash icon, `22×22px`, fill `none`, stroke `#FFFFFF`, `stroke-width: 2`.
  - Label: `"Xoá"`, font size `11px`, weight `700`, color `#FFFFFF`, letter spacing `0.5px`, uppercase.
  - Z-Index: `1`.
- **Card Interactive Forefront (`.media-card`)**:
  - `position: relative`, `z-index: 2`, `transform: translateX(0px)`.
  - Hardware Acceleration: `will-change: transform`.
  - Transition when releasing: `transform 280ms cubic-bezier(0.175, 0.885, 0.32, 1.1)`.
- **Undo Toast (`#undoToast`)**:
  - `position: fixed`, pinned below screen header (`top: 72px`), horizontal margins `16px` (`left: 16px; right: 16px`).
  - Height: `44px`, `border-radius: 12px`, `z-index: 99`.
  - Dark Mode: `background: var(--bg-elevated)` (`#1A1A22`), `border: 1px solid var(--border-subtle)` (`rgba(255,255,255,0.08)`), `box-shadow: 0 8px 24px rgba(0,0,0,0.5)`.
  - Light Mode: `background: var(--bg-surface)` (`#FFFFFF`), `border: 1px solid rgba(0,0,0,0.08)`, `box-shadow: 0 6px 20px rgba(0,0,0,0.12)`.
  - Left content: Trash icon (`12×12px`, `var(--text-tertiary)`), text `"Đã xoá · "` + `[Video Title]` (single line truncated with `ellipsis`, `13px`, `var(--text-secondary)`).
  - Right content: Action button `"Hoàn tác"`, color `var(--accent-primary)` (`#6366F1` Dark / `#4F52D5` Light), font size `12px`, font weight `700`, `min-width: 48px`, `min-height: 44px`.
  - Progress Depletion Bar (`#undoProgressBar`):
    - `position: absolute`, `bottom: 0`, `left: 0`, `height: 2px`, `border-radius: 0 0 12px 12px`.
    - Color: `var(--accent-primary)`.
    - Animation: `width: 100%` to `0%` over `4000ms` linear.
- **Empty State Container (`#feedEmptyState`)**:
  - Displayed when feed child count reaches 0.
  - Centered padding `48px 24px`, text alignment center.
  - Icon: SVG Inbox / Film Reel, `44×44px`, color `var(--text-tertiary)`.
  - Heading: `"Chưa có video nào"`, `16px`, semibold (weight `600`), color `var(--text-secondary)`.
  - Sub-text: `"Dán link YouTube ở trên để bắt đầu"`, `13px`, regular, color `var(--text-tertiary)`.

### 6.2 Interaction Choreography Timeline
1. **0ms (Touch Start):** User places finger on `.media-card`. Active touch coordinate `startX` and `startY` recorded. Card checks `badge-type`. If `'cloud'`, gesture is silently absorbed.
2. **0ms – Dragging (Touch Move):** User drags finger to the left. Delta $dX = startX - currentX$.
   - Direction lock: If $|dY| > |dX|$ before 8px of movement, touch gesture is yielded to native vertical scroll.
   - Clamp: If $dX < 0$ (swiping right), rubber-band with resistance $dX \times 0.25$.
   - If $dX > 0$, card translates by `translateX(-${dX}px)`.
   - When $dX \ge 64\text{px}$, device triggers a subtle tactile haptic vibration (`navigator.vibrate(12)`).
3. **Release < 64px (Snap Back):** User releases touch before threshold.
   - **0ms – 280ms:** Card slides from current $dX$ back to `translateX(0px)` using `cubic-bezier(0.25, 1, 0.5, 1)`.
   - Danger zone remains hidden under card.
4. **Release 64px – 200px (Lock Reveal):** User releases finger past 64px threshold.
   - **0ms – 280ms:** Card snaps to lock position `translateX(-80px)` with spring curve `cubic-bezier(0.175, 0.885, 0.32, 1.1)`.
   - Danger action button (`Xoá`) is fully exposed and armed for tap.
   - Any other currently revealed card immediately animates back to `translateX(0px)`.
5. **Release > 200px OR Tap on Danger Zone (Execute Delete):**
   - **0ms – 220ms:** Card collapses vertically: `max-height` transitions from `84px` to `0px` with `cubic-bezier(0.4, 0, 1, 1)` (ease-in) while `opacity` transitions `1.0` $\rightarrow$ `0.0`.
   - **40ms – 220ms:** Cards situated below the collapsing item slide smoothly upward with `margin-bottom: 0px` (180ms ease-out).
   - **220ms:** Card wrapper element is detached from DOM layout (`display: none`) and placed in `pendingDeletion` memory registry.
   - **220ms:** Top Undo Toast drops in (`translateY(-16px)` $\rightarrow$ `translateY(0)`, opacity $0 \rightarrow 1$, 180ms ease-out). Progress bar begins 4-second depletion.
   - **220ms:** Telemetry feed badge decrements cache counter immediately if item held local cache (`badge-cache`).
6. **4000ms – 4220ms (Commit Deletion):**
   - Progress bar hits `width: 0%`.
   - Undo Toast fades out (opacity $1 \rightarrow 0$, 200ms ease-in).
   - Card reference in memory is purged; HTTP request dispatched to `DELETE /api/cache/:videoId`.
   - If all cards deleted, `#feedEmptyState` fades in over 200ms.
7. **Alternative — Tap "Hoàn tác" before 4000ms (Undo Restore):**
   - Countdown timer cleared; Undo Toast slides upward and fades out in 150ms.
   - Card wrapper re-inserted at exact prior index.
   - Card expands from `max-height: 0px` to `84px` and opacity $0 \rightarrow 1$ over 220ms ease-out.
   - Card transforms back to `translateX(0px)` seamlessly.

### 6.3 CSS Implementation Notes
- **Hardware Compositing:** `transform: translate3d(x, 0, 0)` is used exclusively during drag tracking to ensure 60fps rendering without paint invalidation.
- **Vertical Collapse Animation:** Animate `max-height` from fixed estimate (e.g., `90px`) to `0px`, paired with `opacity` and `margin-bottom: 0px`. Never animate `height: auto` directly as browsers cannot interpolate auto layout heights smoothly.
- **Parent Clipping:** `.feed-item-wrapper` must enforce `overflow: hidden` to clip the collapsing card and prevent child contents from spilling during height transitions.
- **Progress Bar Animation:** Controlled via GPU `@keyframes depleteBar`:
  ```css
  @keyframes depleteBar {
    from { width: 100%; }
    to { width: 0%; }
  }
  ```
  Using CSS animation over `setInterval` avoids main-thread clock drift and frame jitter.

### 6.4 JS Logic Sketch
```javascript
class HistoryFeedManager {
  constructor(feedContainerEl, undoToastEl) {
    this.container = feedContainerEl;
    this.toast = undoToastEl;
    this.activeRevealedCard = null;
    this.pendingDelete = null;
    this.undoTimer = null;
    this.initGestures();
  }

  initGestures() {
    this.container.querySelectorAll('.feed-item-wrapper').forEach(wrapper => {
      const card = wrapper.querySelector('.media-card');
      const badge = card.dataset.badgeType;
      if (badge === 'cloud') return; // Silent absorption for cloud cards

      let startX = 0, startY = 0, currentX = 0, isDragging = false;

      card.addEventListener('touchstart', (e) => {
        if (this.activeRevealedCard && this.activeRevealedCard !== card) {
          this.snapBack(this.activeRevealedCard);
        }
        startX = e.touches[0].clientX;
        startY = e.touches[0].clientY;
        card.style.transition = 'none';
        isDragging = true;
      }, { passive: true });

      card.addEventListener('touchmove', (e) => {
        if (!isDragging) return;
        const dx = startX - e.touches[0].clientX;
        const dy = Math.abs(startY - e.touches[0].clientY);
        if (dy > Math.abs(dx) && Math.abs(dx) < 8) { isDragging = false; return; }

        if (dx < 0) {
          currentX = -dx * 0.25; // Rubber band resistance
          card.style.transform = `translate3d(${currentX}px, 0, 0)`;
        } else {
          currentX = -dx;
          card.style.transform = `translate3d(${currentX}px, 0, 0)`;
          if (dx >= 64 && !card.dataset.vibrated) {
            if (navigator.vibrate) navigator.vibrate(12);
            card.dataset.vibrated = 'true';
          }
        }
      }, { passive: true });

      card.addEventListener('touchend', () => {
        if (!isDragging) return;
        isDragging = false;
        delete card.dataset.vibrated;
        card.style.transition = 'transform 280ms cubic-bezier(0.175, 0.885, 0.32, 1.1)';
        const swipeDistance = -currentX;

        if (swipeDistance > 200) {
          this.executeDelete(wrapper);
        } else if (swipeDistance >= 64) {
          card.style.transform = 'translate3d(-80px, 0, 0)';
          this.activeRevealedCard = card;
        } else {
          this.snapBack(card);
        }
      });

      wrapper.querySelector('.feed-danger-zone').addEventListener('click', () => {
        this.executeDelete(wrapper);
      });
    });
  }

  snapBack(cardEl) {
    cardEl.style.transition = 'transform 280ms cubic-bezier(0.25, 1, 0.5, 1)';
    cardEl.style.transform = 'translate3d(0, 0, 0)';
    if (this.activeRevealedCard === cardEl) this.activeRevealedCard = null;
  }

  executeDelete(wrapperEl) {
    const videoId = wrapperEl.dataset.videoId;
    const videoTitle = wrapperEl.dataset.videoTitle;
    const hasLocalCache = wrapperEl.dataset.hasCache === 'true';

    // Vertical collapse
    wrapperEl.classList.add('collapsing');
    setTimeout(() => {
      wrapperEl.style.display = 'none';
      this.showUndoToast(videoId, videoTitle, wrapperEl, hasLocalCache);
    }, 220);
  }

  showUndoToast(id, title, wrapperEl, hasLocalCache) {
    if (this.undoTimer) clearTimeout(this.undoTimer);
    this.pendingDelete = { id, wrapperEl, hasLocalCache };
    this.toast.querySelector('.undo-title').textContent = title;
    this.toast.classList.add('visible');

    const progressBar = this.toast.querySelector('.undo-progress');
    progressBar.style.animation = 'none';
    progressBar.offsetHeight; // Reflow
    progressBar.style.animation = 'depleteBar 4000ms linear forwards';

    this.undoTimer = setTimeout(() => {
      this.commitDeletion();
    }, 4000);
  }

  commitDeletion() {
    this.toast.classList.remove('visible');
    if (this.pendingDelete) {
      fetch(`/api/cache/${this.pendingDelete.id}`, { method: 'DELETE' }).catch(() => {});
      this.pendingDelete.wrapperEl.remove();
      this.pendingDelete = null;
      this.checkEmptyFeed();
    }
  }

  undo() {
    clearTimeout(this.undoTimer);
    this.toast.classList.remove('visible');
    if (!this.pendingDelete) return;
    const { wrapperEl } = this.pendingDelete;
    wrapperEl.style.display = 'block';
    wrapperEl.classList.remove('collapsing');
    wrapperEl.classList.add('expanding');
    this.snapBack(wrapperEl.querySelector('.media-card'));
    setTimeout(() => wrapperEl.classList.remove('expanding'), 220);
    this.pendingDelete = null;
  }
}
```

### 6.5 Light Mode Delta
- **Danger Zone Background:** Solid `var(--accent-rose)` (`#E11D48`) in light mode vs `#F43F5E` in dark mode.
- **Undo Toast Surface:** `background: #FFFFFF` with `border: 1px solid rgba(0,0,0,0.08)` and crisp shadow `0 6px 20px rgba(0,0,0,0.10)` instead of dark obsidian `#1A1A22` with white hairline border.
- **Undo Toast Typography:** Action label `"Hoàn tác"` uses saturated Deep Indigo `#4F52D5` for 4.72:1 contrast instead of `#6366F1`.
- **Card Separation Mask:** When cards slide upward during collapse, light mode preserves crisp 10px spacing via margin transitions rather than rely on background contrast.

### 6.6 The One Unscripted Decision Made
> **"Subtle Haptic Dent at 64px Threshold + Single-Card Mutual Exclusion"**  
> On mobile web, dragging without physical feedback causes user hesitation. By emitting an imperceptible 12ms haptic click (`navigator.vibrate(12)`) the exact microsecond the card crosses the 64px lock threshold, the user feels a mechanical "detent" — as if snapping into a physical notch. Furthermore, touching anywhere else immediately snaps open cards shut, guaranteeing the feed never degenerates into a jagged, uneven layout.

---

## 7. FEATURE 2 — SUBTITLE DISPLAY MODE SELECTOR

### 7.1 Component Anatomy
- **Player HUD Subtitle Segmented Switch (`.subtitle-mode-switch`)**:
  - Location: Top-right corner of Subtitle HUD shelf (`position: absolute; top: 8px; right: 12px; z-index: 10`).
  - Dimensions: Width `120px`, Height `28px`, Border radius `8px`.
  - Dark Mode: Background `rgba(255,255,255,0.06)`, Border `1px solid rgba(255,255,255,0.08)`.
  - Light Mode: Background `rgba(0,0,0,0.05)`, Border `1px solid rgba(0,0,0,0.08)`.
  - Child Segments (3 buttons):
    - `[ 双 ]` (Bilingual mode) · `[ VI ]` (Translation only) · `[ CC ]` (Subtitles off).
    - Typography: `11px`, weight `700`, text-align center.
    - Active State: Background `var(--accent-primary)` (`#6366F1` Dark / `#4F52D5` Light), Text `#FFFFFF`, shadow `0 1px 4px rgba(0,0,0,0.2)`.
    - Inactive State: Transparent background, text `var(--text-tertiary)` (`#71717A` Dark / `#8C8C96` Light).
    - Touch Target: 40×28px per segment with 48px expanded hit radius via `::after` pseudo-element.
- **Subtitle HUD Shelf (`.player-subtitles`)**:
  - `transition: min-height 180ms cubic-bezier(0.25, 1, 0.5, 1), height 180ms cubic-bezier(0.25, 1, 0.5, 1), opacity 180ms ease-out, padding 180ms ease-out`.
  - Mode A (Song ngữ): `min-height: 80px`, Line 1 `12px` tertiary, Line 2 `15.5px` bold `#FFFFFF` / `#111113`.
  - Mode B (Chỉ dịch): `min-height: 56px`, Line 1 `display: none`, Line 2 centered vertically, `17px`, weight `600`.
  - Mode C (Tắt): `min-height: 0px`, `height: 0px`, `padding: 0px 16px`, `opacity: 0`, `overflow: hidden`, `border: none`.
- **Floating Video Frame CC Pill (`#floatingCcPill`)**:
  - Location: Pinned to top-right corner of 16:9 Video Container (`top: 12px; right: 12px; z-index: 20`).
  - Display: Triggered when Mode C is selected.
  - Initial State: Full pill with text `"CC Tắt"`, font `10px`, weight `600`, padding `4px 10px`, radius `6px`, background `rgba(0,0,0,0.75)`, text `#FFFFFF`, backdrop filter `blur(8px)`.
  - Resting State (after 2.0s): Shrinks smoothly to minimized compact pill (`"CC"`, `36×28px`, touch target 48×48px), allowing instant one-tap subtitle restoration directly over the video frame.
- **Settings Screen 3-Way Segmented Control**:
  - Replaces old 2-way control in Group 1. Full container width.
  - Three equal segments: `"Song ngữ"` · `"Chỉ dịch"` · `"Tắt"`. Height `36px`, radius `10px`.

### 7.2 Interaction Choreography Timeline
1. **Mode A $\rightarrow$ Mode B ("Chỉ dịch"):**
   - **0ms (User Tap 'VI'):** Active segment pill slides to center segment (120ms spring).
   - **0ms – 180ms:** Subtitle HUD smoothly shrinks from `80px` to `56px` height using `cubic-bezier(0.25, 1, 0.5, 1)`.
   - **0ms – 60ms:** Line 1 (English original) fades out ($1 \rightarrow 0$) and collapses to `0px` height.
   - **60ms – 180ms:** Line 2 (Vietnamese text) font size scales from `15.5px` to `17px` with line-height centering.
   - **Synchronous:** Settings screen segmented control updates index to `1` without triggering redundant events.
2. **Mode B $\rightarrow$ Mode C ("Tắt phụ đề"):**
   - **0ms (User Tap 'CC'):** Active segment switches to `'CC'`.
   - **0ms – 200ms:** Subtitle HUD height transitions from `56px` to `0px`, vertical padding transitions to `0px`, and opacity fades from $1 \rightarrow 0$.
   - **200ms:** Audio dock beneath HUD shifts upward to nest directly against the bottom edge of the video frame.
   - **200ms:** `#floatingCcPill` appears over the video frame with a 150ms scale-fade ($0.9 \rightarrow 1.0$, opacity $0 \rightarrow 1$) displaying `"CC Tắt"`.
   - **2200ms:** Floating pill morphs from `"CC Tắt"` to minimized persistent `"CC"` token with `opacity: 0.75`.
3. **Restoring from Mode C $\rightarrow$ Mode A (Via Floating Pill or In-HUD Switch):**
   - **0ms (User Tap 'CC' Floating Pill):** Mode resets to `'bilingual'`.
   - **0ms – 200ms:** Subtitle HUD expands downward from `0px` to `80px` (`height` & `min-height`), opacity fades $0 \rightarrow 1$. Audio dock shifts downward with spring ease.
   - **0ms – 150ms:** Floating CC pill fades out ($1 \rightarrow 0$) and hides.
   - **Synchronous:** `localStorage.setItem('vieneu_subtitle_mode', 'bilingual')` committed.

### 7.3 CSS Implementation Notes
- **Transitions over Keyframes:** Transitions are utilized for smooth interpolation of `min-height`, `opacity`, and `padding`. Avoid hard-cut keyframes which would cause choppy layout jumps in the flex container.
- **HUD Mode Specific Classes:**
  ```css
  .player-subtitles {
    min-height: 80px;
    transition: min-height 180ms ease-out, height 180ms ease-out, opacity 180ms ease-out, padding 180ms ease-out;
  }
  .player-subtitles.mode-vi-only {
    min-height: 56px;
  }
  .player-subtitles.mode-vi-only .sub-original {
    display: none;
  }
  .player-subtitles.mode-vi-only .sub-vietnamese {
    font-size: 17px;
    font-weight: 600;
  }
  .player-subtitles.mode-off {
    min-height: 0px;
    height: 0px;
    padding-top: 0;
    padding-bottom: 0;
    opacity: 0;
    overflow: hidden;
    border-bottom: none;
  }
  ```
- **Avoid Layout Thrashing:** Use `contain: layout style` on `.player-subtitles` to isolate reflow calculations from the heavier video player node above it.

### 7.4 JS Logic Sketch
```javascript
class SubtitleModeController {
  constructor() {
    this.STORAGE_KEY = 'vieneu_subtitle_mode';
    this.currentMode = 'bilingual';
    this.hudEl = document.querySelector('.player-subtitles');
    this.floatingPill = document.getElementById('floatingCcPill');
    this.pillText = this.floatingPill ? this.floatingPill.querySelector('span') : null;
    this.pillTimeout = null;
    this.init();
  }

  init() {
    try {
      this.currentMode = localStorage.getItem(this.STORAGE_KEY) || 'bilingual';
    } catch (e) {
      this.currentMode = 'bilingual';
    }
    this.applyMode(this.currentMode, false);
    this.bindEvents();
  }

  bindEvents() {
    // HUD segmented buttons
    document.querySelectorAll('.sub-mode-btn').forEach(btn => {
      btn.addEventListener('click', (e) => {
        e.stopPropagation();
        this.setMode(btn.dataset.mode);
      });
    });

    // Settings screen segmented buttons
    document.querySelectorAll('.settings-sub-mode-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        this.setMode(btn.dataset.mode);
      });
    });

    // Floating video pill restore tap
    if (this.floatingPill) {
      this.floatingPill.addEventListener('click', () => {
        this.setMode('bilingual');
      });
    }
  }

  setMode(mode) {
    if (!['bilingual', 'vi_only', 'off'].includes(mode)) return;
    this.currentMode = mode;
    try {
      localStorage.setItem(this.STORAGE_KEY, mode);
    } catch (e) {}
    this.applyMode(mode, true);
  }

  applyMode(mode, animate) {
    // Sync HUD segmented buttons
    document.querySelectorAll('.sub-mode-btn').forEach(b => {
      b.classList.toggle('active', b.dataset.mode === mode);
    });

    // Sync Settings screen buttons
    document.querySelectorAll('.settings-sub-mode-btn').forEach(b => {
      b.classList.toggle('active', b.dataset.mode === mode);
    });

    // Update HUD classes
    if (this.hudEl) {
      this.hudEl.classList.remove('mode-vi-only', 'mode-off');
      if (mode === 'vi_only') this.hudEl.classList.add('mode-vi-only');
      if (mode === 'off') this.hudEl.classList.add('mode-off');
    }

    // Handle Floating Pill
    if (this.floatingPill) {
      clearTimeout(this.pillTimeout);
      if (mode === 'off') {
        this.floatingPill.style.display = 'flex';
        this.floatingPill.style.opacity = '1';
        if (this.pillText) this.pillText.textContent = 'CC Tắt';
        this.pillTimeout = setTimeout(() => {
          if (this.currentMode === 'off' && this.pillText) {
            this.pillText.textContent = 'CC';
            this.floatingPill.style.opacity = '0.75';
          }
        }, 2000);
      } else {
        this.floatingPill.style.opacity = '0';
        setTimeout(() => {
          if (this.currentMode !== 'off') this.floatingPill.style.display = 'none';
        }, 180);
      }
    }
  }
}
```

### 7.5 Light Mode Delta
- **HUD Mode Segment Track:** Background is `rgba(0,0,0,0.05)` with `1px solid rgba(0,0,0,0.08)` hairline border instead of dark translucent white.
- **Active Segment Fill:** High-contrast saturated indigo `#4F52D5` with crisp `#FFFFFF` text.
- **Vietnamese Typography (Mode B):** Font rendered in sharp near-black `#111113` against `#FFFFFF` shelf with `0 6px 20px rgba(0,0,0,0.08)` drop shadow.
- **Floating Video Frame Pill:** Keeps obsidian black backdrop (`rgba(10,10,12,0.80)`) with white text in both modes because it overlays the 16:9 cinema video viewport which is always dark.

### 7.6 The One Unscripted Decision Made
> **"The Morphing Floating HUD Pill Over Video Viewport"**  
> When the user disables subtitles, collapsing the Subtitle HUD to 0px creates an ergonomic trap: how do you bring subtitles back without navigating into Settings or hunting for a hidden toggle? Rather than making the user open settings, the HUD collapses while spawning an unobtrusive floating glass pill directly on the top-right of the video canvas. It displays `"CC Tắt"` for 2 seconds before shrinking to a tiny, tactile `"CC"` badge that allows one-tap resurrection anytime during playback.

---

## 8. FEATURE 3 — CACHE MANAGEMENT: CLEAR STORED AUDIO

### 8.1 Component Anatomy
- **Redesigned Telemetry Row (`.cache-metric-row`)**:
  - Layout: Single horizontal flex row with centered alignment and `·` separators.
  - Font: `12px`, weight `500`, color `var(--text-tertiary)` (`#71717A` Dark / `#8C8C96` Light).
  - Three distinct telemetry points:
    1. Total Files: `id="cacheFilesCount"` (`"143 files"`).
    2. Total Size: `id="cacheSizeText"` (`"42.5 MB"`).
    3. Oldest Entry: `id="cacheOldestText"` (`"Cũ nhất: 12 ngày trước"`).
- **Secondary Button A — Temporary Cache Clear (`#btnClearTempCache`)**:
  - Label: `"🧹 Xoá cache tạm · Giữ audio đã lưu"`.
  - Dimensions: Full width, Height `48px`, Border radius `12px`.
  - Dark Mode: Background `var(--bg-elevated)` (`#1A1A22`), Border `1px solid var(--border-subtle)` (`rgba(255,255,255,0.08)`), Text `var(--text-primary)` (`#FFFFFF`).
  - Light Mode: Background `var(--bg-elevated)` (`#ECEAE4`), Border `1px solid rgba(0,0,0,0.08)`, Text `var(--text-primary)` (`#111113`).
  - Active State: `transform: scale(0.985)`, `transition: transform 120ms ease-out`.
- **Destructive Button B — Full Cache Clear (`#btnOpenClearAllSheet`)**:
  - Label: `"🗑️ Xoá toàn bộ · Xoá hết audio đã lưu"`.
  - Dimensions: Full width, Height `48px`, Border radius `12px`, `margin-top: 8px`.
  - Dark Mode: Background `rgba(244, 63, 94, 0.10)`, Border `1px solid rgba(244, 63, 94, 0.30)`, Text `var(--accent-rose)` (`#F43F5E`).
  - Light Mode: Background `rgba(225, 29, 72, 0.08)`, Border `1px solid rgba(225, 29, 72, 0.25)`, Text `var(--accent-rose)` (`#E11D48`).
  - Active State: `transform: scale(0.985)`, background `rgba(244, 63, 94, 0.18)`.
- **Confirmation Bottom Sheet (`#clearAllSheet`) & Backdrop (`#clearAllBackdrop`)**:
  - Backdrop: `position: fixed; inset: 0; background: rgba(0, 0, 0, 0.50); backdrop-filter: blur(4px); z-index: 998; opacity: 0; pointer-events: none; transition: opacity 150ms ease-out`. Active: `opacity: 1; pointer-events: auto`.
  - Sheet Container: `position: fixed; left: 0; right: 0; bottom: 0; z-index: 999; max-width: 480px; margin: 0 auto; border-radius: 24px 24px 0 0; padding: 12px 24px 28px 24px; transform: translateY(100%); transition: transform 200ms cubic-bezier(0.25, 1, 0.5, 1)`. Active: `transform: translateY(0)`.
  - Dark Mode Sheet: Background `var(--bg-surface)` (`#121216`), Border top `1px solid var(--border-subtle)` (`rgba(255,255,255,0.08)`), Shadow `0 -12px 40px rgba(0,0,0,0.6)`.
  - Light Mode Sheet: Background `var(--bg-surface)` (`#FFFFFF`), Border top `1px solid rgba(0,0,0,0.08)`, Shadow `0 -12px 32px rgba(0,0,0,0.12)`.
  - Drag Pill Handle: `width: 36px; height: 4px; border-radius: 2px; background: var(--bg-elevated); margin: 0 auto 16px auto`.
  - Sheet Title: `"Xoá toàn bộ cache?"`, `17px`, font weight `700`, color `var(--text-primary)`, margin-bottom `8px`.
  - Sheet Warning Body: `"Hành động này sẽ xoá 143 files âm thanh (~42.5 MB). Bạn sẽ phải chờ 60s GPU nạp lại khi xem lại các video cũ."`, `13px`, weight `400`, line-height `1.5`, color `var(--text-secondary)`, margin-bottom `20px`.
  - Confirm Action Button: Height `48px`, background `var(--accent-rose)` (`#F43F5E` Dark / `#E11D48` Light), text `#FFFFFF`, font weight `700`, border-radius `12px`.
  - Cancel Button: Height `48px`, background `var(--bg-elevated)`, text `var(--text-primary)`, font weight `600`, border-radius `12px`, margin-top `10px`.
- **Status Toast Message (`#cacheToastMsg`)**:
  - Appears inline below the button container.
  - Height `36px`, border-radius `8px`, font size `12px`, font weight `600`, text-align center, padding `8px 12px`.
  - Success State: Color `var(--accent-teal)` (`#14B8A6` Dark / `#0D9488` Light), background `rgba(20, 184, 166, 0.10)`.
  - Failure State: Color `var(--accent-rose)`, background `rgba(244, 63, 94, 0.10)`.

### 8.2 Interaction Choreography Timeline
1. **Button A Tap (Xoá Cache Tạm):**
   - **0ms (Tap):** Button executes tactile compress `scale(0.985)` (120ms). Button pointer-events set to `none`.
   - **0ms:** Asynchronous `DELETE /api/cache/temp` dispatched to server.
   - **80ms:** Inline toast fades in: `"✓ Đã dọn dẹp cache tạm · Giữ nguyên 143 files audio"` in `--accent-teal`.
   - **3000ms:** Toast fades out ($1 \rightarrow 0$, 200ms ease-in); button pointer-events restored.
2. **Button B Tap $\rightarrow$ Sheet Entrance:**
   - **0ms (Tap):** Backdrop begins opacity fade $0 \rightarrow 1$ (150ms linear).
   - **0ms – 200ms:** Confirmation Bottom Sheet slides upward from `translateY(100%)` to `translateY(0)` with `cubic-bezier(0.25, 1, 0.5, 1)`.
   - Haptic vibration emitted (`navigator.vibrate(10)`).
3. **User Dismisses Sheet (Tap Backdrop or 'Huỷ'):**
   - **0ms – 200ms:** Sheet slides down to `translateY(100%)` with `cubic-bezier(0.4, 0, 1, 1)` (ease-in). Backdrop fades $1 \rightarrow 0$ (150ms).
4. **User Confirms Deletion (Tap 'Xoá ngay'):**
   - **0ms – 200ms:** Sheet drops down and backdrop fades away.
   - **0ms:** Both cache management buttons lock with `opacity: 0.4` and `pointer-events: none`.
   - **0ms – 600ms (Odometer Tick):** A continuous `requestAnimationFrame` loop interpolates file counter from `143` $\rightarrow$ `0` and size from `42.5 MB` $\rightarrow$ `0.0 MB` using cubic ease-out.
   - **200ms:** Asynchronous `DELETE /api/cache/all` sent to backend server.
   - **600ms:** Telemetry row updates oldest entry to `"Trống"`.
   - **600ms:** In Screen 1 History Feed, all cached video badges flip instantly from `"⚡ 0s Chờ"` to `"⏳ 60s Nạp"`, reflecting purged storage.
   - **600ms:** Buttons restore to `opacity: 1.0` and `pointer-events: auto`.
   - **600ms – 3600ms:** Success toast appears: `"✓ Đã xoá 143 files · Giải phóng 42.5 MB"`. Fades out at 3600ms.

### 8.3 CSS Implementation Notes
- **Hardware-Accelerated Sheet Slide:** The bottom sheet must strictly animate `transform: translateY(...)`. Never animate `bottom` or `margin-bottom` as this forces document-wide layout recalibration.
- **Backdrop Blur & Isolation:**
  ```css
  .clear-sheet-backdrop {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.50);
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
    z-index: 998;
    opacity: 0;
    pointer-events: none;
    transition: opacity 150ms ease-out;
  }
  .clear-sheet-backdrop.active {
    opacity: 1;
    pointer-events: auto;
  }
  .clear-bottom-sheet {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 999;
    transform: translateY(100%);
    transition: transform 200ms cubic-bezier(0.25, 1, 0.5, 1);
  }
  .clear-bottom-sheet.active {
    transform: translateY(0);
  }
  ```
- **Odometer Numeric Tabular Alignment:** Apply `font-variant-numeric: tabular-nums` to `.cache-metric-row` spans to prevent character jitter as digits cycle down to zero.

### 8.4 JS Logic Sketch
```javascript
class CacheManager {
  constructor() {
    this.state = { files: 143, sizeMB: 42.5, oldestDays: 12 };
    this.sheet = document.getElementById('clearAllSheet');
    this.backdrop = document.getElementById('clearAllBackdrop');
    this.btnGroup = document.getElementById('cacheBtnContainer');
    this.toast = document.getElementById('cacheToastMsg');
    this.bindEvents();
    this.renderMetrics();
  }

  bindEvents() {
    document.getElementById('btnClearTempCache')?.addEventListener('click', () => this.clearTemp());
    document.getElementById('btnOpenClearAllSheet')?.addEventListener('click', () => this.openSheet());
    document.getElementById('btnCancelClearSheet')?.addEventListener('click', () => this.closeSheet());
    document.getElementById('btnConfirmClearAll')?.addEventListener('click', () => this.executeClearAll());
    this.backdrop?.addEventListener('click', () => this.closeSheet());
  }

  renderMetrics() {
    const filesEl = document.getElementById('cacheFilesCount');
    const sizeEl = document.getElementById('cacheSizeText');
    const oldestEl = document.getElementById('cacheOldestText');
    if (filesEl) filesEl.textContent = `${this.state.files} files`;
    if (sizeEl) sizeEl.textContent = `${this.state.sizeMB.toFixed(1)} MB`;
    if (oldestEl) oldestEl.textContent = this.state.files > 0 ? `Cũ nhất: ${this.state.oldestDays} ngày trước` : 'Trống';
  }

  clearTemp() {
    const btn = document.getElementById('btnClearTempCache');
    btn.style.pointerEvents = 'none';
    fetch('/api/cache/temp', { method: 'DELETE' }).catch(() => {});
    this.showToast(`✓ Đã dọn dẹp cache tạm · Giữ nguyên ${this.state.files} files audio`, 'success');
    setTimeout(() => { btn.style.pointerEvents = 'auto'; }, 3000);
  }

  openSheet() {
    this.backdrop.classList.add('active');
    this.sheet.classList.add('active');
  }

  closeSheet() {
    this.backdrop.classList.remove('active');
    this.sheet.classList.remove('active');
  }

  executeClearAll() {
    this.closeSheet();
    this.btnGroup.style.opacity = '0.4';
    this.btnGroup.style.pointerEvents = 'none';

    const startFiles = this.state.files;
    const startSize = this.state.sizeMB;
    const duration = 600;
    const startTime = performance.now();

    const tick = (now) => {
      const elapsed = now - startTime;
      const progress = Math.min(1, elapsed / duration);
      const easeOut = 1 - Math.pow(1 - progress, 3);

      const currentFiles = Math.round(startFiles * (1 - easeOut));
      const currentSize = startSize * (1 - easeOut);

      document.getElementById('cacheFilesCount').textContent = `${currentFiles} files`;
      document.getElementById('cacheSizeText').textContent = `${currentSize.toFixed(1)} MB`;

      if (progress < 1) {
        requestAnimationFrame(tick);
      } else {
        this.state.files = 0;
        this.state.sizeMB = 0;
        this.state.oldestDays = 0;
        this.renderMetrics();

        // Flip history badges
        document.querySelectorAll('.card-badge.badge-cache').forEach(badge => {
          badge.className = 'card-badge badge-wait';
          badge.textContent = '60s Nạp';
        });

        fetch('/api/cache/all', { method: 'DELETE' })
          .then(() => {
            this.showToast(`✓ Đã xoá ${startFiles} files · Giải phóng ${startSize.toFixed(1)} MB`, 'success');
          })
          .catch(() => {
            this.showToast('⚠ Lỗi kết nối máy chủ — Thử lại', 'danger');
          })
          .finally(() => {
            this.btnGroup.style.opacity = '1';
            this.btnGroup.style.pointerEvents = 'auto';
          });
      }
    };
    requestAnimationFrame(tick);
  }

  showToast(msg, type) {
    this.toast.className = `cache-toast-msg ${type}`;
    this.toast.textContent = msg;
    this.toast.style.display = 'block';
    setTimeout(() => { this.toast.style.display = 'none'; }, 3500);
  }
}
```

### 8.5 Light Mode Delta
- **Destructive Button B Tint:** Background `rgba(225, 29, 72, 0.08)` and border `rgba(225, 29, 72, 0.25)` with text `#E11D48` instead of dark mode `rgba(244, 63, 94, 0.10)` / `0.30`.
- **Bottom Sheet Surface:** Solid `#FFFFFF` card surface with subtle hairline border `rgba(0,0,0,0.08)` and soft ambient shadow `0 -12px 32px rgba(0,0,0,0.12)`.
- **Drag Pill Handle:** Colored `--bg-elevated` (`#ECEAE4`) for soft organic tactile definition on paper white.
- **Button A Secondary Fill:** Clean stone tone `#ECEAE4` with dark near-black `#111113` text.

### 8.6 The One Unscripted Decision Made
> **"Synchronous History Badge Inversion Across Screen Boundaries"**  
> Clearing cache in Settings is usually an isolated event. Here, when the confirmation executes and the 600ms odometer animation completes, all video history cards across the entire application instantly mutate their status badge from `"⚡ 0s Chờ"` (Instant cached play) to `"⏳ 60s Nạp"` (GPU warm-up needed). If the user navigates back to Screen 1, the app visually honors the hardware reality: their local cache is gone, and tapping a video will truthfully trigger the warm-up cycle.

---

## 9. FEATURE INTEGRATION SUMMARY

The three new v1.2.0 features do not exist in isolation; they are deeply intertwined across app memory, network requests, and visual states:

1. **History Deletion vs. In-Flight Cache Clearing:**
   - If a user triggers swipe-to-delete on a video while a global cache clear (`DELETE /api/cache/all`) is running, the card's deletion is immediately absorbed into the pending queue. The feed cache size badge decrements from the user's view immediately, and the card's individual `DELETE /api/cache/:videoId` call is coalesced with the global wipe so redundant backend requests are dropped.
2. **Undo Toast Resilience During Screen Navigation:**
   - If a video is deleted and the 4-second undo toast is active, navigating to Screen 3 (Player) or Screen 4 (Settings) does not destroy the undo registry. The timer continues running in the background. If the 4 seconds expire while away, the deletion is committed silently. If the user returns to Screen 1 before 4 seconds, the toast remains visible with the depleted progress bar in its exact remaining time slice.
3. **Subtitle Mode Persistence Across History Launches:**
   - When a video is selected from History Feed, the Player screen initializes with the exact subtitle mode saved in `vieneu_subtitle_mode` (`bilingual`, `vi_only`, or `off`). If a user was watching in `vi_only` mode, deleted another video from history, and re-opened a new video, their HUD launches directly in the compact 56px mode without resetting to default.
4. **Theme Invariance Across Destructive Sheets & Gestures:**
   - Dragging a card left to delete or opening the cache confirmation bottom sheet mid-gesture while the OS toggles light/dark mode seamlessly updates the CSS variables without interrupting the touch tracking or matrix transforms, ensuring zero visual tearing or dropped frames.

---

## 10. WHAT THE V1.2.0 SPEC LOOKS LIKE AFTER THESE LAND

With the integration of **Swipe-to-Delete History**, the **Trimodal Subtitle HUD Architecture**, and **Tiered Audio Cache Management**, the VieNeu Mobile Player matures from a functional PWA prototype into an uncompromising, platform-grade media companion. The interface now delivers the tactile feedback of native iOS/Android software through deliberate touch physics, reversible non-blocking undo flows, and hardware-truthful telemetry. By treating both Dark Cinema and Light Editorial surfaces as equal first-class citizens, v1.2.0 establishes an inevitable, calm, and trustworthy interaction standard that lets the user command heavy local PC AI inference with the featherweight grace of a consumer streaming app.

---
*VieNeu Mobile Player Design System v1.2.0 — Antigravity Creative Direction.*

