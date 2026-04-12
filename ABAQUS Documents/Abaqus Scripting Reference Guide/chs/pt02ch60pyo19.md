# 60.19 ConcreteCompressionDamage 对象

ConcreteCompressionDamage 对象用于指定混凝土损伤塑性模型的硬化。

**访问**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteCompressionDamage()
```

### 60.19.1 ConcreteCompressionDamage(...)

此方法创建一个 ConcreteCompressionDamage 对象。

**路径**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteCompressionDamage
```

**原型**

```
odb_ConcreteCompressionDamage&
ConcreteCompressionDamage(const odb_SequenceSequenceDouble& table,
                          double tensionRecovery,
                          bool temperatureDependency,
                          int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*tensionRecovery*

一个 Double，指定刚度恢复因子 ![](../graphics/ker_eqn00127.gif) 的值，该因子决定当载荷从压缩变为拉伸时恢复的张拉刚度量。默认值为 0.0。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

- 压缩损伤变量，![](../graphics/ker_eqn00128.gif)。
- 非弹性（压碎）应变，![](../graphics/ker_eqn00129.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteCompressionDamage 对象。

**异常**

RangeError。

### 60.19.2 成员

ConcreteCompressionDamage 对象的成员与 [ConcreteCompressionDamage](pt02ch60pyo19.md#ker-concretecompressiondamage-concretecompressiondamage-cpp) 方法的参数具有相同的名称和描述。

### 60.19.3 对应的分析关键字

| [*CONCRETE COMPRESSION DAMAGE](../key/key-link.md#usb-kws-mconcretecompdamage) |
| --- |
