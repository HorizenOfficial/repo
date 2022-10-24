# Zen APT repository

## Migration notice
This repository has migrated from https://zencashofficial.github.io/repo/ to https://HorizenOfficial.github.io/repo/.

**You have to follow the instructions under [#configuring-the-new-repository-on-existing-installations](https://github.com/HorizenOfficial/repo#configuring-the-new-repository-on-existing-installations) to use the new repository for existing installations.**

## Configuring the new repository on existing installations
Please run the following to switch from the old repository to the new one. This will only work if you set up the old repository following the official instructions.
```
sudo sed -i 's/[zZ][eE][nN][cC][aA][sS][hH][oO][fF][fF][iI][cC][iI][aA][lL]/HorizenOfficial/g' /etc/apt/sources.list.d/zen.list
sudo apt-get update
```
When running `sudo apt-get update` or `sudo apt-get install zen` you might get an error like this:
```
E: Repository 'https://HorizenOfficial.github.io/repo/ $distro Release' changed its 'Origin' value from 'ZencashOfficial' to 'HorizenOfficial'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
```
To fix this please accept the change in origin by pressing `y + ENTER` if this dialog appears:
```
Do you want to accept these changes and continue updating from this repository? [y/N]
```

## Configuring the repository on new installations
Please run the following to set it up.
```
sudo apt-get update
sudo apt-get install apt-transport-https lsb-release

echo 'deb [signed-by=/usr/share/keyrings/horizen-archive-keyring.gpg] https://HorizenOfficial.github.io/repo/ '$(lsb_release -cs)' main' | sudo tee /etc/apt/sources.list.d/zen.list > /dev/null
export GNUPGHOME="$(mktemp -d)"
gpg --batch --keyserver hkps://keys.openpgp.org --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669 || \
gpg --batch --keyserver keyserver.ubuntu.com --recv 219F55740BBF7A1CE368BA45FB7053CE4991B669
gpg --export 219F55740BBF7A1CE368BA45FB7053CE4991B669 | sudo tee /usr/share/keyrings/horizen-archive-keyring.gpg > /dev/null
gpgconf --kill dirmngr || true
gpgconf --kill gpg-agent || true
rm -r "$GNUPGHOME"
unset GNUPGHOME

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
```
