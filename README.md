# set_a_new_Mac_cleanly
After my Macbook Pro (15-inch, 2018. Please remeber this model, worst model in Macbook Pro series) crash several times, I decided to write down the set up steps about how to make a develop-ready Macbook from a new one.



# Config a clean installed MacOS (10.13 High Sierra)



## Preparation



#### Allow from all developer

```shell
sudo spctl --master-disable
```

#### Command Line Tools (CLT) for Xcode (xcode 10.1 the latest for 10.13 High Sierra): 

`xcode-select --install`

 [developer.apple.com/downloads](https://developer.apple.com/downloads) or [Xcode](https://itunes.apple.com/us/app/xcode/id497799835)



#### Homebrew

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```





## Manually installation

##### Dropbox

##### Jitouch

```
We appreciate all the past support that we received. Please use "free_license": 8718498470dee7ab7eb5b8edbac59edc1fdb6966
```

##### Alfred

```shell
# Sync settings from Dropbox
Alfred Preference --> Advanced --> Set preferences folder --> "~/Dropbox/AppData/Alfred"
```

##### Manico

```shell
https://manico.im/
# Quit Manico
mv ~/Library/Application\ Support/im.manico.Manico ~/Library/Application\ Support/im.manico.Manico.bk
ln -s ~/Dropbox/AppData/Manico/im.manico.Manico ~/Library/Application\ Support/im.manico.Manico
# If everything looks fine
rm -rf ~/Library/Application\ Support/im.manico.Manico.bk
# Else restart Manico and see again
# Remove log folder from dropbox
xattr -w com.dropbox.ignored ~/Dropbox/AppData/Manico/im.manico.Manico/com.microsoft.appcenter
```

##### FiraCode

```shell
# X Download latest builds from https://github.com/tonsky/FiraCode
brew tap homebrew/cask-fonts
brew install --cask font-fira-code
```


##### InsomniaX

```shell
# Install Insomnia X to /Applications
# Download and rename script from https://m4.rkw.io/insomnia_218_patch.sh.txt or ~/Dropbox/Application/Mac/Mac_as_new/insomnia_218_patch.sh
sudo ./insomnia_218_patch.sh --install
```

##### ShiftIt

```shell
# Install the patched one here ~/Dropbox/Application/Mac/Mac_as_new/ShiftIt-1.6.6_patched.zip
```

##### <strike>touch here</strike>

```shell
# Using >touch here ....app.zip
# Go to Application, hold ⌘ and drag app into toolbar

# touch here works bad on 10.14
# use https://github.com/RomanSmolka/finder-new-file instead
```



##### 

##### <strike>Total Finder (Download newer version from website)</strike>

```
License Name: Kevin Kelley
License Key: GAWAE-FBZK3-X4M62-5L9UJ-JLGUL-A6LCG-MBLQT-S9HQC-CRN99-JC7GB-FRFDZ-WCDYZ-DFPRA-5LD2R-CLLM

Total finder works bad on 10.14.
Use XtraFinder instead.
```



#### Karabiner-elements && InputSourceSelector && Keyboard Maestro && Language Inputs

```
brew install --cask karabiner-elements keyboard-maestro google-japanese-ime
```

Install InputSourceSelector-master

```shell
cp /Users/reklanirs/Dropbox/Application/Mac/Input/InputSourceSelector-master.zip ~/Downloads/InputSourceSelector-master.zip
unzip ~/Downloads/InputSourceSelector-master.zip
cd InputSourceSelector-master
make
chmod +x InputSourceSelector
mv InputSourceSelector-master /usr/local/bin/InputSourceSelector
```

Language Inputs

```shell
# Google Japanese Input
https://www.google.co.jp/ime/
# 手心拼音
http://www.xinshuru.com/index.html?p=mac
# 皮肤-->新建--> <黑白> 背景白,普通候选黑,透明度满,高亮候选黑
```

keyboard-maestro

```shell
# keyboard-maestro
# File --> Start Syncing Macros... --> Choose /Users/kanoto/Dropbox/AppData/Keyboard Maestro/Keyboard Maestro Macros.kmsync
```

System shortcuts:

```
Keyboard --> Shortcuts --> Input sources --> Select the previous input source --> ⌘Space
Keyboard --> Shortcuts --> Spotlight --> Show Spotlight search --> ⌥⇧Space
Keyboard --> Shortcuts --> Full Keyboard Access: All controls
```

Karabiner-elements configuration is located at `~/.config/Karabiner`, which should already linked there.

Shortcuts in Karabiner activates InputSourceSelector, which is captured by Keyboard Maestro. Keyboard Maestro then performs Keyboard --> Shortcuts --> Input sources --> Select the previous input source --> ⌘Space twice to switch between previous input method then switch back to refresh the current input method.

##### Microsoft and Adobe bundles

```shell
# Microsoft Office 2019 16.41.zip
# Adobe Acrobat DC v20.012.20041
# Adobe Photoshop 2020 v21.2.2
```



##### Kindle and Calibre

```shell
# Kindle
Use the Kindle(special version).zip
# Calibre
brew install --cask calibre

#Start calibre and choose the Library in Dropbox
Calibre --> Preferences --> Plugins --> Load plugin from file --> DeDRM_tools_6.6.1/DeDRM_calibre_plugin/DeDRM_plugin.zip

Calibre --> Preferences --> Plugins --> Get new plugins --> KindleUnpack
```



##### Dictionary

```shell
# Japanese-dictionary  (Japanese.English.Dictionary.v1.2(Best for Mac).zip)
# source1: https://github.com/Jackson-S/japanese-dictionary

# EBMac
brew install --cask ebmac
```



##### Others

```shell
# Earsafe 1.0.1.dmg (2.0 requires 10.14)
# UninstallPKG 1.1.5 (1.1.8 requires 10.14)
# AirExplorer (See new document for licence)
# Find Any File (Menu --> Hold Option and press register https://apps.tempel.org/FindAnyFile/registered.php)
# Aurora Blu-ray Player-2.19.4
# Blu-ray Player Pro-3.3.19
# Default Folder X 5.5b2
# Jump Desktop 8.5.15
```





## Brew and Brewcask installation

#### zsh and oh-my-zsh

```shell
brew install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
chsh -s $(which zsh)
```

#### Move configs

```shell
mv ~/.zshrc ~/.zshrc.bk
ln -s ~/Dropbox/AppData/Mac/zshrc ~/.zshrc
ln -s ~/Dropbox/AppData/Mac/config ~/.config
```

#### Vim

```shell
brew install vim
# Space Vim
curl -sLf https://spacevim.org/install.sh | bash
```

#### Other brew

```shell
brew install rclone autossh wget curl-openssl node
```





### Other Cask


```shell
# Cask list https://formulae.brew.sh/cask/
brew install --cask typora boostnote iterm2 authy mpv youtube-dl shadowsocksx-ng zotero sourcetree
brew install --cask ifunbox skype zoomus hex-fiend macmediakeyforwarder appcleaner
brew install --cask microsoft-edge firefox bitwarden onyx cheatsheet keycast medibangpaintpro
brew install --cask deluge qbittorrent vnc-viewer

brew install --cask dash
# need licence

brew install --cask istat-menus
# need licence

brew install --cask downie
# need licence

brew install --cask pdf-expert
# need licence

brew install --cask lingon-x
# need licence

brew install --cask daisydisk
# need licence

brew install --cask rar
# Put rarreg.key into ~/.rarreg.key  #As long as suffix is rarreg.key


brew install --cask wechat
curl -o- -L https://omw.limingkai.cn/install.sh | bash -s
#微信和微信小助手插件 https://github.com/MustangYM/WeChatExtension-ForMac

brew install --cask mathpix-snipping-tool
# Scanner App for Math and Science

brew install --cask mounty
# Mounty NTFS
# If it shows "Volumn not remountable", connect it to a windows machine or parallels, powershell into the disk then chkdsk /f, finally safely eject it using the icon in the tray.
```



## Development Configuration

### Python

```shell
brew install python3 
brew install --cask anaconda

conda config --set auto_activate_base false
# Paste the following into zshrc to initialize conda
```

```shell
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/usr/local/anaconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/usr/local/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/usr/local/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/usr/local/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

### Latex

```shell
brew install --cask mactex-no-gui
```



### IDE

#### VS Code

```shell
brew install --cask visual-studio-code
# Then turn on sync with outlook account
```

#### Sublime text

```shell
brew install --cask sublime-text

ln -s "~/Dropbox/AppData/Sublime/User" "~/Library/Application Support/Sublime Text 3/Packages/User"
```









## Other Settings

### Finder

```shell
Preference --> General --> New Finder windows show: Downloads
					 --> Advanced --> When performing a search: Search the Current Folder
```

```
chmod +x ~/Dropbox/Application/Mac/exp/*.exp
cp ~/Dropbox/Application/Mac/exp/*.exp /usr/local/sbin/
```



### App Store Downloads


### Server Settings

```shell
# On local machine
ssh-keygen
# Then copy contents of id_rsa.pub, paste into server ~/.ssh/authorized_keys
```



### eGPU support (10.13 only)

```shell
# https://github.com/mayankk2308/purge-wrangler
# ⌘ + R to recovery mode
csrutil disable
# and
# Disable safe boot

Problem     Black screens/slow performance with eGPU.
Resolution  Use `pmset -a gpuswitch 0` to force iGPU.

Sanitizing system...
System sanitized.
Modifications complete.

Reboot to apply changes.

# Remember to shut down eGPU during reboot!
```



### Windows integration

```shell
# Apple iCloud Notes
# Open and login with trust https://www.icloud.com/notes  in Chrome/Edge
# Click three dots on the right top corner
# Chrome --> More tools --> Create shortcut     Edge: Apps --> Install this site as an APP

# Snapdrop (Transfer files within the local network)
# Open https://snapdrop.net/
# Click the right top corner and install as an app
```





### Remaining issues

Good way to manage python2, python3.7, python3-latest

Carbon Copy Cloner or SuperDuper!

Files in downloads(old mac and time machine) and Other Files