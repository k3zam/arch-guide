# Arch Install
Personal guide for stuff to do after settng up arch.
# Table of Contents

## Enable Network and Bluetooth

#### Enables Network
```bash
systemctl enable NetworkManager --now #enable networking
```

#### Enables Bluetooth
```bash
systemctl enable bluetooth.service --now #enable bluetooth
```

## Wayland and hardware accelration on firefox
Follow the steps in https://wiki.archlinux.org/title/firefox

edit ```/etc/environment``` and add the lines below
```
MOZ_ENABLE_WAYLAND=1
MOZ_DBUS_REMOTE=1
```

## Setup yay for AUR
```bash
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

## Setup Timeshift for snapshots
```bash
yay -Sy timeshift
yay timeshift-autosnap
sudo pacman -S grub-btrfs
```
change default amount of snapshots to keep to 5 by editing ```/etc/timeshift-autosnap.conf```
grub-btrfs adds snapshot entries to grub after updating

## Install Yakuake
```bash 
sudo pacman -S yakuake
```

## Appearence
#### Disable blur
Disable blur and transluency effects from compositor

Right click task switcher > enter edit mode > more options > Opacity-Opaque

## Pacman Changes
uncomment color and parallel downloads in pacman.conf and add ILoveCandy

## Install Microcode
```bash
sudo pacman -S intel-ucode
```

## Disable GRUB delay
```bash
sudo nano /etc/default/grub
```
Set GRUB timeout style to hidden

Update GRUB config
```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## Setup Firewall
```bash
sudo pacman -S ufw
```
Enable the firewall from command line or from settings GUI

## Usefull stuff to install
```bash
sudo pacman -S p7zip unrar
```

## Enable thumbnails for video and windows applications
```bash
yay kdegraphics-thumbnailers
yay ffmpegthumbs
yay icoutils
```
Enable thumbnail plugins in Dolphin and Settings Manager 

## Install and setup zsh

```sudo pacman -S zsh```

### Setup powerlevel10k
Follow the steps in https://github.com/romkatv/powerlevel10k

Use the config files
#### Make zsh default
```
chsh -l
chsh -s /usr/bin/zsh
```

## Setup grub theme

## Setup wine and dependencies
```
yay -S lib32-giflib lib32-gnutls lib32-v4l-utils lib32-libpulse alsa-plugins lib32-alsa-plugins lib32-alsa-lib lib32-libxcomposite lib32-libxinerama lib32-opencl-icd-loader lib32-gst-plugins-base-libs lib32-sdl2 libgphoto2
```
## Install Noto Fonts

## How to chroot into the system when you inevitably mess up

```
sudo mount /dev/nvme--- /mnt -o subvol=@
sudo mount /dev/nvme--- /mnt/boot
sudo arch-chroot /mnt
```
## Firefox Configuration for kde

Set widget.use-xdg-desktop-portal.file-picker=1 in about:config to make Firefox always use XDG portals for file pickers, which will make it use KDE's file picker instead of the GTK one.

Install the Plasma Integration addon, and turn off Firefox's built-in media controls (which conflict with the ones offered by PBI) by setting media.hardwaremediakeys.enabled to false in about:config. 
