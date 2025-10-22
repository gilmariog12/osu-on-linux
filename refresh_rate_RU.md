# Для Nvidia GPU

0. Установите пакет `nvidia-settings`, запустив данную команду в терминале:

```
sudo pacman -S nvidia-settings
```

1. Запустите `nvidia-xconfig` для создания `xorg.conf`:

```
sudo nvidia-xconfig
```

2. Запустите `nvidia-settings` от суперпользователя:

```
sudo nvidia-settings
```

3. Перейдите в `X Server Display configuration`:

![](https://vudek.s-ul.eu/MWEWsMzQ)

4. Установите ваше разрешение и частоту обновления:

![](https://vudek.s-ul.eu/YGmgrv8I)

5. Нажмите `Advanced...` и проверьте, что любой из `Composition pipeline` отключен:

6. Нажмите `Save to X configuration file`.

![](https://vudek.s-ul.eu/hTdiJViW)

7. И нажмите `Save`:

8. Теперь вы можете `Quit` из `nvidia-settings`.

# Для любого другого GPU (Nvidia можно настроить и этим методом)

0. Установите `xrandr`, запустив данную команду в терминале:

```
sudo pacman -S xorg-xrandr
```

1. Выполните данную команду в терминале:

```
xrandr
```

2. Найдите ваш выход дисплея (connected):

![](https://vudek.s-ul.eu/RhRvOGbo)

3. Запомните, какой ваш (в моем случае это DP-0):

![](https://vudek.s-ul.eu/OUY56n37)

4. И выполните данную команду в терминале:

```
xrandr --output DP-0 --mode 1920x1080 --rate 144
```

> Измените `DP-0` на ваш выход!

> Измените `--rate 144` на вашу частоту обновления экрана!  

5. Теперь ваш монитор настроен на вашу нативную герцовку!

6. Вы можете настроить автозапуск герцовки при каждом входе в сессию:
   - Добавив эту строку в `.xinitrc`:
   
     ```
     echo "xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.xinitrc
     ```
	 
   - Добавив эту строку в конфиг i3-wm:
   
     ```
     echo "exec_always xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.config/i3/config
     ```
	 
   - Добавив эту строку в конфиг автозапуска openbox:
   
     ```
     echo "xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.config/openbox/autostart
     ```
