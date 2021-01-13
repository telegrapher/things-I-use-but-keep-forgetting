# things-I-use-but-keep-forgetting
Organized cheatsheet of commands I use but keep forgetting.

## [Development](./DEVELOPMENT.md)

## Linux
### Debian
#### Add a key with apt-key
```
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXXXXX
apt-key adv --fetch-keys https://packages.cloud.google.com/apt/doc/apt-key.gpg
```
#### Reset aptitude status
```
rm -f /var/lib/aptitude/pkgstates*
```
#### Remove dangling configurations from uninstalled packages.
```
aptitude purge ?config-files
```
##### With dpkg only
```
dpkg --purge $(dpkg --get-selections | grep deinstall | cut -f1)
```
#### Enable weekly fstrim
```
systemctl enable fstrim.timer
```
#### Change default Java version
```
update-alternatives --config java
```
### Vim
#### Search and replace
```
:%s/search/replace/g 
```
#### Ctags support
```
apt install exhuberant-ctags
cd repos/my_project
ctags -R -f .tags .
```
Launch vim and test looking for a function definition with Ctrl+], return to the previous position with Ctrl+t

### Bash
#### Configuration files
Login shells read:
```
/etc/profile
~/.bash_profile
~/.bash_login
~/.profile
```
Non login shells read:
```
/etc/bash.bashrc
~/.bashrc
```
Since ~/.bash_profile usually loads ~/.bashrc, set there stuff for every shell

### Curl
#### Fixed SSL version
```
curl --tls-max 1.2 --tlsv1.2
```

### Openssl
#### Verify SSL negotiation
```
openssl s_client -starttls smtp -crlf -connect smtp.office365.com:587
```
#### SSL negotiation without SNI
```
openssl s_client -noservername -connect host:port
```
### Docker
#### Inspect image content, avoid layer separation
```
docker create --name=YOLO image:tag
docker export YOLO | tar t
docker rm YOLO
```
### Kubernetes
#### Contexts
```
kubectl config current-context
kubectl config get-contexts
kubectl config use-context yolo
kubectl config set-context --current --namespace=yolo-namespace
```
### Hardware
#### Great list of hardware details: inxi
```
inxi -Fxz
```
#### List of available soundcards
```
cat /proc/asound/cards
```
#### Readable tree with every USB device
```
lsusb -tv
```
