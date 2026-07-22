# Introduction

Step-by-step guide to setup a new MacOS.

# Terminal

## Install software

- [Homebrew](https://brew.sh/)
- [Oh my Zsh](https://ohmyz.sh/)
- `brew install --cask iterm2`
- `brew install bat`
- `brew install fzf`
- `brew install tree`
- `brew install jq`

## Configure terminal

- iTerm2 preferences -> Profiles -> Keys → + icon
  - ⌘← : escape sequence OH
  - ⌘→ : escape sequence OF
  - ⌥← : escape sequence b
  - ⌥→ : escape sequence f

## Configure command line

Create ~/.oh-my-zsh/custom/themes/apple-modified.zsh-theme

Modify `.zshrc`

``` script
ZSH_THEME="apple-modified"
```

Add to `.zshrc`

``` script
##########################################
# Personal configuration - Begin
##########################################
if [ -f ~/.bash_profile ]; then
    . ~/.bash_profile;
fi

# Set up fzf key bindings and fuzzy completion
source <(fzf --zsh)

alias python=python3
alias pip=pip3
##########################################
# Personal configuration - End
##########################################
```

Create `.bashprofile`

``` shell
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

Create `.bashrc`

``` script
alias ll='ls -laG'
```

# Utilities

- [Bitwarden](https://bitwarden.com/)
- `brew install --cask rectangle`
- `brew install --cask hiddenbar`
- `brew install --cask alt-tab`

# CLI

- `brew install awscli`
- `brew install docker`
- `brew install kubernetes-cli`

# Confluent-specific CLI

- `brew install --cask confluent-cli`
- `brew tap common-fate/granted` [Getting Started](https://docs.commonfate.io/granted/getting-started)
- `brew install granted`

# Coding

- `brew install docker`
- `brew install --cask jetbrains-toolbox`
- `brew install --cask visual-studio-code`
- `brew install uv python`
- `brew install --cask dbeaver-community`
- `brew install git`
- `brew install gh`
- `brew install terraform`
- `curl -s "https://get.sdkman.io" | bash`
- `brew install --cask postman`

# Personal

- `brew install --cask spotify`
- `brew install --cask whatsapp`
- `brew install --cask telegram`
