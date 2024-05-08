# Poor-man OS setup
Being poor does not mean being useless

## MacOS
```bash
xcode-select --install

# brew https://brew.sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew update && brew upgrade
brew install zsh wget curl git vim neovim tmux make cmake gfortran gcc g++ btop
brew install --cask keepingyouawake
brew install --cask raycast
brew install --cask mactex
brew install --cask alacritty

# nerd font
brew tap homebrew/cask-fonts
brew install font-caskaydia-cove-nerd-font

wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-x86_64.sh
```


## Ubuntu
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y wget curl git vim tmux make cmake gcc g++ powerline fonts-powerline gfortran gnome-tweaks texlive-full

sudo snap refresh
sudo snap install telegram-desktop slack btop
sudo snap install code --classic
sudo snap install nvim --classic
sudo snap install alacritty --classic

wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
```

### font
```bash
mkdir -p "${HOME}/.local/share/fonts/CaskaydiaCoveNerdFont"
curl -OL https://github.com/ryanoasis/nerd-fonts/releases/latest/download/CascadiaCode.zip
unzip CascadiaCode.zip -d CascadiaCode
mv CascadiaCode/*.ttf "${HOME}/.local/share/fonts/CaskaydiaCoveNerdFont"
rm -rf CascadiaCode CascadiaCode.zip

sudo fc-cache -fv
```

### change default terminal to alacritty
```bash
sudo cp start-alacritty /usr/bin/start-alacritty
sudo chown root:root /usr/bin/start-alacritty
sudo chmod --reference=/usr/bin/ls /usr/bin/start-alacritty
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/start-alacritty 50
sudo update-alternatives --config x-terminal-emulator
```


## Things
```bash
# omz plugins
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone --depth=1 https://github.com/zsh-users/zsh-autosuggestions "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions"
gitc lone --depth=1 https://github.com/zsh-users/zsh-syntax-highlighting.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/"zsh-syntax-highlighting
git clone --depth=1 https://github.com/conda-incubator/conda-zsh-completion.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/"conda-zsh-completion
git clone --depth=1 https://github.com/TamCore/autoupdate-oh-my-zsh-plugins "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/autoupdate"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
git clone --depth=1 https://github.com/eza-community/eza.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/eza"

# rust
curl https://sh.rustup.rs -sSf | sh
cargo install --locked cargo-update tree-sitter-cli ripgrep dua-cli eza zoxide zellij bat yazi-fm yazi-cli

# configs
mkdir -p "${HOME}/.config" && cp -r dotconfig/* "${HOME}/.config"
cp dotfiles/.* $HOME
"${HOME}"/miniforge3/bin/mamba init zsh
```


## fonts
I keep it here just for reference: fonts should be installed with the scripts above
* [CascadiaCode](https://github.com/microsoft/cascadia-code)
* [NerdFont (patched version of fonts, required for terminal and tmux theme though you can use it for vscode as well)](https://github.com/ryanoasis/nerd-fonts)
  * For CascadiaCode version:
    * [archive](https://github.com/ryanoasis/nerd-fonts/releases/latest)
    * [repo link](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/CascadiaCode)


## [intel oneapi](https://software.intel.com/content/www/us/en/develop/tools/oneapi/all-toolkits.html)


## Known issues 
* [vscode long delete time on KDE](https://jamezrin.name/fix-visual-studio-code-freezing-when-deleting)
