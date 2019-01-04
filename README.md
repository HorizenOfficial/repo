# Zen APT repository

Use the following to set it up. 
```
sudo apt-get update
sudo apt-get install apt-transport-https lsb-release

echo 'deb https://zencashofficial.github.io/repo/ '$(lsb_release -cs)' main' | sudo tee --append /etc/apt/sources.list.d/zen.list
gpg --batch --keyserver ha.pool.sks-keyservers.net --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669 || \
gpg --batch --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669 || \
gpg --batch --keyserver pgp.mit.edu --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669 || \
gpg --batch --keyserver keyserver.pgp.com --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669 || \
gpg --batch --keyserver pgp.key-server.io --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669
gpg --export 219F55740BBF7A1CE368BA45FB7053CE4991B669 | sudo apt-key add -

sudo apt-get update
sudo apt-get install zen # to install Zen
sudo apt-get install zencash-desktop-gui-wallet # to install Zen Swing Wallet
sudo apt-get install zenchat # to install ZENChat
```

## Available Packages
```
## AMD64
zen
        Depends: libc6 (>= 2.17), libgcc1 (>= 1:3.0), libgomp1 (>= 4.9), libstdc++6 (>= 5.2)

zencash-desktop-gui-wallet
        Depends: default-jdk, zen

zenchat
        Depends: gconf-service, gconf2, gvfs-bin, libc6, libcap2, libgcrypt11 | libgcrypt20, 
                 libgtk2.0-0, libnotify4, libnss3, libudev0 | libudev1, libxtst6, xdg-utils

## ARM64
zen
        Depends: libc6 (>= 2.17), libgcc1 (>= 1:4.5), libgomp1 (>= 4.9), libstdc++6 (>= 5.2)

zencash-desktop-gui-wallet
        Depends: default-jdk, zen
```
