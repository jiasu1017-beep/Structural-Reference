# 60.51 FailStress 对象

FailStress 对象用于定义基于应力的失效度量参数。

**访问**

```
materialApi.materials()[*name*].elastic().failStress()
```

### 60.51.1 FailStress(...)

此方法创建一个 FailStress 对象。

**路径**

```
materialApi.materials()[*name*].elastic().FailStress
```

**原型**

```
odb_FailStress&
FailStress(const odb_SequenceSequenceDouble& table,
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

- 纤维方向拉伸应力极限，![](../graphics/ker_eqn00251.gif]。
- 纤维方向压缩应力极限，![](../graphics/ker_eqn00252.gif]。
- 横向拉伸应力极限，![](../graphics/ker_eqn00253.gif]。
- 横向压缩应力极限，![](../graphics/ker_eqn00254.gif]。
- ![](../graphics/ker_eqn00083.gif)--![](../graphics/ker_eqn00084.gif) 平面内的剪切强度，![](../graphics/ker_eqn00255.gif]。
- 交叉乘积项系数，![](../graphics/ker_eqn00256.gif)（![](../graphics/ker_eqn00257.gif]）。默认值为零。
- 双轴应力极限，![](../graphics/ker_eqn00258.gif]。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 FailStress 对象。

**异常**

RangeError。

### 60.51.2 成员

FailStress 对象的成员与 [FailStress](pt02ch60pyo51.md#ker-failstress-failstress-cpp) 方法的参数具有相同的名称和描述。

### 60.51.3 对应的分析关键字

| [*FAIL STRESS](../key/key-link.md#usb-kws-mefailstress) |
| --- |
