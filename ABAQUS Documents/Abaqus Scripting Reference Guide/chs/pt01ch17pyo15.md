# 17.15 OptimizationTaskDisplayOptions 对象









OptimizationTaskDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.optimizationTasks=ON
```

OptimizationTaskDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.optimizationTaskOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.optimizationTaskOptions
```

### 17.15.1 setValues(...)

此方法修改 OptimizationTaskDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*topologyTask*

一个 Boolean，指定是否显示拓扑任务符号。默认值为 ON。

*shapeTask*

一个 Boolean，指定是否显示形状任务符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.15.2 成员

OptimizationTaskDisplayOptions 对象的成员与 [setValues](pt01ch17pyo15.md#ker-optimizationtaskdisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





