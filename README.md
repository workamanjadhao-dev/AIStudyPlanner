# 📚 AI Study Planner - Android App

A fully functional Android study planner app powered by **Claude AI (Anthropic)**.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🤖 **AI Chat (Claude)** | Chat with Claude AI for study help, motivation, explanations |
| 📅 **AI Study Schedule** | Generate personalized weekly plans with Claude |
| 📚 **Subject Management** | Add, track & manage your subjects with color coding |
| 📊 **Progress Dashboard** | Charts showing weekly study hours & subject breakdown |
| ⏱️ **Pomodoro Timer** | Customizable focus/break timer with 25/45/60 min presets |
| 🎵 **Lofi Music Player** | Stream ambient music (Lofi, Chillhop, Jazz, Ambient) |
| 📝 **Task Manager** | Create & track study tasks with priorities |
| 🔥 **Streak Tracking** | Daily study streak & completion rate stats |
| 🔔 **Notifications** | Background timer notifications |

---

## 🚀 Setup Instructions

### 1. Prerequisites
- Android Studio **Hedgehog 2023.1.1** or newer
- Android SDK **API 24+** (Android 7.0+)
- **Claude API key** from [console.anthropic.com](https://console.anthropic.com)

### 2. Clone / Open Project
```bash
# Open in Android Studio: File > Open > Select AIStudyPlanner folder
```

### 3. Add Your Claude API Key

**Option A: Via the app (Recommended)**
1. Launch the app
2. Tap **"AI Chat"** tab
3. Send any message → it will prompt for your API key
4. Enter your key from [console.anthropic.com](https://console.anthropic.com)

**Option B: Via gradle.properties**
```properties
# Add to gradle.properties
CLAUDE_API_KEY=your-api-key-here
```

### 4. Add JitPack to settings.gradle
```gradle
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' }  // ← Required for MPAndroidChart
    }
}
```

### 5. Build & Run
```
Build > Make Project (Ctrl+F9)
Run > Run 'app' (Shift+F10)
```

---

## 📁 Project Structure

```
app/src/main/
├── java/com/studyplanner/
│   ├── ui/
│   │   ├── MainActivity.kt          # Main + Splash Activity
│   │   ├── home/HomeFragment.kt     # Dashboard
│   │   ├── ai/AIChatFragment.kt     # Claude AI Chat
│   │   ├── subjects/SubjectsFragment.kt
│   │   ├── schedule/ScheduleFragment.kt
│   │   ├── progress/ProgressFragment.kt
│   │   ├── timer/TimerFragment.kt   # Pomodoro Timer
│   │   └── music/MusicFragment.kt   # Lofi Streaming
│   ├── data/
│   │   ├── api/ClaudeApi.kt        # Anthropic API client
│   │   ├── database/AppDatabase.kt  # Room DB + DAOs
│   │   ├── model/Models.kt          # Data classes
│   │   └── repository/StudyRepository.kt
│   └── utils/
│       ├── PrefsHelper.kt           # SharedPreferences
│       └── AlarmReceiver.kt
└── res/
    ├── layout/     # All XML layouts
    ├── navigation/ # nav_graph.xml
    ├── menu/       # bottom_nav_menu.xml
    ├── values/     # colors, strings, themes
    └── drawable/   # icons
```

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| **Room** | Local SQLite database |
| **Retrofit + OkHttp** | Claude API HTTP calls |
| **Navigation Component** | Fragment navigation |
| **ViewModel + LiveData** | MVVM architecture |
| **MPAndroidChart** | Progress charts |
| **Material 3** | UI components |
| **Coroutines** | Async operations |
| **WorkManager** | Background tasks |

---

## 📱 App Navigation

```
Bottom Navigation Bar:
🏠 Home → Dashboard with stats, quick actions, tasks
📚 Subjects → Grid of subject cards with progress
📅 Schedule → Study sessions list + AI plan generator
📊 Progress → Charts + AI analysis
🤖 AI Chat → Claude AI conversation
⏱️ Timer → Pomodoro with customizable durations
🎵 Music → Lofi streaming radio
```

---

## 🔧 Key Customizations

### Change Timer Defaults
In `TimerFragment.kt`:
```kotlin
private var focusDuration = 25 * 60 * 1000L  // Change 25 to your default
private var breakDuration = 5 * 60 * 1000L   // Change 5 to your default
```

### Add More AI Quick Prompts
In `AIChatFragment.kt`:
```kotlin
private val quickPrompts = listOf(
    "📅 Create my weekly study plan",
    // Add your custom prompts here
)
```

### Change App Theme Colors
In `res/values/colors.xml`:
```xml
<color name="primary">#5C6BC0</color>   <!-- Change to your brand color -->
<color name="accent">#FF7043</color>    <!-- Change accent color -->
```

---

## ⚠️ Permissions Required

```xml
INTERNET            - For Claude API & music streaming
POST_NOTIFICATIONS  - Timer notifications
FOREGROUND_SERVICE  - Background timer
RECEIVE_BOOT_COMPLETED - Restart alarms on reboot
```

---

## 🎵 Music Streams

The app streams from free/public radio stations:
- **Lofi Hip Hop** - ilovemusic.de
- **Chillhop** - fluxfm.de  
- **Ambient/Groovesalad** - SomaFM
- **Jazz** - SomaFM

> Note: Stream availability depends on the station uptime.

---

## 📞 Claude API Usage

The app calls `claude-sonnet-4-6` with:
- **Chat**: General study assistance
- **Study Plan Generation**: Personalized weekly schedules
- **Progress Analysis**: AI insights on your study habits
- **Study Techniques**: Subject-specific recommendations

Cost is pay-per-use via your Anthropic API key.

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| AI not responding | Check API key in AI Chat section |
| Music not playing | Check internet connection; try different stream |
| Build fails | Ensure JitPack repo is in settings.gradle |
| Room crash | Clear app data and reinstall |

---

*Built with ❤️ using Claude AI + Android Jetpack*
