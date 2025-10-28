# Nvidiaユーザ

0. `nvidia-settings`をインストール:

```
sudo pacman -S nvidia-settings
```

1. `nvidia-xconfig` を実行して `xorg.conf`を作成します。:

```
sudo nvidia-xconfig
```

2. スーパーユーザーとして `nvidia-settings` を実行してください:

```
sudo nvidia-settings
```

3. `X Server Display configuration` に移動します:

![](https://vudek.s-ul.eu/MWEWsMzQ)

4. あなたの解像度とリフレッシュレートを設定します。:

![](https://vudek.s-ul.eu/YGmgrv8I)

5. `Advanced...` をクリックし、`Composition pipeline`のいずれかが無効になっていることを確認してください：

6. `Save tp X configuration file`をクリックします。.

![](https://vudek.s-ul.eu/hTdiJViW)

7. そして`Save`をクリックします。:

8. これで`nvidia-settings`を終了できます。 

# その他のGPUについて（Nvidiaもこの方法で設定可能です）

0. ターミナルで次のコマンドを実行して `xrandr` をインストールしてください:

```
sudo pacman -S xorg-xrandr
```
1. インストール後、以下のものを実行します。:
```
xrandr
```
2. 接続されているディスプレイ出力を確認してください(connected)：

![](https://vudek.s-ul.eu/RhRvOGbo)

3. どれが自分のものか覚えておいてください (私の場合はDP-0です):

![](https://vudek.s-ul.eu/OUY56n37)

4. ターミナルで次のコマンドを実行してください：

```
xrandr --output DP-0 --mode 1920x1080 --rate 144
```

> `DP-0`を出力先として設定してください

> `--rate 144` を自分のリフレッシュレート合わせてに変更してください！ 

5. これでLinuxでネイティブのリフレッシュレートが利用可能になりました！

6. セッションの起動時に毎回自動で開始できます:
   - `.xinitrc`に次の行を追加することで:
     ```
     echo "xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.xinitrc
     ```
   - i3-wmの設定ファイル(config)に次の行を追加する:
     ```
     echo "exec_always xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.config/i3/config
     ```
   - openboxの自動起動設定(openbox autostart config)にこの行を追加する:
     ```
     echo "xrandr --output DP-0 --mode 1920x1080 --rate 144" >> ~/.config/openbox/autostart
     ```
