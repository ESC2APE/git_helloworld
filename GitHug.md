##GitHug
[TOC]
> [Refer](https://codingstyle.cn/topics/51)

> - `Workspace`（工作区）：新添加的，和修改的未add操作的。
> - `Stage`（暂存区）：add操作过后，会进入暂存区。
> - `Repository` (本地仓库)：commit操作后，会进入本地仓库。
> - `Remote` (远程仓库)：push操作后，会提交到远程仓库。

---
#### *Level 1. init*
>Question : A new directory, `git_hug`, has been created; initialize an empty repository in it.
git init : Create an empty Git repository or reinitialize an existing one

---
#### *Level 2. config*
>Question : Set up your git name and email, this is important so that your commits can be identified.
git config -l
git config -e
git config --add
git config --unset-all user.name
git config [--global] user.name "[name]"
git config [--global] user.email "[email address]"

---
#### *Level 3. add*
>Question : There is a file in your folder called `README`, you should add it to your staging area
Note: You start each level with a new repo. Don't look for files from the previous one.
git --help
git add .
git add -A
git add README
git add <dirname>

---
####*Level 4.  commit*
>Question : The `README` file has been added to your staging area, now commit it.
git commit -m "commit README"

---
####*Level 5.  clone*
>Question : Clone the repository at https://github.com/Gazler/cloneme.
git clone https://github.com/Gazler/cloneme

---
####*Level 6.  clone_to_folder*
>Question : Clone the repository at https://github.com/Gazler/cloneme to `my_cloned_repo`.
git clone https://github.com/Gazler/cloneme my_cloned_repo

---
####*Level 7.  ignore*
>Question : The text editor 'vim' creates files ending in `.swp` (swap files) for all files that are currently open.  We don't want them creeping into the repository.  Make this repository ignore those swap files which are ending in `.swp`.
touch .gitignore
>>.profile.yml
.gitignore
*.swp

---
####*Level 8.  include*
>Question : Notice a few files with the '.a' extension.  We want git to ignore all but the 'lib.a' file
touch .gitignore
>>.profile.yml
.gitignore
*.a
!lib.a

>*.a           # 忽略所有 .a 结尾的文件

!lib.a           # 但 lib.a 除外

/TODO      # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO

build/           # 忽略 build/ 目录下的所有文件

doc/*.txt     # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt

---
####*Level 9.  status*
>Question : There are some files in this repository, one of the files is untracked, which file is it?
git status

---
####*Level 10.  number_of_files_committed*
>Question : There are some files in this repository, how many of the files will be committed?
git status

---
####*Level 11.  rm*
>Question : A file has been removed from the working tree, however the file was not removed from the repository.  Find out what this file was and remove it.
git commit -a -m "remove deleteme.rb"
git rm <file1> <file2>    #删除文件,并将文件放入暂存区
git mv <file-original> <file-rename>    #改文件名，并将修改后的文件放入暂存区

---
####*Level 12.  rm_cached*
>Question : A file has accidentally been added to your staging area, find out which file and remove it from the staging area.  *NOTE* Do not remove the file from the file system, only from git.
use "git rm --cached <file>..." to unstage
git rm --cached deleteme.rb
git reset HEAD <file>    #由暂存区恢复到工作区（发现提交错了，退回一步）
git reset HEAD    恢复上一次add提交的所有file
git checkout -- <file>    #撤销修改操作，恢复到修改之前的，撤销add后位于工作区下进行的

---
####*Level 13.  stash*
>Question : You've made some changes and want to work on them later. You should save them, but don't commit them.
[git stash](https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%82%A8%E8%97%8F%EF%BC%88Stashing%EF%BC%89)

---
####*Level 14.  rename*
>Question : We have a file called `oldfile.txt`. We want to rename it to `newfile.txt` and stage this change.
git mv oldfile.txt newfile.txt

---
####*Level 15.  restructure*
>Question : You added some files to your repository, but now realize that your project needs to be restructured.  Make a new folder named `src` and using Git move all of the .html files into this folder.
mkdir src
git add src
git mv *.html ./src

---
####*Level 16.  log*
>Question : You will be asked for the hash of most recent commit.  You will need to investigate the logs of the repository for this.
git log
git show
git log -p -2

---
####*Level 17.  tag*
>Question : We have a git repo and we want to tag the current commit with `new_tag`.
git tag -a new_tag -m "githug new_tag"
git tag -d new_tag #delete tag

---
####*Level 18.  push_tags*
>Question : There are tags in the repository that aren't pushed into remote repository. Push them now.
git push origin tag_to_be_pushed
git push origin [tagname]
git push [origin] --tags # all tags

---
####*Level 19.  commit_amend*
>Question : The `README` file has been committed, but it looks like the file `forgotten_file.rb` was missing from the commit.  Add the file and amend your previous commit to include it.
git add forgotten_file.rb
git commit --amend
[--amend](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%92%A4%E6%B6%88%E6%93%8D%E4%BD%9C)

---
####*Level 20.  commit_in_future*
>Question : Commit your changes with the future date (e.g. tomorrow).
git commit --date "2018-02-19 01:00:00" -m ""date

---
####*Level 21.  reset*
>Question : There are two files to be committed.  The goal was to add each file as a separate commit, however both were added by accident.  Unstage the file `to_commit_second.rb` using the reset command (don't commit anything).
git reset to_commit_second.rb

![57408893.png](GitHug_files/57408893.png)

---
####*Level 22.  reset_soft*
>Question : You committed too soon. Now you want to undo the last commit, while keeping the index.
git reset --soft HEAD^
git reset --soft HEAD ~n
>- soft 参数：git reset --soft HEAD～1 意为将版本库软回退1个版本，所谓软回退表示将本地版本库的头指针全部重置到指定版本，且将这次提交之后的所有变更都移动到暂存区
>- 默认的mixed参数：git reset HEAD～1 意为将版本库回退1个版本，将本地版本库的头指针全部重置到指定版本，且会重置暂存区，即这次提交之后的所有变更都移动到未暂存阶段
>- hard参数：git reset --hard HEAD～1 意为将版本库回退1个版本，但是不仅仅是将本地版本库的头指针全部重置到指定版本，也会重置暂存区，并且会将工作区代码也回退到这个版本

---
####*Level 23.  checkout_file*
>Question : A file has been modified, but you don't want to keep the modification.  Checkout the `config.rb` file from the last commit.
git checkout -- config.rb

---
####*Level 24.  remote*
>Question : This project has a remote repository.  Identify it.
git remote show

---
####*Level 25.  remote_url*
>Question : The remote repositories have a url associated to them.  Please enter the url of remote_location.
git remote -v

---
####*Level 26.  pull*
>Question : You need to pull changes from your origin repository.
git pull origin master

---
####*Level 27.  remote_add*
>Question : Add a remote repository called `origin` with the url https://github.com/githug/githug
git remote rm origin  #or delete first then add
git remote add origin https://github.com/githug/githug

---
####*Level 28.  push*
>Question : Your local master branch has diverged from the remote origin/master branch. Rebase your commit onto origin/master and push it to remote.
git branch -a
git pull --rebase origin master
git push
git push origin master

---
####*Level 29.  diff*
>Question : There have been modifications to the `app.rb` file since your last commit.  Find out which line has changed.
git diff app.rb

---
####*Level 30.  blame*
>Question : Someone has put a password inside the file `config.rb` find out who it was.
git blame config.rb

---
####*Level 31.  branch*
>Question : You want to work on a piece of code that has the potential to break things, create the branch test_code.
git branch test_code

---
####*Level 32.  checkout*
>Question : Create and switch to a new branch called my_branch.  You will need to create a branch like you did in the previous level.
git checkout my_branch

---
####*Level 33.  checkout_tag*
>Question :  You need to fix a bug in the version 1.2 of your app. Checkout the tag `v1.2`.
git tag
git checkout tag_name
git checkout 187589f9cb266e697fc07fabdac61a23fb990769

---
####*Level 34.  checkout_tag_over_branch*
>Question : You need to fix a bug in the version 1.2 of your app. Checkout the tag `v1.2` (Note: There is also a branch named `v1.2`).
git checkout 187589f9cb266e697fc07fabdac61a23fb990769

---
####*Level 35.  branch_at*
>Question : You forgot to branch at the previous commit and made a commit on top of it. Create branch test_branch at the commit before the last.
git branch test_branch HEAD^

---
####*Level 36.  delete_branch*
>Question : You have created too many branches for your project. There is an old branch in your repo called 'delete_me', you should delete it.
git branch -D delete_me
git branch -d delete_me

---
####*Level 37.  push_branch*
>Question : You've made some changes to a local branch and want to share it, but aren't yet ready to merge it with the 'master' branch.  Push only 'test_branch' to the remote repository
git checkout test_branch
git push -u origin test_branch
git push origin master

---
####*Level 38.  merge*
>Question : We have a file in the branch 'feature'; Let's merge it to the master branch.
git merge feature

---
####*Level 39.  fetch*
>Question : Looks like a new branch was pushed into our remote repository. Get the changes without merging them with the local repository
git fetch origin

---
####*Level 40.  rebase*
>Question : We are using a git rebase workflow and the feature branch is ready to go into master. Let's rebase the feature branch onto our master branch.
git checkout feature
git rebase master

---
####*Level 41.  rebase_onto*
>Question : You have created your branch from `wrong_branch` and already made some commits, and you realise that you needed to create your branch from `master`. Rebase your commits onto `master` branch so that you don't have `wrong_branch` commits.
git rebase --onto master wrong_branch readme-update
git rebase --onto base from to     #使用(from, to]所指定的范围内的所有commit在base这个commit之上进行重建
[info](http://blog.csdn.net/endlu/article/details/51605861)

---
####*Level 42.  repack*
>Question : Optimise how your repository is packaged ensuring that redundant packs are removed.
git repack -d

---
####*Level 43.  cherry-pick*
>Question : Your new feature isn't worth the time and you're going to delete it. But it has one commit that fills in `README` file, and you want this commit to be on the master as well.
git branch -a
git checkout master
git log --oneline README.md
git checkout master
git cherry-pick ca32a6d
[info](https://www.jianshu.com/p/08c3f1804b36)

---
####*Level 44.  grep*
>Question : Your project's deadline approaches, you should evaluate how many TODOs are left in your code
git grep TODO

---
####*Level 45.  rename_commit*
>Question : Correct the typo in the message of your first (non-root) commit.
git log -p 
git log --oneline
git rebase -i 36f4179     # `pick` 修改为`edit`后保存
git commit --amend    #edit commit message in new window
git rebase --continue
[info 1](http://blog.csdn.net/garfielder007/article/details/60885107)
[info 2](https://help.github.com/articles/changing-a-commit-message/)

---
####*Level 46.  squash*
>Question : You have committed several times but would like all those changes to be one commit.
git log -p
git rebase -i 25a85797c7494c52c7eed245942aa78e18034bf7 #change pick to squash

---
####*Level 47.  merge_squash*
>Question : Merge all commits from the long-feature-branch as a single commit
git branch -a
git merge --squash long-feature-branch
git commit

---
####*Level 48.  reorder*
>Question :  You have committed several times but in the wrong order. Please reorder your commits.
git log -p
git rebase -i c6bd7780ae90f6befb399ba0ac353ff163d8cff9
git commit --amend
git rebase --continue
git commit --amend
git rebase --continue

---
####*Level 49.  bisect*
>Question : A bug was introduced somewhere along the way.  You know that running `ruby prog.rb 5` should output 15.  You can also run `make test`.  What are the first 7 chars of the hash of the commit that introduced the bug.
git bisect start
ruby prog.rb 5
git bisect bad master
git log
git checkout 80a9b3d
ruby prog.rb 5
git bisect good
ruby prog.rb 5
git bisect good
...
git bisect bad
git bisect reset

>or
>git bisect start HEAD v1.0 
>git bisect run test-error.sh

---
####*Level 50.  stage_lines*
>Question : You've made changes within a single file that belong to two different features, but neither of the changes are yet staged. Stage only the changes belonging to the first feature.
git status
git diff
git add -p
e     #edit

---
####*Level 51.  find_old_branch*
>Question : You have been working on a branch but got distracted by a major issue and forgot the name of it. Switch back to that branch.
git relog
git checkout solve_world_hunger

---
####*Level 52.  revert*
>Question : You have committed several times but want to undo the middle commit. All commits have been pushed, so you can't change existing history.
git revert HEAD^1

---
####*Level 53.  restore*
>Question : You decided to delete your latest commit by running `git reset --hard HEAD^`.  (Not a smart thing to do.)  You then change your mind, and want that commit back.  Restore the deleted commit.
git log -p
git reflog
git checkout 37baa81

---
####*Level 54.  conflict*
>Question : You need to merge mybranch into the current branch (master). But there may be some incorrect changes in mybranch which may cause conflicts. Solve any merge-conflicts you come across and finish the merge.
git branch -a
git merge master mybranch
git status
vi poem.txt
git add poem.txt
git commit

---
####*Level 55.  submodule*
>Question : You want to include the files from the following repo: `https://github.com/jackmaney/githug-include-me` into a the folder `./githug-include-me`. Do this without manually cloning the repo or copying the files from the repo into this repo.
git submodule add https://github.com/jackmaney/githug-include-me ./githug-include-me

---
####*Level 56.  contribute*
>Question : This is the final level, the goal is to contribute to this repository by making a pull request on GitHub.  Please note that this level is designed to encourage you to add a valid contribution to Githug, not testing your ability to create a pull request.  Contributions that are likely to be accepted are levels, bug fixes and improved documentation.


---
