<!-- TOC START min:1 max:3 link:true update:true -->
- [git 基本概念及常見名詞介紹](#git-)
  - [什麼是 HEAD？](#-head)
    - [補充 - commit id 格式](#---commit-id-)
- [環境建置](#)
- [常用操作](#-1)
- [操作分支](#-2)
- [合併](#-3)
- [輔助功能](#-4)
- [回溯](#-5)
  - [git revert](#git-revert)
  - [git reset](#git-reset)

<!-- TOC END -->

# git 基本概念及常見名詞介紹
- 版本: 在 git 通常指成功的 commit
- `HEAD`: 是一個參考 (reference)，指向當前所在 branch 的最新版本，當 `git checkout`、`git commit`、`git reset` 時就會改動
- `index` / `staging area`: 已經被 add 但尚未 commit

## 什麼是 HEAD？
很多人知道 HEAD 是當前分支的別名，那他實際是如何運作的呢？
首先，在任意 git 目錄下輸入 `cat .git/HEAD`，可以看到 `ref: refs/heads/<branch_name>`，這代表什麼呢？HEAD 其實是一個參考 (reference)，指向當前所在 branch。那我們這次換輸入 `cat .git/refs/heads/<branch_name>`，發現他儲存的會是目前的 branch 最新版本的 commit_id，也就是說，`git show HEAD` 等同於 `git show refs/heads/<branch_name>`，也等同於 `git show <commit_id>`。但要注意的是，`.git/refs/heads/<branch_name>` 本身並非參考，實際上 .git/ 裡並沒有檔名為 commit_id 的檔案。
懶人包：HEAD = 當前分支 -> 當前分支最後的 commit_id

### 補充 - commit id 格式
- `<commit_id>/<branch_name>/HEAD`: 最基本的使用方式， commit_id 是 SHA-1 hash (可以用 git log 查詢)
- `...^`: 這代表上一個 commit
- `...~n`: 這代表前 n 個 commit

# 環境建置
- `git init`: 建立新的 Repo (建立新的 .git)
- `git clone <URL>`: 複製遠端數據庫到本地並進行追蹤 (包含 `remote add origin <URL>`)
- `git remote`: 顯示遠端數據庫清單
- `git remote add <remote-name> <URL>`: 追蹤遠端數據庫並命名
- `git remote rm <remote-name>`: 取消追蹤遠端數據庫

通常起手式是 `git init` + `git remote <URL>` / `git clone <URL>` + `cd <workspace>`

# 常用操作
- git add
- git commit
- git push
- `git pull [remote-name] [branch-name]`: 將 commit 推上遠端，remote-name 預設 origin，branch-name 預設 master。

# 操作分支
- `git branch`: 列出所有分支以及當前所在分支
- `git branch <branch-name>`: 新建分支
- `git checkout <branch-name>`: 將當前 HEAD 切換成特定分支
- `git push --set-upstream <remote-name> <branch-name>`: 使用時機是本地新建分支，但遠端數據庫尚未有此分支時，需要用這個將當前分支推上遠端數據庫

# 合併
- `git merge`:
- `git rebase`:

# 輔助功能
- `git status`: 查看 git 目前狀態 (stage)
- `git log`: 查看之前的 commit

# 回溯

## git revert
- `git revert <commit_id>`:

## git reset
- `git reset [--soft] <commit_id>`: 版本回撤，將此
- `git reset --hard <commit_id>`
- `git checkout -- <file_name>`: 將目標檔案的所有 unstaged change 都捨棄掉。
