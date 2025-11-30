# Discord Rich Presence Controller

A lightweight Electron desktop app that gives you complete control over your Discord Rich Presence status. Customize every aspect of how your activity appears to friends - from activity type to images, buttons, and timestamps.

![Electron](https://img.shields.io/badge/Electron-33.0.0-47848F?logo=electron&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-blue)

## Features

- **Multiple Activity Types** - Playing, Streaming, Listening, Watching, Competing
- **Custom Text** - Set details and state with full control
- **Image Support** - Large and small images with hover text (asset names or URLs)
- **Clickable Buttons** - Add up to 2 buttons with custom labels and links
- **Timestamps** - Show elapsed time or countdown remaining
- **Auto-Reconnect** - Automatically reconnects if Discord restarts
- **Dark Theme** - Discord-inspired UI that feels native

## Installation

```bash
# Clone the repository
git clone https://github.com/ijuice-j/discord-rich-presence-controller.git
cd discord-rich-presence-controller

# Install dependencies
npm install

# Run the app
npm start
```

## Usage

### 1. Get a Discord Application ID

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications)
2. Create a new application (or use an existing one)
3. Copy the **Application ID** from the General Information page

### 2. Set Up Rich Presence Assets (Optional)

1. In your Discord application, go to **Rich Presence** → **Art Assets**
2. Upload images you want to use for large/small icons
3. Note the asset names for use in the app

### 3. Connect and Customize

1. Paste your Application ID in the app
2. Click **Connect**
3. Fill in the fields you want to display
4. Click **Update Presence**

## Configuration Options

| Field | Description | Max Length |
|-------|-------------|------------|
| Details | First line of text | 128 chars |
| State | Second line of text | 128 chars |
| Large Image | Asset name or HTTPS URL | - |
| Large Image Text | Hover text for large image | 128 chars |
| Small Image | Asset name or HTTPS URL | - |
| Small Image Text | Hover text for small image | 128 chars |
| Button 1/2 Label | Button text | 32 chars |
| Button 1/2 URL | Button link | Valid URL |

## Activity Types

| Type | Display Format |
|------|---------------|
| Playing | "Playing {details}" |
| Streaming | "Streaming {details}" |
| Listening | "Listening to {details}" |
| Watching | "Watching {details}" |
| Competing | "Competing in {details}" |

## Timestamps

- **Elapsed** - Shows "XX:XX elapsed" counting up from when you started
- **Remaining** - Shows "XX:XX left" counting down (requires duration input)

## Architecture

```
src/
├── main/
│   ├── index.js           # Electron main process & window management
│   ├── discord-service.js # Discord RPC client & activity handling
│   ├── timer-manager.js   # Reconnection timer management
│   └── constants.js       # Shared constants
├── renderer/
│   ├── index.html         # Application UI
│   ├── styles.css         # Discord-themed styling
│   └── renderer.js        # UI logic & event handlers
└── preload.js             # Secure IPC bridge (context isolation)
```

## Tech Stack

- **[Electron](https://www.electronjs.org/)** - Cross-platform desktop framework
- **[@xhayper/discord-rpc](https://github.com/xhayper/discord-rpc)** - Discord RPC library
- **Vanilla JS/HTML/CSS** - No frontend framework bloat

## Notes

- Discord must be running for Rich Presence to work
- Buttons are only visible to other users (not yourself)
- Image URLs must be publicly accessible HTTPS URLs
- Changes may take a few seconds to appear in Discord

## License

MIT
