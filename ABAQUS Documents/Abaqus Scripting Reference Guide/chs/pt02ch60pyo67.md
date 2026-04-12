# 60.67 LowDensityFoam 对象

LowDensityFoam 对象用于指定低密度泡沫的特性。

**访问**

```
materialApi.materials()[*name*].lowDensityFoam()
```

### 60.67.1 LowDensityFoam(...)

此方法创建一个 LowDensityFoam 对象。

**路径**

```
materialApi.materials()[*name*].LowDensityFoam
```

**原型**

```
odb_LowDensityFoam&
LowDensityFoam(bool elementRemoval,
               odb_Union maxAllowablePrincipalStress,
               bool extrapolateStressStrainCurve,
               const odb_String& strainRateType,
               double mu0,
               double mu1,
               double alpha);
```

**必需参数**

无。

**可选参数**

*elementRemoval*

一个布尔值，指定如果超过最大主拉伸应力是否移除单元。此参数仅在定义了 *maxAllowablePrincipalStress* 时有效。默认值为 false。

*maxAllowablePrincipalStress*

字符串"NONE"或一个 Double，指定最大允许主拉伸应力。默认值为"NONE"。

*extrapolateStressStrainCurve*

一个布尔值，指定如果超过最大应变率是否外推应力-应变曲线。默认值为 false。

*strainRateType*

一个 odb_String，指定用于本构计算的应变率度量。可能的值为"PRINCIPAL"和"VOLUMETRIC"。默认值为"VOLUMETRIC"。

*mu0*

一个 Double，指定松弛系数 ![](../graphics/ker_eqn00288.gif]。默认值为 10–4。

*mu1*

一个 Double，指定松弛系数 ![](../graphics/ker_eqn00070.gif]。默认值为 0.510–2。

*alpha*

一个 Double，指定松弛系数 ![](../graphics/ker_eqn00090.gif]。默认值为 2.0。

**返回值**

一个 LowDensityFoam 对象。

**异常**

RangeError。

### 60.67.2 成员

LowDensityFoam 对象的成员与 [LowDensityFoam](pt02ch60pyo67.md#ker-lowdensityfoam-lowdensityfoam-cpp) 方法的参数具有相同的名称和描述。

此外，LowDensityFoam 对象可以具有以下成员：

**原型**

```
odb_UniaxialTestData uniaxialTensionTestData() const;
odb_UniaxialTestData uniaxialCompressionTestData() const;
```

*uniaxialTensionTestData*

一个 [UniaxialTestData](pt02ch60pyo101.md) 对象。

*uniaxialCompressionTestData*

一个 [UniaxialTestData](pt02ch60pyo101.md) 对象。

### 60.67.3 对应的分析关键字

| [*LOW DENSITY FOAM](../key/key-link.md#usb-kws-mlowdensfoam) |
| --- |
