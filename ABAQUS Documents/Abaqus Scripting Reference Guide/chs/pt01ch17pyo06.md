# 17.6 GeometryDisplayOptions 对象









GeometryDisplayOptions 对象存储指定如何在特定视口中显示装配的设置。GeometryDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.geometryOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.geometryOptions
session.viewports[*name*].layers[*name*].partDisplay.geometryOptions
session.viewports[*name*].partDisplay.geometryOptions
```

### 17.6.1 setValues(...)

此方法修改 GeometryDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*geometryEdgesInShaded*

一个 Boolean，指定是否在着色模式下显示几何边缘。默认值为 ON。

*geometryHiddenEdges*

一个 Boolean，指定是否在隐藏线模式下显示（点线）几何隐藏边缘。默认值为 OFF。

*geometrySilhouetteEdges*

一个 Boolean，指定是否显示几何轮廓边缘。默认值为 ON。

*datumAxes*

一个 Boolean，指定是否显示基准轴。默认值为 ON。

*datumCoordSystems*

一个 Boolean，指定是否显示基准坐标系。默认值为 ON。

*datumPlanes*

一个 Boolean，指定是否显示基准平面。默认值为 ON。

*referencePointLabels*

一个 Boolean，指定是否显示参考点标签。默认值为 ON。

*referencePointSymbols*

一个 Boolean，指定是否显示参考点符号。默认值为 ON。

*referenceRepresentation*

一个 Boolean，指定是否显示属于部件或实例的参考表示的几何。默认值为 OFF。

*referenceRepTranslucency*

一个 Boolean，指定是否对属于部件或实例的参考表示的几何应用半透明度。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.6.2 成员

GeometryDisplayOptions 对象的成员与 [setValues](pt01ch17pyo06.md#ker-geometrydisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





