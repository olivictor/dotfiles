# Macbook setup

Stuff I set up everytime I change laptops.
I'm trying to script those as possible.

## Settings

- Increase mouse speed to 80%
- Tap to click
- Bottom right corner for secondary click

## Clone Dotfiles

```
git clone git@github.com:olivictor/dotfiles.git
```

## Homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew update
```

## iTerm2

```
brew install --cask iterm2
```

- Copy [preferences](./iterm2_preferences) to `Library/Application Support/iTerm2/DynamicProfiles`

## Oh My Zsh

```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

~/.zshrc

```
autoload -U promptinit; promptinit
prompt pure
ZSH_THEME="refined"
alias be='bundle exec'
alias gbpurge='git branch --merged | grep -v "\*" | grep -v "master" | grep -v "develop" | grep -v "staging" | xargs -n 1 git branch -d'
alias rubocopall='git diff origin/master...HEAD --name-only | xargs bundle exec rubocop -a'
```

## Git

~/.gitconfig

```
rias = rebase -i --autosquash origin/master
```

## Firefox Developer Edition

https://www.mozilla.org/en-GB/firefox/developer/

## BitWarden

https://bitwarden.com/download/
