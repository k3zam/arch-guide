# Arch Install
Personal guide for stuff to do after settng up arch.
# Table of Contents

## Enable Network and Bluetooth

### Enables Network
```systemctl enable NetworkManager --now #enable networking```

### Enables Bluetooth
```systemctl enable bluetooth.service --now #enable networking```

## Install Yakuake
```sudo pacman -S yakuake```

## Enable thumbnails for video
```bash
yay kdegraphics-thumbnailers #thumbnails
yay ffmpegthumbs #thumbnail
```

Enable thumbnail plugins in Dolphin and Settings Manager 
