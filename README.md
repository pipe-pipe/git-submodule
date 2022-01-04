# git-submodule

git submodule command

- delete/remove submodule

```
git submodule deinit <path_to_submodule>
git rm <path_to_submodule>
rm -rf .git/modules/<path_to_submodule>
git commit -am "Removed submodule "
```

- add submodule

```shell
git submodule add git@github.com:pipe-pipe/git-submodule.git # <opt local dir name>
```

- config private submodule url

```shell
git config submodule.git-submodule.url <private git url>
```

- clone repo with submodule

```shell
git clone repo_url
git submodule init
git submodule update
# simpler way
git clone --recurse-submodules repo_url
# had clone
git submodule update --init
# submodule with submodule
git submodule update --init --recursive
```

- work with submodule repo

```shell
# pull submodule update from upstream
# cd to submodule dir
git fetch
git merge
git diff --submodule
# config diff with --submodule
git config --global diff.submodule log
# simple way
git submodule update --remote
# set fetch branch
git config -f .gitmodules submodule.xxx.branch stable
# config git status with submodule
git config status.submodulesummary 1
# see git log with submodule
git log -p --submodule
# pull submodule
git pull
git submodule update --init --recursive
# simple way
git pull --recurse-submodules
# fix: submodule url modified
git submodule sync --recursive
git submodule update --init --recursive
# push local commit
# push parent repo : before push check submodule had pushed
git push --recurse-submodules=check|on-demand
git config push.recurseSubmodules check|on-demand
# batch op foreach submodule
git submodule foreach 'git stash'
git submodule foreach 'git checkout -b featureA'
git diff;git submodule foreach 'git diff'
```

- alias

```shell
git config alias.sdiff '!'"git diff && git submodule foreach 'git diff'"
git config alias.spush 'push --recurse-submodules=on-demand'
git config alias.supdate 'submodule update --remote --merge'
```

- submodule with branch

```shell
git checkout --recurse-submodules
git config submodule.recurse true
```

- change sub dir to submodule

```shell
git rm -r xxx
git submodule add repo-url
git checkout -f master
# cd to sub dir
git checkout .
```
