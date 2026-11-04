<p align="center">
  <img src="icon.png" width="128" height="128" alt="Termina app icon">
</p>

<h1 align="center">Termina</h1>

<p align="center">
  <b>A native SSH client for iPhone, iPad and Mac.</b><br>
  Fast, light and private: your passwords and keys never leave your device.
</p>

<p align="center">
  <b>English</b> · <a href="README.it.md">Italiano</a>
</p>

![Termina on Mac: server list and terminal](screenshots/mac-terminal-en.jpg)

## Contents

- [Features](#features)
- [System requirements](#system-requirements)
- [Download](#download)
- [User guide](#user-guide)
  - [1. Add a server](#1-add-a-server)
  - [2. Quick Connect](#2-quick-connect)
  - [3. Using the terminal](#3-using-the-terminal)
  - [4. Command Deck and keyboard](#4-command-deck-and-keyboard)
  - [5. Files (SFTP)](#5-files-sftp)
  - [6. Port forwarding (tunnels)](#6-port-forwarding-tunnels)
  - [7. Sessions that survive: tmux](#7-sessions-that-survive-tmux)
  - [8. Settings and language](#8-settings-and-language)
  - [9. Sync between iPhone, iPad and Mac](#9-sync-between-iphone-ipad-and-mac)
  - [Keyboard shortcuts](#keyboard-shortcuts)
- [Security and privacy](#security-and-privacy)
- [Troubleshooting](#troubleshooting)
- [Support](#support)

## Features

- **Real terminal**: xterm-256color with GPU (Metal) rendering, true colour, vim, htop, tmux, colour profiles.
- **Tabs**: several servers open at once, switch with ⌘1…⌘9.
- **Quick Connect**: type `user@host` and you are in, like `ssh` in Terminal.
- **Command Deck**: Esc, Tab, Ctrl, Alt, arrows, symbols and your own one-tap macros.
- **Files (SFTP)** next to the terminal: upload, download, preview, edit text files, change permissions.
- **Port forwarding**: local (-L) and remote (-R) tunnels with live status and traffic.
- **Secure credentials**: passwords and keys in the Keychain, unlocked with Face ID or Touch ID;
  hardware keys generated in the **Secure Enclave** that can never be copied.
- **iCloud sync**: servers, macros, tunnels, passwords and keys on all your iPhone, iPad and Mac,
  end-to-end encrypted, with no account to create.
- **Tailscale** detected automatically; **tmux** keeps your shell alive when the connection drops.
- 5 languages: English, Italiano, Français, Deutsch, Español.

| | |
|---|---|
| ![Welcome screen with Quick Connect](screenshots/mac-welcome-en.jpg) | ![Terminal with the Files panel](screenshots/mac-files-en.jpg) |
| Welcome screen, recent servers and Quick Connect | Terminal with the Files panel |
| ![Port forwarding](screenshots/mac-tunnels-en.jpg) | ![Server editor](screenshots/mac-editor-en.jpg) |
| Port forwarding with live status | Server editor: icon, colour, group, authentication |
| ![iPad terminal](screenshots/ipad-terminal-en.jpg) | ![Settings](screenshots/mac-settings-en.jpg) |
| iPad with the Command Deck | Settings |

<p align="center">
  <img src="screenshots/iphone-welcome-en.jpg" width="240" alt="iPhone welcome screen">
  &nbsp;
  <img src="screenshots/iphone-terminal-en.jpg" width="240" alt="iPhone terminal">
  &nbsp;
  <img src="screenshots/ipad-portrait-terminal-en.jpg" width="360" alt="iPad in portrait">
</p>

## System requirements

| | iPhone | iPad | Mac |
|---|---|---|---|
| **Operating system** | iOS 17 or later | iPadOS 17 or later | macOS 15 Sequoia or later |
| **Devices** | iPhone XS, XR or later | iPad (6th gen.), iPad mini (5th gen.), iPad Air (3rd gen.), iPad Pro (2nd gen.) or later | Apple silicon (M1 or later) or Intel Macs that run macOS 15 |
| **Liquid Glass look** | iOS 26 | iPadOS 26 | macOS 26 Tahoe |
| **Unlocking credentials** | Face ID, Touch ID or device passcode (a passcode must be set) | Face ID, Touch ID or passcode (a passcode must be set) | Touch ID or Mac password |
| **Secure Enclave keys** | All supported iPhones | All supported iPads | Apple silicon, or Intel Macs with the T2 chip |
| **Hardware keyboard** | Optional | Optional (Magic Keyboard, Smart Keyboard, Bluetooth) | Built in |

On older systems the app works the same, with a classic (non-glass) look. You also need an SSH server to
connect to (Linux, macOS, BSD, Raspberry Pi, NAS, router…) reachable from your device: on your network,
over the Internet or through a VPN such as Tailscale.

## Download

Termina is coming to the App Store for iPhone, iPad and Mac. New versions and release notes are published on the
[Releases](https://github.com/kikoz85/Termina/releases) page of this repository.

## User guide

### 1. Add a server

1. Press **+** at the top of the server list (or ⌘N).
2. Fill in **Address** (IP or hostname), **Port** (usually 22) and **User**. The **Label** is the name you will see in the list.
3. Optional: pick a **group** (Local, Mac Mini, Production), a **colour** and an **icon**, so you can find it at a glance.
4. Choose how to sign in:
   - **Password**: typed once and saved in the Keychain.
   - **Key**: import an OpenSSH private key (Ed25519 or RSA) from Files, with its passphrase if it has one.
   - **Secure Enclave**: Termina creates a key inside your device's chip. Copy the public key shown and add it
     to `~/.ssh/authorized_keys` on the server. The private key can never be exported or copied.
5. Press **Save**, then tap the server to connect.

The first time you connect, Termina shows the server's **fingerprint**: compare it with the server's own
(`ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub`) and choose **Trust**. If it ever changes, Termina refuses
to connect and warns you: it may be an attack, or the server was reinstalled.

### 2. Quick Connect

On the welcome screen, type `user@host` (or `user@host:port`) next to `ssh` and press Return.
Termina connects straight away and asks for the password, like `ssh` does. The password stays in memory only for that
session. To keep the server, open the session menu (**⋯**) and choose **Save Server**: the password you typed is filled in for you.

If the address matches a server you already saved, its saved session opens instead.

### 3. Using the terminal

- Each server opens in a **tab**. The **+** next to the tabs opens another server; **×** closes the tab.
- The title shows `user@host — process — columns×rows`.
- **Pinch** (or ⌘+ / ⌘-) to change the text size.
- **⌘F** searches the output; **⌘K** clears the screen and scrollback.
- Select text to copy it; links in the output can be opened directly.
- If the connection drops, a card shows the reason with **Reconnect** and **Edit Server** (to fix the address,
  user or password without leaving the session).

### 4. Command Deck and keyboard

The bar under the terminal (the **Command Deck**) gives you the keys a touch keyboard lacks:

- **ctrl** and **alt** stay locked for the next key: tap **ctrl**, then **c** to send Control-C.
- **esc**, **tab**, arrows, `|` `~` `/` `-` and shortcuts such as **^C ^D ^Z ^R**.
- **Macros**: buttons that type a whole command (`ls -la`, `htop`, `docker ps`…). Press **+** to add your own,
  with a name, an icon and the option to run it immediately. Macros belong to each server.

With a **hardware keyboard** (Magic Keyboard on iPad, or the Mac's own) the Deck can show only macros or hide
completely: see *Settings → Keyboard → Command Deck*. **⌘.** always sends Esc, even on keyboards without an Esc key.
**Option as Meta** makes Option send Esc+key (useful in Emacs, bash and tmux); turn it off to type accented letters with Option.

### 5. Files (SFTP)

Press the **folder** button in the toolbar (⇧⌘F) to open the files of the server next to the terminal.

- Tap a folder to open it; tap the path at the top to go back; **↑** goes to the parent folder.
- Tap a text file to **edit** it; other files open in **Quick Look**.
- **Upload** with the share button or by **dragging** files in; long-press (or right-click) a file to **save** it,
  **rename** it, change **permissions**, copy its path or delete it.
- **Open in Terminal** runs `cd` to that folder in the shell.

### 6. Port forwarding (tunnels)

Use tunnels to reach services that only the server can see, for example a database or an admin panel.
Press the **tunnel** button in the toolbar (⇧⌘T), then **+**:

- **Local (-L)**: listens on your device and forwards to the server. Example: device `127.0.0.1:5432` → server
  `127.0.0.1:5432` lets you open the server's PostgreSQL from apps on your iPad or Mac.
- **Remote (-R)**: listens on the server and forwards to your device or your network.

Each tunnel shows its state and live traffic; web tunnels can be opened in the browser with one tap. On iPhone and
iPad, local tunnels work while Termina is in the foreground (also in Split View and Slide Over).

### 7. Sessions that survive: tmux

iOS closes network connections about 30 seconds after an app goes to the background. To keep long jobs running,
type a name in **tmux session** when editing a server: Termina starts `tmux new-session -A -s <name>` after
login and reattaches to the same shell when it reconnects. `tmux` must be installed on the server.

### 8. Settings and language

Open **Settings** with the gear button (or ⌘,):

- **Profile**: six colour themes with live preview, and opacity.
- **Text**: font and size. **Cursor**: shape and blinking.
- **Keyboard**: Option as Meta and Command Deck behaviour.
- **Language**: *Automatic* follows your system language (English if your language is not available), or choose
  English, Italiano, Français, Deutsch or Español. The new language applies the next time the app opens; on Mac you can restart it right away.

### 9. Sync between iPhone, iPad and Mac

Termina keeps your devices in step through **your own iCloud**: there is no Termina account to create.
It is on by default (*Settings → Sync → iCloud*); you only need to be signed in with the same Apple Account
on every device.

- **What syncs**: servers (with groups, colours, icons), macros, tunnels, trusted host keys, passwords and
  private keys. Add a server on the Mac and connect from the iPad without typing the password again.
- **Privacy**: everything is end-to-end encrypted with keys in your iCloud Keychain; Apple can't read it.
- **What stays on each device**: Secure Enclave keys (they never leave the chip: create one per device and
  add each public key to `authorized_keys`) and the list of recent servers.
- Changes arrive within seconds; **Sync Now** in Settings forces a check. If two devices edit the same
  server, the most recent change wins.
- Passwords saved before sync was turned on are uploaded the first time you connect with them.

### Keyboard shortcuts

| Keys | Action |
|---|---|
| ⌘T / ⌘W | New tab / close tab |
| ⌘1…⌘9, ⇧⌘[ ⇧⌘] | Go to tab / previous / next |
| ⌘K | Clear screen and scrollback |
| ⌘F, ⌘G, ⇧⌘G | Find, next, previous |
| ⌘+ ⌘- ⌘0 | Text size |
| ⌘. | Esc |
| ⇧⌘T | Tunnels |
| ⇧⌘F, ⌘↑ | Files, parent folder |
| ⌘N / ⌘, | New server / Settings |
| ⌘R | Reconnect |

On iPad, hold **⌘** to see every shortcut.

## Security and privacy

- Passwords and private keys are stored only in your device's **Keychain**, protected by Face ID, Touch ID or your
  passcode. With iCloud sync on they also travel through your own iCloud, end-to-end encrypted: neither
  Apple nor the developer can read them.
- Secure Enclave keys are created inside the chip and **cannot be extracted**, not even by Termina.
- Every server's identity is checked (host key fingerprint) to protect you from man-in-the-middle attacks.
- No accounts, no analytics, no tracking: Termina connects only to the servers you add (and, with sync on, to your own iCloud).

Full policy: [Privacy](https://kikoz85.github.io/Termina/en/privacy.html).

## Troubleshooting

| Problem | What to do |
|---|---|
| "Credential not found in Keychain" | Open **Edit Server** from the session card and type the password or import the key again. |
| "Authentication failed" | Check user and password. For keys, make sure the public key is in `~/.ssh/authorized_keys` on the server. |
| "The host key has changed" | If you reinstalled the server, delete it from Termina and add it again. Otherwise do **not** connect. |
| `100.x.x.x` or `*.ts.net` unreachable | Turn on the Tailscale VPN on your device. |
| The connection drops in the background | Use a **tmux session** (see the guide, section 7). |
| Accented letters with Option don't work | Turn off **Option as Meta** in Settings. |
| A server doesn't appear on another device | Check you are signed in to iCloud with the same Apple Account, then **Settings → Sync Now**. |

## Support

- Help and contact: [Support page](https://kikoz85.github.io/Termina/en/support.html)
- Bugs and suggestions: open an [issue](https://github.com/kikoz85/Termina/issues) or write to enricofanucchi@gmail.com

© 2026 Enrico Fanucchi
