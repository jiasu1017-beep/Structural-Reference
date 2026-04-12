# 60.22 ConcreteTensionDamage 对象

ConcreteTensionDamage 对象用于指定混凝土损伤塑性模型的硬化。

**访问**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteTensionDamage()
```

### 60.22.1 ConcreteTensionDamage(...)

此方法创建一个 ConcreteTensionDamage 对象。

**路径**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteTensionDamage
```

**原型**

```
odb_ConcreteTensionDamage&
ConcreteTensionDamage(const odb_SequenceSequenceDouble& table,
                      double compressionRecovery,
                      const odb_String& type,
                      bool temperatureDependency,
                      int dependencies);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*compressionRecovery*

一个 Double，指定刚度恢复因子 ![](../graphics/ker_eqn00135.gif) 的值，该因子决定当载荷从拉伸变为压缩时恢复的压刚度量。默认值为 1.0。

*type*

一个 odb_String，指定拉伸损伤数据的类型。设置 *type*="STRAIN" 以将拉伸损伤变量指定为裂缝应变的函数。设置 *type*="DISPLACEMENT" 以将拉伸损伤变量指定为裂缝位移的函数。可能的值为"STRAIN"和"DISPLACEMENT"。默认值为"STRAIN"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

**表数据**

如果 *type*=STRAIN，表数据指定以下内容：
- 拉伸损伤变量，![](../graphics/ker_eqn00136.gif)。
- 直接裂缝应变，![](../graphics/ker_eqn00137.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表数据指定以下内容：
- 拉伸损伤变量，![](../graphics/ker_eqn00136.gif)。
- 直接裂缝位移，![](../graphics/ker_eqn00138.gif)。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteTensionDamage 对象。

**异常**

RangeError。

### 60.22.2 成员

ConcreteTensionDamage 对象的成员与 [ConcreteTensionDamage](pt02ch60pyo22.md#ker-concretetensiondamage-concretetensiondamage-cpp) 方法的参数具有相同的名称和描述。

### 60.22.3 对应的分析关键字

| [*CONCRETE TENSION DAMAGE](../key/key-link.md#usb-kws-mconcretetensdamage) |
| --- |
