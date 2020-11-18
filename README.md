# things-I-use-but-keep-forgetting
Organized cheatsheet of commands I use but keep forgetting.

## Development
### Git
#### Rebase my fork to the latest commits in the main repo.
Rebase the master branch of my fork with the master branch of the main repository.
1. Make sure that indeed I'm working with my fork and not the main repo.
```
git remote -v
```
2. In the previous command, I will see the origin remote pointing to my repo. If I already created the remote for the main repository, it will be there too.
3. Add the new remote, pointing to the main repository.
```
git remote add the_main_repository git@github.com:MainOrg/MainRepo.git
```
4. Fetch the new origin.
```
git fetch the_main_repository
```
5. Create a local branch tracking the master branch of the new remote.
```
git branch --track main_repo_master_branch the_main_repository/master
```
6. Checkout the just created branch.
```
git checkout main_repo_master_branch
```
7. Find and copy the latest commit hash.
```
git log
```
8. Checkout the master branch of my fork.
```
git checkout master
```
9. Rebase my master branch to the last commit of the main repo master branch.
```
git rebase the_hash_copied_in_step_seven
```
10. Push the change if needed.

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
