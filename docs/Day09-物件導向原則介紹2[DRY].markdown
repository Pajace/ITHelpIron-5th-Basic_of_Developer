物件導向原則介紹 2-DRY
=======================

#### 今天所要介紹的是物件導向的第二個原則: DRY(Do not repeat yourself)
  
在電腦的世界裡面，最擅長的就是做重複的事情。無論是你要它做10次、100次甚至是10000次，他都不會跟你說-好煩喔!反而是每次都會做得一模一樣。所以，當我們在寫程式的時候就不要去重複做一樣的事情，重複的事就交給電腦來做。
  
只是因為這是電腦的專長，所以就交給電腦來做嗎?
  
當然不是阿！
第一次聽到「DRY」這個觀念是在「深入淺出-物件導向分析與設計」這本書上看到的！他的核心概念就是
  
 > 『關於系統裡每一個資訊與行為的片段都存在單一、合理的地方。』
   
也就是說我們在設計程式時，絕對不要使用複製貼上或者重複的邏輯、變數或功能。因為只有開發程式的過程中，我們對於程式碼的熟悉度才是最高的。等過陣子很可能就會漸漸的變得陌生。如果在一個專案中，當我們想修改某一個變數時卻需要修改兩個或以上的地方，這時候就會非常容易被遺忘，蟲重危機也就慢慢地展開來了。
  
就這樣嗎？當然還不止囉！除了維護的議題之外，還有合理性…等。
  
根據Andrew Hunt及David Thomas所合著的The Pragmatic Programmer一書中將DRY分成四大部分：
  
1. 加強重複(Imposed duplication)
2. 無意的重複(inadvertent duplication)
3. 無耐心的重複(impatient duplication)
4. 開發者之間的重複(inter-developer duplication
  
無論是哪一種重複，基本上對軟體的傷害其實都不小，所要負擔的維護成本也相對的高很多。
  
### 加強重複
記得當我們在學習寫程式時，關於寫註解跟不寫註解其實有很大的爭議。以前的教科書上說，寫程式一定要寫註解，否則後人維護時會變得很困難。當時年紀小小的我覺得書上說的真是沒錯！後來畢業後，看了Uncle Bob所寫的一本書「Clean Code」。 書上說：『寫程式不要寫註解，只有寫的很糟的程式才需要註解』。 我又覺得，「阿！說的真好」（頓時覺得自己好像牆頭草，兩邊倒倒）。後來有稍稍長點智慧了之後發現，其實兩邊都對。註解還是要寫，只是看地方寫並且寫的要精簡。
  
關於註解還有另外一個問題：如果程式出問題需要修改時，改了程式碼讓程式恢復運作了。那註解呢？有改！沒改？對於使用者而言都沒差阿。如果時間很趕，你猜開發人員會不會忘了改呢？這時候又有一句格言了：
  
> 『錯誤的註解，比沒有更糟』
  
看看下面的C++範例：

```cpp .h檔
// 計算圓形場地面積  
// radius: 半徑  
// return: 面積  
double CalculateCircleArea(double radius);  
// 計算方形場地面積  
// length: 長  
// width : 寬  
// return: 面積  
double CalculateRectangleArea(double width, double length);  
// 計算三角形場地面積  
// base  : 底  
// height: 高  
// return: 面積  
double CalculateTriangleArea(double base, double height);  
```
  
```c++ .cpp 檔
// 計算圓形場地面積  
// radius: 半徑  
// return: 面積  
double CalculateCircleArea(double radius){  
    return radius*radius*PI;  
}  
  
// 計算方形場地面積  
// length: 長  
// width : 寬  
// return: 面積  
double CalculateRectangleArea(double width, double length){  
    return width*length;  
}  
  
// 計算三角形場地面積  
// base  : 底  
// height: 高  
// return: 面積  
double CalculateTriangleArea(double base, double height){  
    return base*height/2;  
} 
``` 
  
有沒有發現什麼問題呢？是不是在.h及.cpp出現了相同的註解。假設今天客戶要求，無論是什麼場地的面積都一律加上一倍的大小，因為所有的場地都變成雙層的！所以我將程式碼更改如下，但是我忘了改註解：
  
```c++
// 計算圓形場地面積  
// radius: 半徑  
// return: 面積  
double CalculateCircleArea(double radius){  
    return radius*radius*PI*2;  
}  
  
// 計算方形場地面積  
// length: 長  
// width : 寬  
// return: 面積  
double CalculateRectangleArea(double width, double length){  
    return width*length*2;  
}  
  
// 計算三角形場地面積  
// base  : 底  
// height: 高  
// return: 面積  
double CalculateTriangleArea(double base, double height){  
    return base*height;  
}  
```
  
這樣一來是不是就發生問題了：以後維護的人一定覺得很奇怪，公式好像不太對勁。以及兩邊重複的註解萬一不同，那麼那邊才是對的？
  
  
### 無意的重複
  
先來看個例子吧！有沒有看出什麼問題呢？
  
```
class 正方體 {  
    public double 長 { get; set; }  
    public double 寬 { get; set; }  
    public double 高 { get; set; }  
    public double 體積 { get; set; }  
}  
```
  
沒錯，我重複了體積這個屬性。如果有人將長、寬、高分別給予值2, 3, 4，接著又不小心把體積設成240，這時候蟲蟲就又跑出來了。
  
    
### 無耐心的重複
  
在寫程式的過程中不可穢言的，相信大家（當然包括我）都用過**CV**（Ctrl+C, Ctrl+V），我更相信又更多的人也犯了 **CV** 過去後卻忘了改某幾個變數，一直到程式出錯了才在想-奇怪！到底錯在哪裡。直到找到了之後又會說：「阿！就是這裡啦。厚~我怎麼會忘了改。」
  
或許聽起來很好笑，不過這卻是真真實時發生在很多人包含我身上的真實案例阿！以前老一備的常說：「甲ㄍ一ㄥˋ弄破碗，欲速則不達」，像這種無耐心的重複也是很傷的。
  
  
### 開發者之間的重複
  
這個我想應該是最難避免的一個重複議題了。因為這包含的範圍太廣，牽扯團對開發之間的溝通。我就先不提了。有興趣的人可以參考『The Pragmatic Programmer』這本書上有一些介紹！
  
### 結論：
上面所提到的都是屬於程式開發中的「重複」，這些重複一定要儘量避免。除了這些之外，還是有其他的重複，例如：在開發過程中可能需要用到某些工具，可能需要輸入一連串的指令，這時候也應該將這一連串的指令建立一個script或批次檔，不用每次都輸入相通的工作，也是能提高工作效率！反正，只要遇到重複的事情就交給電腦去做就對了！相信我，電腦絕對會做的比你好！
