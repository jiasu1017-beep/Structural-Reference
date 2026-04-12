# 60.61 Hyperfoam 对象

Hyperfoam 对象用于指定超弹性泡沫的弹性特性。

**访问**

```
materialApi.materials()[*name*].hyperfoam()
```

### 60.61.1 Hyperfoam(...)

此方法创建一个 Hyperfoam 对象。

**路径**

```
materialApi.materials()[*name*].Hyperfoam
```

**原型**

```
odb_Hyperfoam&
Hyperfoam(bool testData,
          odb_Union poisson,
          int n,
          bool temperatureDependency,
          const odb_String& moduli,
          const odb_SequenceSequenceDouble& table);
```

**必需参数**

无。

**可选参数**

*testData*

一个布尔值，指定是否提供测试数据。默认值为 false。

*poisson*

字符串"NONE"或一个 Double，指定材料的有效泊松比，![](../graphics/ker_eqn00164.gif]。此参数仅在 *testData*=true 时有效。默认值为"NONE"。

*n*

一个整数，指定应变能势的阶数。可能的值为 1 ![](../graphics/ker_eqn00283.gif) 6。默认值为 1。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*moduli*

一个 odb_String，指定材料常数的时间依赖性。可能的值为"INSTANTANEOUS"和"LONG_TERM"。默认值为"LONG_TERM"。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。此参数仅在 *testData*=false 时有效。默认值为空序列。

**表数据**

对于 ![](../graphics/ker_eqn00088.gif] 的值，表数据指定以下内容：
- 对于从 1 到 ![](../graphics/ker_eqn00088.gif] 的 ![](../graphics/ker_eqn00270.gif]，为 ![](../graphics/ker_eqn00268.gif) 和 ![](../graphics/ker_eqn00269.gif]。
- ![](../graphics/ker_eqn00284.gif]。
- 温度（如果数据依赖温度）。在 Abaqus/Explicit 分析中，4 ![](../graphics/ker_eqn00272.gif) 6 时不允许温度依赖。

**返回值**

一个 Hyperfoam 对象。

**异常**

RangeError。

### 60.61.2 成员

Hyperfoam 对象的成员与 [Hyperfoam](pt02ch60pyo61.md#ker-hyperfoam-hyperfoam-cpp) 方法的参数具有相同的名称和描述。

此外，Hyperfoam 对象可以具有以下成员：

**原型**

```
odb_BiaxialTestData biaxialTestData() const;
odb_VolumetricTestData volumetricTestData() const;
odb_PlanarTestData planarTestData() const;
odb_SimpleShearTestData simpleShearTestData() const;
odb_UniaxialTestData uniaxialTestData() const;
```

*biaxialTestData*

一个 [BiaxialTestData](pt02ch60pyo04.md) 对象。

*volumetricTestData*

一个 [VolumetricTestData](pt02ch60pyo110.md) 对象。

*planarTestData*

一个 [PlanarTestData](pt02ch60pyo76.md) 对象。

*simpleShearTestData*

一个 [SimpleShearTestData](pt02ch60pyo91.md) 对象。

*uniaxialTestData*

一个 [UniaxialTestData](pt02ch60pyo101.md) 对象。

### 60.61.3 对应的分析关键字

| [*HYPERFOAM](../key/key-link.md#usb-kws-mhyperfoam) |
| --- |
