# Dotfiles

Stuff I set up everytime I change Macbooks.

## Steps

1. Install Firefox Developer Edition

2. Install Bitwarden extension and login

3. Sign in to Firefox

4. Clone dotfiles
    ```
    git clone git@github.com:olivictor/dotfiles.git
    ```

## Manual setup

These are not as easy to automate, so let's do them manually

- Settings > Keyboard > Modifier Keys: Caps Lock → Esc 
- Settings > Keyboard > Modifier Keys: Globe → Caps Lock
- Settings > Keyboard > Input Sources: ⌥ + command + Space to select next source
- Settings > Keyboard > Text input: US International - PC & US 

## Set defaults

https://macos-defaults.com/

```bash
# Increase trackpad/mouse speed to max available via settings
defaults write -g com.apple.mouse.scaling 5.0

# Trackpad: tap to click
defaults -currentHost write -globalDomain com.apple.mouse.tapBehavior -int 1

# Disable press-and-hold for keys in favor of key repeat
defaults write -g ApplePressAndHoldEnabled -bool false

# Show the ~/Library folder.
chflags nohidden ~/Library

# Use top-left corner to start the screen saver
defaults write com.apple.dock "wvous-tl-corner" -int 5
defaults write com.apple.dock "wvous-tl-modifier" -int 0

# Lock after 3 seconds of screensaver
defaults -currentHost write com.apple.screensaver askForPasswordDelay -int 3

# Move Dock to the left
defaults write com.apple.dock "orientation" -string "left"

# Auto-hide Dock quickly
defaults write com.apple.dock "autohide" -bool "true"
defaults write com.apple.dock "autohide-time-modifier" -float "0.3"

# Do not keep recent apps in the Dock
defaults write com.apple.dock "show-recents" -bool "false"

# Adjust icon size
defaults write com.apple.dock tilesize -int 42

# Clear all Dock apps
defaults write com.apple.dock persistent-apps -array

# Display the Bluetooth menu on the top nav
defaults -currentHost write com.apple.controlcenter.plist Bluetooth -int 18

# Disable two-finger swipe to navigate back and forth
defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool FALSE
defaults write org.mozilla.Firefox AppleEnableSwipeNavigateWithScrolls -bool FALSE
sudo defaults write com.apple.Safari AppleEnableSwipeNavigateWithScrolls -bool FALSE

```

## Homebrew Apps

```bash
# Installs homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

brew install --cask visual-studio-code
brew install --cask google-chrome
brew install --cask spotify
brew install --cask raycast
brew install --cask warp
brew install --cask zed

```

## Programming languages

```bash
# ASDF tool version manager
brew install asdf

asdf plugin add ruby && asdf install ruby latest
asdf plugin add python && asdf install python latest
asdf plugin add nodejs && asdf install nodejs latest

# it's not recommended to use ASDF for Rust
brew install rustup
```

## Oh My Zsh

```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

~/.zshrc

```
autoload -U promptinit; promptinit
ZSH_THEME="refined"
alias be='bundle exec'
alias gbpurge='git branch --merged | grep -v "\*" | grep -v "master" | grep -v "develop" | grep -v "staging" | xargs -n 1 git branch -d'
alias rubocopall='git diff origin/master...HEAD --name-only | xargs bundle exec rubocop -a'
```

## Git

```
cp ./gitconfig ~/.gitconfig
git config --global user.email "your_email@gmail.com"
ssh-keygen -t ed25519 -C "your_email@gmail.com"
pbcopy < ~/.ssh/id_ed25519.pub
```

~/.ssh/config
``` 
Host github.com
 Hostname ssh.github.com
 Port 443
 
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

```
ssh -T git@github.com
```

## VSCode

1. Navigate & open this project in VSCode
    ```
    open . -a "Visual Studio Code"
    ```
2. Install recommended extensions