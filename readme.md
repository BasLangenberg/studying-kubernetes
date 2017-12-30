# Introduction
This repo contains the infrastructure I use to examine kubernetes the hard way, the excellent introduction written up by Kelsey Hightower.

# Prerequisites

1. virtualbox
2. vagrant
3. vagrant-hostmanager

the latter can be installed with `vagrant plugin install vagrant-hostmanager`

# Easy of use
login to client with `vagrant ssh client` and install tmux, git and pip

`sudo apt install tmux git python-pip ansible`

Then install tmuxp

`pip install --user tmuxp`

you can then do 

`tmuxp load /vagrant/`

to start a tmux session for studying all the hosts in the k8s cluster

Tested with [baslangenberg-dotfiles](https://github.com/BasLangenberg/dotfiles)
