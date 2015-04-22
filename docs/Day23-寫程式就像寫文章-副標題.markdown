不論是礦世巨作或者是散文小品，都一定會有內文。而內文就是屬於細節！
軟體開發也是一樣！小程式或者大系統，也一定都會有細節，可是如果把所有的細節都兜在一起，那會是什麼情況呢？
  
不論是礦世巨作或者是散文小品，都一定會有內文。而內文就是屬於細節！
軟體開發也是一樣！小程式或者大系統，也一定都會有細節！
  
小時候寫作文時，老師都會要求一個段落不要寫太長，要適時的分段、分句。如果能做到起承轉合更好。那寫程式呢？老師卻沒說一個函示（Method）不要太長。
  
今天要跟大家介紹的的就是，怎麼樣寫才算是一個比較好的函示(Method)，長度多少才比較剛好。在介紹之前，先說個書上的真實小故事：
  
時間是在1999年的時候（13年前了XD），[Robert Martin][Robert_Martin] 去 [Kent Beck][Kent_beck] 家中拜訪他時，Kent Beck 秀一段程式碼給 Robert 看。那是一個叫做 Sparkle 的程式，是用 Java Swing 寫的。這支程式會在滑鼠的游標上做一些特效，不過重點是當 Robert 看到原始碼的時候，他嚇到了！因為每一個 method 不是一行、就是兩行、三行最多四行（不含註解）。
  
天哪，13年前耶！他就有如此的功力！Kent Beck大師說過：每個 Method 只做一件事，並且把那件事做好，因為只能做一件事。
  
或許我們會想，怎麼可能那麼少行阿！可是仔細想想，我們寫文章不也是如此！可能這個大段落我們會給一個子標題，每個子標題裡面又會有很多個副標題，接著才是文章的內容。相對的每個Method也是阿！我們一個Method裡面可能也會呼叫好幾個private method組合起來成為一個大功能。
  
舉例來說，我這個method的目的是要擷取台灣銀行今天的黃金報價，然後回傳。

```c#
public decimal GetGoldPriceToday() {  
    var 網頁資料 = getWebPageData(某某某網址);  
    var 黃金價格 = GoldParser.GetGodPrice(網頁資料);  
    return 黃金價格;  
}  
```
  
是不是，只有三行！！這是主要的Method，他會再去呼叫其他的Method來完成這個工作！
  
[Robert_Martin]: <http://en.wikipedia.org/wiki/Robert_Cecil_Martin>
[Kent_beck]: <http://www.techcn.com.cn/index.php?doc-view-131735.html>