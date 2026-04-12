# 60.55 GasketMembraneElastic 对象

GasketMembraneElastic 对象用于定义垫片膜剪切行为的弹性参数。

**访问**

```
materialApi.materials()[*name*].gasketMembraneElastic()
```

### 60.55.1 GasketMembraneElastic(...)

此方法创建一个 GasketMembraneElastic 对象。

**路径**

```
materialApi.materials()[*name*].GasketMembraneElastic
```

**原型**

```
odb_GasketMembraneElastic&
GasketMembraneElastic(const odb_SequenceSequenceDouble& table,
                      bool temperatureDependency,
                      int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 杨氏模量，![](../graphics/ker_eqn00163.gif]。
- 泊松比，![](../graphics/ker_eqn00164.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 GasketMembraneElastic 对象。

**异常**

RangeError。

### 60.55.2 成员

GasketMembraneElastic 对象的成员与 [GasketMembraneElastic](pt02ch60pyo55.md#ker-gasketmembraneelastic-gasketmembraneelastic-cpp) 方法的参数具有相同的名称和描述。

### 60.55.3 对应的分析关键字

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |
