# Git Notes

## Start

    git status

## Operations

撤销未add的修改 / Rollback modifications not added·

    git checkout <fileName>

修改上一commit / Modify previous commit

    git commit --amend --no-edit
    git commit --amend -m "new message"
    git push -f

回滚 / Rollback

    git reset --soft HEAD~1

变更缓存 / Cache

    git stash
    git stash pop

删除所有本地修改 / Abandon local commits

    git reset --hard origin/<branch_name>

空commit / Empty commit

    git commit --allow-empty -m "Retrigger pipeline."

防止branch合并入自身 / Prevent merge branch itself

    git fetch & git rebase

不再追踪某些文件 / git ignore

    # ignore a folder except few files
    folder/*  
    !folder/file.format
    # ignore a folder
    folder/
    # Ignore files with cache
    git rm -r --cached .
    git add .
    git commit -m "Remove cache." 

获取tag / Get tag

    git fetch --all --tags

配置 / Set git config

    git config --global user.name "dog"
    git config --global user.email "dog@dog.com"

## Branch

重命名branch / Rename branch

    git branch  -m <old> <new>
  
删除本地与远程branch / Delete branch locally & remotely 

    git branch -d localBranchName
    git push origin --delete remoteBranchName

新建branch / New branch

    git checkout -b <new-feature> <origin-branch>

## Warnings

- Do not use `git add .` , which may add unexpected files.
