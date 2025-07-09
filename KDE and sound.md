# KDE Audio Setup with PipeWire (Arch Linux)

This guide explains how to enable volume control and Fn audio keys in a minimal KDE install using PipeWire (without PulseAudio).

---

## ✅ System Overview

- **DE**: KDE Plasma
- **Audio**: PipeWire + `pipewire-pulse`
- **Goal**: Enable sound icon and Fn volume keys without installing PulseAudio daemon

---

## 🛠 Installed Packages

Minimal KDE setup (already installed):
```bash
sudo pacman -S plasma-desktop kde-system-meta kde-gtk-config \
konsole dolphin plasma-workspace xdg-desktop-portal-kde plasma-workspace-wallpapers
