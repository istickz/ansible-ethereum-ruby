# Ansible: Ruby on Rails Server (Ubuntu 16.x)

Use this ansible playbook to setup a fresh server with the following components:

* Nginx
* Puma App Server
* Certbot (Let's Encrypt)
* Postgresql
* Parity
* Monit (to keep Puma and Sidekiq runnig)
* ruby-install
* chruby
* Directories to deploy Rails with Capistrano and Puma App Server (see below)
* Swapfile (useful for small DO instances)
* Locales
* Tools (tmux, vim, htop, git, wget, curl etc.)

## Install Playbook

Change your hosts in `./hosts` file
Put your public keys into group_vars/public_keys
Modify your public keys location in `group_vars/all.yml`

```
ssh_public_key_files:
  - "./group_vars/public_keys/some_key_example"
```

Change General settings in `group_vars/all.yml` to your own settings

First install:

```ansible-playbook droplet.yml -i hosts```.

After run droplet.yml you have server without root user login and all commands need your private key
The rest of the configuration will be through with accounts-service.yml
Just run

```ansible-playbook droplet.yml -i hosts```.
