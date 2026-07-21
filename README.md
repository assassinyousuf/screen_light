# 💡 Screen Light — Portable & Adjustable Reading Light

Turn any monitor or display into a highly customizable, flicker-free, and adaptive ambient reading light. **Screen Light** is an offline-first, single-file web application built with zero external dependencies.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

---

## 🌟 Key Features

*   **⚡ Zero Dependencies**: Self-contained single `index.html` file. Works completely offline.
*   **🎨 Color Temperature Engine**: True blackbody radiation simulation (Tanner Helland's algorithm) ranging from a warm candle glow (**1800K**) to clear blue sky (**10000K**).
*   **⚙️ Advanced Fine-Tuning**: Adjust brightness, saturation, green-magenta tint, white balance, contrast, and gamma correction.
*   **🌅 Smart Circadian Mode**: Automatically transitions the temperature and brightness throughout the day based on your system clock to match your circadian rhythm.
*   **🌬️ Ambient Animations**: Organic breathing pulses, and smooth timer-based sunrise/sunset simulation sequences.
*   **🕒 Utilities Overlay**: Dynamic real-time clock overlay (12h/24h) and sleep timer with gradual fade-to-black auto-dimming.
*   **🛡️ Screen Wake Lock**: Keeps your screen awake during long reading sessions (requires browser compatibility).
*   **📂 Favorites & Profiles**: Save your customized configurations, and easily import/export settings using standard JSON schemas.
*   **⌨️ Keyboard Shortcuts**: Fully navigable through keyboard bindings with an interactive help modal.

---

## ⚙️ How It Works (The Color Pipeline)

Screen Light calculates the screen background color in a sequence of color adjustments to ensure optimal color precision:

```mermaid
graph TD
    A[Start: Base Temp/Color] --> B[White Balance & Warmth Adjustment]
    B --> C[Green-Magenta Tint Shifting]
    C --> D[Luminance-based Saturation]
    D --> E[Mid-gray Contrast Scaling]
    E --> F[Gamma Power-law Correction]
    F --> G[Master Brightness & Ambient Scale]
    G --> H[Clamping [0, 255] -> Final Background]
```

1.  **Base Color**: Computes initial RGB using Tanner Helland's blackbody approximation or user color picker.
2.  **White Balance**: Adjusts R and B channel multipliers based on fine warmth values.
3.  **Tint**: Shifts green channel while balancing red and blue offsets.
4.  **Saturation**: Linearly interpolates channels towards luminance values.
5.  **Contrast**: Scales values around a mid-gray point (127.5).
6.  **Gamma**: Applies power-law scaling to maintain smooth gradient transitions.
7.  **Brightness**: Scales the final values and merges any ongoing ambient animation multiplier.

---

## 📅 Smart Circadian Schedule

When **Smart Circadian Mode** is active, Screen Light shifts color settings automatically based on the time of day:

| Time Slot | Period | Target Kelvin | Master Brightness |
| :--- | :--- | :---: | :---: |
| 🌅 **6 AM – 9 AM** | Morning Boost | `5000K` | `75%` |
| ☀️ **9 AM – 5 PM** | Daylight Concentration | `6500K` | `90%` |
| 🌇 **5 PM – 8 PM** | Evening Winddown | `4000K` | `65%` |
| 🌙 **8 PM – 10 PM** | Night Reading | `3000K` | `50%` |
| 🌌 **After 10 PM** | Late Night Glow | `2200K` | `25%` |

*Note: Manually adjusting sliders or switching custom colors instantly disables Circadian Mode to avoid conflicting states.*

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
| :---: | :--- |
| `Space` | Toggle Control Panel visibility (show/hide UI) |
| `F` | Toggle true browser fullscreen mode (Double-click screen also works) |
| `Esc` | Exit fullscreen |
| `▲` / `▼` | Brightness Up / Down (steps of 5%) |
| `◀` / `▶` | Color Temperature Down / Up (steps of 100K) |
| `P` | Cycle through predefined system reading modes |
| `T` | Open Timer drawer |
| `C` | Toggle clock overlay |
| `H` | Toggle Keyboard Shortcuts help modal |
| `R` | Reset all configuration parameters to defaults |

---

## 🚀 Getting Started

1.  Clone this repository:
    ```bash
    git clone https://github.com/assassinyousuf/screen_light.git
    ```
2.  Open `index.html` in any modern web browser (Chrome, Firefox, Safari, Edge).
3.  Add the page to your bookmarks or home screen. Since it has no external network assets, it runs completely offline.

---

## 📄 License

This project is open-source software licensed under the [MIT License](LICENSE).
