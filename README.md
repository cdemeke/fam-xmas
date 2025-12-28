# Demeke Family Xmas Games 2025

A festive Christmas game tracker for family game nights. Track scores, display leaderboards on TV, and crown the ultimate champion!

## Two Versions Available

| Version | Best For | Sync |
|---------|----------|------|
| **Web App** | Quick setup, browser-based | localStorage (same device) |
| **Android App** | TV + Phone combo, real-time sync | Firebase Realtime Database |

---

## Android App (Recommended for TV)

The Android app provides the best TV experience with a dedicated phone controller.

### Features

- **TV Leaderboard** - Beautiful full-screen display with snowfall animation
- **Phone Controller** - Manage players, record games, trigger effects
- **Real-time Sync** - Firebase keeps TV and phone in sync instantly
- **Celebration Effects** - Confetti animations on game completion
- **D-pad Navigation** - Full TV remote support

### Prerequisites

- Android Studio (Arctic Fox or newer)
- Android SDK 24+ (Android 7.0)
- Firebase account (free tier works fine)

### Setup Instructions

#### 1. Clone and Open Project

```bash
git clone https://github.com/cdemeke/fam-xmas.git
cd fam-xmas/android-app
```

Open the `android-app` folder in Android Studio.

#### 2. Setup Firebase

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Create a new project (or use existing)
3. Add an Android app:
   - Package name: `com.demeke.famxmas`
   - Download `google-services.json`
4. Place `google-services.json` in `android-app/app/`
5. Enable **Realtime Database**:
   - Go to Build → Realtime Database
   - Create database in **test mode** (for development)
   - Note your database URL

#### 3. Configure Database Rules (Production)

For production, update your Firebase rules:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

#### 4. Build and Deploy

**For Phone (Admin Controller):**
```bash
# Build debug APK
./gradlew assembleDebug

# Install on connected phone
./gradlew installDebug
```

**For Android TV (Leaderboard Display):**
```bash
# Same APK works on TV - it auto-detects device type
adb -s <TV_DEVICE_ID> install app/build/outputs/apk/debug/app-debug.apk
```

#### 5. Release Build (Optional)

```bash
# Create release keystore (first time only)
keytool -genkey -v -keystore release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias famxmas

# Build release APK
./gradlew assembleRelease

# APK location: app/build/outputs/apk/release/app-release.apk
```

### Deploying to Devices

#### Install on Phone via ADB
```bash
adb devices  # List connected devices
adb install app/build/outputs/apk/debug/app-debug.apk
```

#### Install on Android TV
```bash
# Enable Developer Options on TV: Settings → About → Build number (click 7 times)
# Enable ADB debugging in Developer Options
# Connect via WiFi:
adb connect <TV_IP_ADDRESS>:5555
adb install app/build/outputs/apk/debug/app-debug.apk
```

#### Sideload APK (No ADB)
1. Build the APK
2. Upload to Google Drive or transfer via USB
3. On TV: Use a file manager app (like X-plore) to install

### Google Play Store Deployment

1. Create a [Google Play Developer account](https://play.google.com/console) ($25 one-time fee)
2. Create a new app in Play Console
3. Fill in app details, content rating, etc.
4. Upload your signed release APK or AAB:
   ```bash
   ./gradlew bundleRelease
   # AAB location: app/build/outputs/bundle/release/app-release.aab
   ```
5. Submit for review

### Project Structure

```
android-app/
├── app/
│   ├── src/main/
│   │   ├── java/com/demeke/famxmas/
│   │   │   ├── MainActivity.kt           # Entry point, TV/Phone detection
│   │   │   ├── FamXmasApplication.kt     # Firebase initialization
│   │   │   ├── data/
│   │   │   │   ├── Player.kt             # Data models
│   │   │   │   └── FirebaseRepository.kt # Firebase operations
│   │   │   ├── ui/
│   │   │   │   ├── phone/
│   │   │   │   │   └── PhoneAdminScreen.kt
│   │   │   │   ├── tv/
│   │   │   │   │   └── TvLeaderboardScreen.kt
│   │   │   │   └── theme/
│   │   │   │       ├── Theme.kt
│   │   │   │       └── Type.kt
│   │   │   └── viewmodel/
│   │   │       └── GameViewModel.kt
│   │   ├── res/
│   │   └── AndroidManifest.xml
│   ├── build.gradle.kts
│   └── google-services.json  # YOU ADD THIS
├── build.gradle.kts
└── settings.gradle.kts
```

---

## Web App (Original)

The web version works great for single-device use or when casting from your phone.

**Live Site:** https://cdemeke.github.io/fam-xmas/

### Features

- **Leaderboard** - Real-time rankings with points and win counts
- **Game History** - Log of all games played with timestamps
- **Admin Panel** - PIN-protected (default: `1225`)
- **TV Display Mode** - Dedicated full-screen view for casting
- **Dramatic Reveal** - Suspenseful winner announcement

### Quick Start

1. Open https://cdemeke.github.io/fam-xmas/
2. Tap **Admin** and enter PIN: `1225`
3. Add players and start playing!

### TV Display Setup

1. Open https://cdemeke.github.io/fam-xmas/tv.html on your phone
2. Cast/AirPlay to your TV
3. Open another tab with the main site to manage games
4. TV auto-updates every 1.5 seconds

---

## Scoring System

| Placement | Points |
|-----------|--------|
| 1st Place | 3 points |
| 2nd Place | 2 points |
| 3rd Place | 1 point |

---

## Troubleshooting

### Android App

**Firebase not connecting:**
- Verify `google-services.json` is in `app/` folder
- Check your Firebase database URL matches
- Ensure Realtime Database rules allow read/write

**TV not detected as TV:**
- The app uses `UiModeManager` to detect TV mode
- Ensure your Android TV is running in TV mode (not tablet mode)

**ADB can't find TV:**
- Enable Developer Options on TV
- Enable USB/Network debugging
- Try: `adb kill-server && adb start-server`

### Web App

**Data not syncing between devices:**
- Web app uses localStorage (device-specific)
- For cross-device sync, configure Firebase or use the Android app

**TV display not updating:**
- Ensure both tabs are on the same device
- Check browser localStorage is enabled

---

## Tech Stack

**Android App:**
- Kotlin + Jetpack Compose
- Firebase Realtime Database
- Material3 Design
- Leanback library for TV

**Web App:**
- Pure HTML/CSS/JavaScript
- localStorage
- Web Audio API

---

## License

MIT License - Fork and customize for your own family game nights!

---

Made with love for the Demeke Family Christmas 2025
