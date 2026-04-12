# 60.91 SimpleShearTestData 对象

SimpleShearTestData 对象提供简单剪切测试数据。

**访问**

```
materialApi.materials()[*name*].hyperfoam().simpleShearTestData()
```

### 60.91.1 SimpleShearTestData(...)

此方法创建一个 SimpleShearTestData 对象。

**路径**

```
materialApi.materials()[*name*].hyperfoam().SimpleShearTestData
```

**原型**

```
odb_SimpleShearTestData&
SimpleShearTestData(const odb_SequenceSequenceDouble& table);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

无。

**表数据**

- 名义剪切应力，![](../graphics/ker_eqn00332.gif]。
- 名义剪切应变，![](../graphics/ker_eqn00040.gif]。
- 名义横向应力，![](../graphics/ker_eqn00366.gif]（垂直于剪切应力边缘）。此应力值是可选的。

**返回值**

一个 SimpleShearTestData 对象。

**异常**

无。

### 60.91.2 成员

SimpleShearTestData 对象的成员与 [SimpleShearTestData](pt02ch60pyo91.md#ker-simplesheartestdata-simplesheartestdata-cpp) 方法的参数具有相同的名称和描述。

### 60.91.3 对应的分析关键字

| [*SIMPLE SHEAR TEST DATA](../key/key-link.md#usb-kws-msimplesheartestdata) |
| --- |
