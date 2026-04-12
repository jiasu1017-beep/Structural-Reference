# 60.29 CycledPlastic 对象

CycledPlastic 对象为 ORNL 本构模型指定循环屈服应力数据。

**访问**

```
materialApi.materials()[*name*].plastic().cycledPlastic()
```

### 60.29.1 CycledPlastic(...)

此方法创建一个 CycledPlastic 对象。

**路径**

```
materialApi.materials()[*name*].plastic().CycledPlastic
```

**原型**

```
odb_CycledPlastic&
CycledPlastic(const odb_SequenceSequenceDouble& table,
              bool temperatureDependency);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

**表数据**

- 屈服应力。
- 塑性应变。
- 温度（如果数据依赖温度）。

**返回值**

一个 CycledPlastic 对象。

**异常**

无。

### 60.29.2 成员

CycledPlastic 对象的成员与 [CycledPlastic](pt02ch60pyo29.md#ker-cycledplastic-cycledplastic-cpp) 方法的参数具有相同的名称和描述。

### 60.29.3 对应的分析关键字

| [*CYCLED PLASTIC](../key/key-link.md#usb-kws-mcycledplastic) |
| --- |
