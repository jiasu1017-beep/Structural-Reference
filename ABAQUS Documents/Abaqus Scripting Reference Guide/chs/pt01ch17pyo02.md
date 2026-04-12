# 17.2 BCDisplayOptions 对象









BCDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.bcs=ON
```

BCDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.bcOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.bcOptions
```

### 17.2.1 setValues(...)

此方法修改 BCDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*displacement*

一个 Boolean，指定是否显示位移符号。默认值为 ON。

*velocity*

一个 Boolean，指定是否显示速度符号。默认值为 ON。

*acceleration*

一个 Boolean，指定是否显示加速度符号。默认值为 ON。

*symmetry*

一个 Boolean，指定是否显示对称符号。默认值为 ON。

*antiSymmetry*

一个 Boolean，指定是否显示反对称符号。默认值为 ON。

*temperature*

一个 Boolean，指定是否显示温度符号。默认值为 ON。

*porePressure*

一个 Boolean，指定是否显示孔隙压力符号。默认值为 ON。

*fluidCavityPressure*

一个 Boolean，指定是否显示流体腔压力符号。默认值为 ON。

*acousticPressure*

一个 Boolean，指定是否显示声压符号。默认值为 ON。

*electricPotential*

一个 Boolean，指定是否显示电位符号。默认值为 ON。

*concentration*

一个 Boolean，指定是否显示浓度质量扩散符号。默认值为 ON。

*encastre*

一个 Boolean，指定是否显示固定符号。默认值为 ON。

*pinned*

一个 Boolean，指定是否显示销钉符号。默认值为 ON。

**返回值**

无

**异常**

无。

### 17.2.2 成员

BCDisplayOptions 对象的成员与 [setValues](pt01ch17pyo02.md#ker-bcdisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





