# 60.4 BiaxialTestData 对象

BiaxialTestData 对象提供等双轴试验数据（压缩和/或拉伸）。

**访问**

```
materialApi.materials()[*name*].hyperelastic().biaxialTestData()
materialApi.materials()[*name*].hyperfoam().biaxialTestData()
materialApi.materials()[*name*].mullinsEffect().biaxialTests(*i*)
```

### 60.4.1 BiaxialTestData(...)

此方法创建一个 BiaxialTestData 对象。

**路径**

```
materialApi.materials()[*name*].hyperelastic().BiaxialTestData
materialApi.materials()[*name*].hyperfoam().BiaxialTestData
materialApi.materials()[*name*].mullinsEffect().BiaxialTestData
```

**原型**

```
odb_BiaxialTestData&
BiaxialTestData(const odb_SequenceSequenceDouble& table,
                odb_Union smoothing,
                bool lateralNominalStrain,
                bool temperatureDependency,
                int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定以下内容：
- 名义应力，![](../graphics/ker_eqn00086.gif)。
- 名义应变，![](../graphics/ker_eqn00087.gif)。

**可选参数**

*smoothing*

字符串"NONE"或一个整数，指定平滑值。如果 *smoothing*="NONE"，则不采用平滑。默认值为"NONE"。

*lateralNominalStrain*

一个布尔值，指定是否包含横向名义应变。默认值为 false。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**返回值**

一个 BiaxialTestData 对象。

**异常**

无。

### 60.4.2 成员

BiaxialTestData 对象的成员与 [BiaxialTestData](pt02ch60pyo04.md#ker-biaxialtestdata-biaxialtestdata-cpp) 方法的参数具有相同的名称和描述。

### 60.4.3 对应的分析关键字

| [*BIAXIAL TEST DATA](../key/key-link.md#usb-kws-mbitestdata) |
| --- |
