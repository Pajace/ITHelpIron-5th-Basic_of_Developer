#總結

在這三十天裡，每天寫一篇文章的確是有難度的。
一開始我有小小的擬定了一下每天要寫的內容，可是到後來都走偏了，原本沒想到要介紹的跑了出來，預定要介紹的卻又縮了回去。
  
我這次鐵人賽的主題是：軟體路上不孤單，主要的方向就是要介紹開發軟體！那為什麼這麼廣呢？因為小弟我深怕寫不出東西來，定的廣才好寫！不過寫到後來我發現，真的是定太廣了，好多東西都是點到而已，很基本、都是概念。
  
另外有個東西我忘了介紹，趁最後一天的文章我一定要提一下才行，那就是軟體開發的架構。
  
在軟體開發時有一件事情非常重要，就是「三層式的架構」。
![][3tier]
  
因為唯有將這三層分別開來，我們的軟體才有機會寫的夠彈性、夠軟，也才能夠測試！
  
我舉一個最簡單的例子：加法器。
相信大家對下面的程式碼一定非常熟悉。
  
```c#
private void ButtonClick(){  
    int a = int.Parse(NumberA.Text);  
    int b = int.Parse(NumberB.Text);  
    int result = a + b;  
    NumberC.Text = result.ToString();  
}  
```
  
其中 NumberA, NumberB 以及 NumberC 畫面上的 TextBox 。
  
可是這樣寫有個問題，要怎麼測試呢？現在是因為加法所以看起來很容易，很簡單。可是如果把加法改成非常複雜的計算呢？那不就是無法測試了。
  
所以程式邏輯一定要跟UI及DB完全切割開來，這樣骨架對了，程式邏輯怎樣亂寫都是可以重構成比較好結果。
  
```c#
private void ButtonClick() {  
    int a = int.Parse(NumberA.Text);  
    int b = int.Parse(NumberB.Text);  
    int result = Adder.add(a, b);  
    NumberC.Text = result.ToString();  
}  
```
  
這樣一來，我們就把加法這個邏輯給抽離開來了！下次如果有更複雜的運算，我們也只需要針對那個物件做測試。UI怎麼改跟程式邏輯就沒關係了！


[3tier]: <https://www.dropbox.com/s/fnb9iby49rc01sh/Day30-3tier.png?dl=1>