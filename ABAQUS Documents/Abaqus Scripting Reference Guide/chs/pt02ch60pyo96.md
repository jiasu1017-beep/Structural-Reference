# 60.97 TensionCutOff 对象

TensionCutOff 对象用于指定不同材料模型的拉伸截断，例如 Mohr-Coulomb 塑性模型。

**访问**

```
materialApi.materials()[*name*].mohrCoulombPlasticity().tensionCutOff()
```

### 60.97.1 TensionCutOff(...)

此方法创建一个 TensionCutOff 对象。

**路径**

```
materialApi.materials()[*name*].mohrCoulombPlasticity().TensionCutOff
```

**原型**

```
odb_TensionCutOff&
TensionCutOff(const odb_SequenceSequenceDouble& table,
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

- 拉伸截断应力。
- 对应拉伸塑性应变值。（输入的第一个表值必须始终为零。）
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 TensionCutOff 对象。

**异常**

RangeError。

### 60.97.2 成员

TensionCutOff 对象的成员与 [TensionCutOff](pt02ch60pyo97.md#ker-tensioncutoff-tensioncutoff-cpp) 方法的参数具有相同的名称和描述。

### 60.97.3 对应的分析关键字

| [*TENSION CUTOFF](../key/key-link.md#usb-kws-mtensioncutoff) |
| --- |
