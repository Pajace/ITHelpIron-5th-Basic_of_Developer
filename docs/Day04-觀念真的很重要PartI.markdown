我相信寫C#的人，應該還是有很多人對於C#的觀念不是很熟悉，就是會用而已！因為，C#實在是太方便了，很容易就可以上手。以我來說，我本來是寫Java的，後來因為工作關係，改寫C#，但也是到了最近我才明白一些觀念。但是，這些觀念真的很重要。因為，觀念若正確會少走很多冤枉路，也會較容易google到所需要的資料。若沒有正確的觀念，可能問題出現了，找也找不出來。
  
現在很多軟體開發的人員用的程式語言不是JAVA就是C#或C++，當然還有別的！但這三種我覺得應該是最多的吧！！
  
舉例來說，我相信寫C#的人，應該還是有很多人對於C#的觀念不是很熟悉，就是會用而已！因為，C#實在是太方便了，很容易就可以上手。以我來說，我本來是寫Java的，後來因為工作關係，改寫C#，但也是到了最近我才明白一些觀念。但是，這些觀念真的很重要。因為，觀念若正確會少走很多冤枉路，也會較容易google到所需要的資料。若沒有正確的觀念，可能問題出現了，找也找不出來。
  
例如：在.Net中有Value Type（數值型別）變數，也有Reference Type（參考型別）變數。但是，有多少人會知道這兩者差在那邊呢？我相信應該不多，因為，不知道差別照樣可以把程式寫好，照樣可以完成工作達到目的。那應該會有人會問說，既然如此，我為何需要知道。那是因為，現在的電腦普遍效能都很好，所以才會沒感覺。但是，如果哪天遇到效能的問題，不知道這兩者的區別，可能這個問題恐怕就要石沈大海了。
  
舉例來說 Value type 與 Reference type根據MSDN上的解釋：
Value type : 存的是自己的資料。
Reference type: 存的是參考，而這個參考是指向真實的資料位置。
  
而這兩種會透過boxing(裝箱)和unboxing(拆箱)操作來做互相轉換。然而在boxing與unboxing之間就會多耗掉一些效能，如果可以避免，必然會提高許多效能的。因為，Value type 是儲存在 stack、而Reference type 則是儲存在heap上。(Stack的速度較快，但容量較少；heap速度較慢，但容量較大)
  
又例如：String 與 StringBuilder，以下面兩個Function來說:
  
```c#
String CombineString1(String s1, String s2, String s3) {   
    String result = s1;  
    result += s2;  
    result =+ s3;  
    return result;  
}  
String CombineString2(String s1, String s2, String s3){  
    StringBuilder result = new StringBuilder();  
    result.Append(s1);  
    result.Append(s2);  
    result.Append(s3);  
    return result.ToString();  
} 
```
  
CombineString1 與 CombineString2 做的事情是一樣的，但是其效能就是完全不一樣。如果要結合的字串少，那還感覺不太出來，但是這個Function - CombineString1被使用的次數如果越多，那整體效能就會越差。因為字串在.NET中具有不可修改的特性，也就是說一旦初始化後就不能在被修改，所以每次更改都會強制建立一個新的字串物件。不過StringBuilder就不一樣了，它在內部有一個private的String 成員，並且只有在ToString()這個方法被呼叫時，才會將字串塞給這個 private 的 string成員。因此整個效能就大大的提升。
  
所以，雖然條條大路通羅馬，各種方式都可以達到我們所想要的功能，但是，如果在學習一個（程式）語言的時候，除了基本必的(常用的API)之外，其他的單字（也就是API）可以需要的時候在去查即可。但是，這個語言的基本特性，還有一些重要的觀念一定要先知道，否則真的會遇到很多很奇怪的問題，然後自己也搞不懂為什麼。