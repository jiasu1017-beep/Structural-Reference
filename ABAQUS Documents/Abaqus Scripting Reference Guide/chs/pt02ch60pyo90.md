# 60.90 ShearTestData 对象

ShearTestData 对象用于指定归一化剪切蠕变柔量或松弛模量随时间的变化。

**访问**

```
materialApi.materials()[*name*].viscoelastic().shearTestData()
```

### 60.90.1 ShearTestData(...)

此方法创建一个 ShearTestData 对象。

**路径**

```
materialApi.materials()[*name*].viscoelastic().ShearTestData
```

**原型**

```
odb_ShearTestData&
ShearTestData(const odb_SequenceSequenceDouble& table,
              odb_Union shrinf);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定依赖于 [Viscoelastic](pt02ch60pyo106.md) 对象的 *time* 成员的值。

如果 *time*="RELAXATION_TEST_DATA"，表数据指定以下内容：
- 归一化剪切松弛模量 ![](../graphics/ker_eqn00117.gif]。![](../graphics/ker_eqn00118.gif]。
- 时间 ![](../graphics/ker_eqn00093.gif]。![](../graphics/ker_eqn00121.gif]。

如果 *time*="CREEP_TEST_DATA"，表数据指定以下内容：
- 归一化剪切柔量 ![](../graphics/ker_eqn00122.gif]。![](../graphics/ker_eqn00365.gif]。
- 时间 ![](../graphics/ker_eqn00093.gif]。![](../graphics/ker_eqn00121.gif]。

**可选参数**

*shrinf*

字符串"NONE"或一个 Double，指定归一化剪切值。*shrinf* 的值取决于 [Viscoelastic](pt02ch60pyo106.md) 对象的 *time* 成员的值。默认值为"NONE"。

如果 *time*="RELAXATION_TEST_DATA"，*shrinf* 指定长期归一化剪切模量 ![](../graphics/ker_eqn00115.gif] 的值。

如果 *time*="CREEP_TEST_DATA"，*shrinf* 指定长期归一化剪切柔量 ![](../graphics/ker_eqn00116.gif] 的值。

**返回值**

一个 ShearTestData 对象。

**异常**

无。

### 60.90.2 成员

ShearTestData 对象的成员与 [ShearTestData](pt02ch60pyo90.md#ker-sheartestdata-sheartestdata-cpp) 方法的参数具有相同的名称和描述。

### 60.90.3 对应的分析关键字

| [*SHEAR TEST DATA](../key/key-link.md#usb-kws-msheartestdata) |
| --- |
