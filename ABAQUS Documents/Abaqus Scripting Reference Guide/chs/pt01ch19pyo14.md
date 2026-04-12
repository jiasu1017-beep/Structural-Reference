# 19.14 SpringDashpotToGround 对象









SpringDashpotToGround 对象定义部件或装配区域上点与地面之间的弹簧和/或阻尼器。

SpringDashpotToGround 对象派生自 [SpringDashpot](pt01ch19pyo13.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.springDashpots[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.springDashpots[*name*]
```

### 19.14.1 SpringDashpotToGround(...)

此方法创建 SpringDashpotToGround 对象。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.SpringDashpotToGround
mdb.models[*name*].rootAssembly.engineeringFeatures\
.SpringDashpotToGround
```

**必需参数**

*name*

一个 String，指定存储库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用弹簧和/或阻尼器的区域。

*dof*

一个 Int，指定与弹簧和阻尼器行为相关联的 degrees of freedom。

**可选参数**

*orientation*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定弹簧和/或阻尼器的局部方向。如果 *orientation*=`None`，则弹簧和/或阻尼器数据在全局坐标系中定义。默认值为 `None`。

*springBehavior*

一个 Boolean，指定是否将弹簧行为应用于所选点。默认值为 OFF。

必须指定 *springBehavior*=ON 或 *dashpotBehavior*=ON 中的至少一个。

*dashpotBehavior*

一个 Boolean，指定是否将阻尼器行为应用于所选点。默认值为 OFF。

必须指定 *springBehavior*=ON 或 *dashpotBehavior*=ON 中的至少一个。

*springStiffness*

一个 Float，指定弹簧的相对位移力。默认值为 0.0。

*dashpotCoefficient*

一个 Float，指定阻尼器的相对速度力。默认值为 0.0。

**返回值**

一个 SpringDashpotToGround 对象。

**异常**

无。

### 19.14.2 setValues(...)

此方法修改 SpringDashpotToGround 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SpringDashpotToGround](pt01ch19pyo14.md#ker-springdashpottoground-springdashpottoground-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.14.3 成员

SpringDashpotToGround 对象具有与 [SpringDashpotToGround](pt01ch19pyo14.md#ker-springdashpottoground-springdashpottoground-pyc) 方法的参数相同的名称和描述的成员。

此外，SpringDashpotToGround 对象还有以下成员：

*suppressed*

一个 Boolean，指定弹簧/阻尼器是否被抑制。默认值为 OFF。

### 19.14.4 对应的分析关键字

| [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=SPRING1; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=DASHPOT1; [*SPRING](../key/key-link.md#usb-kws-mspring); [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |





