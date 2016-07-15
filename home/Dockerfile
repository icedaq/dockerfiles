# Container to do some normal shell stuff.
#
# docker run --rm -ti \
#	-v /data/home:/root/home \
#	-v /mnt/nuc:/mnt/nuc -v /home/core/files:/mnt/downloads \
#	--name home \
#	home
#

FROM ubuntu:latest
MAINTAINER Pascal Liniger <pascal.liniger@gmail.com>

# some environment variables
ENV TERM xterm-256color
ENV MC_SKIN=modarin256
ENV GOPATH=/root/home/go

# install some software we need
RUN apt-get update && apt-get upgrade -y \
	&& apt-get install -y vim curl git \
	tmux mc golang zsh docker.io gocode

# Change default shell to zsh.
RUN usermod -s /usr/bin/zsh root

# oh-my-zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"; exit 0

# shell config files.
ADD files/shell/zshrc /root/.zshrc
ADD files/shell/honukai.zsh-theme /root/.oh-my-zsh/themes/honukai.zsh-theme

# vim config
ADD files/vim /root/.vim
RUN ln -sf /root/.vim/vimrc /root/.vimrc

# setup tmux
ADD files/tmux/tmux.conf /root/.tmux.conf

# TODO:
# FASD
# Dir colors?
#  

CMD ["/usr/bin/zsh"]
