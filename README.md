# 🦀 Clawdroid

**NanoClaw Flutter Client** — A mobile chat client for NanoClaw with real-time WebSocket communication.

## 📱 What It Is

Clawdroid is a Flutter-based Android app that connects to NanoClaw (a lightweight, container-based AI assistant framework) via WebSocket. It provides a clean, Material 3 chat interface for interacting with your AI assistant.

## ✨ Features

- 🌐 **Real-time WebSocket** — Connects to NanoClaw on `ws://localhost:8765`
- 🎨 **Material 3 Design** — Modern dark theme with smooth animations
- 🔄 **Auto-reconnect** — Automatically reconnects on connection loss
- 💬 **Message History** — Full conversation history with timestamps
- 📡 **Connection Status** — Live indicator (green = connected, red = disconnected)
- 📦 **Release APK** — Pre-built APK included for quick testing

## 🏗️ Architecture

```
┌─────────────────┐         WebSocket          ┌─────────────────┐
│   Clawdroid     │ ◄──────────────────────►   │    NanoClaw     │
│  (Flutter App)  │      Port 8765             │  (Node.js +     │
│                 │                            │   Containers)   │
└─────────────────┘                            └─────────────────┘
```

### Message Format

**Outbound (App → NanoClaw):**
```json
{
  "type": "message",
  "chatJid": "flutter:main",
  "senderName": "Flutter User",
  "content": "Hello!",
  "timestamp": 1234567890
}
```

**Inbound (NanoClaw → App):**
```json
{
  "type": "response",
  "chatJid": "flutter:main",
  "content": "Hi! How can I help?",
  "timestamp": 1234567890
}
```

## 🚀 Quick Start

### Option 1: Use Pre-built APK

1. Ensure NanoClaw is running with Flutter channel enabled
2. Install `clawdroid.apk` on your Android device
3. Open the app and start chatting!

### Option 2: Build from Source

```bash
cd flutter_client
flutter pub get
flutter build apk --release
```

## 📋 Prerequisites

### For Running the App
- **NanoClaw** running with Flutter WebSocket channel
- **WebSocket server** listening on port 8765 (default)

### For Building
- Flutter SDK (3.0+)
- Android SDK / Android Studio
- NanoClaw repository (for server-side changes)

## 🔧 Configuration

### Change Server Address

Edit `lib/main.dart`:
```dart
_channel = WebSocketChannel.connect(
  Uri.parse('ws://YOUR_SERVER_IP:8765'),
);
```

### Change Chat ID

Edit `lib/main.dart`:
```dart
String _chatId = 'your_custom_id';
```

## 📁 Project Structure

```
clawdroid/
├── flutter_client/       # Flutter app source
│   ├── lib/
│   │   └── main.dart     # Main app code
│   ├── android/          # Android-specific config
│   ├── pubspec.yaml      # Dependencies
│   └── README.md         # Flutter app docs
├── clawdroid.apk         # Pre-built release APK
├── .gitignore
└── README.md             # This file
```

## 🔗 Related Projects

- **NanoClaw**: https://github.com/qwibitai/nanoclaw
- **OpenClaw**: https://github.com/openclaw/openclaw

## 📝 License

MIT — Build something awesome!

## 🙏 Credits

Built with:
- Flutter & Dart
- web_socket_channel
- NanoClaw framework

---

**Made with 🦀 for the AI assistant ecosystem**
