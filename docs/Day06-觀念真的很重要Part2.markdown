觀念真的很重要 Part2
====================

今天想要介紹的是IDE的觀念篇!! IDE不是神，但是有IDE幫忙卻有如神助!!

IDE(integrated development environment)，也是我們在開發程式時的最常用的工具。例如: Visual Studio或Eclipse或DEV-C++ …等，這些開發工具就稱為IDE。

為什麼想介紹IDE的使用觀念呢?因為小弟剛開始就是缺乏這些觀念，以為會程式語法了就可以開始用IDE開發工具來寫程式。

一開始如果使用的很順利的話或者沒遇到什麼問題時就可能會覺得，就這樣用就好啦!!講那麼多做什麼。那是因為有太多太多的工作都被IDE幫我們做掉了，所以我們才能專心地把心思都放在程式開發這件事上，只要管好我們自己的Class，或這用到什麼Pattern...等，其他的都可以不用去理會。其實這樣可能會浪費掉IDE給予我們許多方便的工具或者當我們開啟別人的專案時，就會有常常Build不過或者Release Build過了，偏偏Debug Build就是不會過，這樣要怎麼Debug阿~等等其奇怪怪的問題。

說了這麼多，首先我先介紹一開始我遇到的幾個常常會被新手忽略的觀念!!在此我先以C++為例子做說明:

### 1.Debug build & Release build: 
通常在開發階段，我們都會用 Debug build 來產生執行檔或者Library，這樣的好處是當我們在使用IDE做DEBUG時，每個變數的值都可以看得到，可以很清楚我們要的值到底是什麼。相對的Release build 裡面當然就不會有這些用來做Debug的資訊，加上 Release build 會做很多最佳化的動作，讓程式小一點以及快一點。這時候千萬不要說，你還在用 printf() 或 cout 做 debug 的動作!嘗試學著用IDE來做debug，若程式已經上線甚至可以使用 debugview 來做debug這樣一定會比用輸出來做 debug 更有效率更方便。

當然IDE可以使用的Build configuration絕對不止這兩種。如果你的電腦的OS是x64的版本，在同一份source code 你還可以同時 build x86 及 build x64 的版本。如果再更強一點，甚至還可以同時build for win7, build for win8, build for vista..等等。這些如果都要用指令慢慢輸入，那真的是每 compile 一次都會花上很多時間，重點是還必須有 build configuration 的觀念才會想去做這些動作。

### 2. Static and Dynamic Library:
(1) .lib 及 .dll 的差別 
(2) 如何去 include 別人的 .h 檔

(1) 這個其實是C++本身就有的功能，只是我們可以利用IDE幫我們做掉!否則自己做當然也可以，只是每次要 build source code 時，你就要輸入一堆又臭又長的指令。
.lib 的 library又稱作靜態連結。也就是說，當我們在開發的時候會用到 .lib 的 library。而當我們程式產生出來後，不用將 .lib 交於客戶，.lib的資料本身就會包含在我們的程式檔案裡了。
.dll 就跟 .lib 剛好項反。.dll又稱為動態連結，也就是說當我們在build source code 時，如果沒有.dll其實是沒差的!!但是，當我們要執行程式時 .dll 檔一定要在程式的同一個目錄底下，否則程式就會因為沒有.dll檔而無法執行。
(2) 那 include 別人的 .h 呢?這個動作是在 compile time 時去做的，所以我們可將這些 .h 的路徑預先輸入在 IDE 中，這樣每次 compile IDE 就會自動幫我們加上 "-I被include的目錄" 這個動作了。

### 3. C++有個很方便的 Preprocessor 可以用
相信有去下載C++所寫的 source code 一定會很容易就看到 #def, #ifdef …等符號。其實這些符號後面就可以接Preprocessor。舉例來說，我在開發程式的時候我希望我在 debug 的版本會印很多我需要的 log 到檔案中，但是到了release 版本時，我又不希望他印這麼多，因為這樣一來除了會拖慢速度，而且也不太適合這樣做。但是我又不想寫兩份 source code ，這時候我就可以利用 Preprocessor 來幫我達到這樣的功能。以 Visual Studio 為例，他在 debug 版本時，他就會預先幫你輸入一個 Preprocessor :_DEBUG, 而 Release 版本則是:NDEBUG。當然，我們也可以定義我們自己想要的 Preprocessor。那這個 Preprocessor 要怎麼使用呢?請看下面的範例:

```c++
Void printVersion() {  
#ifdef _DEBUG  
    cout << “I am debug version” << endl;  
#else  
    cout << “I am release version” << endl;  
#endif  
}  
```

當我們在 Compile 的時候， compiler 就會去判斷，假設我們有定義 _DEBUG 他就會自動忽略掉印出 “I am release version” 這行，當作他不存在。那若是沒有定應 _DEBUG 這個 Preprocessor 呢?當然就是會忽略掉 ”I am debug version” 這行囉!!上面只是個例子，Preprocessor 還是可以有更多的應用的!!

## 結論:
以上所介紹的其實都是程式語言本身就有的功能，只是我們可以利用IDE讓我們在compile程式時可以更輕鬆，專心在開發的工作上面。如果說我可以用Visual Studio來使用Preprocessor這個功能，我當然也可以在Eclipse CDT上面使用這個功能。請記住，IDE他只是幫我們節省很多繁瑣制式的工作而已，所以，盡量地去熟悉程式語言的功能，再去IDE找出相關的設定，這樣一來開發程式就會變得輕鬆許多!!

## 後記:
記得一開始我還沒有這個觀念時，我在用 C++ 開發工具時，我用的是 Google C++ Testing Framework ，我可是寫了很多的 script 來幫助我 Compile 以及執行測試等相關功能。如果那時候我有這個觀念，我只要利用IDE就可以完成這些工作了，只要一個按鍵就個完成，豈不是輕鬆又愉快!!!
