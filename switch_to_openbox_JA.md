#  Openbox最速セットアップ

1. ターミナルで次のコマンドを実行し、`openbox` と `tint2` をインストールします:  
   
```
sudo pacman -S openbox tint2
```

2. リポジトリから設定ファイルをダウンロードします:
   
```
mkdir -p ~/.config/openbox && mkdir -p ~/.config/tint2 && wget https://raw.githubusercontent.com/Vudek/osu-on-linux/refs/heads/main/openbox/autostart -O ~/.config/openbox/autostart && wget https://raw.githubusercontent.com/Vudek/osu-on-linux/refs/heads/main/openbox/rc.xml -O ~/.config/openbox/rc.xml && wget https://raw.githubusercontent.com/Vudek/osu-on-linux/refs/heads/main/tint2/tint2rc -O ~/.config/tint2/tint2rc
```

3. **Win+Shift+E** を押して i3 から Greeter に移動します。
   
5. 右隅の 🔧 をクリックして openbox を選択します。
   
7. `Log In` をクリックします。
