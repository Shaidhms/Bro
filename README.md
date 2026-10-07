# Bro 😎

A cartoon desktop buddy for **macOS and Windows** who lives on your screen, walks around, reminds you to drink water, keeps you
off YouTube, Instagram and OTT sites when you've had enough, tidies your folders and chats with you. **Biscuit the
cat** is the default buddy; switch any time with right-click → **Character** (Bro (Denim), Iron Man, Drop or Buddy).

- **Water reminders.** Every 45 minutes he pops up with a water pose and asks *"Did you drink water?"*.
  **YES** logs a glass; he cheers and does a happy run across the screen. **Remind me later** makes him sad and he
  comes back in 10 minutes.
- **Screen-time guard.** Open YouTube, Instagram, Netflix, Prime Video, JioHotstar and more, and he asks
  *"How much time do you need?"* (5 min / 15 min / 30 min / 1 hr; 15 min if you don't answer). The question
  vanishes as soon as you pick, and he disappears with a poof into the menu bar, where 😎 counts down. Near the end
  he comes back to nag you, gets angry, then leaps up to the tab strip, smashes it and closes the tab.
- **Folder tidy.** Right-click → **Tidy a folder** (Downloads, Desktop or any folder). Images, videos, audio,
  documents and archives go into their own folders. He counts first and asks before moving anything; nothing is
  deleted, and **Undo last tidy** puts everything back. Works fully offline: no AI, no internet.
- **Chat.** Double-click him to chat. Offline he understands simple commands: *"tidy my downloads"*, *"undo"*,
  *"I drank water"*, *"walk left"*. Turn on **Agentic chat** in Settings with your own API key (OpenAI,
  Anthropic Claude, Google Gemini or any OpenAI-compatible service) for real conversations; he can still tidy and
  log water from chat.
- **Fun bits.** Single-click for his swag move, drag him anywhere, and he waves hello when he starts.
  **Minimise Bro** sends him off with a poof; bring him back from 😎 in the menu bar or from the Dock.
- **First-run tutorial.** A quick guided tour on first launch (Next → Next → Got it); replay it from right-click →
  **Show tutorial**.

> **Personal, non-commercial fan project.** The characters are likenesses of actor Vijay (Bro (Denim)) and of
> Marvel's Iron Man. Bro is not affiliated with or endorsed by Vijay, Marvel or Disney. The buddies were made with AI
> image and video tools, just for fun. Don't sell or redistribute builds that contain them. Bro ships with no API keys.

## Install

| Your computer | File |
|---|---|
| Mac with Apple Silicon (M1/M2/M3/M4…) or Intel, macOS 13 Ventura or newer | `Bro-1.0.dmg` |
| Windows 10/11 (64-bit) | `Bro-1.0-Windows.exe` |

### Mac

1. Download `Bro-1.0.dmg` from [Releases](../../releases/latest), open it and drag **Bro** into **Applications**.
2. Open Bro from Applications.

**First launch (one time only).** macOS blocks Bro the first time (the app isn't signed with a paid Apple
certificate, that's why):

1. Double-click **Bro**. macOS says it *"could not verify"* Bro. Click **Done**.
2. Open **System Settings → Privacy & Security**.
3. Scroll down to *"Bro was blocked…"* and click **Open Anyway**.
4. In the pop-up, click **Open Anyway** / **OK** and enter your **Mac password**.
5. Bro opens. After this he opens normally every time.

The first time you open YouTube or a streaming site, macOS asks *"Bro wants to control Google Chrome / Safari"*.
Click **OK**, or he can't see your tabs. Works with Google Chrome, Safari, Brave and Arc.

### Windows

1. Download `Bro-1.0-Windows.exe` from [Releases](../../releases/latest) and save it somewhere you'll keep it
   (for example **Documents**). There's nothing to install: double-click it and Bro appears.
2. **First launch (one time only).** Windows SmartScreen may say *"Windows protected your PC"* (the app isn't signed
   with a paid certificate, that's why). Click **More info → Run anyway**. After this he opens normally every time.
3. To start him automatically, right-click Bro → **Settings** → tick **Start Bro when Windows starts** → **Save**.
   Don't move the `.exe` after that.

On Windows he watches the tab title in Chrome, Edge, Brave, Firefox, Opera, Vivaldi and Arc. When he hides, click
the little **Bro** pill at the bottom-right of the screen to bring him back (it shows the time left).

## How to use him

| Do this | What happens |
|---|---|
| **Click** | Swag move (or logs a glass when he's asking about water) |
| **Double-click** | Opens chat |
| **Drag** | Move him anywhere |
| **Right-click** | Everything else: Character, Tidy a folder, I drank water, Minimise, Settings, Show tutorial, Quit |
| **😎 in the menu bar** | Show / hide Bro, chat, settings, quit. Shows the time left while you're on a watched site |

## Settings

Right-click Bro → **Settings…**. Changes apply straight away:

- **You:** what Bro calls you (default *Bro*), character, walk around, start at login
- **Sites & OTT:** YouTube, Instagram, Facebook, X / Twitter, Reddit, Netflix, Prime Video, JioHotstar, JioCinema,
  SonyLIV, ZEE5, Disney+, aha, Sun NXT
- **Screen time:** ask how much time you need, the time choices, the default if you don't answer, water reminder interval
- **Agentic chat:** provider, model and your own API key

Everything is stored in `~/Library/Application Support/Bro/` (Mac) or `%APPDATA%\Bro\` (Windows): `config.json` for settings, `stickers/` for the
characters and `ai.key` for your API key (readable only by you). Bro ships with **no API keys**.

## Characters

Each character is a folder in `~/Library/Application Support/Bro/stickers/<name>/`. A pose is a single image
(`idle.png`) or a folder of frames (`walk/001.png`, `002.png`…) played in order:

| Pose | Used for |
|---|---|
| `idle` | Standing around (required) |
| `walk` / `run` | Walking around / the happy run after drinking water and the leap to the tab |
| `water` | Water reminder |
| `happy` | After *YES* |
| `warn` | Sad face after *Remind me later*, and nags |
| `angry` | Final warning and the tab smash |
| `hello2` | Swag move on single click |

`character.json` sets the display name, playback speed and which way the walk/run clips face. Missing poses fall
back to `idle`. Prompts used to make the characters (ChatGPT image + Kling image-to-video) are in
[characters/PROMPTS.md](characters/PROMPTS.md).

## Development

Swift + AppKit, no dependencies. Requires the Xcode command line tools.

```bash
./build.sh                       # personal build → ~/Applications/Bro.app
./build-share.sh                 # shareable build → dist/Bro-<version>.dmg (universal, no voice, no keys)
CHARS="biscuit denim" ./build-share.sh    # choose which characters to bundle (first = default + app icon)
FPS=24 ./import-character.sh biscuit ~/Downloads/biscuit-poses   # turn images/clips into a character
```

`import-character.sh` removes backgrounds on-device with Apple Vision and turns `.mp4` clips into frame folders.

**Windows build:** run `./windows/pack_assets.sh` on the Mac (turns the characters into WebP frames and makes
`bro.ico`), copy the `windows/` folder to a Windows PC with Python 3.11+, and double-click `build_windows.bat`.
It produces `windows\dist\Bro.exe`.

## Project layout

```
Sources/main.swift      app, character animation, water reminders, screen-time guard, menus
Sources/Chat.swift      chat routing, offline commands
Sources/AIChat.swift    agentic chat (OpenAI / Anthropic / Gemini / OpenAI-compatible)
Sources/Settings.swift  Settings window and first-run tutorial
Sources/Tidy.swift      folder tidy + undo
Sources/Effects.swift   poof / sparkle effects
Sources/Edition.swift   personal vs share build, offline brain
tools/                  background cutout, sticker packing, app icon
characters/PROMPTS.md   prompts for making new characters
windows/                Windows version (Python + tkinter, built into one Bro.exe with PyInstaller)
share/                  READ ME FIRST that goes inside the DMG
```

Made by Shaid · [shaid360.com](https://shaid360.com)
