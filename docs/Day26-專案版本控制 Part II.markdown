#專案版本控制 Part II

接著昨天的介紹，今天要介紹如何使用這免費的版本控制工具。
  
## 在Server端
開啟VisualSVN Server之後會看到一個視窗如下圖：
![][SvnServer_01]
  
  
因為當初在安裝的時候，我是選擇 **Subversion authtication** 所以會多出 **User** 及 **Groups** 這兩個資料夾！其實這兩個資料夾的目的就是在做權限的控管，比如某個群組可以存取某個分支或某個User可以存取某個專案！其設定方式就跟windows 大同小異，在這裡就不多做介紹！唯一要注意的是，一個User好像不能隸屬兩個群組（含）以上，否則會有一點小問題，不知道現在修復了沒。這裡稍微注意一下就好！
  
而在 Repositories 的部分，可以單擊滑鼠右鍵去 **Create New Repository**
![][SvnServer_02]
  
在 **Create New Repository** 時，我們可以看到對話視窗正下方會有一個選項 **Create default structure (trunk, branches, tags)** ，這個選項是代表系統會幫我們把 trunk, branches, tags  這三個資料夾給建立起來供我們使用！
![][SvnServer_03]
  
  
### trunk, branches 及 tags的簡單介紹
#### Trunk
這個資料夾通常放的是穩定，可以Build過且能正常執行的原始碼。  
  
#### branches
這個資料夾稱之為「分支」，通常要新增一個功能時都會從trunk複製一份「分支」到branches這個資料夾下進行開發，當開發完後會再Merge（合併）回去trunk當中。  
  
#### tags
這個資料夾通常是當這個專案釋出一個版本時，從trunk中去標記一個號碼放到tags這個資料夾裡，當我們再一直更新的過程中，隨時都可以從這裡找回之前任何一個版本。  
  
當然，除了這三個資料夾之外你也可以隨意的新增屬於自己想要的資料夾，trank, branchers, tags只是常用的建議而已！沒有說一定非這樣做不可！
  
接著我們先隨意的新增一個TestProject來練習使用！
![][SvnServer_04]
  
再到 Users 中心增一位User！
接著就可以打開瀏覽器輸入網址 https://127.0.0.1/svn (也可以使用內部的IP網址或有對外的IP都行)
![][SvnServer_05]
  
輸入帳號密碼後就可以看到我們剛剛新增的專案了！
  
![][SvnServer_06]  
  
  
  
## 在Client端
接著我們就可以任一資料夾下單擊滑鼠右鍵，點選SVN取出：
![][SvnServer_07]  
  
在輸入我們剛剛看到的網址：https://127.0.0.1/svn/TestProject/trunk
![][SvnServer_08]  
  
接著按確定，就可以把這個空專案取出了！
  
這時候該專案的資料單擊滑鼠右鍵時就會多出 **SVN更新**,  **SVN送交** 這兩個功能！這時候當我們的專案有異動時就可以選擇送交，每次送交就必須填寫一些關於這次異動的說明。這樣一來，如果有需要用到之前的版本，也可以利用 **TortoiseSVN** --> **更新至版本** 來還原我們所需要的資料。
  
關於版本控制其實還有很多資料，在此我先介紹個入門，有需要進一步資料的伙伴就可以自行GOOGLE找資料囉！！
  

<!-- Image link -->
[SvnServer_01]: <https://www.dropbox.com/s/8zv8pnxokbupnil/Day26-SvnServer01.png?dl=1>
[SvnServer_02]: <https://www.dropbox.com/s/wbjnsd1c93vwql8/Day26-SvnServer02.png?dl=1>
[SvnServer_03]: <https://www.dropbox.com/s/m0n4cbokilt8vs9/Day26-SvnServer03.png?dl=1>
[SvnServer_04]: <https://www.dropbox.com/s/oa3zm7dog3z6m0n/Day26-SvnServer04.png?dl=1>
[SvnServer_05]: <https://www.dropbox.com/s/9f5pwd6yetu2iwa/Day26-SvnServer05.png?dl=1>
[SvnServer_06]: <https://www.dropbox.com/s/ddk7ll7yhzfbhzf/Day26-SvnServer06.png?dl=1>
[SvnServer_07]: <https://www.dropbox.com/s/n15p936dqcsdqti/Day26-SvnServer07.png?dl=1>
[SvnServer_08]: <https://www.dropbox.com/s/8qiu5e38hprl5mk/Day26-SvnServer08.png?dl=1>