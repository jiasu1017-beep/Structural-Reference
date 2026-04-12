# 11.3 Layer 对象

可以通过在不同图层中显示对象来实现对象叠加。

**访问**

```
session.viewports[*name*].layers[*name*]
```

### 11.3.1 Layer(...)

此方法在 Layer 存储库中创建 Layer 对象。

**路径**

```
session.viewports[*name*].Layer
```

**必需参数**

*name*

String，指定存储库密钥。

**可选参数**

*copyViewName*

String，指定要复制的图层名称。

**返回值**

Layer 对象。

**异常**

无。

### 11.3.2 moveBefore(...)

此方法将图层对象移动到层存储库中另一个对象之前。

**必需参数**

*name*

String，指定另一个 Layer 对象的名称。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 11.3.3 moveAfter(...)

此方法将图层对象移动到层存储库中另一个对象之后。

**必需参数**

*name*

String，指定另一个 Layer 对象的名称。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 11.3.4 成员

Layer 对象的成员与 [Layer](pt01ch11pyo03.md#ker-layer-layer-pyc) 方法的参数具有相同的名称和描述。

此外，Layer 对象可以具有以下成员：

*displayedObject*

[Displayable](#ker-displayable-pyc) 对象，指定要显示的对象。[Displayable](#ker-displayable-pyc) 类型是一个抽象概括。具体的可能类型为 [Part](pt01ch37pyo01.md)、[Assembly](pt01ch06pyo01.md)、[ConstrainedSketch](pt01ch48pyo01.md)、[Odb](pt01ch34pyo01.md) 或 [XYPlot](pt01ch55pyo16.md)。

*view*

[View](pt01ch54pyo01.md) 对象，指定控制图层查看的对象。

*odbDisplay*

[OdbDisplay](pt01ch35pyo01.md) 对象，指定 [Odb](pt01ch34pyo01.md) 对象的显示选项。

*partDisplay*

[PartDisplayOptions](pt01ch17pyo16.md) 对象，指定 [Part](pt01ch37pyo01.md) 对象的显示选项。

*assemblyDisplay*

[AssemblyDisplayOptions](pt01ch17pyo01.md) 对象，指定 [Assembly](pt01ch06pyo01.md) 对象的显示选项。
