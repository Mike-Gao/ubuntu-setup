# Mike's Ubuntu Setup Scripts

### Packages to Install
```
sudo apt-get update
sudo apt autoremove
sydo apt install python3
sudo apt install python-is-python3
sudo apt install python3-pip
sudo apt install curl clang neovim git gcc
sudo apt install ubuntu-restricted-extras
sudo apt install openjdk-14-jdk
sudo apt install emacs
sudo apt install dino-im vim
sudo apt install language-pack-zh*
sudo apt install evolution evolution-ews
sudo apt install seahorse-nautilus
sudo apt install gnome-boxes
sudo apt install mpv
sudo apt install celluloid
sudo snap install lxd
sudo snap install meshlab
sudo snap install foliate
sudo snap install discord
sudo snap install simplenote
sudo snap install gimp
sudo snap install inkscape
sudo snap install blender
sudo snap install valgrind --classic
sudo snap install sublime-text --classic
sudo snap install pycharm-professional --classic
sudo snap install clion --classic
sudo snap install intellij-idea-ultimate --classic
git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
```
#### Non-Official
```
sudo snap installzoom-client
sudo apt install alsa-ucm-conf
```
#### Python Stuff
````
python -m pip install ptpython
python -m pip install scipy matplotlib virtualenv
python -m pip install torch torchvision
````
#### Signal
```
curl -s https://updates.signal.org/desktop/apt/keys.asc | sudo apt-key add -
echo "deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main" | sudo tee -a /etc/apt/sources.list.d/signal-xenial.list
sudo apt update && sudo apt install signal-desktop
```
#### Discord
```
snap connect discord:process-control
snap connect discord:system-observe
snap connect discord:unity7 :unity7
```
#### Keybase
```
curl --remote-name https://prerelease.keybase.io/keybase_amd64.deb
sudo apt install ./keybase_amd64.deb
run_keybase
```
#### Typora
````
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
sudo apt-get install typora
````
#### Matlab
```
sudo apt install install matlab-support
```
#### Shell Stuff
```
sudo apt install fonts-powerline
```
#### Vulkan Stuff
````
sudo apt install vulkan-utils
wget -qO - https://packages.lunarg.com/lunarg-signing-key-pub.asc | sudo apt-key add -
sudo apt update
sudo apt install vulkan-sdk
sudo wget -qO /etc/apt/sources.list.d/lunarg-vulkan-1.2.148-focal.list https://packages.lunarg.com/vulkan/1.2.148/lunarg-vulkan-1.2.148-focal.list
sudo apt-get update
sudo apt install libvulkan1 libvulkan1:i386
sudo apt install libvulkan-dev
````
#### GStreamer
````
apt-get install libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
````
### Disable Grub Screen
##### **`/etc/default/grub`**
```apacheconf
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_DISABLE_OS_PROBER=true
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

```
sudo gedit /etc/default/grub
sudo update-grub
```

### Pinyin Input
```
sudo apt-get install ibus-rime
ibus restart
ibus engine rime
```

### Configure Swap
```
sudo swapoff -a
sudo fallocate -l 8G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo gedit /etc/fstab
```

### Preferring Chinese Fonts to Japanese Fonts
```
sudo apt install ttf-wqy-zenhei ttf-wqy-microhei fonts-arphic-ukai fonts-arphic-uming
sudo fc-cache -f -v
```
##### **`/etc/fonts/conf.d/64-language-selector-prefer.conf`**
```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Noto Sans CJK SC</family>
			<family>Noto Sans CJK TC</family>
			<family>Noto Sans CJK HK</family>
			<family>Noto Sans CJK JP</family>
			<family>Noto Sans CJK KR</family>
			<family>Lohit Devanagari</family>
		</prefer>
	</alias>
	<alias>
		<family>serif</family>
		<prefer>
			<family>Noto Serif CJK SC</family>
			<family>Noto Serif CJK TC</family>
			<family>Noto Serif CJK JP</family>
			<family>Noto Serif CJK KR</family>
			<family>Lohit Devanagari</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
			<family>Noto Sans Mono CJK HK</family>
			<family>Noto Sans Mono CJK JP</family>
			<family>Noto Sans Mono CJK KR</family>
		</prefer>
	</alias>
</fontconfig>
```

### Adding Desktop Shortcut
Place `.desktop` in `~/.local/share/applications`
```apacheconf
[Desktop Entry]
Name=Visual Studio Code
Comment=Code Editing. Redefined.
GenericName=Text Editor
Exec=/usr/bin/toolbox run -c main code --no-sandbox --unity-launch %F
Icon=com.visualstudio.code
Type=Application
StartupNotify=false
StartupWMClass=Code
Categories=Utility;TextEditor;Development;IDE;
MimeType=text/plain;inode/directory;
Actions=new-empty-window;
Keywords=vscode;

[Desktop Action new-empty-window]
Name=New Empty Window
Exec=/usr/bin/toolbox run -c main code --no-sandbox --new-window %F
Icon=com.visualstudio.code
```

### Configuring Git
```
git config --global core.editor "subl -n -w"
git config --global user.name "Mike Gao"
git config --global user.email "contact@mikegao.net"
git config --global user.signingkey E43CFB9C6B95BE84
git config --global commit.gpgsign true
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=3600'
git config --global core.autocrlf input
git config --global core.excludesfile ~/.gitignore_global
```
### Restart MOK Key Enrollment Process
```
sudo update-secureboot-policy --enroll-key
```
### Properly Remove Stuff
```
sudo apt-get autoremove -o APT::Autoremove::SuggestsImportant=0 --purge
```
### Useful Git Commands
```
find . -type f -size +100M
```
