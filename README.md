## Installation
Before you start, make sure you have a USB drive an Arch Linux ISO image. It is also important that you have a stable and fast internet connection, as you will need to download packages during the installation. This guide uses kernel: 6.2.1.

##  0-Set up your keyboard the way you want (Optional)
```
loadkeys YOURDISTRIBUTION (en=english, es=spanish, etc.)
```

##  1-Wifi (Optional)
```
iwctl
|_  device list
    |_  station YOURNETWORK connect "NAME OF YOUR NETWORK"
```

##  2-Create and resize partitions (part 1)
```
archinstall
|_  language: English
    keyboard layout: es
    mirror region: spain
    locale lang: en_US
    locale encoding: utf-8
    drive: "select desired one with TAB" + ENTER
    disk layout: wipe all - ext4 - "separate partition for /home" - yes
    bootloader: grub-install
    hostname: desired one
    root password: desired one
    user account: desired one (give super-user)
    profile: minimal
    audio: none
    kernels: linux
    aditional packages: git
    network configuration: copy
    tinmezone: desired one
    ntp: true
    optional repositories: multilib
    |_  install
```

##  3-Surface packages & kernel
First you need to import the keys we use to sign packages.
```
curl -s https://raw.githubusercontent.com/linux-surface/linux-surface/master/pkg/keys/surface.asc \
    | sudo pacman-key --add -
```
```
sudo pacman-key --finger 56C464BAAC421453
sudo pacman-key --lsign-key 56C464BAAC421453
```
You can now add the repository by adding the following to the end of /etc/pacman.conf
```
[linux-surface]
Server = https://pkg.surfacelinux.com/arch/
```
After doing that you need to refresh the repository metadata, then you can install the linux-surface kernel and its dependencies.
NOTE: libwacom-surface is packaged through the AUR, so you need to install it from there.

https://aur.archlinux.org/packages/libwacom-surface
```
sudo pacman -Syu
```
```
sudo pacman -S linux-surface linux-surface-headers iptsd
```
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

##  4-Utilities
The following repositories aim to help you keep your kernel and accompanying software up-to-date. To this end, the Debian, Arch Linux, and Fedora repositories provide the latest kernels pre-compiled as binary packages and pre-signed for secure boot (see the secure boot page).

https://aur.archlinux.org/packages/surface-control
https://aur.archlinux.org/packages/surface-dtx-daemon
```
sudo pacman -Syu
```

##  5-Desktop environment
Using install script (Clone the repository).
```
git clone https://www.github.com/Othrondir/dotfiles-2.git
cd dotfiles
chmod +x install-on-arch.sh
./install-on-arch.sh
```
ENTER + :q! to exit vim

## Cheat sheet


<details>
<summary>Keybinds</summary>

These are the basic keybinds. Read through the [i3](./config/i3/config) config for more keybinds.

|        Keybind         |                 Function                 |
| ---------------------- | ---------------------------------------- |
| `Win + Enter`          | Launch terminal (alacritty)              |
| `Win + Shift + Q`      | Close window                             |
| `Win + Q`              | Stacking layout                          |
| `Win + W`              | Tabbed layout                            |
| `Win + E`              | Default layout                           |
| `Win + R`              | Resize mode                              |
| `Win + T`              | Restore layout                           |
| `Win + Y`              | Save layout                              |
| `Win + A`              | Rofi open windows menu                   |
| `Win + S`              | Rofi full menu                           |
| `Win + D`              | Rofi menu                                |
| `Win + Z`              | Rofi bookmarks                           |
| `Win + X`              | Rofi powermenu                           |
| `Win + C`              | Rofi screenshot script                   |
| `Win + G`              | Gaps settings                            |
| `Win + V`              | Set vertical orientation                 |
| `Win + H`              | Set horizontal orientation               |
| `Win + I`              | Lock screen                              |
| `Win + O`              | Show polybar                             |
| `Win + P`              | Hide polybar                             |
| `Win + B`              | Move workspace to another monitor        |
| `Win + N`              | Dual monitor mode                        |
| `Win + M`              | Single monitor mode                      |
| `Win + arrows (jkl;)`  | Resizing, moving windows                 |
| `Win + Shift + E`      | Exit i3                                  |
| `Win + Shift + R`      | Restart i3                               |

Note: `Win` refers to the `Super/Mod` key.

</details>

<details>
<summary>Colors</summary>

|        Color           |                 Hex code                 |
| ---------------------- | ---------------------------------------- |
|  background            | #1b1b25                                  |
|  background 2          | #282A36                                  |
|  background 3          | #16161e                                  |
|  border                | #343746                                  |
|  foreground            | #dedede                                  |
|  white                 | #eeffff                                  |
|  black                 | #15121c                                  |
|  red                   | #cb5760                                  |
|  green                 | #999f63                                  |
|  yellow                | #d4a067                                  |
|  blue                  | #6c90a8                                  |
|  purple                | #776690                                  |
|  cyan                  | #528a9b                                  |
|  pink                  | #ffa8c5                                  |
|  orange                | #c87c3e                                  |

</details>

## Support and Thankies

You can support me simply by dropping a **star** on **[github](https://github.com/Keyitdev/dotfiles/tree/v3)** or giving a **subscription** on **[YouTube](http://www.youtube.com/channel/UCVoGVyAP2sHPQyegwBMJKyQ?sub_confirmation=1)**.

<!-- If you enjoyed it and would like to show your appreciation, you can **tip** using **[kofi]()** or **[paypal]()**. -->

**Big thanks to:**
[adi1090x](https://github.com/adi1090x),
[Totoro](https://github.com/totoro-ghost).

Thanks to all contributors! :D

## Contributions

Feel free to create issue or pull request.    
If you need any help, you can ask questions here on **[discussions](https://github.com/Keyitdev/dotfiles/discussions/categories/q-a)** or contact me on **[discord](https://discord.com/users/908702082578665474)** / **[reddit](https://www.reddit.com/user/Keyitdev)**.

Distributed under the **[GPLv3+](https://www.gnu.org/licenses/gpl-3.0.html) License**.    
Copyright (C) 2022 Keyitdev.
