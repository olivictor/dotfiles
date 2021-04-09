# Macbook setup

Stuff I set up everytime I change laptops.
I'm trying to script those as possible.

## Settings

- Increase mouse speed to 80%
- Tap to click
- Bottom right corner for secondary click
- Hot corner for screensaver
- Lock after 5 seconds of screensaver

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

```
git config --global user.name "Victor Oliveira"
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

## Firefox Developer Edition

https://www.mozilla.org/en-GB/firefox/developer/

## BitWarden

https://bitwarden.com/download/

## VSCode

```
brew install --cask visual-studio-code
```
Extensions:
- [Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

## Node

```
brew instal node
npm install -g yarn
```
