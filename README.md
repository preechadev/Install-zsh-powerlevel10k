# Howto install Zsh, Oh-my-zsh, powerlevel10k and zsh plugins on Ubuntu

## Install zsh
`sudo apt install zsh -y`

## Install Oh-my-zsh
`sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

## Download and install necessary fonts
```
# Download fonts
mkdir -p ~/.fonts && cd ~/.fonts
curl -LO https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf
curl -LO https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf
curl -LO https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf
curl -LO https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf

# Install fonts
command fc-cache || sudo apt install fontconfig -y
fc-cache -f -v
```
## Download powerlevel10k theme
`git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`

## Download zsh-z zsh-autosuggestions zsh-syntax-highlighting plugin
```
git clone https://github.com/agkozak/zsh-z $ZSH_CUSTOM/plugins/zsh-z
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
## Set theme and plugins
* Set `ZSH_THEME="powerlevel10k/powerlevel10k"` to `~/.zshrc`

  `sed -i 's|^ZSH_THEME=.*|ZSH_THEME="powerlevel10k/powerlevel10k"|g' ~/.zshrc`

* Set `plugins=(git zsh-z zsh-autosuggestions zsh-syntax-highlighting)` to `~/.zshrc`

  `sed -i 's|^plugins=.*|plugins=(git zsh-z zsh-autosuggestions zsh-syntax-highlighting)|g' ~/.zshrc`

## Initialze the wizard for Powerlevel10k prompt
source ~/.zshrc

### Lastly, link below is how to install this on MacOS
https://www.josean.com/posts/terminal-setup
