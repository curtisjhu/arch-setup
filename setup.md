# Setup

#### terminal
- alacritty

#### others
- polybar
- ly or lightdm
- feh
- picom
- polybar

```
sudo pacman -S alacritty i3-gaps rofi firefox feh polybar

```

### i3-gaps
```
sudo pacman -S i3-gaps
i3-config-wizard
cp /etc/i3/config ~/.config/i3/config
```
`xprop` is helpful for finding `class_g`

### feh
Check out more [here](https://man.finalrewind.org/1/feh/).
In you ~/.fehbg, which you'll put in your ~/.config/i3/config
```
feh --bg-center [.jpg]
exec_always --no-startup-id $HOME/.fehbg &
```

### polybar
[Check out](https://github.com/adi1090x/polybar-themes)
```
cp /usr/share/doc/polybar/examples/config.ini /home/curtis/.config/polybar/config.ini
```

### picom
Make sure to set alacritty background_opacity=1 if you use with picom
```
cp /etc/xdg/picom.conf /home/curtis/.config/picom/picom.conf
exec_always --no-startup-id picom &
```

### if you choose alacritty
Check out all the color themes [here](https://github.com/eendroroy/alacritty-theme).
```
cp /usr/share/doc/alacritty/example/alacritty.yml /home/curtis/.config/alacritty/alacritty.yml
```

### lightdm
```
sudo pacman -S lightdm lightdm-slick-greeter
vim /etc/lightdm/lightdm.conf
cp /etc/lightdm/lightdm-gtk-greeter.conf /etc/lightdm/lightdm-slick-greeter.conf 
```

background scripts
- .Xresources
- .xinitrc
- .xprofile
- .xmonad
- .vimrc
- .zshrc


### Fonts
- JetBrainsMono
- NerdFonts
```
sudo pacman -S ttf-jetbrains-mono ttf-iosevka-nerd ttf-nerd-fonts-symbols
```
