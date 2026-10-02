#  NFC & Motion Phone Guard

> **Cross-Platform Anti-Theft Guard for Dorms, Cafes, and Travel**  
> Developed by **Bereketab Mihiretab** • Version 2.0

An anti-theft progressive web app (PWA) designed to protect your smartphone when resting on a desk, nightstand, or bedside table. If an intruder or thief lifts or moves your phone, a loud multi-tone siren sounds, screen lockdown engages, and the phone cannot be silenced without your **4-digit PIN** or **Biometrics (Face ID, Touch ID, or Android Fingerprint)**.

---

##  Key Features

-  **Universal Cross-Platform Support (iPhone & Android)**:
  - **Universal Motion Guard (iPhone & Android)**: Uses the device's accelerometer and gyroscope with baseline gravity calibration to instantly detect lift, tilt, and shift.
  - **NFC Tag Guard (Android Chrome)**: Pairs with any physical NFC card (dorm keycard, transit card, hotel card, or NFC sticker).
  - **Dual Guard (NFC + Motion)**: Combines NFC tag proximity with motion sensing for double protection.
-  **Biometric Disarming (WebAuthn)**:
  - Disarm the alarm in a fraction of a second using native **Face ID / Touch ID** (iOS Safari) or **Fingerprint / Face Unlock** (Android Chrome).
  - Emergency 4-digit PIN fallback with an on-screen keypad and anti-brute-force rate limiting.
-  **Anti-Theft Lockdown**:
  - **Unsilenceable Siren**: High-gain synthesized dual-tone siren (sawtooth + square wave) that recovers automatically if interrupted.
  - **Navigation Trapping**: Traps the Android back button (`popstate`) and warns on page leave (`beforeunload`).
  - **Screen Wake Lock**: Prevents the screen from turning off or sleeping while armed or alarming.
  - **Flashing Strobe UI**: Fullscreen high-visibility emergency strobe clearly alerting anyone nearby that the device is stolen.
-  **Complete PWA & Offline Support**:
  - Ready for **Add to Home Screen** on both Chrome (Android/Desktop) and Safari (iOS).
  - High-resolution app icons (`192x192`, `512x512`, `apple-touch-icon.png`, vector SVG, and favicons).
  - Works 100% offline via Service Worker (`sw.js`).

---

##  How It Works

### For iPhone Users (iOS Safari)
1. Open the app in **Safari** on iOS.
2. Tap the **Share** button (`⎙` / square with arrow) and tap **Add to Home Screen**.
3. Open the app from your home screen.
4. Set your **4-digit PIN** and tap **Enable Biometrics** to link Face ID / Touch ID.
5. Tap **Arm Alarm** (grant motion permission when prompted).
6. A 5-second countdown allows you to place the phone flat on your desk or nightstand.
7. Any attempt to lift or move the phone immediately sets off the siren!

### For Android Users (Chrome)
1. Open the app in **Chrome** on Android.
2. Tap the three dots menu  and select **Install app** or **Add to Home screen**.
3. Choose your preferred guard mode:
   - **Motion Guard**: Protects phone using movement sensors anywhere.
   - **NFC Guard**: Place an NFC keycard against the phone to lock.
   - **Dual Guard**: Requires both NFC contact and no movement.
4. Set your PIN and tap **Arm Alarm**.

---

##  Security & Disarm Methods

| Method | Description |
| :--- | :--- |
| **Face ID / Touch ID / Fingerprint** | Hardware-level biometric authentication via `WebAuthn` (`PublicKeyCredential`). |
| **4-Digit PIN** | Secure custom on-screen keypad with dot indicators and 10-second penalty lockout after 3 failed attempts. |

---

##  Repository Structure

```
nfc-guard/
├── index.html           # Main PWA application, UI, sensors, WebAuthn & audio synthesizer
├── manifest.json        # Web App Manifest with icons and standalone display mode
├── sw.js                # Service Worker for offline caching and assets
├── icon.svg             # Vector shield and padlock logo
├── icon-192.png         # 192x192 PWA install icon (maskable)
├── icon-512.png         # 512x512 High-res splash icon (maskable)
├── apple-touch-icon.png # 180x180 iOS home screen icon
├── favicon-32x32.png    # 32x32 Favicon
├── favicon.ico          # Browser favicon
└── README.md            # Documentation and user guide
```

---

##  Local Testing & Deployment

To run and test locally:
```bash
# Using Python
python -m http.server 8000

# Open in browser:
# http://localhost:8000
```
> **Note for Biometrics & NFC**: WebAuthn and Web NFC require a secure context (`https://` or `localhost`). When deploying to **GitHub Pages**, both work automatically over HTTPS!
