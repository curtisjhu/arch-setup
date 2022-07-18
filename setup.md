# Setup

#### terminal
- alacritty
- xterm
- urxvt

#### others
- polybar or xmobar
- ly or lightdm
- font awesome 5 
- feh
- python-pywal
- picom
- polybar

```
sudo pacman -S alacritty i3 rofi firefox feh polybar

```

### feh (or just use pywal)
Check out more [here](https://man.finalrewind.org/1/feh/).
In you ~/.fehbg, which you'll put in your ~/.xinitrc
```
feh --bg-center [.jpg]
```
### pywal
Check out persisting, automatically applying themes [here](https://github.com/dylanaraps/pywal/wiki/Getting-Started)
```
wal -i [~/Wallpapers/img.png]
```
.bashrc/.zshrc
```
(cat ~/.cache/wal/sequences &)
cat ~/.cache/wal/sequences
source ~/.cache/wal/colors-tty.sh
```
.xinitrc
```
wal -R
```

### xmobar
~/.xmobarrc
```
cd .xmonad
touch xmobarrc
xmobar ~/.xmonad/xmobarrc &
```

### polybar
[Check out](https://github.com/adi1090x/polybar-themes)
```
cp /usr/share/doc/polybar/examples/config.ini /home/curtis/.config/polybar/config.ini
```

### picom
Make sure to set background_opacity=1 if you use with picom
```
cp /etc/xdg/picom.conf /home/curtis/.config/picom/picom.conf
pkill picom
picom --experimental-backends -b
picom -f &
```

### if you choose urxvt
```
sudo pacman -S rxvt-unicode
urxvt
```
```
vim ~/.Xresources
xrdb .Xresources
```

### if you choose alacritty
Check out all the color themes [here](https://github.com/eendroroy/alacritty-theme).
```
cp /usr/share/doc/alacritty/example/alacritty.yml /home/curtis/.config/alacritty/alacritty.yml
```

background scripts
- .Xresources
- .xinitrc
- .xprofile
- .xmonad
- .vimrc
- .zshrc
