# things-I-use-but-keep-forgetting
Organized cheatsheet of commands I use but keep forgetting.

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
#### Enable weekly fstrim
```
systemctl enable fstrim.timer
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
### Kubernetes
#### Contexts
```
kubectl config current-context
kubectl config get-contexts
kubectl config use-context yolo
kubectl config set-context --current --namespace=yolo-namespace
```
