# things-I-use-but-keep-forgetting
Organized cheatsheet of commands I use but keep forgetting.

## Linux
### Debian
#### Add a key with apt-key
```
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXXXXX
apt-key adv --fetch-keys https://packages.cloud.google.com/apt/doc/apt-key.gpg
```
### Vim
#### Ctags support
apt install exhuberant-ctags
//Inside code folder create a hidden tags file
ctags -R -f .tags .
//Launch vim and test looking for a function definition with Ctrl+]
