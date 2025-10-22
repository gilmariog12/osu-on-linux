# For Nvidia

0. Install package `nvidia-settings`:

```
sudo pacman -S nvidia-settings
```

1. Run `nvidia-xconfig` to create `xorg.conf`:

```
sudo nvidia-xconfig
```

2. Run `nvidia-settings` as superuser:

```
sudo nvidia-settings
```

3. Go to `X Server Display configuration`:

![](https://vudek.s-ul.eu/MWEWsMzQ)

4. Set your resolution and refresh rate:

![](https://vudek.s-ul.eu/YGmgrv8I)

5. Click `Advanced...` and check that any of `Composition pipeline` is disabled:

6. Click `Save tp X configuration file`.

![](https://vudek.s-ul.eu/hTdiJViW)

7. And click `Save`:

8. Now you can `Quit` from `nvidia-settings`.

# For any other GPU (Nvidia can be configured by this way too)

0. Install `xrandr` by executing this command in terminal:

```
sudo pacman -S xorg-xrandr
```
1. After install, run it:
```
xrandr
```
2. Find your display output (connected):

![](https://vudek.s-ul.eu/RhRvOGbo)

3. Remember which one is yours (in my case it's DP-0):

![](https://vudek.s-ul.eu/OUY56n37)

4. And run this command in terminal:

```
xrandr --output DP-0 --mode 1920x1080 --rate 144
```

> Change `DP-0` to your output!

> Change `--rate 144` to your refresh rate!  

5. Now you have your native refresh rate in Linux!

6. You can autostart this at every entry of session:
   - By adding this line to `.xinitrc`:
     ```
     echo "xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.xinitrc
     ```
   - By adding this line to i3-wm config:
     ```
     echo "exec_always xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.config/i3/config
     ```
   - By adding this line to openbox autostart config:
     ```
     echo "xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.config/openbox/autostart
     ```
