# 60.52 FailureRatios 对象

FailureRatios 对象用于指定 [Concrete](pt02ch60pyo18.md) 模型失效面的形状。

**访问**

```
materialApi.materials()[*name*].concrete().failureRatios()
```

### 60.52.1 FailureRatios(...)

此方法创建一个 FailureRatios 对象。

**路径**

```
materialApi.materials()[*name*].concrete().FailureRatios
```

**原型**

```
odb_FailureRatios&
FailureRatios(const odb_SequenceSequenceDouble& table,
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

- 最终双轴压缩应力与单轴压缩极限应力之比。默认值为 1.16。
- 失效时单轴拉伸应力与失效时单轴压缩应力之比的绝对值。默认值为 0.09。
- 双轴压缩下极限应力时主塑性应变分量与单轴压缩下极限应力时塑性应变之比。默认值为 1.28。
- 平面应力下剪切时（当另一个非零主应力分量达到极限压缩应力值时）的拉伸主应力值与单轴拉伸下拉伸开裂应力之比。默认值为 1/3。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 FailureRatios 对象。

**异常**

RangeError。

### 60.52.2 成员

FailureRatios 对象的成员与 [FailureRatios](pt02ch60pyo52.md#ker-failureratios-failureratios-cpp) 方法的参数具有相同的名称和描述。

### 60.52.3 对应的分析关键字

| [*FAILURE RATIOS](../key/key-link.md#usb-kws-mfailureratios) |
| --- |
