# osu-on-linux
osu!低遅延ガイド2025

# Language: [JA](README_JA.md) | [EN](README.md) | [RU](README_RU.md)

# 以前のガイドが誰かによって削除されたので、Githubへ移行することを決めました。

このガイドは安定した動作のWine環境、ドラッグ＆ドロップやその他の設定を含むLinuxでosu!を低遅延で動かすためのガイドです。

![Arch Linux](https://vudek.s-ul.eu/3gOtpcXN) 

まずは [公式サイトからArch Linuxのiso](https://archlinux.org/download/)をダウンロードしてください。

[Ventoy](https://sourceforge.net/projects/ventoy/files/v1.1.07/ventoy-1.1.07-windows.zip/download)をダウンロードし、任意の場所に展開します。

**Ventoy2Disk**を開き、USBドライブを選択して**Install**をクリックします。USBが初期化されることを2回確認します。インストールが完了すると、VENTOY、VENTOYEFIが認識されます。**VENTOY**にArch Linuxのisoをコピーしてください。
# スクリーンショット:
![](https://vudek.s-ul.eu/DarJQ8Ar)

![](https://vudek.s-ul.eu/re0gc5FJ)

![](https://vudek.s-ul.eu/Lyd0u1tp)

![](https://vudek.s-ul.eu/HCHi80g3)

コピーが完了したら、PCを再起動してBIOSを開いて、USBを起動します。
![](https://vudek.s-ul.eu/Jy9WWfeo)

重要:VentoyでArch Linuxのisoを選択したあと、**Boot in grub2 mode**を選択するとArch Linuxのインストールが成功しやすいです。
![](https://vudek.s-ul.eu/IkIYfIwM)

それではArch Linuxをパソコンにインストールしましょう:

1. isoを選択すると、以下のようなArch Linuxの起動画面が出ます。:
   - BIOSの場合:
     
     ![](https://vudek.s-ul.eu/G5wEsEPG)
     
   - UEFIの場合:
     
     ![](https://vudek.s-ul.eu/wrPKhSdP)
   `Arch Linux install medium`を選択し、セットアップがターミナルを起動するまで待ちます。

2. ターミナルが起動すると次のような画面になります。:
   
   ![](https://vudek.s-ul.eu/hPtc7p7w)
   
4. `archinstall`と入力して**Enter**を押すと、セットアップ画面が起動します。
   
   ![](https://vudek.s-ul.eu/qaUvSJxD)
   
6. `Mirrors and repositories`を選択して**Enter**を押すと、メニューが出てきます。:
   
   ![](https://vudek.s-ul.eu/502pegGo)

   もう一度**Enter**を押すとメニュー画面に入り、Arch Linuxミラーの地域を選択できます。素早く検索するには、`/`を押して国名を入力してください。私の場合は、`/Belarus`と入力します。:
   
   ![](https://vudek.s-ul.eu/dCb5wmmK)

   **Enter** キーを押すと前のメニューに戻ります。`Additional repositories` を選択し、**Enter** キーを押してください。:
   ![](https://vudek.s-ul.eu/zTT8vJ6c)

   `multilib`を選択し、**Enter**を押します。、その後**Back**を選択し、**Enter**を押すと、インストールのメインメニューに戻ります。:
   
   ![](https://vudek.s-ul.eu/VcqZHE7Q)

7. `Disk configuration`を選択し、**Enter**キーを押してください:
   
   ![](https://vudek.s-ul.eu/KoClO7ji)

   **Enter**キーを押してください:
   
   ![](https://vudek.s-ul.eu/bINWpLyf)

   ### 警告:本ガイドは別ディスクへのインストール用です。Windowsがインストールされているディスク上でのインストールは行わないでください。

   `Use a best-effort default partition layout` を選択し、ディスクを選択してください:

   ![](https://vudek.s-ul.eu/edO7zAd8)

   Choose `ext4`:
   
   ![](https://vudek.s-ul.eu/5e2BMYQQ)

   ディスクは自動的にパーティション分割されます。:
   
   ![](https://vudek.s-ul.eu/UcU4i24T)

   ディスク容量が64GBから256GBの場合は、次の手順をスキップして6番の段落に進んでください。

   # パーティションを手動でサイズ変更したい場合は、次の手順を実行してください:
   
   再度`Partitioning`を選択し、`Manual Partitioning`に進みます。:
   
   ![](https://vudek.s-ul.eu/ISVikhfK)

   もう一度ディスクを選択してください:

   ![](https://vudek.s-ul.eu/F1rbo5Yd)

   すると、以下のメニューが表示されます。:

   ![](https://vudek.s-ul.eu/SZE5KvwD)

   ラベル`/`の２番目のパーティションを選択し、`Enter`を押すと、次のメニューが表示されます。:
   ![](https://vudek.s-ul.eu/LX0CkWMy)

   `Delete partition`を選択し、**Enter**キーを押します。これで`free`パーティションが作成されました:

   ![](https://vudek.s-ul.eu/4pO26fPB)

    `free`パーティションを選択し、**Enter**キーを押すとメニューが表示されます。そこで新しいパーティションのサイズを選択できます:

   ![](https://vudek.s-ul.eu/egJ2A592)

   私の場合、ルートパーティション `/` をサイズ 20GiB で作成します。

   サイズを入力したら、Enter キーを押して `ext4` ファイルシステムを選択します:

   ![](https://vudek.s-ul.eu/CPcmG1Ey)

   **Enter**キーを押すと、`Mountpoint`メニューが表示されます。最初のパーティションには `/` と入力してください:

   ![](https://vudek.s-ul.eu/jnimdjZ9)

   **Enter**を押すと、ディスクレイアウトが表示された前のメニューに戻ります。空きパーティションの`Size`を覚えておいてください。:

   ![](https://vudek.s-ul.eu/KZq0WUIJ)

   `free` パーティションを選択し、**Enter** キーを押してください:

   ![](https://vudek.s-ul.eu/De8PQchb)

   この場合、私の空きパーティションサイズは19GiBです。あなたの場合は、前の手順で確認した空きパーティションサイズを入力してください:

   ![](https://vudek.s-ul.eu/De8PQchb)

   `ext4`を選択してください。:

   ![](https://vudek.s-ul.eu/iOLjBdDt)

   mountpoint`/home` を選択してください:

   ![](https://vudek.s-ul.eu/Toa1c977)

   **Enter**を押すと、`Disk configuration`に戻ります。:

   ![](https://vudek.s-ul.eu/PYNgs9dT)

   では、この手順を実行すると、ご覧の通り、`/boot`、`/`、`/home` のパーティションが作成されます！
   `確認して終了`を選択し、**Enter**キーを押してください:

   ![](https://vudek.s-ul.eu/oT6qh4qY)

   `Back`を選択すると、インストールのメインメニューに戻ります。:

   ![](https://vudek.s-ul.eu/8yea7R8Y)

8. `Bootloader`に進みます:

   ![](https://vudek.s-ul.eu/9FfnyLbi)

   私の場合、デフォルトのブートローダーとして`grub`が使用されています（仮想環境の設定がレガシーBIOSのせいです）。
   あなたのケースでは、デフォルトで `systemd-boot` が使用されます（UEFI BIOS の場合）、または同じ `grub` がデフォルトで使用されます（レガシー BIOS の場合）。

9. `hostname`に進みます。:

   ![](https://vudek.s-ul.eu/e9Le37VX)

   Enterを押すと、そこに好きなことを何でも書くことができます（制限は１～６３文字）:

   ![](https://vudek.s-ul.eu/zGqqRMo2)

   その後、インストール時のメインメニューにあなたの`hostname`が以下のように表示されます:

   ![](https://vudek.s-ul.eu/GtFqHl2V)

10. `Authentification`に進んで、**Enter**を押します。:

   ![](https://vudek.s-ul.eu/UZ5r8NNW)

   ここで、`Root password` を選択し、**Enter** キーを押すとメニューに入ります。そこで root パスワードを入力できます:

   ![](https://vudek.s-ul.eu/jlRAam5b)

   rootのパスワードを入力したら、**Enter**を押して、確認のためパスワードをもう一度入力してください。:

   ![](https://vudek.s-ul.eu/BSz6wHci)

   Enterキーを押すと、`Authentification`メニューに戻ります。`User account`を選択してください:
   
   ![](https://vudek.s-ul.eu/esdajcmh)

   **Enter** キーを押すと、このメニューに入ります:

   ![](https://vudek.s-ul.eu/vEtZmWaS)

   `Add a user`を選択し、**Enter**を押してください。:

   ![](https://vudek.s-ul.eu/XviyuFGw)

   適当なユーザー名を入力してください。(**admin**と入力することは禁止されています。):

   ![](https://vudek.s-ul.eu/XviyuFGw)

   ![](https://vudek.s-ul.eu/V5QPJBVP)

   次のステップでは、前のステップと同じメニューが表示されます。ユーザーアカウントのパスワードを2回入力してください:

   ![](https://vudek.s-ul.eu/eKws0Kgp)

   ![](https://vudek.s-ul.eu/nwEFZaQE)

   その後、「%user% をスーパーユーザー（sudo）にしますか？」という質問が表示されます。「はい」を選択し、**Enter** キーを押してください:

   ![](https://vudek.s-ul.eu/46Ih9Dbr)

   ![](https://vudek.s-ul.eu/7EKkIGKa)

   変更を確認してください。`Confirm and exit`**Enter**を押してください。:

   ![](https://vudek.s-ul.eu/psXqAifU)

   「戻る」を選択すると、インストールのメインメニューに戻ります:

   ![](https://vudek.s-ul.eu/t7cRFoH3)

   すべてが正しく、rootにパスワードが設定されており、パスワード付きユーザーアカウントとsudo権限がある場合は、次のステップに進んでください。

11. `Profile`に進み、**Enter** キーを押してください。:

   ![](https://vudek.s-ul.eu/X0pBjlEI)

   `Type` を選択し、**Enter** キーを押してください。:

   ![](https://vudek.s-ul.eu/V5uU47cK)

   `Desktop`を選択し**Enter**キーを押してください。:

   ![](https://vudek.s-ul.eu/jDT7Ei0e)

   メニュー画面が表示されます。ここでデスクトップ環境を選択できます。より良いレイテンシーのためには、i3-wm を選択し、**Enter** キーを押してください:

   ![](https://vudek.s-ul.eu/zeyPgvdf)

   `Profile`メニューに戻るので、`Graphics driver`を選択し、**Enter**キーを押してください。:

   ![](https://vudek.s-ul.eu/xlDKHUXe)

   ここでは、お使いのGPUに応じて、お好みのグラフィックドライバを選択できます。

   CheatSheet:

   - **AMD / ATI (open-source)** — AMDGPU全て
   - **All open-source** — このリストのすべてのオープンソースがインストールされます。
   - **Intel (open-source)** — Intel GPU（内蔵またはArc）用。
   - **Nvidia (open kernel module for newer GPU's, Turing+)** — 20xxシリーズ以降の最新Nvidia GPUの場合に選択。
   - **Nvidia (open-source nouveau driver)** — 絶対に選択しないでください！
   - **Nvidia (proprietary)** — 旧世代のNvidia GPU（RTXシリーズ以前）の場合に選択。
   - **VirtualBox (open-source)** — VirtualBoxのインストール用に選択。

   お好みのGPUドライバーを選択したら、**Enter**キーを押してメインメニューに戻ってください:

   ![](https://vudek.s-ul.eu/SWZowNH7)

12. `Applications`に移動し、**Enter**キーを押します:
   
   ![](https://vudek.s-ul.eu/qC7P5QmP)

   `Audio`を選択し、**Enter**キーを押してください:

   ![](https://vudek.s-ul.eu/DbCDZSd9)

   このメニューで `pipewire` を選択し、**Enter** キーを押してください:

   ![](https://vudek.s-ul.eu/8jlmHzI7)

   `Back`を選択し、メインメニューに戻るには、**Enter**キーを押してください:

   ![](https://vudek.s-ul.eu/rr2ogUHt)

13. `Kernels`に移動し、**Enter**キーを押します:
    
    ![](https://vudek.s-ul.eu/85zkonsN)

    スペースキーを押して、`linux`から`x`を削除し、`linux-zen`を選択して再度スペースキーを押し、**Enter**キーを押してください:

    ![](https://vudek.s-ul.eu/8cAKQxVy)

    ![](https://vudek.s-ul.eu/bm0l2CBH)

14. `Network configuration`に移動し、**Enter**キーを押してください:

    ![](https://vudek.s-ul.eu/NeLf6hxX)

    `Copy ISO network configuration to installation` を選択し、**Enter** キーを押します:

    ![](https://vudek.s-ul.eu/AwFoPNb4)

15. `Additional packages`に移動し、**Enter**キーを押してください:

    ![](https://vudek.s-ul.eu/ctZvGaJE)

    簡単にパッケージを選択するには、以下の手順を実行してください:
    - `/`を押す;
    - パッケージ名を入力;
    - キーボードの矢印キーでパッケージを選択;
    - **Esc**を押す;
    - **Spacebar**を押す.

    手順の実演:

    ![](https://vudek.s-ul.eu/yTbTuWQ4)

    では、以下のパッケージを選択してください:

    `git chromium winetricks lib32-gnutls lib32-libxcomposite kitty rofi nemo flameshot`

    Nvidia GPUをお持ちの場合は、追加でこのパッケージを選択してください: `lib32-nvidia-utils`

    ![](https://vudek.s-ul.eu/dUgvjOxj)

    必要なパッケージをすべて選択したら、**Enter**キーを押してください。すべてが以下のようになります:

    ![](https://vudek.s-ul.eu/TPDK3UYi)

16. `Timezone`に移動し、**Enter**キーを押してください:

    ![](https://vudek.s-ul.eu/SKVECPHx)

    ここで、`/`を押して検索し、タイムゾーンを選択してください（私の場合は `/Minsk` です):

    ![](https://vudek.s-ul.eu/p5NyW2Zb)

    **Enter**を押してメインメニューに戻ります:

    ![](https://vudek.s-ul.eu/XTJw85OJ)

17. `Install`に進み、**Enter**を押します。:

    ![](https://vudek.s-ul.eu/PcK0t7fP)

    ![](https://vudek.s-ul.eu/dPeZLvk3)

    「指定された構成が適用されます。続行しますか？」という質問が表示されます。`Yes` を選択し、**Enter** キーを押してください:

    ![](https://vudek.s-ul.eu/4drvTzi9)

    ![](https://vudek.s-ul.eu/2rzHyRgC)

    いよいよインストールが開始されます。この段階では、インターネット接続速度次第で時間がかかるため、くつろいだりお茶を淹れたりしてお待ちください。お待ちの間、私のSNSをフォローしてくださいね🥺:
      - [Telegram](https://t.me/vudekosu)
      - [X (Twitter)](https://twitter.com/vudek_)
      - [YouTube](https://youtube.com/c/vudek)
      - [Twitch](https://twitch.tv/vudek_)
    
    インストールが終了すると、このメニューが表示されます:

    ![](https://vudek.s-ul.eu/WBCh8eL7)

    `Reboot system`を選択し、**Enter**キーを押します。再起動中にUSBフラッシュドライブを取り外し、BIOS設定画面でArch Linuxへの起動を選択してください。

# ついに、ARCH LINUXが、起動しました！！！！！！！！！！！！！！
  ArchLinuxがロードされると、このログイン画面が表示されます。:

  ![](https://vudek.s-ul.eu/DFy8EJau)

  パスワードを入力し、Enterキーを押すと、i3-wmデスクトップ環境に入ります。

  初回ログイン時、i3-wmは基本設定の生成について尋ねます。Enterキーを2回押してください。

  ![](https://vudek.s-ul.eu/9fE7eW7j)

  ![](https://vudek.s-ul.eu/4fPehK4T)

  これ以降、基本的な i3-wm の設定が `~/.config/i3/config`に書き込まれます。これでキーバインドを使用できるようになります。 

  **Win+D**を押し、`kitty`と入力して**Enter**を押します。 
  **Win+2**を押してデスクトップ2に切り替わります。
  もう一度**Win+D**を押すと、`chromium`と入力して**Enter**を押します。:

  ![](https://vudek.s-ul.eu/rJW33xBm)

  ブラウザで[this webpage](https://github.com/Vudek/osu-on-linux)を開き、以下をコピーしてください:

  ```
  wget http://puu.sh/KClvp/49aa8dee55 -O ~/.config/i3/config
  ```

  Win+1を押して最初のデスクトップに戻り、**Shift+Insert**を押すか、マウスの中ボタンをクリックしてコピーした行をキティターミナルに貼り付け、**Enter**を押します。
  Type:

  ```
  i3 reload
  ```

  **Enter**を押すと、以下のキーバインドが適用された高度なi3-wm設定が適用されます。:
  - **Win+R**を押すとメニューが表示されます。
  - **Win+Enter**を押すとレガシーメニューが表示されます。
  - デスクトップを変更するには**Win+1**, **Win+2**, ... **Win+0**を押します。
  - アクティブなデスクトップを切り替えるには、**Ctrl+Win+⬅** または **Ctrl+Win+⮕** を押します。
  - アクティブなウィンドウをほかのデスクトップに移動するには **Win+Shift+1**, **Win+Shift+2**, ... **Win+Shift+0**を押します。
  - ソフトを閉じるには**Win+Shift+Q**を押します。
  - 🩼 ＊Alt+Tabのようにデスクトップを切り替えるには*Win+Tab**を押します。
  - ターミナルを開くには**Win+Enter**を押します、

  そしたら、ターミナルを開いて、以下のコマンドを打ちます。:

  ```
  sudo pacman -S pipewire-media-session
  ```

  その後、**Enter**キーを押すと、パスワードの入力を求められます。

  警告:パスワードはターミナルに表示されません！

  Y を入力し、Enter キーを押して `removing wireplumber` を実行します。
  Y を入力し、もう一度 Enter キーを押して `pipewire-media-session` をインストールします。

  ![](https://vudek.s-ul.eu/DfPgb6tR)

  この手順の後、wine-1x を wine-9.22-1 にダウングレードする必要があります。ターミナルに以下をコピーしてください:

  ```
  mkdir -p ~/Downloads && cd ~/Downloads && wget https://github.com/Vudek/wine-9.22-1-x86_64/releases/download/wine-9.22-1-x86_64.pkg.tar.zst/wine-9.22-1-x86_64.pkg.tar.zst && sudo pacman -U wine-9.22-1-x86_64.pkg.tar.zst && cd
  ```

  **Enter**を押してください。パッケージのダウングレードを確認するプロンプトが表示されます。Yと入力し、Enterキーを押してください。

  ![](https://vudek.s-ul.eu/Rl5xVht4)

  Wineは完全に9.22-1にダウングレードされました。これでwineprefixを作成し、osu!をインストールできます。

# osu! installation

  始める前に、これをターミナルにコピーして**Enter**キーを押してください。すべてのパッケージがインストールされていることを確認するためです:

  ```
  sudo pacman -S giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls \
mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error \
lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo \
sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama \
ncurses lib32-ncurses opencl-icd-loader lib32-opencl-icd-loader libxslt lib32-libxslt libva lib32-libva gtk3 \
lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader
  ```

  その後、osu!のためのwineprefixを作ります。以下のコマンドをターミナルに貼り付けてください。:

  ```
  WINEARCH=win32 WINEPREFIX=~/.wineosu winetricks dotnet45 cjkfonts gdiplus
  ```

  その後**Enter**を押します。**Mono** のインストール画面が表示されたら、**キャンセル** を押してください。

  次のインストールは、このステップではWindowsっぽくなります。チェックマークでインストールに同意し、次へを押して待ちます。dotnetのインストール後、**後で再起動**を押してください。

  そして、すべてが終わったら、osu!のフォルダーを作ります。以下のコマンドをターミナルに貼り付けて**Enter**を押します。:

  ```
  mkdir ~/osu/
  ```

  osu!をダウンロード:

  ```
  wget --output-document ~/osu/osu\!.exe https://m1.ppy.sh/r/osu\!install.exe
  ```

  binフォルダーを作成:

  ```
  mkdir -p ~/.local/bin
  ```

  開始スクリプトを作成:

  ```
  nano ~/.local/bin/osu
  ```

  スタートスクリプトを貼り付けます。:

  ```
  #!/usr/bin/env bash
  #export PATH="/opt/wine-osu/bin:$PATH" #custom WINE ArchLinux
  export PATH="$HOME/wine-osu/bin:$PATH" #custom WINE new

  export WINEARCH=win32
  export WINEPREFIX="$HOME/.wineosu"
  export WINEFSYNC=1
  export WINE_DISABLE_VK_CHILD_WINDOW_RENDERING_HACK=1

  export STAGING_AUDIO_DURATION=13333
  export STAGING_AUDIO_PERIOD=13333

  export vblank_mode=0 #For AMD, Intel and others

  #export __GL_SYNC_TO_VBLANK=0 #For NVIDIA 
  export __GL_MaxFramesAllowed=0
  export __GL_THREADED_OPTIMIZATIONS=1 


  cd ~/osu
  #wine --version
  wine "osu!.exe"
  ```

  Ctrl+Oを押して保存、Ctrl+Xで終了します。

  終了するスクリプトを作成します:

  ```
  nano ~/.local/bin/osukill
  ```

  終了するスクリプトを貼り付けます:

  ```
  #!/usr/bin/env bash
  #export PATH="/opt/wine-osu/bin:$PATH" #custom WINE ArchLinux
  export PATH="$HOME/wine-osu/bin:$PATH" #custom WINE new

  export WINEARCH=win32
  export WINEPREFIX="$HOME/.wineosu"

  wineserver -k
  ```

  Ctrl+Oを押して保存、Ctrl+Xで終了します。

  以下のコマンドをターミナルに貼り付けます:

  ```
  chmod +x ~/.local/bin/osu && chmod +x ~/.local/bin/osukill
  ```

  これでスクリプトとキルスクリプトは実行可能になりました！

  > Nvidiaユーザー - #を削除\
  > ```export __GL_SYNC_TO_VBLANK=0 #For NVIDIA``` \
  > そして以下の行の最初に#を追加 \
  > ```export vblank_mode=0 #For AMD, Intel and others``` 

  .desktopファイルを作成します。つまりosu!はアプリケーションランチャーが表示されます。:

  ```
  nano ~/.local/share/applications/osu.desktop
  ```

  以下を貼り付けます:

  ```
  [Desktop Entry]
  Type=Application
  Comment=osu!
  Exec=.local/bin/osu
  GenericName=osu!
  Name=osu!
  StartupNotify=true
  ```
  Ctrl+Oを押して保存、Ctrl+Xで終了します。

  このファイルを実行可能にするには、これをターミナルにコピーして**Enter**キーを押してください:

  ```chmod +x ~/.local/share/applications/osu.desktop```

  これで、あなたの osu.desktop アプリケーションが実行可能になりました！
  
  その後、これをターミナルにコピー＆ペーストしてください

  ```
  cd ~/Downloads && wget http://puu.sh/KAnxf/6e2425cc8f.xz -O wine-osu-7.15.2-x86_64.tar.xz && tar -xvf wine-osu-7.15.2-x86_64.tar.xz && cp -r wine-osu ~/wine-osu && rm -rf wine-osu && cd
  ```

  Pipewireを設定しましょう。以下の内容をターミナルにコピー＆ペーストし、**Enter**キーを押してください:

  ```
  cd && mkdir -p ~/.config/pipewire && cp -r /usr/share/pipewire/* ~/.config/pipewire/ && wget http://puu.sh/KBIwU/04254728f0.conf -O ~/.config/pipewire/pipewire.conf && wget http://puu.sh/KBIx1/120c9f7b39.conf -O ~/.config/pipewire/pipewire-pulse.conf && wget http://puu.sh/KBIx9/f8b9cdc5ce.conf -O ~/.config/pipewire/media-session.d/alsa-monitor.conf
  ```

  その後、変更を適用するためにオーディオサーバーを再起動しましょう。以下の内容をターミナルにコピーし、**Enter**キーを押してください:
  
  ```
  systemctl --user restart pipewire.service pipewire.socket pipewire-media-session.service pipewire-pulse.service pipewire-pulse.socket
  ```

  Pipewireの設定が完了しました！

  ターミナルを閉じるには、**Win+Shift+Q**を押します。

  > お使いのpcが高性能なら、 [私のTelegramチャンネルでPipewireのオーディオレイテンシーを最小限に抑える高度なガイドを読んでください](https://t.me/vudekosu/596).

# さあ、osu!を起動しよう！

  Win+Rキーを押すとアプリケーション一覧が開きます。osu! と入力し、**Enter**キーを押してください:

  ![](https://vudek.s-ul.eu/v742bcLJ)

  低遅延オーディオを楽しみたい場合は、`オーディオ互換モード`のチェックボックスが有効になっていることを確認してください。
  
# リフレッシュレートの変更方法

  ![これを見てください](refresh_rate_JA.md)

# OpenTabletDriverのインストール方法 

  WinキーとEnterキーを同時に押してターミナルを開きます。
ターミナルに以下をコピーしてください:

  ```
  sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay-bin.git && cd yay-bin && makepkg -si && yay -S opentabletdriver osu-handler osu-mime
  ```

  > 「クリーンビルドするパッケージ」とプロンプトが表示されたら、ターミナルに `N` と入力し、**Enter** キーを押してください。

  > 「表示する差異」を尋ねられたら、ターミナルに `N` と入力し、**Enter** キーを押してください。
  
  このコマンドは `yay`、`opentabletdriver`、`osu-handler`、および `osu-mime` をインストールします

  OTDのインストール後、以下のコマンドをターミナルにコピー＆ペーストしてください:

  ```
  echo "blacklist wacom" | sudo tee -a /etc/modprobe.d/blacklist.conf
  ```

  ```
  sudo rmmod wacom
  ```

  ```
  echo "blacklist hid_uclogic" | sudo tee -a /etc/modprobe.d/blacklist.conf
  ```

  ```
  sudo rmmod hid_uclogic
  ```

  ```
  systemctl --user daemon-reload
  ```

  ```
  systemctl --user enable opentabletdriver --now
  ```

  ```
  sudo udevadm control --reload-rules && sudo udevadm trigger
  ```
  
  ```
  systemctl --user start opentabletdriver --now
  ```

  `MODULE ISN'T LOADED`のようなエラーが表示されても、無視してください。

   OTDを開きましょう:

  - Win+3 を押してデスクトップを切り替える
  - Win+R を押してアプリケーション一覧を開く
  - OpenTabletDriver を検索する
  - **Enter** キーを押す

  するとOTDが開きます！

  エリアとフィルターを設定し、Save/Applyをクリック。**Ctrl+Q** または Win+Shift+Q で GUI を閉じます。

  **Win+1**を押してデスクトップを1番に変更してください。これでosu!がプレイできます！！

  > `マウスローインプット(生入力値)を使う`が無効になっていることを確認してください

  > `osu!のウィンドウ内で必ずローインプットを有効にします。`がオンになっていることを確認してください。

# キーボードレイアウトを変更する方法

  Depends on which languages do you want.

  まず、ターミナルを開いて次のコマンドを入力してください:
  
  ```
  nano ~/.config/i3/config
  ```

  ファイルの一番下の行に次の設定があります:
  
  ```
  exec --no-startup-id "setxkbmap -layout us -option grp:alt_shift_toggle"
  ```

  ここで、us の後に自分が使いたい言語コードを追加します。:

  ```
  exec --no-startup-id "setxkbmap -layout us,jp -option grp:alt_shift_toggle"
  ```

  Ctrl+Oを押して保存、Ctrl+Xで終了します。

  > You can also change your keybind for changing layout to `grp:ctrl_shift_toggle` or `grp:caps_toggle` (last is my favourite).

  そしてターミナルに以下のコマンドを打って**Enter**を押します:

  ```
  setxkbmap -layout us,%youraddedlanguage% -option grp:alt_shift_toggle
  ```
  
  すぐに変更が適用されます！

#  ガイドは[Vudek](https://osu.ppy.sh/users/8816345)によって書かれました

  Donate:
  
  BTC - `bc1q29v9rcdzhs8ds35wmlr8a58u0qk3cvaj2wnpvr`
  
  ETH - `0x7BA5a25A669Fb3570EC7C047b978066D309753A2`
  
  USDT (TRC20) - `TTgd8EejwyxzTNbzLpGK7L5gzfRAdXaxjH`
  
  USDT (ERC20) - `0x7BA5a25A669Fb3570EC7C047b978066D309753A2`
 

meow :3 


    
