# 19.5 DebondVCCT 对象









DebondVCCT 对象定义激活使用 VCCT 进行裂缝扩展所需的参数。

DebondVCCT 对象派生自 [Crack](pt01ch19pyo04.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.cracks[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.cracks[*name*]
```

### 19.5.1 DebondVCCT(...)

此方法创建 DebondVCCT 对象。尽管构造函数可用于部件和装配，但 DebondVCCT 对象目前仅在装配下支持。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.DebondVCCT
mdb.models[*name*].rootAssembly.engineeringFeatures.DebondVCCT
```

**必需参数**

*name*

一个 String，指定存储库键。

*initiationStep*

一个 String，指定创建 DebondVCCT 对象的步骤名称。

*surfToSurfInteraction*

一个 String，指定定义裂缝表面之间表面到表面接触的 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md) 对象的名称。

**可选参数**

*debondingForceAmplitude*

一个 SymbolicConstant，指定裂缝尖端处两个表面之间的脱粘力是在脱粘后的下一个增量中立即释放还是逐渐释放。可能的值为 STEP 和 RAMP。默认值为 STEP。

*printToDATFrequency*

一个 Int，指定输出打印到 DAT 文件的频率。默认值为 1。

**返回值**

一个 DebondVCCT 对象。

**异常**

无。

### 19.5.2 setValues(...)

此方法修改 DebondVCCT 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DebondVCCT](pt01ch19pyo05.md#ker-debondvcct-debondvcct-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.5.3 成员

DebondVCCT 对象具有与 [DebondVCCT](pt01ch19pyo05.md#ker-debondvcct-debondvcct-pyc) 方法的参数相同的名称和描述的成员。

此外，DebondVCCT 对象还有以下成员：

*suppressed*

一个 Boolean，指定裂缝是否被抑制。默认值为 OFF。

### 19.5.4 对应的分析关键字

| [*DEBOND](../key/key-link.md#usb-kws-hdebond) |
| --- |





