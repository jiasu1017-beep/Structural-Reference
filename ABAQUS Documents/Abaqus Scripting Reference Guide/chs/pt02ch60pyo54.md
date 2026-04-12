# 60.54 GapFlow 对象

GapFlow 对象用于指定孔隙压力内聚单元的切向流动本构参数。

**访问**

```
materialApi.materials()[*name*].gapFlow()
```

### 60.54.1 GapFlow(...)

此方法创建一个 GapFlow 对象。

**路径**

```
materialApi.materials()[*name*].GapFlow
```

**原型**

```
odb_GapFlow&
GapFlow(const odb_SequenceSequenceDouble& table,
        odb_Union kmax,
        bool temperatureDependency,
        int dependencies,
        const odb_String& type);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*kmax*

字符串"NONE"或一个 Double，指定应使用的最大渗透率值。如果 *kmax*="NONE"，Abaqus 假定渗透率无界。此值仅在 *type*="NEWTONIAN" 时有意义。默认值为"NONE"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*type*

一个 odb_String，指定间隙流动类型。可能的值为"NEWTONIAN"和"POWER_LAW"。默认值为"NEWTONIAN"。

**表数据**

如果 *type*=NEWTONIAN，表数据指定以下内容：
- 孔隙粘度。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=POWER_LAW，表数据指定以下内容：
- 稠度。
- 指数。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 GapFlow 对象。

**异常**

无。

### 60.54.2 成员

GapFlow 对象的成员与 [GapFlow](pt02ch60pyo54.md#ker-gapflow-gapflow-cpp) 方法的参数具有相同的名称和描述。

### 60.54.3 对应的分析关键字

| [*GAP FLOW](../key/key-link.md#usb-kws-mgapflow) |
| --- |
