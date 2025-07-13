# KDE Display Scaling Fix

## Problem

After installing the KDE Plasma desktop environment on Arch Linux (alongside GNOME), the **display scaling** option was missing in:


As a result, everything appeared too small on high-resolution monitors.

---

## Cause

The package `kscreen` (KDE's screen management backend) was not installed. This package is responsible for enabling resolution, orientation, and **scaling** options in KDE’s System Settings.

---

## Solution

### ✅ Install `kscreen`

```bash
sudo pacman -S kscreen
```

