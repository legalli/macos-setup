# Introduction

Step-by-step guide to setup a new MacOS.

# Terminal

## Install terminal

- Install [Homebrew](https://brew.sh/)
- Install [Oh my Zsh](https://ohmyz.sh/)
- Run
```script
brew install --cask iterm2
brew install bat fzf tree jq bash`
echo "/opt/homebrew/bin/bash" | sudo tee -a /etc/shells
```


## Configure terminal and command line

- iTerm2 preferences -> Profiles -> Keys → + icon
  - ⌘← : escape sequence OH
  - ⌘→ : escape sequence OF
  - ⌥← : escape sequence b
  - ⌥→ : escape sequence f

``` script
cp apple-modified.zsh-theme ~/.oh-my-zsh/custom/themes/apple-modified.zsh-theme
```

### `.zshrc`

- Modify

``` script
ZSH_THEME="apple-modified"
```

- Add

``` script
##########################################
# Personal configuration - Begin
##########################################
if [ -f ~/.bash_profile ]; then
    . ~/.bash_profile;
fi
##########################################
# Personal configuration - End
##########################################
```

### `.bashprofile`

``` shell
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

### `.bashrc`

``` script
alias ll='ls -laG'
alias python=python3
alias pip=pip3

# Set up fzf key bindings and fuzzy completion
source <(fzf --zsh)

export PATH=/opt/homebrew/bin:$PATH
```


# Utilities

- Install [Bitwarden](https://bitwarden.com/)
- Run
``` script
brew install --cask rectangle obsidian
```


# Virtualization

``` script
brew install docker kubernetes-cli helm minikube
```


# Confluent-specific CLI

``` script
brew install --cask confluent-cli
brew tap common-fate/granted
brew install granted
```
[Getting started with granted](https://docs.commonfate.io/granted/getting-started)


# Coding

``` script
brew install --cask visual-studio-code dbeaver-community postman
brew install git gh
brew tap hashicorp/tap && brew install hashicorp/tap/terraform
```

## Python

``` script
brew install python
curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Java

``` script
brew install --cask jetbrains-toolbox
curl -s "https://get.sdkman.io" | bash
```


# Personal

``` script
brew install --cask spotify whatsapp telegram
```


# Configure behavior

- Setup key repetition
  - `defaults write -g ApplePressAndHoldEnabled -bool false`
- Setup redo
  - System settings --> Keyboard --> Keyboard Shortcuts --> App Shortcuts --> + --> All Applications
  - Menu Title: `Redo`
  - Keyboard Shortcut: ⌘Y
- Add separation in the Dock

``` script
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'; killall Dock
 defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="small-spacer-tile";}'; killall Dock
 ```