# How to setup a local development environment

## Local development environment with Ubuntu

### Docker

```bash
sudo apt install docker
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
sudo chown root:docker /var/run/docker.sock
```

Then restart your computer.


### Composer and PHP

Composer is required to resolve PHP dependencies.

```bash
sudo apt install composer
sudo apt install php-common php-curl php-gd php-iconv php-intl php-json php-ldap php-mbstring php-mysql php-pgsql php-soap php-sqlite3 php-tidy php-xml php-zip
```

### Instal npm

```bash
curl -fsSL https://deb.nodesource.com/setup_19.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```

### Configure git

```bash

echo -e ".idea\nThumbs.db\n.DS_Store\n.vscode\n" > ~/.gitignore
git config --global core.excludesfile ~/.gitignore
git config --global core.autocrlf false
git config --global core.eol lf
```