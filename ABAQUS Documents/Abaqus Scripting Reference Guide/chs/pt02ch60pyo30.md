# 60.30 CyclicHardening 对象

CyclicHardening 对象用于定义非线性等向/运动硬化模型弹性域的演化。

**访问**

```
materialApi.materials()[*name*].plastic().cyclicHardening()
```

### 60.30.1 CyclicHardening(...)

此方法创建一个 CyclicHardening 对象。

**路径**

```
materialApi.materials()[*name*].plastic().CyclicHardening
```

**原型**

```
odb_CyclicHardening&
CyclicHardening(const odb_SequenceSequenceDouble& table,
                bool temperatureDependency,
                int dependencies,
                bool parameters);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*parameters*

一个布尔值，指定材料参数是否直接输入。默认值为 false。

**表数据**

- 等效应力。
- ![](../graphics/ker_eqn00160.gif)（仅在 *parameters*=ON 时）。
- 硬化参数（仅在 *parameters*=ON 时）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CyclicHardening 对象。

**异常**

无。

### 60.30.2 成员

CyclicHardening 对象的成员与 [CyclicHardening](pt02ch60pyo30.md#ker-cyclichardening-cyclichardening-cpp) 方法的参数具有相同的名称和描述。

### 60.30.3 对应的分析关键字

| [*CYCLIC HARDENING](../key/key-link.md#usb-kws-mcyclichardening) |
| --- |
