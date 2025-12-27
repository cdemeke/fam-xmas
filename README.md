# Demeke Family Xmas Games 2025

A festive Christmas game tracker for family game nights. Track scores, display leaderboards on TV, and crown the ultimate champion!

🎄 **Live Site:** https://cdemeke.github.io/fam-xmas/

## Features

- **Leaderboard** - Real-time rankings with points and win counts
- **Game History** - Log of all games played with timestamps
- **Admin Panel** - PIN-protected (default: `1225`) for managing players and recording results
- **TV Display Mode** - Dedicated full-screen view optimized for TV casting
- **Dramatic Reveal** - Suspenseful winner announcement with sound effects and confetti
- **Festive Design** - Christmas theme with falling emoji animations

## Scoring System

| Placement | Points |
|-----------|--------|
| 🥇 1st Place | 3 points |
| 🥈 2nd Place | 2 points |
| 🥉 3rd Place | 1 point |

## How to Use

### Basic Setup (Single Device)

1. Open https://cdemeke.github.io/fam-xmas/ on your phone
2. Tap **Admin** and enter PIN: `1225`
3. Add all players
4. Record game results as you play
5. View the **Leaderboard** to see rankings

### TV Display Setup

#### Option 1: Cast from Same Phone (Recommended)

1. On your phone, open the TV display: https://cdemeke.github.io/fam-xmas/tv.html
2. Cast/mirror that browser tab to your TV:
   - **iPhone**: Use AirPlay to Apple TV or AirPlay-compatible TV
   - **Android**: Use Chromecast or Smart View
3. Open a new browser tab on the same phone: https://cdemeke.github.io/fam-xmas/
4. Use the Admin panel to manage games
5. The TV display auto-updates every 1.5 seconds!

#### Option 2: Different Devices (Requires Firebase)

To use separate devices (phone for admin, laptop/tablet connected to TV):

1. Create a free Firebase project at https://console.firebase.google.com
2. Create a Realtime Database in "test mode"
3. Add a web app and copy the config
4. Update the `FIREBASE_CONFIG` in both `index.html` and `tv.html`

### Using the Dramatic Reveal

1. Click **TV Mode** from the main page
2. Watch the suspenseful reveal: 3rd → 2nd → 1st place
3. Celebrate with confetti when the winner is announced!
4. Click "Skip to Leaderboard" to see full rankings anytime

## Pages

| Page | URL | Purpose |
|------|-----|---------|
| Main App | `/index.html` | Admin panel, leaderboard, game recording |
| TV Display | `/tv.html` | Clean, auto-updating display for TV |

## Admin Functions

- **Add Players** - Enter names before games begin
- **Record Games** - Select 1st, 2nd, 3rd place winners
- **Change PIN** - Update the admin access code
- **Reset Data** - Clear all players and games (requires confirmation)

## Data Storage

All data is stored in your browser's localStorage. This means:
- ✅ Data persists between sessions
- ✅ No account or login required
- ⚠️ Data is device-specific (unless Firebase is configured)
- ⚠️ Clearing browser data will erase game history

## Tech Stack

- Pure HTML, CSS, JavaScript (no frameworks)
- Google Fonts (Inter, Mountains of Christmas)
- Web Audio API for sound effects
- localStorage for data persistence
- Optional Firebase Realtime Database for cross-device sync

## Local Development

```bash
# Clone the repository
git clone https://github.com/cdemeke/fam-xmas.git
cd fam-xmas

# Open in browser
open index.html
```

## Customization

### Change the Title
Edit the `<h1>` tags in both `index.html` and `tv.html`

### Change the PIN
Default PIN is `1225` (Christmas Day!). Change it in the Admin → Settings panel, or edit the default in the JavaScript.

### Add More Falling Emojis
Find the `emojis` array in the `createSnowflakes()` function and add your favorites!

## License

MIT License - Feel free to fork and customize for your own family game nights!

---

Made with ❤️ for the Demeke Family Christmas 2025
