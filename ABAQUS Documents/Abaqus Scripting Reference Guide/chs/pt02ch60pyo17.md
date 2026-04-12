# 60.17 CombinedTestData 对象

CombinedTestData 对象同时指定归一化剪切和体积柔量或松弛模量作为时间的函数。

**访问**

```
materialApi.materials()[*name*].viscoelastic().combinedTestData()
```

### 60.17.1 CombinedTestData(...)

此方法创建一个 CombinedTestData 对象。

**路径**

```
materialApi.materials()[*name*].viscoelastic().CombinedTestData
```

**原型**

```
odb_CombinedTestData&
CombinedTestData(const odb_SequenceSequenceDouble& table,
                 odb_Union volinf,
                 odb_Union shrinf);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。表数据的值取决于 [Viscoelastic](pt02ch60pyo106.md) 对象的 *time* 成员的值。

**可选参数**

*volinf*

字符串"NONE"或一个 Double，指定归一化体积。*volinf* 的值取决于 [Viscoelastic](pt02ch60pyo106.md) 对象的 *time* 成员的值。默认值为"NONE"。

如果 *time*="RELAXATION_TEST_DATA"，*volinf* 指定长期归一化体积模量的值，![](../graphics/ker_eqn00113.gif)。

如果 *time*="CREEP_TEST_DATA"，*volinf* 指定长期归一化体积柔量的值，![](../graphics/ker_eqn00114.gif)。

*shrinf*

字符串"NONE"或一个 Double，指定归一化剪切。*shrinf* 的值取决于 [Viscoelastic](pt02ch60pyo106.md) 对象的 *time* 成员的值。默认值为"NONE"。

如果 *time*="RELAXATION_TEST_DATA"，*shrinf* 指定长期归一化剪切模量的值，![](../graphics/ker_eqn00115.gif)。

如果 *time*="CREEP_TEST_DATA"，*shrinf* 指定长期归一化剪切柔量的值，![](../graphics/ker_eqn00116.gif)。

**表数据**

如果 *time*=RELAXATION_TEST_DATA，表数据指定以下内容：
- 归一化剪切模量，![](../graphics/ker_eqn00117.gif) ![](../graphics/ker_eqn00118.gif)。
- 归一化体积（体积）模量，![](../graphics/ker_eqn00119.gif) ![](../graphics/ker_eqn00120.gif)。
- 时间 ![](../graphics/ker_eqn00093.gif) ![](../graphics/ker_eqn00121.gif)。

如果 *time*=CREEP_TEST_DATA，表数据指定以下内容：
- 归一化剪切柔量，![](../graphics/ker_eqn00122.gif) ![](../graphics/ker_eqn00123.gif)。
- 归一化体积（体积）柔量，![](../graphics/ker_eqn00124.gif) ![](../graphics/ker_eqn00125.gif)。
- 时间 ![](../graphics/ker_eqn00093.gif) ![](../graphics/ker_eqn00126.gif)。

**返回值**

一个 CombinedTestData 对象。

**异常**

无。

### 60.17.2 成员

CombinedTestData 对象的成员与 [CombinedTestData](pt02ch60pyo17.md#ker-combinedtestdata-combinedtestdata-cpp) 方法的参数具有相同的名称和描述。

### 60.17.3 对应的分析关键字

| [*COMBINED TEST DATA](../key/key-link.md#usb-kws-mcombinedtestdata) |
| --- |
