#寫程式就像寫文章-排版

文不如表，表不如圖！
那一表呢？三千里！不是啦~
此表非彼表~（又扯遠了XD）
  
今天想要介紹的是排版的觀念，那根圖表有什麼館係呢？
其實是沒什麼關係！但是也是有點關係！因為文字密密麻麻的，所以需要兩好的排版才會讓人一目了然。雖然文不如表，但是排版若排的好，「文」也是會有像「表」一樣的功能的！
  
再一開始參加鐵人賽的前幾天，因為沒有寫文章的習慣，因此寫出來的文章-之的很難看！怎麼說呢，因為我都沒有留白的概念！一段接著一段好像要省空間似的，反倒讓人要很用力才知道，我到底在講什麼。（感謝前輩們的提醒阿，後來我去改掉了。）雖然現在分段的功力還不是很好，但至少我有留白的觀念了！
  
寫程式也是如此！
  
將相關的函示、變數放在附近，對後來維護的人看起來也比較輕鬆。適時的留白也會讓閱讀程式碼的人更容易瞭解程式碼的內容。
  
看看這個沒有留白的範例：
```c#
using System;  
using System.Windows.Controls;  
using Microsoft.Phone.Controls.Primitives;  
namespace Microsoft.Phone.Controls {  
    abstract class DataSource : ILoopingSelectorDataSource {  
        private DateTimeWrapper _selectedItem;  
        public object GetNext(object relativeTo) {  
            DateTime? next = GetRelativeTo(((DateTimeWrapper)relativeTo).DateTime, 1);  
            return next.HasValue ? new DateTimeWrapper(next.Value) : null; }  
        public object GetPrevious(object relativeTo) {  
            DateTime? next = GetRelativeTo(((DateTimeWrapper)relativeTo).DateTime, -1);  
            return next.HasValue ? new DateTimeWrapper(next.Value) : null; }  
        protected abstract DateTime? GetRelativeTo(DateTime relativeDate, int delta);  
..(略)  
        public event EventHandler<SelectionChangedEventArgs> SelectionChanged;  
    }  
..(略)  
}  
```
  
如果給予適當的留白：
```c#
using System;  
using System.Windows.Controls;  
using Microsoft.Phone.Controls.Primitives;  
namespace Microsoft.Phone.Controls {  
    abstract class DataSource : ILoopingSelectorDataSource {  
      
        private DateTimeWrapper _selectedItem;  
          
        public object GetNext(object relativeTo) {  
            DateTime? next = GetRelativeTo(((DateTimeWrapper)relativeTo).DateTime, 1);  
            return next.HasValue ? new DateTimeWrapper(next.Value) : null;   
        }  
          
        public object GetPrevious(object relativeTo) {  
            DateTime? next = GetRelativeTo(((DateTimeWrapper)relativeTo).DateTime, -1);  
            return next.HasValue ? new DateTimeWrapper(next.Value) : null;   
        }  
          
        protected abstract DateTime? GetRelativeTo(DateTime relativeDate, int delta);  
      
    ..(略)  
  
        public event EventHandler<SelectionChangedEventArgs> SelectionChanged;  
    }  
  
    ..(略)  
  
} 
```
  
是不是感覺好很多呢！
另外，如果有留白但卻多了註解那這樣的排版會變怎樣呢？
```c#
public class Reporter {  
      
    /** 
    *  Reporter listener 的類別名稱 
    */  
    private String className;  
      
    /** 
    *  Reporter listener 的屬性 
    */  
    private List<Property> properties = new ArrayList<Property();  
      
    /** 
    *  增加屬性 
    */  
    public void addProperty(Property property){  
        properties.add(property);  
    }  
}  
```
  
是不是感覺還好，只是有那麼一點怪，因為多了一些註解。
若改成這樣：
```c#
public class Reporter {  
      
    private String className;  
    private List<Property> properties = new ArrayList<Property();  
  
    public void addProperty(Property property){  
        properties.add(property);  
    }  
}  
```
  
各位覺得如何呢？
  
當然，不是說一定不要加註解，或一定要怎麼樣排版。我相信每個團隊都會有自己的 guideline ，只要大家統一好。因為相同的 排版（好的排版）一定對程式碼的 **可讀性** 有一定的貢獻。今天介紹 **排版** 只是想再強調一下，它其實還滿重要的！

