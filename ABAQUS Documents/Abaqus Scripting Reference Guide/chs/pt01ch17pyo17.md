# 17.17 StopConditionDisplayOptions 对象









StopConditionDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.stopConditions=ON
```

StopConditionDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.stopConditionOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.stopConditionOptions
```

### 17.17.1 setValues(...)

此方法修改 StopConditionDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*localStopCondition*

一个 Boolean，指定是否显示局部停止条件符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.17.2 成员

StopConditionDisplayOptions 对象的成员与 [setValues](pt01ch17pyo17.md#ker-stopconditiondisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





