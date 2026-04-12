# 40.18 OdbDisplayOptions 对象

OdbDisplayOptions 对象存储与 [OdbInstance](pt01ch34pyo15.md) 对象关联的显示选项。此对象没有构造函数。创建 [OdbInstance](pt01ch34pyo15.md) 对象时，Abaqus 使用创建时当前视口的显示选项创建 OdbDisplayOptions 对象。

**访问**

```
import assembly
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions
import visualization
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions
import part
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions
```

### 40.18.1 成员

OdbDisplayOptions 对象具有以下成员：

*commonOptions*

 [DGCommonOptions](pt01ch40pyo02.md) 对象。

*superimposeOptions*

 [DGSuperimposeOptions](pt01ch40pyo22.md) 对象。

*contourOptions*

 [DGContourOptions](pt01ch40pyo03.md) 对象。

*symbolOptions*

 [DGSymbolOptions](pt01ch40pyo23.md) 对象。

*materialOrientationOptions*

 [DGOrientationOptions](pt01ch40pyo20.md) 对象。

*displayBodyOptions*

 [DGDisplayBodyOptions](pt01ch40pyo05.md) 对象。

