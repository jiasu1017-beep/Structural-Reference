# 60.5 BrittleCracking 对象

BrittleCracking 对象用于指定脆性断裂材料模型的断裂和后断裂特性。

**访问**

```
materialApi.materials()[*name*].brittleCracking()
```

### 60.5.1 BrittleCracking(...)

此方法创建一个 BrittleCracking 对象。

**路径**

```
materialApi.materials()[*name*].BrittleCracking
```

**原型**

```
odb_BrittleCracking&
BrittleCracking(const odb_SequenceSequenceDouble& table,
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

一个 odb_String，指定后断裂行为的类型。可能的值为"STRAIN"、"DISPLACEMENT"和"GFI"。默认值为"STRAIN"。

**表数据**

如果 *type*=STRAIN，表数据指定以下内容：
- 断裂后的剩余直接应力。
- 直接断裂应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表数据指定以下内容：
- 断裂后的剩余直接应力。
- 直接断裂位移。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=GFI，表数据指定以下内容：
- 失效应力。
- I 型断裂能。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 BrittleCracking 对象。

**异常**

无。

### 60.5.2 成员

BrittleCracking 对象的成员与 [BrittleCracking](pt02ch60pyo05.md#ker-brittlecracking-brittlecracking-cpp) 方法的参数具有相同的名称和描述。

此外，BrittleCracking 对象可以具有以下成员：

**原型**

```
odb_BrittleShear brittleShear() const;
odb_BrittleFailure brittleFailure() const;
```

*brittleShear*

一个 [BrittleShear](pt02ch60pyo07.md) 对象。

*brittleFailure*

一个 [BrittleFailure](pt02ch60pyo06.md) 对象。

### 60.5.3 对应的分析关键字

| [*BRITTLE CRACKING](../key/key-link.md#usb-kws-mcracking) |
| --- |
