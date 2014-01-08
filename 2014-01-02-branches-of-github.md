---
layout: post
title: 'Branches of GitHub'
date: 2014-01-02 09:39
comments: true
categories: [github]
---
**GitHub 的特色就是可以多人針對同一個專案做各自的改動，而後再合併回專案中；其中可避免多人改動同一處而造成的衝突、或是在改動後出問題後的回復。**

clone 完畢後、選擇 local 本地的 My Repositories ；點擊向右的箭頭進入。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.23.37.jpg">

在 History 會出現所有修改的記錄。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.25.13.jpg">

**在進行下一步編輯文件前、要先創建一個分支/ Branches。**
切換到 Branches 頁面 -> 點選 "+" -> 輸入分支的名字 ex: 2014-01-02 Branch -> 點擊 Branch。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.34.57.jpg">

在建好後就發現目前已經切換到"2014-01-02 Branch"的分支上、此時可以開始修改了。

修改 readme.md。（使用 markdown 語法）

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.39.39.jpg">

修改後、假設今天的程式碼都改完了；記住目前的修改都在"2014-01-02 Branch"的分支上，和 Master 並無關係。
這時切回 GitHub 中的 Changes 、可以看到未提交的改動。輸入 Commit -> 點擊 Commit 按鈕；就提交完成了。要注意的是目前還是提交到"2014-01-02 Branch"的分支。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.45.24.jpg">

**切換回 Master 、獲得最新更新**
在實務上、有可能我們修改的同時，也有其他人也在修改並且也提交了修改後的程式；所以我們要先再次得到最新的更新。
選擇 Branches 頁面 -> 點選 Master 切回主線　-> 點選 Sync Branch 獲得最新更新。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.49.53.jpg">

**最重要的一步、合併分支到主線 Master 。**
在 Branches 頁面中、點選 Merge View 後，先將"2014-01-02 Branch"的分支拖到第一個空格，再將 Master 拖到第二個空格。因為最終會將代碼合併到 Master 主線上而不是"2014-01-02 Branch"分支上。
點擊 Merge Branches 。若修改的文件沒有和其他人修改的衝突，那麼就會自動合併成功。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.53.28.jpg">

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.59.07.jpg">

如果和其他人修改了同一個文件，那麼就會出現提示"合併失敗"，此時就要手動去處理衝突的部份。
GitHub 會自動把有衝突的部份都標示出來

合併完成後、點選上方的 Sync Branch 將修改結果上傳到 GitHub上。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8810.59.58.jpg">

收工。

<img class="center" src="https://dl.dropboxusercontent.com/u/12573607/For%20Blog/2014-Jan-02/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202014-01-02%20%E4%B8%8A%E5%8D%8811.01.38.jpg">