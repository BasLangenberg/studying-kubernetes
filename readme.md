# Introduction
This repo contains the infrastructure I use to examine kubernetes the hard way, the excellent introduction written up by Kelsey Hightower.

# Prerequisites

1. virtualbox
2. vagrant
3. vagrant-hostmanager

the latter can be installed with `vagrant plugin install vagrant-hostmanager`

# Ease of use
login to client with `vagrant ssh client` and install Ansible

`sudo apt install ansible`

Then apply the playbook for the client to install other dependencies.

`ansible-playbook -i hosts  setup-client.yml`

you can then open a tmux window which has a connection to all the servers and the documentation, which makes the system easier to explore. Please note you need to start a new session before this works.

`tmuxp load /vagrant/`

# Automated install with Ansible
TBD

# Disclaimers and further notes
Inspired by [Kubernetes the hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
Tested with [baslangenberg-dotfiles](https://github.com/BasLangenberg/dotfiles)
