#UML介紹 5-活動圖介紹

![][UML-ControlNodes]
這些符號都認識嗎，如果不認識那就繼續往下看吧！！
  
今天要介紹的是活動圖(Activity Diagram)。
活動圖主要是一系列的程序顯示出來，在這些程序中包含了系統要做的事情，也可以包含非系統做的事情。當然，主要的目的還是為了溝通，所以還是以不要將活動圖繪製得太複雜為原則。
  
首先先來介紹下列圖形的說明：
![][UML-ActionObjectsNodes]
  
### 活動節點（Action node）：  
根據UML裡的定義是說：『An activity node is an abstract class for points in the flow of an activity connected by edges.』看起來似乎有點複雜，可是，在看過例子之後就會覺得其實沒那麼複雜。因為每一個節點就是可以看做一個事件，例如：下訂單、申請成績單…等。
  
### 物件節點（Object node）：   
一般來說我是比較少看到有人用，可能我用的不多吧！物件節點與活動節點最大的差別就是，活動節的是不攜帶任何資料的，而物件節點是有攜帶資料，這個稍後我們可以從範例中可以很清楚的看出來。
  
### 控制節點(Control Node)的圖形如下：   
![][UML-ControlNodes]
  
### 啟始節點(Initial node)：   
每一張活動圖一定要有一個開始的地方，而這個地方就是叫做啟始節點(Initial node)。
  
  
在UML中有兩種終止節點(Final nodes)：**活動終止(Activity final)**及**流程終止(flow final)**。而這兩種分別代表不同的終止意思。
  
**Activity final** 代表的是整個Activity Diagram的流程終止。
**Flow final** 代表的是Activity Diagram的分支流程終止，這時候如果有其他流程在跑，則不會受到該分支流程終止的影響。
  
**Merge node(合併節點)** 與 **Decision node(判斷節點)**:   
顧名思義，就是合併不同分支及判斷流程(flow)該往那個分支的意思。
  
**控制流成(Control flow)** 與 **物件流程(Object flow)** 最大的差別就是在，控制流程無發攜帶任何資料或物件給下一個流程，而物件流程可以攜帶資料或物件。



![][UML_ControlFlow]
![][UML_ObjectFlow]
從上方兩個圖就可以看出，活動節點(activity node)與活動節點之間一定是控制流程(Control flow)，而活動節點與物件節點(object node)之間就是物件流程(object low)。


[UML-ControlNodes]: <https://www.dropbox.com/s/ubvvtcio3v9qfx3/Day20-UML_ControlNodes.png?dl=1>
[UML-ActionObjectsNodes]: <https://www.dropbox.com/s/88w4pj7swihm47g/Day20-UML_nodes_action_object.png?dl=1>
[UML_ControlFlow]: <https://www.dropbox.com/s/vxynescnidy9vvz/Day20-UML_ControlFlow.png?dl=1>
[UML_ObjectFlow]: <https://www.dropbox.com/s/8efk0h39zhpyd45/Day20-UML_ObjectlFlow.png?dl=1>