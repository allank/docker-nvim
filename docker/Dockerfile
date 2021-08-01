FROM alpine:3.14

# Set list of command line tools to install
ARG UTILS="curl git tmux zsh stow"

# Update alpine and install defined UTILS
RUN apk update
RUN apk add --no-cache ${UTILS}

# Install 0.5 branch of neovim
RUN apk add neovim --repository=https://dl-cdn.alpinelinux.org/alpine/edge/community

# Clone my dotfiles
RUN git clone https://github.com/allank/dotconf /root/dotfiles

# Use stow to symlink dotfiles into place
WORKDIR /root/dotfiles
RUN stow --target /root tmux

# Install packer for neovim
RUN git clone https://github.com/wbthomason/packer.nvim /root/.local/share/nvim/site/pack/packer/start/packer.nvim

WORKDIR /data

CMD ["/usr/bin/tmux"]
