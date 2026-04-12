# 60.76 PlanarTestData 对象

PlanarTestData 对象用于指定平面测试（或纯剪切）数据（压缩和/或拉伸）。

**访问**

```
materialApi.materials()[*name*].hyperelastic().planarTestData()
materialApi.materials()[*name*].hyperfoam().planarTestData()
materialApi.materials()[*name*].mullinsEffect().planarTests(*i*)
```

### 60.76.1 PlanarTestData(...)

此方法创建一个 PlanarTestData 对象。

**路径**

```
materialApi.materials()[*name*].hyperelastic().PlanarTestData
materialApi.materials()[*name*].hyperfoam().PlanarTestData
materialApi.materials()[*name*].mullinsEffect().PlanarTestData
```

**原型**

```
odb_PlanarTestData&
PlanarTestData(const odb_SequenceSequenceDouble& table,
               odb_Union smoothing,
               bool lateralNominalStrain,
               bool temperatureDependency,
               int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*smoothing*

字符串"NONE"或一个 Int，指定平滑值。如果 *smoothing*="NONE"，则不采用平滑。默认值为"NONE"。

*lateralNominalStrain*

一个布尔值，指定是否包含横向名义应变。默认值为 false。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

对于超弹性材料模型，表数据指定以下内容：
- 名义应力，![](../graphics/ker_eqn00332.gif]。
- 加载方向的名义应变，![](../graphics/ker_eqn00333.gif]。

对于超泡沫材料模型，表数据指定以下内容：
- 名义应力，![](../graphics/ker_eqn00334.gif]。
- 加载方向的名义应变，![](../graphics/ker_eqn00335.gif]。
- 横向名义应变，![](../graphics/ker_eqn00336.gif]。默认值为 0。

**返回值**

一个 PlanarTestData 对象。

**异常**

无。

### 60.76.2 成员

PlanarTestData 对象的成员与 [PlanarTestData](pt02ch60pyo76.md#ker-planartestdata-planartestdata-cpp) 方法的参数具有相同的名称和描述。

### 60.76.3 对应的分析关键字

| [*PLANAR TEST DATA](../key/key-link.md#usb-kws-mplanartestdata) |
| --- |
