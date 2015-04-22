#UML介紹 3-關係(2)

今天接著介紹在UML中的 Association(結合關係), Generalization(一般化) 和 Implementation(實做)的圖形。
  
### Association（結合關係）
所謂的結合關係就是代表這兩者有關連，那是什麼樣的關連呢？就要看什麼樣的圖形了。通常如果只是一條線，現的兩頭什麼符號都沒有，那就只是代表這兩者有關係。那如果有箭頭，則代表A可到B、或B可到A，端看見頭方向而定。那如果是菱形空心或實心就是上面所介紹的shared aggregation 或composite aggregation。
  
而在結合的端點上，根據UML規格書上說明有以下幾種表示方式：
![][Association]
  
第一種代表A可以到B，B也可以到A。
第二種代表C不能到D並且D也不能到C，其實這個圖基本上是沒意義的。一開始也不是很清楚為什麼規格書上會有這樣的圖形，後來才發現，其實在畫圖的時候可以用X代表取消這兩個（C和D）的結合關係。
第三種就純粹代表E跟F有關係，至於方向就沒有特別強調。
第四種代表G可以到H，而H不能到G。
第五種基本上是與第四種一樣。I可以到J，J不能到I。
  
  
### Generalization（一般化）
其實在UML中的一般化也就是我們在寫程式時常講的「繼承」。只不過用一般化會比繼承來得貼切許多。因為，繼承會給人一種有先後的感覺。假設小孩繼承爸爸，那應該是先要有爸爸才會有小孩。可是仔細想想，我們在寫程式時，我們的父類別不都是由子類別去粹取(extract)出來的嗎？那如果用繼承不就是感覺怪怪的嗎？所以在UML裡才會用「一般化」來表示。下圖就是表示哺乳類是人類的「一般化」。如果寫程式可能就會講成：「人類繼承哺乳類」。
  
![][Generalization]
  
  
### Implementation（實做）
所謂的實做就是「實做一個或多個介面」。通常我們在做Refactor的時候，如果相同的行為被粹取（extract）出來時，通常都是以介面來表示。來看一下這個範例：
  
![][Implementation]
  
  
上圖就是表示軟碟、硬碟及USB都實做IO控制介面。
  
終於講完了，可是感覺還是有漏掉什麼。如果有不清楚的在麻煩大家給我一些些回饋囉！！^﹍^
  

[Association]: <https://www.dropbox.com/s/15ky651qk3jxxug/Day18-UML_Association.png?dl=1>
[Generalization]: <https://www.dropbox.com/s/wp2ujqyxdlqzc8o/Day18-UML_Generalization.png?dl=1>
[Implementation]: <https://www.dropbox.com/s/odo73mukab7b8s8/Day18-UML_Implementation.png?dl=1>