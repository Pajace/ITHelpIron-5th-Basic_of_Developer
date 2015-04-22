物件導向原則介紹 7-DIP
======================

今天要介紹的是「相依性反轉原則」(DIP, Dependency Inversion Principle)，但這個原則也是最容易被程式設計師給忽略的！（例如我）
  
所謂的相依性反轉就是
  
 > 高階模組不要依賴低階模組，兩者都必須要依賴抽象模組；
 > 抽象不能依賴細節，細節必須依賴抽象
   
聽起來好像真的很抽象！但如果瞭解了核心意義後，就會覺得一點也不抽象了。舉個我們IT人最喜歡的電腦為例：電腦中有很多零組件，有硬碟、顯示卡、CPU…等等零件。拿硬碟來說，硬碟的廠商有A廠商、B廠商、C廠商…等等。可是，不管是A或B或C廠商的硬碟，只要介面一樣我們都可以裝在我們的電腦上（例如SATAII）。
  
我們可以把SATAII這個介面當想成是「抽象」，而各個廠商的硬碟想成是細節（也就是實做）。所以各加廠商都依賴「抽象（SATAII）」而實做出（SATAII的）硬碟。這樣到我們的手上才可以使用。如果各家廠商都用自己覺得最快的方式做出他們自己的硬碟，那們我們就會被綁死。因為，互相都不能相容阿~
  
接下來我們就用硬碟這個例子來看的範例吧！！
  
首先是違反DIP的範例：

```c#
class PC {      
    private HDD _hdd1;  
    public HDD HDD1 {   
        get { return _hdd1; }   
        set { this._hdd1 = value; }   
    }      
    public void UseHDD1 {  
        // Do something here  
    }  
}  
  
class HDD {  
    public void WriteData(string data) {  
        // Write data into HDD  
    }  
    public void ReadData(string data) {  
        // read data from HDD  
    }  
}  
```
  
如果要使用，就會向下面這個樣子：

```c#
    HDD hdd = new HDD();  
    PC myPC = new PC();  
    myPC.HDD1 = hdd;  
}  
```
  
看到了嗎？PC中有一顆硬碟，但是這硬碟並沒有依賴「抽象」反而是依賴「細節」（也就是實做）。如果哪一天我的硬碟要增加其他的功能或者要更換另一種更好的，那我勢必要修改HDD這個類別才能達到目的。所以，我將成是更改如下：

```c#
class PC {  
  
    private HDD _hdd1;  
    public HDD HDD1 {  
        get { return _hdd1; }  
        set { this._hdd1 = value; }  
    }  
  
    public void UseHDD1 {  
        // Do something here  
    }  
}  
  
abstract class HDD {  
    abstract public void ReadData();  
    abstract public void WriteData();  
}  
  
class MyHDD:HDD {  
  
    public override void ReadData() {  
        // Do something here  
    }  
  
    public override void WriteData() {  
         // Do something here  
    }  
}  
```
  
使用方式如下：  

```c#
public void example() {  
    HDD myHdd = new MyHDD();  
    PC myPC = new PC();  
    myPC.HDD1 = myHdd;  
}  
```
  
如此樣子一來，如果有更新的HDD，我只要再增加一個硬碟就可以了，不需要再去修改HDD這個類別，而我原本的程式碼自然也不需要做更動了！
  
說到這裡有沒有感覺很與之前介紹的某一個原則很類似呢？沒錯，就是 **「開放／封閉原則」(OCP, Open / Close Principle)** 。其實這幾個原則如果常常看，把他們記在心理，就會發現這些原則真的會有某些部分的交集，因為目的都是一樣的！對吧！
