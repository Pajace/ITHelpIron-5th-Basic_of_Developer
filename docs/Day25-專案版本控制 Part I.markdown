#專案版本控制 Part I

在軟體開發的過程中，備份是個好習慣，如果有備份，當你需要之前的資料，就可以很容易的找回來。那要怎麼備份呢？當然！這裡指的是「程式碼的備份」。也可以說是版本控制管理。
今天就是要介紹免費的版本控制管理軟體 TortoiseSVN 及 VisualSVN。
  
在開發過程中備份或者版本控制是一件很重要的事情。無論這個專案是你一個人開發，或者一群人開發，它（版本控制或備份）都很重要！
  
如果是一個人開發，有些人或許會覺得：「我只有一個人，為何需要版本控制，自己就可以控制得很好啦。」但是，有沒有想過一旦需要回覆到某一個版本，或者，不小心改掉先前的某個功能時，要怎麼辦呢？（其實如果使用TDD，這個問題應該可能會少一點啦）
  
今天就要跟大家介紹一個非常簡單又容易的版本控制工具！真的很簡單！並且不用多花錢，無論是在Windows下開發或Linux下都可行！
  
## 第一步：安裝
### (1)版本控制的服務端–VisualSVN  
(伺服器端是 windows 的版本)
![][VisualSvn_Server01]
  
在安裝的過程中記得要選擇 **VisualSVN Server and Management Console** 這個選項！
![][VisualSvn_Server02]
  
再來需要注意的是 **Respositories** 的位置，也就是將來存放開發過程（包含程式碼、文件…等）所有資料的地方。其次是 **Authentication**：可以選擇由 Subversion 裡面設定，也可以使用 Windows 本身的帳號。
我的經驗是，如果有登入網域且多人使用的話，建議使用 **Windows authentication**，若沒有登入網域，無論單人使用或多人都可以用 **Subversion authentication** 比較方便。
![][VisualSvn_Server03]
  
### ((2)安裝 Client 端的SVN軟體，在Windows上我是使用TortoiseSVN
目前最新版本是 [1.7.7 for 32bit OS][SVNServer_177_32bit] / [for 64bit OS][SVNServer_177_64bit]
  
如果需要的話也可以下載中文的語系安裝檔：[for 32bit OS][SVNServer_177_Cht_pak_32bit] / [for 64bit OS][SVNServer_177_Cht_pak_64bit]
  
在安裝主程式和語系檔後，你就可以直接在桌面或檔案總管中單擊滑鼠右鍵，就可以看到多出兩個選項了。
![][VisualSvn_Server04]
  
這時候你就可以透過 **TortoiseSVN** -> **Settings** 中的 **General** 去更改語系（畢竟我還是比較習慣中文XD）
![][VisualSvn_Server05]
  
  
## 第二步：使用
在這裡先賣個關子，明天繼續為大家介紹。
  
  
<!-- 圖片 link -->
[VisualSvn_Server01]: <https://www.dropbox.com/s/jhz3irei5rzk3ar/Day25-SVNServer01.png?dl=1>
[VisualSvn_Server02]: <https://www.dropbox.com/s/le8mp3u3zweib39/Day25-SVNServer02.png?dl=1>
[VisualSvn_Server03]: <https://www.dropbox.com/s/2ancntc63zcubpo/Day25-SVNServer03.png?dl=1>
[VisualSvn_Server04]: <https://www.dropbox.com/s/8vsfrk3828d1axd/Day25-SVNServer04.png?dl=1>
[VisualSvn_Server05]: <https://www.dropbox.com/s/3eeqrlx8082tuqb/Day25-SVNServer05.png?dl=1>

<!-- web link -->
[SVNServer_177_32bit]: <http://sourceforge.net/projects/tortoisesvn/files/1.7.10/Application/TortoiseSVN-1.7.10.23359-win32-svn-1.7.7.msi/download?accel_key=61%3A1350547489%3Ahttp%253A//tortoisesvn.net/downloads.html%3Ac2053ad0%24b7ead3f5495606a035aea34159990e214f2e438f&click_id=7ceef412-18fa-11e2-a4ae-0200ac1d1d90&source=accel>

[SVNServer_177_64bit]: <http://sourceforge.net/projects/tortoisesvn/files/1.7.10/Application/TortoiseSVN-1.7.10.23359-x64-svn-1.7.7.msi/download?accel_key=61%3A1350547489%3Ahttp%253A//tortoisesvn.net/downloads.html%3Ac2053ad0%24b7ead3f5495606a035aea34159990e214f2e438f&click_id=7ceef412-18fa-11e2-a4ae-0200ac1d1d90-1&source=accel>

[SVNServer_177_Cht_pak_32bit]: <http://downloads.sourceforge.net/tortoisesvn/LanguagePack_1.7.10.23359-win32-zh_TW.msi?download>
[SVNServer_177_Cht_pak_64bit]: <http://downloads.sourceforge.net/tortoisesvn/LanguagePack_1.7.10.23359-x64-zh_TW.msi?download>