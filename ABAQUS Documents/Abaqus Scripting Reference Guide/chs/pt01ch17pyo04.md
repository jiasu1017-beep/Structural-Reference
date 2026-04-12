# 17.4 EngineeringFeatureDisplayOptions 对象









EngineeringFeatureDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.engineeringFeatures=ON
```

EngineeringFeatureDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.engineeringFeatureOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.engineeringFeatureOptions
import part
session.viewports[*name*].layers[*name*].partDisplay\
.engineeringFeatureOptions
session.viewports[*name*].partDisplay.engineeringFeatureOptions
```

### 17.4.1 setValues(...)

此方法修改 EngineeringFeatureDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*pointMassInertia*

一个 Boolean，指定是否显示点质量惯性符号。默认值为 ON。

*nonstructuralMass*

一个 Boolean，指定是否显示非结构质量符号。默认值为 ON。

*heatCapacitance*

一个 Boolean，指定是否显示热容符号。默认值为 ON。

*contourIntegral*

一个 Boolean，指定是否显示轮廓积分符号。默认值为 ON。

*springToGround*

一个 Boolean，指定是否显示接地弹簧符号。默认值为 ON。

*twoPointSpring*

一个 Boolean，指定是否显示二点弹簧符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.4.2 成员

EngineeringFeatureDisplayOptions 对象的成员与 [setValues](pt01ch17pyo04.md#ker-engineeringfeaturedisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





