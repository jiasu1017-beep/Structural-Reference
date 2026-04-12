# 17.14 MeshDisplayOptions 对象









MeshDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.mesh=ON
```

MeshDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.meshOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.meshOptions
session.viewports[*name*].layers[*name*].partDisplay.meshOptions
session.viewports[*name*].partDisplay.meshOptions
```

### 17.14.1 setValues(...)

此方法修改 MeshDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*nodeLabels*

一个 Boolean，指定是否显示节点标签。默认值为 OFF。

*elementLabels*

一个 Boolean，指定是否显示单元标签。默认值为 OFF。

*meshVisibleEdges*

一个 SymbolicConstant，指定如何绘制网格的边缘。可能的值为：
- ALL，指定显示所有边缘。
- EXTERIOR，指定仅显示外部边缘。
- FEATURE，指定基于 *featureAngle* 显示边缘。
- FREE，指定仅显示自由边缘。
- NONE，指定不显示边缘。

默认值为 EXTERIOR。

*featureAngle*

一个 Float，指定用于计算特征边缘图的角度（度）。可能的值为 0 ≤ *featureAngle* ≤ 90。默认值为 20.0。

*meshEdgesInShaded*

一个 Boolean，指定是否在着色模式下显示网格边缘。默认值为 ON。

*meshTechnique*

一个 Boolean，指定是否根据分配给区域的网格技术对装配区域进行颜色编码。此参数在 partDisplay 中被忽略。默认值为 OFF。

*seeds*

一个 Boolean，指定是否显示种子。此参数在 partDisplay 中被忽略。默认值为 OFF。

**返回值**

无

**异常**

RangeError。

### 17.14.2 成员

MeshDisplayOptions 对象的成员与 [setValues](pt01ch17pyo14.md#ker-meshdisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





