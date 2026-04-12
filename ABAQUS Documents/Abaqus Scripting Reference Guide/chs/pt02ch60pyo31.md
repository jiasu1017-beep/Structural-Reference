# 60.31 DamageEvolution 对象

DamageEvolution 对象用于指定定义损伤演化的材料特性。

**访问**

```
materialApi.materials()[*name*].ductileDamageInitiation()\
.damageEvolution()
materialApi.materials()[*name*].fldDamageInitiation().damageEvolution()
materialApi.materials()[*name*].flsdDamageInitiation().damageEvolution()
materialApi.materials()[*name*].hashinDamageInitiation().damageEvolution()
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.damageEvolution()
materialApi.materials()[*name*].maxeDamageInitiation().damageEvolution()
materialApi.materials()[*name*].maxpeDamageInitiation().damageEvolution()
materialApi.materials()[*name*].maxpsDamageInitiation().damageEvolution()
materialApi.materials()[*name*].maxsDamageInitiation().damageEvolution()
materialApi.materials()[*name*].mkDamageInitiation().damageEvolution()
materialApi.materials()[*name*].msfldDamageInitiation().damageEvolution()
materialApi.materials()[*name*].quadeDamageInitiation().damageEvolution()
materialApi.materials()[*name*].quadsDamageInitiation().damageEvolution()
materialApi.materials()[*name*].shearDamageInitiation().damageEvolution()
```

### 60.31.1 DamageEvolution(...)

此方法创建一个 DamageEvolution 对象。

**路径**

```
materialApi.materials()[*name*].ductileDamageInitiation().DamageEvolution
materialApi.materials()[*name*].fldDamageInitiation().DamageEvolution
materialApi.materials()[*name*].flsdDamageInitiation().DamageEvolution
materialApi.materials()[*name*].hashinDamageInitiation().DamageEvolution
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.DamageEvolution
materialApi.materials()[*name*].maxeDamageInitiation().DamageEvolution
materialApi.materials()[*name*].maxpeDamageInitiation().DamageEvolution
materialApi.materials()[*name*].maxpsDamageInitiation().DamageEvolution
materialApi.materials()[*name*].maxsDamageInitiation().DamageEvolution
materialApi.materials()[*name*].mkDamageInitiation().DamageEvolution
materialApi.materials()[*name*].msfldDamageInitiation().DamageEvolution
materialApi.materials()[*name*].quadeDamageInitiation().DamageEvolution
materialApi.materials()[*name*].quadsDamageInitiation().DamageEvolution
materialApi.materials()[*name*].shearDamageInitiation().DamageEvolution
```

**原型**

```
odb_DamageEvolution&
DamageEvolution(const odb_String& type,
                const odb_SequenceSequenceDouble& table,
                const odb_String& degradation,
                bool temperatureDependency,
                int dependencies,
                const odb_String& mixedModeBehavior,
                const odb_String& modeMixRatio,
                odb_Union power,
                const odb_String& softening);
```

**必需参数**

*type*

一个 odb_String，指定损伤演化类型。可能的值为"DISPLACEMENT"和"ENERGY"。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*degradation*

一个 odb_String，指定退化。可能的值为"MAXIMUM"和"MULTIPLICATIVE"。默认值为"MAXIMUM"。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*mixedModeBehavior*

一个 odb_String，指定混合模式行为。可能的值为"MODE_INDEPENDENT"、"TABULAR"、"POWER_LAW"和"BK"。默认值为"MODE_INDEPENDENT"。

*modeMixRatio*

一个 odb_String，指定模式混合比。可能的值为"ENERGY"和"TRACTION"。默认值为"ENERGY"。

*power*

字符串"NONE"或一个 Double，指定幂律中或定义内聚力单元断裂能随模式混合变化的 Benzeggagh-Kenane 准则中的指数。默认值为"NONE"。

*softening*

一个 odb_String，指定软化。可能的值为"LINEAR"、"EXPONENTIAL"和"TABULAR"。默认值为"LINEAR"。

**表数据**

如果 *type*=DISPLACEMENT，*softening*=LINEAR，*mixedModeBehavior*=MODE_INDEPENDENT，表数据指定以下内容：
- 从损伤起始时刻测量的失效时的等效总位移或塑性位移。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，*softening*=LINEAR，*mixedModeBehavior*=MODE_INDEPENDENT，表数据指定以下内容：
- 断裂能。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，*softening*=LINEAR，*mixedModeBehavior*=TABULAR，表数据指定以下内容：
- 从损伤起始时刻测量的失效时的总位移。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，*softening*=LINEAR，*mixedModeBehavior*=TABULAR，表数据指定以下内容：
- 断裂能。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，*softening*=EXPONENTIAL，*mixedModeBehavior*=MODE_INDEPENDENT，表数据指定以下内容：
- 从损伤起始时刻测量的失效时的等效总位移或塑性位移。
- 指数律参数。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，*softening*=EXPONENTIAL，*mixedModeBehavior*=MODE_INDEPENDENT，表数据指定以下内容：
- 断裂能。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，*softening*=EXPONENTIAL，*mixedModeBehavior*=TABULAR，表数据指定以下内容：
- 从损伤起始时刻测量的失效时的总位移。
- 指数律参数。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，*softening*=EXPONENTIAL，*mixedModeBehavior*=TABULAR，表数据指定以下内容：
- 断裂能。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，*softening*=TABULAR，*mixedModeBehavior*=MODE_INDEPENDENT，表数据指定以下内容：
- 损伤变量。
- 从损伤起始时刻测量的等效总位移或塑性位移。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，*softening*=TABULAR，*mixedModeBehavior*=TABULAR，表数据指定以下内容：
- 损伤变量。
- 从损伤起始时刻测量的等效总位移或塑性位移。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，*softening*=LINEAR 或 EXPONENTIAL，*mixedModeBehavior*=POWER_LAW 或 BK，表数据指定以下内容：
- 正模式断裂能。
- 第一个剪切方向失效的剪切模式断裂能。
- 第二个剪切方向失效的剪切模式断裂能。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，*softening*=LINEAR 且 [DamageInitiation](pt02ch60pyo32.md) 的构造函数为 `HashinDamageInitiation`，表数据指定以下内容：
- 纤维拉伸断裂能。
- 纤维压缩断裂能。
- 基体拉伸断裂能。
- 基体压缩断裂能。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DamageEvolution 对象。

**异常**

RangeError。

### 60.31.2 成员

DamageEvolution 对象的成员与 [DamageEvolution](pt02ch60pyo31.md#ker-damageevolution-damageevolution-cpp) 方法的参数具有相同的名称和描述。

### 60.31.3 对应的分析关键字

| [*DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mdamageevolution) |
| --- |
