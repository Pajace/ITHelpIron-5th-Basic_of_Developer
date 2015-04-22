#C++測試框架介紹

昨天我們談到軟體開發很重要的一環 – 測試!
那寫 Test Case 到底要怎麼寫呢? 自己寫嗎?
有沒有好用的工具呢? 
今天為大家介紹一套我個人很愛用，也覺得很棒的 Testing Framework!
  
今天要為大家介紹的是 C++ Testing Framework，也是我第一次使用C++開發軟體時所使用的測試框架! 
  
這個 Framework 全名為 **Google C++ Testing Framework**，顧名思義，他是Google所開發出來的 Testing Framework，並且我們最常使用的 Chrome 也是使用這套 Testing Framework 去開發的! 既然全世界數一數二的軟體公司都用了，為什麼我們還不用呢!!
  
### 在開始寫 Test Case 之前  
  
通常寫測試程式最重要的就是，**測試程式不含邏輯**
因為如果你的測試程式內涵邏輯，那你就又必須寫另一個測試工具來測你的測試程式有沒有寫錯!
  
根據 91 大大對測試程式的規範，測試程式只做三件事情:  
  
1.Arrange (準備, 準備要測試的物件)
2.Act(行動, 做要被測試的動作)
3.Assert(驗證, 驗證動作後的結果是不是你要的)
就只有這三件!!
  
### 開始介紹
這個測試框架我認為最大的優點就是，使用起來很簡單，並且在Linux或Windows下都能使用!(如果你覺得Visual Studio內建的C++ Testing Framework不是那麼好用的話，你可以考慮試試看這個測試框架)  
![][google_cpp_testing_framework]
  
  
今天先介紹基本的使用方式，明天在介紹如何安裝。(基本上下載只後可以使用CMAKE將Google C++ Testing Framework build 出 .lib 再把他 include 到你的C++專案就可以了! )
  
其實也沒什麼特別的地方，最常用的API就是:
```c++
ASSERT_TRUE(condition);  
ASSERT_FALSE(condition);  
ASSERT_EQ(expected, actual); 
```
  
這三個。
  
當然還是有更進階的應用，明天再繼續為大家介紹!



[google_cpp_testing_framework]: <https://www.dropbox.com/s/a9s00wbe6t2s7h3/Day29-DownloadGoogleCppTestingFramework.png?dl=1>