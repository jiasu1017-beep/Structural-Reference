# 17.18 SymbolDisplayOptions 对象









SymbolDisplayOptions 对象存储指定如何在特定视口中显示装配的设置。SymbolDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.symbolOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.symbolOptions
```

### 17.18.1 setValues(...)

此方法修改 SymbolDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*otherSymbolSize*

一个 Int，指定标量属性符号的大小。可能的值为 1 ≤ *scalarSymbolSize* ≤ 30。默认值为 6。

*arrowSymbolSize*

一个 Int，指定矢量和张量属性符号的大小。可能的值为 1 ≤ *vectorSymbolSize* ≤ 30。默认值为 6。

*faceSymbolDensity*

一个 Int，指定在几何面上绘制的属性符号的相对密度。可能的值为 1 ≤ *faceSymbolDensity* ≤ 10。默认值为 5。

*edgeSymbolDensity*

一个 Int，指定在几何边缘上绘制的属性符号的相对密度。可能的值为 1 ≤ *edgeSymbolDensity* ≤ 10。默认值为 5。

*meshSymbolFraction*

一个 Float，指定在孤立网格区域上绘制的属性符号的分数。可能的值为 0.0 ≤ *meshSymbolFraction* ≤ 1.0。默认值为 1.0。

*showFields*

一个 Boolean，指定符号是否应根据分析场值进行缩放。默认值为 ON。

**返回值**

无

**异常**

无。

### 17.18.2 成员

SymbolDisplayOptions 对象的成员与 [setValues](pt01ch17pyo18.md#ker-symboldisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





