# Internet-Cafe-Streaming-Debian-AMD64

This setup is designed to turn a minimal Debian system into a lightweight streaming box for Discord and Firefox — perfect for screen sharing or remote access in environments like virtual machines (tested on VMware).

---

## 🖥️ System Requirements for 1280x720 Streaming

| Component | Minimum Requirement |
| --------- | ------------------- |
| CPU       | 2 Cores (x86\_64)   |
| RAM       | 2 GB                |
| Storage   | 8 GB                |

---

## 🔐 Getting Started: Superuser Setup

### Step 1: Install Essential Packages

Open a terminal and run the following command:

```bash
sudo apt install flatpak htop pipewire-audio icewm x11-utils x11-xserver-utils xinit -y && sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo && sudo reboot
```

**What this does:**

* `flatpak`: A package manager that installs modern apps.
* `htop`: A system monitor (optional, but useful).
* `pulseaudio`: Handles audio for Firefox and Discord.
* `icewm`: A super lightweight window manager.
* `x11-utils`, `x11-xserver-utils`, `xinit`: Tools to manage the graphical session.
* `flatpak remote-add`: Adds the Flathub repository (needed to install apps via Flatpak).
* `reboot`: Reboots your machine to apply everything cleanly.

---

### Step 2: Install Firefox and Discord + Launch Desktop

After rebooting, log in again and run:

```bash
sudo flatpak install flathub org.mozilla.firefox com.discordapp.Discord && exec icewm
```
```bash
startx
```

**What this does:**

* Installs **Firefox** and **Discord** from Flathub.
* `exec icewm`: Starts the IceWM window manager.
* `startx`: Launches the graphical desktop environment.
*Next time, you can just run `startx` to launch IceWM.*

---

## 📺 Optional: Set Display Resolution

If your display doesn't look good, you can manually change the resolution using `xrandr`.

### 1. List Available Displays

```bash
xrandr
```

Look for something like `Virtual1` or `eDP-1`.

### 2. Set Display Resolution

```bash
xrandr --output Virtual1 --mode 1280x720
```

**Customize this if needed:**

```bash
xrandr --output <DISPLAY> --mode <RESOLUTION>
```

Replace `<DISPLAY>` with your display name (e.g., `Virtual1`) and `<RESOLUTION>` with your preferred resolution (e.g., `1920x1080`, `1280x720`, etc.).

---

## ✅ You're Done!

You now have a minimal, fast Debian system ready to stream via Discord and browse with Firefox. Ideal for virtual machines or low-resource setups.
