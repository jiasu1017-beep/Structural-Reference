# 50.9 MassScaling 对象

MassScaling 对象定义质量和控制质量缩放的区域。

**访问**

```
import step
mdb.models[*name*].steps[*name*].massScaling[*i*]
```

### 50.9.1 成员

MassScaling 对象可以具有以下成员：

*objective*

一个 SymbolicConstant，指定质量缩放定义的目标。可选值为 SEMI_AUTOMATIC、AUTOMATIC 和 REINITIALIZE。默认值为 SEMI_AUTOMATIC。

*occurs*

一个 SymbolicConstant，指定是在步骤开始时还是在整个步骤中执行质量缩放。可选值为 AT_BEGINNING 和 THROUGHOUT_STEP。

*type*

一个 SymbolicConstant，指定缩放类型。可选值为 UNIFORM、BELOW_MIN、SET_EQUAL_DT 和 ROLLING。默认值为 BELOW_MIN。

*factor*

一个 Float，指定缩放因子。

*dt*

一个 Float，指定目标时间增量。

*frequency*

一个 Int，指定执行质量缩放计算的频率。

*numberInterval*

一个 Int，指定执行质量缩放计算的间隔数。

*feedRate*

一个 Float，指定稳态条件下轧制方向上工件的估计平均速度。

*extrudedLength*

一个 Float，指定挤压方向上的平均元素长度。

*crossSection*

一个 Int，指定工件横截面中的节点数。

*direction*

一个 SymbolicConstant，指定轧制方向。可选值为 GLOBAL_X、GLOBAL_Y、GLOBAL_Z 和 GLOBAL_NONE。默认值为 GLOBAL_X。

*region*

SymbolicConstant MODEL 或一个 [Region](pt01ch45pyo03.md) 对象，指定应用质量缩放的位置。默认值为 MODEL。
