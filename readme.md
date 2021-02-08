Steps to bootstrap a new Mac
Install Apple's Command Line Tools, which are prerequisites for Git and Homebrew.
xcode-select --install
Clone repo into new hidden directory.
# Use SSH (if set up)...
git clone git@github.com:alphabravoab/macdotfile.git ~/.dotfiles

# ...or use HTTPS and switch remotes later.
git clone https://github.com/alphabravoab/macdotfile ~/.dotfiles
Create symlinks in the Home directory to the real files in the repo.
# There are better and less manual ways to do this;
# investigate install scripts and bootstrapping tools.

ln -s ~/.dotfiles/.zshrc ~/.zshrc
ln -s ~/.dotfiles/.gitconfig ~/.gitconfig
ln -s ~/.dotfiles/.gitignore_global ~/.gitignore_global
Install Homebrew, followed by the software listed in the Brewfile.
# These could also be in an install script.

# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Then pass in the Brewfile location...
brew bundle --file ~/.dotfiles/Brewfile

# ...or move to the directory first.
cd ~/.dotfiles && brew bundle