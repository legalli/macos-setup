# Introduction

Step-by-step guide to setup a new MacOS.

# Terminal

## Install terminal

- [Homebrew](https://brew.sh/)
- [Oh my Zsh](https://ohmyz.sh/)
- `brew install --cask iterm2`
- `brew install bat`
- `brew install fzf`
- `brew install tree`
- `brew install jq`


## Configure terminal and command line

- iTerm2 preferences -> Profiles -> Keys → + icon
  - ⌘← : escape sequence OH
  - ⌘→ : escape sequence OF
  - ⌥← : escape sequence b
  - ⌥→ : escape sequence f

- Create ~/.oh-my-zsh/custom/themes/apple-modified.zsh-theme

```script
function toon {
  echo -n ""
}

autoload -Uz vcs_info
zstyle ':vcs_info:*' check-for-changes true
zstyle ':vcs_info:*' unstagedstr '%F{red}*'   # display this when there are unstaged changes
zstyle ':vcs_info:*' stagedstr '%F{yellow}+'  # display this when there are staged changes
zstyle ':vcs_info:*' actionformats '%F{5}[%F{2}%b%F{3}|%F{1}%a%c%u%F{5}]%f '
zstyle ':vcs_info:*' formats '%F{5}[%F{2}%b%c%u%F{5}]%f '
zstyle ':vcs_info:svn:*' branchformat '%b'
zstyle ':vcs_info:svn:*' actionformats '%F{5}[%F{2}%b%F{1}:%F{3}%i%F{3}|%F{1}%a%c%u%F{5}]%f '
zstyle ':vcs_info:svn:*' formats '%F{5}[%F{2}%b%F{1}:%F{3}%i%c%u%F{5}]%f '
zstyle ':vcs_info:*' enable git cvs svn

theme_precmd () {
  vcs_info
}

setopt prompt_subst
PROMPT=$'
%{$fg[green]%}%n@%M:%{$reset_color%}%{$fg[yellow]%}%/ %{$reset_color%}${vcs_info_msg_0_}%{$reset_color%}\
%{$fg[green]%}$(toon) %{$reset_color%}'

autoload -U add-zsh-hook
add-zsh-hook precmd theme_precmd
```

- Modify `.zshrc`

``` script
ZSH_THEME="apple-modified"
```

- Add to `.zshrc`

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

- Create `.bashprofile`

``` shell
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

- Create `.bashrc`

``` script
alias ll='ls -laG'
alias python=python3
alias pip=pip3

# Set up fzf key bindings and fuzzy completion
source <(fzf --zsh)

export PATH=/opt/homebrew/bin:$PATH
```


# Utilities

- [Bitwarden](https://bitwarden.com/)
- `brew install --cask rectangle`
- `brew install --cask hiddenbar`
- `brew install --cask alt-tab`
- `brew install --cask obsidian`


# CLI

- `brew install bash`
- `echo "/opt/homebrew/bin/bash" | sudo tee -a /etc/shells`
- `brew install awscli`
- `brew install docker`
- `brew install kubernetes-cli`


# Confluent-specific CLI

- `brew install --cask confluent-cli`
- `brew tap common-fate/granted` [Getting Started](https://docs.commonfate.io/granted/getting-started)
- `brew install granted`


# Coding

- `brew install --cask jetbrains-toolbox`
- `brew install --cask visual-studio-code`
- `brew install --cask dbeaver-community`
- `brew install git`
- `brew install gh`
- `brew tap hashicorp/tap && brew install hashicorp/tap/terraform`
- `curl -s "https://get.sdkman.io" | bash`
- `brew install --cask postman`

## Python

- `brew install python`
- `curl -LsSf https://astral.sh/uv/install.sh | sh`


# Personal

- `brew install --cask spotify`
- `brew install --cask whatsapp`
- `brew install --cask telegram`


# Configure behavior

- Setup key repetition
  - `defaults write -g ApplePressAndHoldEnabled -bool false`
- Setup redo
  - System settings --> Keyboard --> Keyboard Shortcuts --> App Shortcuts --> + --> All Applications
  - Menu Title: `Redo`
  - Keyboard Shortcut: ⌘Y
- Add separation in the Dock
  - `defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'; killall Dock`
  - `defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="small-spacer-tile";}'; killall Dock`