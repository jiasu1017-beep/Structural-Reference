# 60.9 CapCreepConsolidation 对象

CapCreepConsolidation 对象用于指定帽盖蠕变模型和材料特性。

**访问**

```
materialApi.materials()[*name*].capPlasticity().capCreepConsolidation()
```

### 60.9.1 CapCreepConsolidation(...)

此方法创建一个 CapCreepConsolidation 对象。

**路径**

```
materialApi.materials()[*name*].capPlasticity().CapCreepConsolidation
```

**原型**

```
odb_CapCreepConsolidation&
CapCreepConsolidation(const odb_SequenceSequenceDouble& table,
                      const odb_String& law,
                      bool temperatureDependency,
                      int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*law*

一个 odb_String，指定帽盖蠕变定律。可能的值为"STRAIN"、"TIME"、"SINGHM"和"USER"。默认值为"STRAIN"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *law*=STRAIN 或 *law*=TIME，表数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *law*=SINGHM，表数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00090.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- ![](../graphics/ker_eqn00091.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CapCreepConsolidation 对象。

**异常**

无。

### 60.9.2 成员

CapCreepConsolidation 对象的成员与 [CapCreepConsolidation](pt02ch60pyo09.md#ker-capcreepconsolidation-capcreepconsolidation-cpp) 方法的参数具有相同的名称和描述。

### 60.9.3 对应的分析关键字

| [*CAP CREEP](../key/key-link.md#usb-kws-mcapcreep) |
| --- |
