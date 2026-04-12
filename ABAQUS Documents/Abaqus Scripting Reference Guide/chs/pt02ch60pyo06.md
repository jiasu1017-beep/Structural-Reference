# 60.6 BrittleFailure 对象

BrittleFailure 对象用于指定材料的脆性失效。

**访问**

```
materialApi.materials()[*name*].brittleCracking().brittleFailure()
```

### 60.6.1 BrittleFailure(...)

此方法创建一个 BrittleFailure 对象。

**路径**

```
materialApi.materials()[*name*].brittleCracking().BrittleFailure
```

**原型**

```
odb_BrittleFailure&
BrittleFailure(const odb_SequenceSequenceDouble& table,
               bool temperatureDependency,
               int dependencies,
               const odb_String& failureCriteria);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*failureCriteria*

一个 odb_String，指定失效准则。可能的值为"UNIDIRECTIONAL"、"BIDIRECTIONAL"和"TRIDIRECTIONAL"。默认值为"UNIDIRECTIONAL"。

**表数据**

如果父级 [BrittleCracking](pt02ch60pyo05.md) 成员 *type*=STRAIN，表数据指定以下内容：
- 直接断裂失效应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果父级 [BrittleCracking](pt02ch60pyo05.md) 成员 *type*=DISPLACEMENT 或 *type*=GFI，表数据指定以下内容：
- 直接断裂失效位移。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 BrittleFailure 对象。

**异常**

RangeError。

### 60.6.2 成员

BrittleFailure 对象的成员与 [BrittleFailure](pt02ch60pyo06.md#ker-brittlefailure-brittlefailure-cpp) 方法的参数具有相同的名称和描述。

### 60.6.3 对应的分析关键字

| [*BRITTLE FAILURE](../key/key-link.md#usb-kws-mbrittlefailure) |
| --- |
