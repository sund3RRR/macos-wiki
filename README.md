# macos-wiki
This is a collection of my personal dotfiles and knowledge about macOS.
## Desktop environment
To transform MacOS to normal daily system we need to install some apps, which will improve window management, input system and external display.
### Apps
- [Rectangle](https://github.com/rxhanson/Rectangle) Will add support for dragging windows to the edges of the screen.
```bash
brew install --cask rectangle
```
- [MonitorControl](https://github.com/MonitorControl/MonitorControl) Will add the ability to change external monitor brightness/volume using keyboard keys
```bash
brew install --cask monitorcontrol
```
- [Mos](https://github.com/Caldis/Mos?tab=readme-ov-file) Will improve mouse scrolling with ability to blacklist some apps.
```bash
brew install --cask mos
```
- [AltTab](https://github.com/lwouis/alt-tab-macos) Will add windows-like alt-tab menu which is more convenient than macOS native menu.
```bash
brew install --cask alt-tab
```
- [Karabiner-Elements](https://github.com/pqrs-org/Karabiner-Elements) Is a powerful utility to customize keyboard. You can change shortcuts and reassign some keys (like swap fn and ctrl).
```bash
brew install --cask karabiner-elements
```
- [Pock](https://github.com/pock/pock) (For MacBooks with TouchBar) Will provide widget to move dock into TouchBar.
```bash
brew install --cask pock
```
- [OpenInTerminal](https://github.com/Ji4n1ng/OpenInTerminal) Will add context menu item for Finder to open folder in terminal/vscode/etc.
```bash
brew install --cask openinterminal
```
- [Stats](https://github.com/exelban/stats) Will add menu bar system monitor widgets
```bash
brew install --cask stats
```
### Install all apps
```bash
brew install --cask rectange monitorcontrol mos alt-tab karabiner-elements pock openinterminal stats
```

## Terminal
[Fish](https://github.com/fish-shell/fish-shell) is a powerful user-friendly shell with convenient extension support and useful features. To manage plugins you can also install [fisher](https://github.com/jorgebucaran/fisher)
```bash
brew install fish fisher
```
### Plugins
- [Tide](https://github.com/IlanCosman/tide) Is the ultimate Fish prompt
```bash
fisher install IlanCosman/tide@v6
```
### Set up with default terminal app
Change your shell entrypoint to `/opt/homebrew/bin/fish`
![[Pasted image 20240405074928.png]]
Add `-fish` to black list **Ask before closing**
![[Pasted image 20240405075019.png]]Edit `~/.config/fish/config.fish` and add these lines to add homebrew packages to PATH
#### **`~/.config/fish/config.fish`**
```fish
if status is-interactive
    eval "$(/opt/homebrew/bin/brew shellenv)"
    # Commands to run in interactive sessions can go here
end
```
### Terminal editor
[Micro](https://github.com/zyedidia/micro) Is the modern and intuitive terminal-based text editor.
```bash
brew install micro
```
If you want to use **micro** as default terminal editor, you can set environment variable in `~/.config/fish/config.fish
#### **`~/.config/fish/config.fish`**
```bash
if status is-interactive
    export EDITOR=micro
    eval "$(/opt/homebrew/bin/brew shellenv)"
    # Commands to run in interactive sessions can go here
end
```
You can set other terminal editor as default like nvim/nano/etc
```bash
export EDITOR=nvim
```

## Virtualization
The best choice in my opinion is the [VMware Fusion](https://www.vmware.com/products/fusion.html). It is free to personal use.
If you have [this](https://unix.stackexchange.com/questions/700721/gnome-42-wayland-vmware-a-white-square-appears-when-i-click-on-the-edges-of) annoying issue, you can fix it by disabling `motionUngrab`.
#### **`~/Library/Preferences/VMware\ Fusion/preferences`**
```
pref.motionUngrab = "FALSE"
pref.grabOnMouseClick = "TRUE"
pref.motionGrab = "FALSE"
... the rest of preferences
```