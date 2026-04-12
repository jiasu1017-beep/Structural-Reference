# 60.60 Hyperelastic 对象

Hyperelastic 对象用于指定近似不可压缩弹性体的弹性特性。

**访问**

```
materialApi.materials()[*name*].hyperelastic()
```

### 60.60.1 Hyperelastic(...)

此方法创建一个 Hyperelastic 对象。

**路径**

```
materialApi.materials()[*name*].Hyperelastic
```

**原型**

```
odb_Hyperelastic&
Hyperelastic(const odb_SequenceSequenceDouble& table,
             const odb_String& type,
             const odb_String& moduliTimeScale,
             bool temperatureDependency,
             int n,
             odb_Union beta,
             bool testData,
             bool compressible,
             int properties,
             const odb_String& deviatoricResponse,
             const odb_String& volumetricResponse,
             double poissonRatio,
             const odb_String& materialType,
             const odb_String& anisotropicType,
             const odb_String& formulation,
             const odb_String& behaviorType,
             int dependencies,
             int localDirections);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。此参数仅在 *testData*=OFF 时有效。

**可选参数**

*type*

一个 odb_String，指定应变能势的类型。可能的值为：
- "ARRUDA_BOYCE"
- "MARLOW"
- "MOONEY_RIVLIN"
- "NEO_HOOKE"
- "OGDEN"
- "POLYNOMIAL"
- "REDUCED_POLYNOMIAL"
- "USER"
- "VAN_DER_WAALS"
- "YEOH"
- "UNKNOWN"

默认值为"UNKNOWN"。

*moduliTimeScale*

一个 odb_String，指定时间响应的性质。可能的值为"INSTANTANEOUS"和"LONG_TERM"。默认值为"LONG_TERM"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*n*

一个整数，指定应变能势的阶数。默认值为 1。

如果 *testData*=ON 且 *type*="POLYNOMIAL"，*n* 只能取 1 或 2 的值。

如果 *testData*=ON 且 *type*="OGDEN" 或对于任一类型 *testData*=OFF，1 ![](../graphics/ker_eqn00263.gif) 6。

如果 *type*="USER"，则不能使用此参数。

*beta*

字符串"FITTED_VALUE"或一个 Double，指定不变量混合参数。此参数仅在 *testData*=ON 且 *type*="VAN_DER_WAALS" 时有效。默认值为"FITTED_VALUE"。

*testData*

一个布尔值，指定是否提供测试数据。默认值为 true。

*compressible*

一个布尔值，指定超弹性材料是否可压缩。此参数仅适用于用户定义的超弹性材料。默认值为 false。

*properties*

一个整数，指定作为用户定义超弹性材料数据所需的属性值数量。默认值为 0。

*deviatoricResponse*

一个 odb_String，指定使用哪些测试数据。可能的值为"UNIAXIAL"、"BIAXIAL"和"PLANAR"。默认值为"UNIAXIAL"。

*volumetricResponse*

一个 odb_String，指定体积响应。可能的值为"DEFAULT"、"VOLUMETRIC_DATA"、"POISSON_RATIO"和"LATERAL_NOMINAL_STRAIN"。默认值为"DEFAULT"。

*poissonRatio*

一个 Double，指定泊松比。此参数仅在 *volumetricResponse*="POISSON_RATIO" 时有效。默认值为 0.0。

*materialType*

一个 odb_String，指定材料类型。可能的值为"ISOTROPIC"和"ANISOTROPIC"。默认值为"ISOTROPIC"。

*anisotropicType*

一个 odb_String，指定应变能势的类型。可能的值为"FUNG_ANISOTROPIC"、"FUNG_ORTHOTROPIC"、"HOLZAPFEL"和"USER_DEFINED"。默认值为"FUNG_ANISOTROPIC"。

*formulation*

一个 odb_String，指定公式的类型。可能的值为"STRAIN"和"INVARIANT"。默认值为"STRAIN"。

*behaviorType*

一个 odb_String，指定各向异性超弹性材料行为的类型。可能的值为"INCOMPRESSIBLE"和"COMPRESSIBLE"。默认值为"INCOMPRESSIBLE"。

*dependencies*

一个整数，指定 *volumetricTable* 中数据的场变量依赖数量。默认值为 0。

*localDirections*

一个整数，指定 *volumetricTable* 中数据的局部方向数量。默认值为 0。

**表数据**

如果 *type*=ARRUDA_BOYCE，表数据指定以下内容：
- ![](../graphics/ker_eqn00041.gif]。
- ![](../graphics/ker_eqn00264.gif]。
- ![](../graphics/ker_eqn00172.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=MOONEY_RIVLIN，表数据指定以下内容：
- ![](../graphics/ker_eqn00265.gif]。
- ![](../graphics/ker_eqn00266.gif]。
- ![](../graphics/ker_eqn00267.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=NEO_HOOKE，表数据指定以下内容：
- ![](../graphics/ker_eqn00265.gif]。
- ![](../graphics/ker_eqn00267.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=OGDEN，对于 ![](../graphics/ker_eqn00088.gif) 的值，表数据指定以下内容：
- 对于从 1 到 ![](../graphics/ker_eqn00088.gif] 的 ![](../graphics/ker_eqn00270.gif)，为 ![](../graphics/ker_eqn00268.gif) 和 ![](../graphics/ker_eqn00269.gif]。
- ![](../graphics/ker_eqn00088.gif] 个系数 ![](../graphics/ker_eqn00271.gif]。
- 温度（如果数据依赖温度）。在 Abaqus/Explicit 分析中，4 ![](../graphics/ker_eqn00272.gif) 6 时不允许温度依赖。

如果 *type*=POLYNOMIAL，对于 ![](../graphics/ker_eqn00088.gif) 的值，表数据指定以下内容：
- 对于从 ![](../graphics/ker_eqn00274.gif) 到 ![](../graphics/ker_eqn00088.gif] 的 ![](../graphics/ker_eqn00270.gif)，其中 ![](../graphics/ker_eqn00276.gif] 从 ![](../graphics/ker_eqn00274.gif) 减小到零，![](../graphics/ker_eqn00276.gif] 从零增加到 ![](../graphics/ker_eqn00274.gif)，为 ![](../graphics/ker_eqn00273.gif]。
- ![](../graphics/ker_eqn00088.gif] 个系数 ![](../graphics/ker_eqn00271.gif]。
- 温度（如果数据依赖温度）。在 Abaqus/Explicit 分析中，3 ![](../graphics/ker_eqn00272.gif) 6 时不允许温度依赖。

如果 *type*=REDUCED_POLYNOMIAL，对于 ![](../graphics/ker_eqn00088.gif) 的值，表数据指定以下内容：
- 对于从 1 到 ![](../graphics/ker_eqn00088.gif] 的 ![](../graphics/ker_eqn00270.gif]，为 ![](../graphics/ker_eqn00277.gif]。
- ![](../graphics/ker_eqn00088.gif] 个系数 ![](../graphics/ker_eqn00271.gif]。
- 温度（如果数据依赖温度）。在 Abaqus/Explicit 分析中，4 ![](../graphics/ker_eqn00272.gif) 6 时不允许温度依赖。

如果 *type*=VAN_DER_WAALS，表数据指定以下内容：
- ![](../graphics/ker_eqn00041.gif]。
- ![](../graphics/ker_eqn00264.gif]。
- ![](../graphics/ker_eqn00278.gif]。
- ![](../graphics/ker_eqn00095.gif]。
- ![](../graphics/ker_eqn00172.gif]。
- 温度（如果数据依赖温度）。

如果 *type*=YEOH，表数据指定以下内容：
- ![](../graphics/ker_eqn00265.gif]。
- ![](../graphics/ker_eqn00279.gif]。
- ![](../graphics/ker_eqn00280.gif]。
- ![](../graphics/ker_eqn00267.gif]。
- ![](../graphics/ker_eqn00281.gif]。
- ![](../graphics/ker_eqn00282.gif]。
- 温度（如果数据依赖温度）。在 Abaqus/Explicit 分析中不允许温度依赖。

如果 *testData*=ON，则默认值为 `None` 对象。

**返回值**

一个 Hyperelastic 对象。

**异常**

InvalidNameError 和 RangeError。

### 60.60.2 成员

Hyperelastic 对象的成员与 [Hyperelastic](pt02ch60pyo60.md#ker-hyperelastic-hyperelastic-cpp) 方法的参数具有相同的名称和描述。

此外，Hyperelastic 对象可以具有以下成员：

**原型**

```
odb_BiaxialTestData biaxialTestData() const;
odb_PlanarTestData planarTestData() const;
odb_UniaxialTestData uniaxialTestData() const;
odb_VolumetricTestData volumetricTestData() const;
odb_Hysteresis hysteresis() const;
```

*biaxialTestData*

一个 [BiaxialTestData](pt02ch60pyo04.md) 对象。

*planarTestData*

一个 [PlanarTestData](pt02ch60pyo76.md) 对象。

*uniaxialTestData*

一个 [UniaxialTestData](pt02ch60pyo101.md) 对象。

*volumetricTestData*

一个 [VolumetricTestData](pt02ch60pyo110.md) 对象。

*hysteresis*

一个 [Hysteresis](pt02ch60pyo63.md) 对象。

### 60.60.3 对应的分析关键字

| [*HYPERELASTIC](../key/key-link.md#usb-kws-mhyperelast) |
| --- |
