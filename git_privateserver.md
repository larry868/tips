# Git Tips - Private Server


By convention the name of the git project on the private server must end with `.git`


### Check existing repos on the server

Open en ssh session on the git server

```bash
# list repos
ls -a ~/gitrepo

# list files related to last commit -origin on a specific repo
cd ~/gitrepo/{myrepo}.git
git ls-tree HEAD
```

### Create a new GIT BARE repo

```bash
cd ~/gitrepo

# Init new repo
git init --bare <{newrepo}.git>

# Show it's content (shoud be empty)
git ls-tree --full-tree -r HEAD

# Check what your repository's HEAD is currently referencing
git symbolic-ref HEAD

# update your repository's HEAD to a valid ref
git symbolic-ref HEAD refs/heads/{my-branch}
```


