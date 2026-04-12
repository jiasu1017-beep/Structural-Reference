# 60.57 GasketTransverseShearElastic 对象

GasketTransverseShearElastic 对象用于定义垫片横向剪切行为的弹性参数。

**访问**

```
materialApi.materials()[*name*].gasketTransverseShearElastic()
```

### 60.57.1 GasketTransverseShearElastic(...)

此方法创建一个 GasketTransverseShearElastic 对象。

**路径**

```
materialApi.materials()[*name*].GasketTransverseShearElastic
```

**原型**

```
odb_GasketTransverseShearElastic&
GasketTransverseShearElastic(const odb_SequenceSequenceDouble& table,
                             const odb_String& variableUnits,
                             bool temperatureDependency,
                             int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*variableUnits*

一个 odb_String，指定定义横向剪切行为的单位系统。可能的值为"STRESS"和"FORCE"。默认值为"STRESS"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 剪切刚度。（此值不能为负。）
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 GasketTransverseShearElastic 对象。

**异常**

RangeError。

### 60.57.2 成员

GasketTransverseShearElastic 对象的成员与 [GasketTransverseShearElastic](pt02ch60pyo57.md#ker-gaskettransverseshearelastic-gaskettransverseshearel-cpp) 方法的参数具有相同的名称和描述。

### 60.57.3 对应的分析关键字

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |
