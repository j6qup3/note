# 開發 SOP
- 將卡拉到中間
- 終端機切到專案目錄
- `git checkout master`
- `git pull mega master`: 從 mega 更新 master
- `git branch <branch_name>`: 創建新的分支
- 進行修改
- `git commit -a -m "<commit>"`
- `git push --set-upstream origin <branch_name>`: 把本地 commit push 上自己帳號底下的新分支
- 發 PR 並邀請，注意 branch 不要弄錯。
- 改 issue 並連上 PR
- 將卡拉到右邊

# branch 命名原則

- `feature/` ：新功能分支
- `bugs/` ：為了修正某些問題的分支
- `refactor/` ：用於修改目前已存在的功能，例如功能需求變更
- `junk/` ：實驗性質或是為了整理其它不同 branch 所存在的分支，不會發 PR
