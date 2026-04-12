# 60.99 TriaxialTestData 对象

TriaxialTestData 对象提供三轴测试数据。

**访问**

```
materialApi.materials()[*name*].druckerPrager().triaxialTestData()
```

### 60.99.1 TriaxialTestData(...)

此方法创建一个 TriaxialTestData 对象。

**路径**

```
materialApi.materials()[*name*].druckerPrager().TriaxialTestData
```

**原型**

```
odb_TriaxialTestData&
TriaxialTestData(const odb_SequenceSequenceDouble& table,
                 odb_Union a,
                 odb_Union b,
                 odb_Union pt);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*a*

字符串"NONE"或一个 Double，指定材料常数 ![](../graphics/ker_eqn00278.gif] 的值。当值未知或不安保持在输入值时使用"NONE"。默认值为"NONE"。

*b*

字符串"NONE"或一个 Double，指定材料常数 ![](../graphics/ker_eqn00038.gif] 的值。当值未知或不安保持在输入值时使用"NONE"。默认值为"NONE"。

*pt*

字符串"NONE"或一个 Double，指定材料常数 ![](../graphics/ker_eqn00373.gif] 的值。当值未知或不安保持在输入值时使用"NONE"。默认值为"NONE"。

**表数据**

- 围压应力的符号和大小，![](../graphics/ker_eqn00374.gif]。
- 加载方向应力的符号和大小，![](../graphics/ker_eqn00375.gif]。

**返回值**

一个 TriaxialTestData 对象。

**异常**

RangeError。

### 60.99.2 成员

TriaxialTestData 对象的成员与 [TriaxialTestData](pt02ch60pyo99.md#ker-triaxialtestdata-triaxialtestdata-cpp) 方法的参数具有相同的名称和描述。

### 60.99.3 对应的分析关键字

| [*TRIAXIAL TEST DATA](../key/key-link.md#usb-kws-mtritestdata) |
| --- |
