# Development
## Git
### Safely store git credentials in gnome-keyring.
gnome-keyring is generally installed with every Linux desktop. Seahorse is the GUI used to manage all the stored credentials.
1. Compile and install the support for git.
```
sudo apt install libsecret-1-0 libsecret-1-dev
sudo cd /usr/share/doc/git/contrib/credential/libsecret
sudo make
```
2. Configure git to use the new helper.
```
git config --global credential.helper /usr/share/doc/git/contrib/credential/libsecret/git-credential-libsecret
```
3. The git credentials will be stored from now on and visible in seahorse.
### Remove all staged changes (git add)
```
git reset
```
### Remove not commited changes (repo or file)
```
git checkout .
git checkout file
```
### Rebase my fork to the latest commits in the main repo
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
4. Fetch the new remote.
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
### Nuke my forked repository with the main repository.
1. Since this should be tried if the rebase doesn't work (or is not worth solving the conflicts), the previous origins and branches should be created.
2. Download the very last changes to the branch following the master branch of the main repository.
```
git checkout main_repo_master_branch
git pull
```
3. Checkout the fork's master branch.
```
git checkout master
```
4. Nuke it locally with the master branch of the main repository.
```
git reset --hard the_main_repository/main_repo_master_branch
```
5. Now nuke the remote of the forked repository. Since we rewrite history, it has to be forced.
```
git push -f origin master
```
### Apply a PR in my local repository
```
curl -L <pr-url>.patch | git am -
```


