# Fixing `cmatrix` Black Background in Transparent Terminal Emulators (Arch Linux)

If you're an Arch Linux user who enjoys a transparent terminal background (like in Kitty, Alacritty, or Terminator) but find that `cmatrix` insists on rendering with a solid black background, you're not alone. This is a common frustration, especially when other command-line tools (like `pipes.sh`) correctly display with transparency.

## The Problem

The core issue often stems from how `cmatrix` is compiled, particularly the version found in the official Arch Linux repositories. Certain build configurations, especially those utilizing CMake, can cause `cmatrix` to explicitly set its own background color to black, effectively overriding your terminal emulator's transparency settings. This leads to an inconsistent visual experience where `cmatrix` stands out with an opaque black box.

## The Solution: Use the AUR `cmatrix-git` Package

The most reliable solution for Arch Linux users is to switch from the official `cmatrix` package to the `cmatrix-git` package available in the Arch User Repository (AUR).

The `cmatrix-git` package compiles `cmatrix` directly from its source, often using an older or different build system that does not exhibit this transparency-overriding behavior. As a result, this version of `cmatrix` will correctly inherit and display your terminal's transparent background.

### Prerequisites for Transparency

Before proceeding, ensure your terminal emulator and desktop environment are properly configured for transparency:

1.  **Terminal Emulator Transparency:** Verify your terminal's configuration file (e.g., `~/.config/kitty/kitty.conf` for Kitty, `~/.config/alacritty/alacritty.toml` for Alacritty) has `opacity` or `background_opacity` set to a value less than `1.0`. For example:
    ```
    background_opacity 0.8
    ```
2.  **Compositor (for X11 users):** If you are using an X11-based desktop environment or window manager (e.g., i3, Openbox, XFCE, Plasma, GNOME on X11), a compositor like `picom` is **essential** for transparency to work. Ensure a compositor is running and properly configured for your session. You can install `picom` with `sudo pacman -S picom` and typically add `picom &` or `exec_always picom` to your autostart script.

### Installation Steps (using `yay` or `paru`)

1.  **Remove the official `cmatrix` package (if installed):**
    ```bash
    sudo pacman -R cmatrix
    ```
2.  **Install `cmatrix-git` from the AUR:**
    Use your preferred AUR helper (e.g., `yay` or `paru`).

    ```bash
    yay -S cmatrix-git
    ```
    or
    ```bash
    paru -S cmatrix-git
    ```

    Follow the prompts to build and install the package. This process may take a few moments as it downloads and compiles the source code.

## Verification

After installing `cmatrix-git`, open a new terminal window (or restart your existing one). When you run `cmatrix`, you should now observe it respecting your terminal's transparency settings, blending seamlessly with your desktop background instead of displaying an opaque black box.
