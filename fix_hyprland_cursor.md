# 🖱️ Fixing Cursor Theme in Hyprland


## 🚨 Problem

I couldn't change the **cursor size** using the line `env = XCURSOR_SIZE,...` in `hyprland.conf`.  
No matter what value I set, Hyprland would still use the old or default size(24).

This was especially frustrating when trying to use large cursors for better visibility.  
Turns out, Hyprland doesn't reliably apply cursor size from the `env` variable at startup.


---

## ✅ Solution

I discovered that I could **manually set the cursor** using the `hyprctl setcursor` command. Here's how I fixed it:

### 🛠️ Step-by-Step Fix

1. **Pick your cursor theme** (can be a regular Xcursor theme or a Hyprcursor theme).
2. Use the following command format:

   ```bash
   hyprctl setcursor <theme-name> <size>
   ```

   ### 💡 Example:
   ```bash
   hyprctl setcursor Banana 40
   ```

   This sets the cursor to the `Banana` theme with size 40.

3. To make it work **automatically on startup**, I added it to my `exec-once` section in `hyprland.conf`:

   ```conf
   exec-once = hyprctl setcursor Banana 40
   ```

   ✅ You can place this near your other startup apps or settings.

---

## ⚠️ Note

- The new cursor **might not show up immediately** on startup, you might see the hypr-cursor theme if you ever installed it.
- But once you **hover over any app or panel (like Waybar)**, the cursor **switches to your chosen theme** 🎉.

---

## 📝 TL;DR

```bash
hyprctl setcursor Banana 40
```

Add to `hyprland.conf`:

```conf
exec-once = hyprctl setcursor Banana 40
```

Enjoy your new cursor! 🍌🖱️
