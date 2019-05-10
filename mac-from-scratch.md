# Steps to Set up a Mac from Scratch

## Getting Started

1. Install all OSX updates, enable dark mode.
2. Install xcode developer tools by running `xcode-select --install`.
3. Unpin all dock items.

## System Preferences and General Config

### General

1. Tick "Use dark menu bar and Dock".
2. Change "Default web browser" to Chrome.
3. Untick "Allow handoff between this Mac and your iCloud devices".

### Desktop & Screen Saver

1. Get a fancy wallpaper! How about from [here](https://alpha.wallhaven.cc)?

### Dock

1. Reduce "Size" slightly.
2. Enable "Magnification" and set it to slightly larger than "Size".
3. Tick "Automatically hide and show the Dock".

### Security & Privacy

#### General

1. Set "Require password" to 1 minute.
2. Set "Allow apps downloaded from" to "App Store and identified developers" (if not already set to this).

#### Privacy

1. Tick "Enable Location Services" (but disable "Siri & Dictation").

### Spotlight

Untick all "Search Results" except for:

- Applications
- Calculator
- Folders
- System preferences

### Keyboard

1. Under "App Shortcuts" add shortcuts for "Toggle Full Screen", "Enter Full Screen" and "Exit Full Screen" as `ctrl+opt+cmd+f`.

### Trackpad

1. Untick "Look up & data detectors".
2. Set "Tracking speed" to 5.

### iCloud

1. Turn everything off except "Find My Mac".

### Bluetooth

1. Click "Turn Bluetooth Off".

### Date & Time

1. Under "Clock", tick "Show date".

## Finder Preferences

1. Open finder, press `cmd+,`.
2. Change "New finder windows show:" to user home directory.
3. Go to "Sidebar", untick "iCloud", "AirDrop", and "Tags".
4. Tick "Pictures" and user home directory.
5. Go to "Advanced", tick "Show all filename extensions".

## Homebrew and Base Installations

1. Open terminal, install Homebrew by running the following (from [here](https://brew.sh)):

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Run the following (_note: installing yarn automatically installs node_):

```
brew install cask
brew install yarn
# have to install with npm due to a bug with vscode
npm i -g standard
brew install diff-so-fancy
brew install watch
brew install tldr
brew install mysql
brew install composer
composer global require "squizlabs/php_codesniffer=*"
echo 'export PATH=$PATH:~/.composer/vendor/bin' >> ~/.zshrc
brew cask install google-chrome
brew cask install iterm2
brew cask install sublime-text
brew cask install visual-studio-code
brew cask install homebrew/cask-versions/sequel-pro-nightly
brew cask install keepassxc
```

3. Install Oh-my-zsh by running the following (from [here](https://github.com/robbyrussell/oh-my-zsh)):

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

4. Install [Fira Code](https://github.com/tonsky/FiraCode).

## Applications Setup and Config

### Chrome

1. Sign in to Chrome to download extensions.

### KeePass and GitHub ssh keys

1. Download KeePass database.
2. Save ssh keys from KeePass database to `~/.ssh`, and make sure permissions are correct by running the following:
   - `chmod 600 ~/.ssh/id_rsa`
   - `chmod 644 ~/.ssh/id_rsa.pub`

### Vim

1. Set up `.vimrc` by running the following (from [here](https://github.com/amix/vimrc/)):

```
curl https://raw.githubusercontent.com/amix/vimrc/master/vimrcs/basic.vim > ~/.vimrc
```

### iTerm

1. Install [shell integration](https://iterm2.com/documentation-shell-integration.html).
2. Open settings, set "Load preferences from a custom folder or URL" to `https://raw.githubusercontent.com/liamjcrewe/personal-config/master/iterm-settings.plist`.

### Oh-my-zsh

1. Edit `~/.zshrc` and set theme to `af-magic`.
2. Edit `~/.zshrc` and set plugins to `(git zsh-syntax-highlighting alias-tips)`.
3. Run the following to install plugins:

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/djui/alias-tips.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/alias-tips
```

### Git

1. Run the following to configure Git:

```
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/gitconfig > ~/.ssh/.gitconfig`
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/gitignore_global > ~/.ssh/.gitignore_global
```

### MySQL

1. Run the following to configure MySQL:

```
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/my.conf > ~/.my.conf
mysql.server restart
mysql -u root -e "ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '';"
mysql.server restart
```

### Sequel Pro

1. Download query editor theme by running `curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/darkside-contrast-modified.spTheme > ~/Documents/darkside-contrast-modified.spTheme`.
2. Open Sequel Pro, add localhost as a favourite.
3. Open Preferences, go to "General", set "MySQL Content Font" to Fira Code Retina 15 pt.
4. Go to "Query Editor", set "Font" to Fira Code Retina 15 pt, tick "Auto uppercase words", untick "Complete with backticks".
5. Import the theme downloaded above (cog icon > "Import Color Theme").

### Sublime

1. Install package manager by pressing `` ctrl+` `` then running the following (from [here](https://packagecontrol.io/installation)):

```
import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

2. Run the following to copy Package Control settings to sublime:

```
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/sublime/Package%20Control.sublime-settings > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/Package\ Control.sublime-settings
```

3. Restart Sublime and wait for packages to be installed.
4. Run the following to copy the [remaining package settings](https://github.com/liamjcrewe/personal-config/tree/master/sublime) to Sublime:

```
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/sublime/Base%20File.sublime-settings > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/Base\ File.sublime-settings
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/sublime/JavaScript%20(Babel).sublime-settings > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/JavaScript\ (Babel).sublime-settings
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/sublime/PHP.sublime-settings > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/PHP.sublime-settings
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/sublime/Preferences.sublime-settings > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/Preferences.sublime-settings
curl https://raw.githubusercontent.com/liamjcrewe/personal-config/master/sublime/SublimeLinter.sublime-settings > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/SublimeLinter.sublime-settings
```

5. Restart Sublime and verify everything is good.

### VSCode

1. Install extension "Settings Sync".
2. Open command palette, run `Sync: Download Settings` to download VSCode settings. You'll need a GitHub token and Gist id `4800a0023156d0548abceaae5d2f941f`.
3. Allow extensions to be installed.
4. Restart VSCode and verify everything is good.
