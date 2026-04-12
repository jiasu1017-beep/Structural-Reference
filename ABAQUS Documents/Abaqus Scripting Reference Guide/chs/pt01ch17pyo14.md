# 17.13 LoadDisplayOptions 对象









LoadDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.loads=ON
```

LoadDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.loadOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.loadOptions
```

### 17.13.1 setValues(...)

此方法修改 LoadDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*concentratedForce*

一个 Boolean，指定是否显示集中力符号。默认值为 ON。

*moment*

一个 Boolean，指定是否显示力矩符号。默认值为 ON。

*pressure*

一个 Boolean，指定是否显示压力符号。默认值为 ON。

*pipePressure*

一个 Boolean，指定是否显示管道压力符号。默认值为 ON。

*bodyForce*

一个 Boolean，指定是否显示体力符号。默认值为 ON。

*lineLoad*

一个 Boolean，指定是否显示线载荷符号。默认值为 ON。

*gravity*

一个 Boolean，指定是否显示重力符号。默认值为 ON。

*boltLoad*

一个 Boolean，指定是否显示螺栓载荷符号。默认值为 ON。

*pegLoad*

一个 Boolean，指定是否显示 PEG 载荷符号。默认值为 ON。

*connectorForce*

一个 Boolean，指定是否显示连接器力符号。默认值为 ON。

*connectorMoment*

一个 Boolean，指定是否显示连接器力矩符号。默认值为 ON。

*inertiaRelief*

一个 Boolean，指定是否显示惯性释放符号。默认值为 ON。

*rotationalIntertiaLoad*

一个 Boolean，指定是否显示转动惯性载荷符号。默认值为 ON。

*coriolisForce*

一个 Boolean，指定是否显示科里奥利力符号。默认值为 ON。

*bodyHeatFlux*

一个 Boolean，指定是否显示体热通量符号。默认值为 ON。

*surfaceHeatFlux*

一个 Boolean，指定是否显示面热通量符号。默认值为 ON。

*concentratedHeatFlux*

一个 Boolean，指定是否显示集中热通量符号。默认值为 ON。

*concentratedPoreFluid*

一个 Boolean，指定是否显示集中孔隙流体符号。默认值为 ON。

*surfacePoreFluid*

一个 Boolean，指定是否显示面孔隙流体符号。默认值为 ON。

*hydroFluidFlow*

一个 Boolean，指定是否显示流体流动符号。默认值为 ON。

*concentratedCharge*

一个 Boolean，指定是否显示集中电荷符号。默认值为 ON。

*concentratedCurrent*

一个 Boolean，指定是否显示集中电流符号。默认值为 ON。

*surfaceCharge*

一个 Boolean，指定是否显示面电荷符号。默认值为 ON。

*surfaceCurrent*

一个 Boolean，指定是否显示面电流符号。默认值为 ON。

*bodyCharge*

一个 Boolean，指定是否显示体电荷符号。默认值为 ON。

*bodyCurrent*

一个 Boolean，指定是否显示体电流符号。默认值为 ON。

*inwardVolAccel*

一个 Boolean，指定是否显示内向体积加速度符号。默认值为 ON。

*bodyConcentrationFlux*

一个 Boolean，指定是否显示体浓度通量符号。默认值为 ON。

*surfaceConcentrationFlux*

一个 Boolean，指定是否显示面浓度通量符号。默认值为 ON。

*concentratedConcentrationFlux*

一个 Boolean，指定是否显示集中浓度通量符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.13.2 成员

LoadDisplayOptions 对象的成员与 [setValues](pt01ch17pyo13.md#ker-loaddisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





