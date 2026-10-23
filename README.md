# A Minimal Plymouth Boot/Shutdown Splash featuring Arch-tan
| Startup | Shutdown |
| -------------- | --------------- |
| https://github.com/user-attachments/assets/6d227347-ba45-4198-bd1e-e7ffb2eca49e | https://github.com/user-attachments/assets/cf99885d-4371-4041-85bc-a59fca86cfba |

## 🚀 Installation
### Arch Linux (AUR)
The package for this theme is available in the Arch User Repository.
With your AUR helper of choice:
```bash
paru -S plymouth-arch-tan-git
```

Then set arch-tan as your default plymouth theme and rebuild your initramfs if needed:
```bash
sudo plymouth-set-default-theme -R arch-tan
```

### Manual
Clone the repository:
```bash
git clone https://github.com/SSeanin/plymouth-arch-tan
```

Then manually copy the theme files to your theme folder of choice under the plymouth themes directory:
```bash
sudo mkdir -p /usr/share/plymouth/themes/arch-tan && \
cp -r plymouth-arch-tan/* /usr/share/plymouth/themes/arch-tan
```

And of course don't forget to set the theme:
```bash
sudo plymouth-set-default-theme -R arch-tan
```

## 🚨 Problems and Troubleshooting
### Theme appearing for a split second or not appearing at all
Depending on your setup the theme could be passing so fast that you don't see it. This could happen both in bootup and/or shutdown/reboot. You could add a 5s artificial delay after plymouth loads to fully see the animations. For example using service drop-ins:
```bash
sudo systemctl edit plymouth-poweroff.service
```
```conf
[Service]
ExecStartPost=/usr/bin/sleep 5
```
Do this for `plymouth-reboot.service` as well.

### Animation frames missing
Check out the `arch-tan.plymouth` file and make sure that all the paths are correct and available.
I recommend checking [plymouth page on the arch wiki](https://wiki.archlinux.org/title/Plymouth) as it contains some very useful information.
