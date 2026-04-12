# 60.72 MullinsEffect 对象

MullinsEffect 用于指定 Mullins 数据的属性。

**访问**

```
materialApi.materials()[*name*].mullinsEffect()
```

### 60.72.1 成员

MullinsEffect 对象可以具有以下成员：

**原型**

```
odb_String definition() const;
bool temperatureDependency() const;
int dependencies() const;
int properties() const;
odb_SequenceSequenceDouble table() const;
odb_SequenceUniaxialTestData uniaxialTests() const;
odb_UniaxialTestData uniaxialTests(int index) const;
odb_SequenceBiaxialTestData biaxialTests() const;
odb_BiaxialTestData biaxialTests(int index) const;
odb_SequencePlanarTestData planarTests() const;
odb_PlanarTestData planarTests(int index) const;
```

*definition*

一个 odb_String，指定数据定义方法。可能的值为"USER"、"CONSTANTS"和"TEST_DATA"。默认值为"CONSTANTS"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*properties*

一个整数，指定作为用户定义超弹性材料数据所需的属性值数量。默认值为 0。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。默认值为空序列。

*uniaxialTests*

一个 [UniaxialTestData](pt02ch60pyo101.md) 对象序列。

*biaxialTests*

一个 [BiaxialTestData](pt02ch60pyo04.md) 对象序列。

*planarTests*

一个 [PlanarTestData](pt02ch60pyo76.md) 对象序列。
