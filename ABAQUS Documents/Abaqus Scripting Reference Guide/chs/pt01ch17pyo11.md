# 17.10 InteractionDisplayOptions 对象









InteractionDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.interactions=ON
```

InteractionDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.interactionOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.interactionOptions
```

### 17.10.1 setValues(...)

此方法修改 InteractionDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*surfaceContact*

一个 Boolean，指定是否显示面接触符号。默认值为 ON。

*selfContact*

一个 Boolean，指定是否显示自接触符号。默认值为 ON。

*elasticFoundation*

一个 Boolean，指定是否显示弹性基础符号。默认值为 ON。

*actuatorSensor*

一个 Boolean，指定是否显示执行器/传感器符号。默认值为 ON。

*radiationAmbient*

一个 Boolean，指定是否显示面对环境辐射符号。默认值为 ON。

*filmCondition*

一个 Boolean，指定是否显示面薄膜条件符号。默认值为 ON。

*concentratedRadiationToAmbient*

一个 Boolean，指定是否显示集中辐射到环境符号。默认值为 ON。

*concentratedFilmCondition*

一个 Boolean，指定是否显示集中薄膜条件符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.10.2 成员

InteractionDisplayOptions 对象的成员与 [setValues](pt01ch17pyo10.md#ker-interactiondisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





