# 17.5 PredefinedFieldDisplayOptions 对象









PredefinedFieldDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.predefinedFields=ON
```

PredefinedFieldDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.predefinedFieldOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.predefinedFieldOptions
```

### 17.5.1 setValues(...)

此方法修改 PredefinedFieldDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*temperatureField*

一个 Boolean，指定是否显示温度场符号。默认值为 ON。

*velocityField*

一个 Boolean，指定是否显示平动速度符号。默认值为 ON。

*generalField*

一个 Boolean，指定是否显示通用场符号。默认值为 ON。

*stressField*

一个 Boolean，指定是否显示应力场符号。默认值为 ON。

*hardeningField*

一个 Boolean，指定是否显示硬化场符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.5.2 成员

PredefinedFieldDisplayOptions 对象的成员与 [setValues](pt01ch17pyo05.md#ker-predefinedfielddisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





