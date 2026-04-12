# 60.7 BrittleShear 对象

BrittleShear 对象用于指定脆性断裂模型中材料的后断裂剪切行为。

**访问**

```
materialApi.materials()[*name*].brittleCracking().brittleShear()
```

### 60.7.1 BrittleShear(...)

此方法创建一个 BrittleShear 对象。

**路径**

```
materialApi.materials()[*name*].brittleCracking().BrittleShear
```

**原型**

```
odb_BrittleShear&
BrittleShear(const odb_SequenceSequenceDouble& table,
             bool temperatureDependency,
             int dependencies,
             const odb_String& type);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*type*

一个 odb_String，指定后断裂剪切行为的类型。可能的值为"RETENTION_FACTOR"和"POWER_LAW"。默认值为"RETENTION_FACTOR"。

**表数据**

如果 *type*=RETENTION_FACTOR，表数据指定以下内容：
- 剪切保留因子。
- 裂纹张开应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=POWER_LAW，表数据指定以下内容：
- e。
- p。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 BrittleShear 对象。

**异常**

RangeError。

### 60.7.2 成员

BrittleShear 对象的成员与 [BrittleShear](pt02ch60pyo07.md#ker-brittleshear-brittleshear-cpp) 方法的参数具有相同的名称和描述。

### 60.7.3 对应的分析关键字

| [*BRITTLE SHEAR](../key/key-link.md#usb-kws-mbrittleshear) |
| --- |
