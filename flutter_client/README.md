# NanoClaw Flutter Client

A Flutter-based chat client for NanoClaw that connects via WebSocket.

## Features

- ✅ Real-time WebSocket communication with NanoClaw
- ✅ Dark mode UI with Material 3 design
- ✅ Auto-reconnect on connection loss
- ✅ Message history with timestamps
- ✅ Connection status indicator

## Setup

### Prerequisites

- Flutter SDK installed
- NanoClaw running with Flutter channel enabled

### Install Dependencies

```bash
flutter pub get
```

### Run the App

```bash
flutter run
```

## Architecture

### Connection Details

- **WebSocket URL:** `ws://localhost:8765`
- **Protocol:** Custom JSON message format

### Message Format

**Outbound (Flutter → NanoClaw):**
```json
{
  "type": "message",
  "chatJid": "flutter:your_user_id",
  "senderName": "Your Name",
  "content": "Hello, NanoClaw!",
  "timestamp": 1234567890
}
```

**Inbound (NanoClaw → Flutter):**
```json
{
  "type": "response",
  "chatJid": "flutter:your_user_id",
  "content": "Hello! How can I help?",
  "timestamp": 1234567890
}
```

### Chat ID Format

- Format: `flutter:{user_id}`
- Example: `flutter:main_user`, `flutter:tablet_user`
- Each unique chat ID creates a separate conversation context in NanoClaw

## Customization

### Change WebSocket Port

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

## Troubleshooting

### Connection Refused

1. Ensure NanoClaw is running: `npm run start` in NanoClaw directory
2. Check WebSocket server is listening on port 8765
3. Verify firewall allows connections

### No Response from NanoClaw

1. Check NanoClaw logs: `tail -f logs/nanoclaw.log`
2. Verify Flutter channel is loaded (look for "Flutter WebSocket server listening")
3. Ensure message format matches expected schema

### Build Errors

```bash
flutter clean
flutter pub get
flutter run
```

## Future Enhancements

- [ ] Multi-user support with chat switching
- [ ] Message threading/replies
- [ ] File/image attachments
- [ ] Push notifications
- [ ] Offline message queue
- [ ] Custom themes
