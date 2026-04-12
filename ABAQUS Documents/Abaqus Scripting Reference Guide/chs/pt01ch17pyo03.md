# 17.3 ConstraintDisplayOptions 对象









ConstraintDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.constraints=ON
```

ConstraintDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.constraintOptions
session.viewports[*name*].layers[*name*].assemblyDisplay.constraintOptions
```

### 17.3.1 setValues(...)

此方法修改 ConstraintDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*constraintEquation*

一个 Boolean，指定是否显示约束方程符号。默认值为 ON。

*tieConstraint*

一个 Boolean，指定是否显示绑定约束符号。默认值为 ON。

*rigidBodyConstraint*

一个 Boolean，指定是否显示刚体约束符号。默认值为 ON。

*displayBodyConstraint*

一个 Boolean，指定是否显示显示体约束符号。默认值为 ON。

*couplingConstrain*

一个 Boolean，指定是否显示耦合约束符号。默认值为 ON。

**返回值**

无

**异常**

无。

### 17.3.2 成员

ConstraintDisplayOptions 对象的成员与 [setValues](pt01ch17pyo03.md#ker-constraintdisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





