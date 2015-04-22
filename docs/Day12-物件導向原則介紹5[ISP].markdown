物件導向原則介紹 5-ISP
======================

目前在寫程式這方面，大部分使用的都是物件導向（Object Oriented），在連續介紹了四個原則之後，今天在介紹的是第五個-ISP(Interface Segregation Principle) 介面分割原則。雖然這些原則感覺很枯燥，不過忍耐一下，這些原則如果看過了之後，多少都會在心裡有個底。對於程式開發也一定會有幫助的！
  
 > 所謂的介面分離原則就是：『用戶不應該被迫相依於他們用不到的函示』
   
其實這個我昨天提到的Liskov替換原則有點相近，如果我實做的介面有三個函示，而我只實做了兩個，另一個我根本不能用或者是不要用。那這時候就違反了這個ISP（介面分割原則），此時我這個類別也等於無法相容於基礎類別，那又違反了Liskov替換原則了。
  
所以 **寧願多用幾個介面**，也不要將很多個方式全部放到一個介面當中讓來實做的類別誤用，污染了這個介面。
  
來看一下這個範例：
```c#
interface I工人介面 {  
    public void 吃飯();  
    public void 工作();  
}  
  
class 工人 : I工人介面 {  
    public void 工作() {  
        Console.WriteLine("工作~工作~");  
    }  
  
    public void 吃飯() {  
        Console.WriteLine("吃飯休息囉~");  
    }  
}  
  
class 超級賽亞工人 : I工人介面 {  
    public void 工作() {  
        Console.WriteLine("工作*3~工作*3~");  
    }  
  
    public void 吃飯() {  
        Console.WriteLine("吃飯休息囉~");  
    }  
}  
  
class 總管 {  
    I工人介面 工人;  
  
    public void 安排工人(I工人介面 被安排的工人) {  
        工人 = 被安排的工人;  
    }  
  
    public void 開始工作() {  
        工人.工作();  
    }  
}  
```
  
看起來好像沒什麼問題吧！但是，如果我的工人裡有機器人呢？那怎麼辦？如果讓機器人直接實做I工人介面，那機器人就會被強迫實做「吃飯（）」這個函示，這時候鐵定是行不通的。讓我們將程式碼修改如下：
  
```c#
interface I可以吃{  
    public void 吃飯();  
}  
  
interface I可以工作{  
    public void 工作();  
}  
  
class 工人 : I可以吃, I可以工作 {  
    public void 工作() {  
        Console.WriteLine("工作~工作~");  
    }  
  
    public void 吃飯() {  
        Console.WriteLine("吃飯休息囉~");  
    }  
}  
  
class 超級賽亞工人 : I可以吃, I可以工作 {  
    public void 工作() {  
        Console.WriteLine("工作*3~工作*3~");  
    }  
  
    public void 吃飯() {  
        Console.WriteLine("吃飯休息囉~");  
    }  
}  
  
class 機器人 : I可以工作 {  
    public void 工作() {  
        Console.WriteLine("工作*3~工作*3~");  
    }  
}  
  
class 總管 {  
    I可以工作 工人;  
  
    public void 安排工人(I可以工作 被安排的工人) {  
        工人 = 被安排的工人;  
    }  
  
    public void 開始工作() {  
        工人.工作();  
    }  
}  
```
  
看到了嗎？我將工人的介面拆成「可以吃()」和「可以工作()」這兩個介面。這樣一來機器人只要實做可以工作就好了，也就不會違反ISP(介面分割原則)了。
  
後記：
這幾天在寫文章的時候發覺，用中文寫真的好不習慣喔。感覺滿怪的！大家覺得這樣可讀性真的有比較好嗎？