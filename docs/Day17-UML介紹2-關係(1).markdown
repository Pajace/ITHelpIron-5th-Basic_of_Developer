人與人之間的關係可能很複雜，但是在設計程式的時候關係儘量簡單一點比較好。今天就是要跟大家介紹圖形與圖形之間的關係！
接下來要幫大家介紹的是：
  
1. Shared aggregation
2. Composite aggregation
3. Association
4. Generalization
5. Implementation
  
這五種關係..
  
人與人之間的關係可能很複雜，但是在設計程式的時候關係儘量簡單一點比較好。今天就是要跟大家介紹圖形與圖形之間的關係！
  
有寫過程式的人一定都知道寫程式會用到：組合(Composition)、聚合(Aggregation)、繼承(extends)、使用(use)…等關係。所以如果要用圖形語言來表達，這些關係的表示方式一定是不能少的。
  
![][Relation]
  
### Shared aggregation(分享的聚合):
  
![][SharedAggregation]
  
上圖表示一搜船可以有多顆引擎，如果船沒了引擎也可以給另一艘船用。也就是說：船與引擎的生命週期不是共生共存的意思。引擎是屬於part，而船是屬於whole。
  
### Composite aggregation(組合關係):
  
![][CompositeAggregation]
  
上圖是表示，一隻智慧型手機（Whole）中，有一個面板、一顆電池、及1至三根天線的意思。用Composition來表示則代表這whole-part的生命週期是一致的，假設手機壞了這些零件也就會跟著報廢的意思。
  

[Relation]: <https://www.dropbox.com/s/m8lmfhz1ajcsbxd/Day17-UML_relation.png?dl=1>
[SharedAggregation]: <https://www.dropbox.com/s/3ovf1s72om7zsrr/Day17-UML_shared_aggregation.png?dl=1>
[CompositeAggregation]: <https://www.dropbox.com/s/hoszbwvcazf4rxy/Day17-UML_composite_aggregation.png?dl=1>