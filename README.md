# Zen APT repository

Use the following to set it up and install Zen + Swing Wallet. 
```
sudo apt-get update
sudo apt-get install apt-transport-https lsb-release

echo 'deb https://zencashofficial.github.io/repo/ '$(lsb_release -cs)' main' | sudo tee --append /etc/apt/sources.list.d/zen.list
gpg --keyserver ha.pool.sks-keyservers.net --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669
gpg --export 219F55740BBF7A1CE368BA45FB7053CE4991B669 | sudo apt-key add -

sudo apt-get update
sudo apt-get install zen zencash-desktop-gui-wallet
```

```
## AMD64
zen
        Depends: libc6 (>= 2.17), libgcc1 (>= 1:3.0), libgomp1 (>= 4.9), libstdc++6 (>= 5.2)

zencash-desktop-gui-wallet
        Depends: default-jdk, zen

## ARM64
zen
        Depends: libc6 (>= 2.17), libgcc1 (>= 1:4.5), libgomp1 (>= 4.9), libstdc++6 (>= 5.2)

zencash-desktop-gui-wallet
        Depends: default-jdk, zen
```
