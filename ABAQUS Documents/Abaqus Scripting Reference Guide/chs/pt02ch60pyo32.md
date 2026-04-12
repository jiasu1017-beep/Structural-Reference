# 60.32 DamageInitiation 对象

DamageInitiation 对象用于指定定义损伤起始的材料特性。

**访问**

```
materialApi.materials()[*name*].ductileDamageInitiation()
materialApi.materials()[*name*].fldDamageInitiation()
materialApi.materials()[*name*].flsdDamageInitiation()
materialApi.materials()[*name*].hashinDamageInitiation()
materialApi.materials()[*name*].johnsonCookDamageInitiation()
materialApi.materials()[*name*].maxeDamageInitiation()
materialApi.materials()[*name*].maxpeDamageInitiation()
materialApi.materials()[*name*].maxpsDamageInitiation()
materialApi.materials()[*name*].maxsDamageInitiation()
materialApi.materials()[*name*].mkDamageInitiation()
materialApi.materials()[*name*].msfldDamageInitiation()
materialApi.materials()[*name*].quadeDamageInitiation()
materialApi.materials()[*name*].quadsDamageInitiation()
materialApi.materials()[*name*].shearDamageInitiation()
```

### 60.32.1 DuctileDamageInitiation(...)

此方法创建一个 DamageInitiation 对象。

**路径**

```
materialApi.materials()[*name*].DuctileDamageInitiation
```

**原型**

```
odb_DamageInitiation&
DuctileDamageInitiation(const odb_SequenceSequenceDouble& table,
                        const odb_String& definition,
                        double feq,
                        double fnn,
                        double fnt,
                        int frequency,
                        double ks,
                        int numberImperfections,
                        bool temperatureDependency,
                        int dependencies,
                        double alpha,
                        double omega,
                        double tolerance,
                        const odb_String& direction);
```

**必需参数**

*table*

一个 odb_SequenceSequenceDouble，指定"表数据"部分中描述的项目。

**可选参数**

*definition*

一个 odb_String，指定损伤起始定义。可能的值为"FLD"和"MSFLD"。默认值为"MSFLD"。

*feq*

一个 Double，指定等效塑性应变变形严重度指数的临界值。默认值为 10.0。

*fnn*

一个 Double，指定与凹槽方向垂直的应变变形严重度指数的临界值。默认值为 10.0。

*fnt*

一个 Double，指定剪切应变变形严重度指数的临界值。默认值为 10.0。

*frequency*

一个整数，指定执行 Marciniak-Kuczynski 分析的频率（以增量为单位）。默认值为 1。

*ks*

一个 Double，指定 Ks 的值。默认值为 0.0。

*numberImperfections*

一个整数，指定用于 Marciniak-Kuczynski 分析评估的缺陷数量。这些缺陷假定在角方向上等距分布。默认值为 4。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*alpha*

一个 Double，指定将乘以 Hashin 纤维起始准则中剪切贡献的系数值。默认值为 0.0。

*omega*

一个 Double，指定用于过滤主应变率比值的因子，用于 MSFLD 损伤起始准则的评估。默认值为 1.0。

*tolerance*

一个 Double，指定损伤起始准则必须满足的容差。默认值为 0.05。

*direction*

一个 odb_String，指定损伤起始方向。可能的值为"NMORI"和"TMORI"。默认值为"NMORI"。

**表数据**

如果构造函数是 `DuctileDamageInitiation`，表数据指定以下内容：
- 损伤起始时的等效断裂应变。
- 应力三轴度。
- 应变率。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `FldDamageInitiation`，表数据指定以下内容：
- 损伤起始时的主应变。
- 次应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `FlsdDamageInitiation`，表数据指定以下内容：
- 损伤起始时的主应力。
- 次应力。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `JohnsonCookDamageInitiation`，表数据指定以下内容：
- Johnson-Cook 失效参数 D1。
- Johnson-Cook 失效参数 D2。
- Johnson-Cook 失效参数 D3。
- Johnson-Cook 失效参数 D4。
- Johnson-Cook 失效参数 D5。
- 熔化温度。
- 转变温度。
- 参考应变率。

如果构造函数是 `MkDamageInitiation`，表数据指定以下内容：
- 相对于截面标称厚度的缺陷大小。
- 相对于局部材料方向 1 方向的角度（以度为单位）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `MsfldDamageInitiation` 且 *definition*=MSFLD，表数据指定以下内容：
- 纯正模态下损伤起始的名义应变。
- 局部颈缩起始时的等效塑性应变。
- 次应变与主应变之比。
- 等效塑性应变率。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `MsfldDamageInitiation` 且 *definition*=FLD，表数据指定以下内容：
- 局部颈缩起始时的主应变。
- 局部颈缩起始时的等效塑性应变。
- 次应变与主应变之比。
- 等效塑性应变率。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `QuadeDamageInitiation` 或 `MaxeDamageInitiation`，表数据指定以下内容：
- 纯正模态下损伤起始的名义应变。
- 仅涉及沿第一剪切方向分离的剪切模态下损伤起始的名义应变。
- 仅涉及沿第二剪切方向分离的剪切模态下损伤起始的名义应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `QuadsDamageInitiation` 或 `MaxsDamageInitiation`，表数据指定以下内容：
- 纯正模态下损伤起始的名义应变。
- 仅涉及沿第一剪切方向分离的剪切模态下损伤起始的名义应变。
- 仅涉及沿第二剪切方向分离的剪切模态下损伤起始的名义应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `MaxpeDamageInitiation`，表数据指定以下内容：
- 损伤起始时的最大主应变。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `MaxpsDamageInitiation`，表数据指定以下内容：
- 损伤起始时的最大主应力。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `ShearDamageInitiation`，表数据指定以下内容：
- 损伤起始时的等效断裂应变。
- 剪切应力比。
- 应变率。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数是 `HashinDamageInitiation`，表数据指定以下内容：
- 纤维拉伸强度。
- 纤维压缩强度。
- 基体拉伸强度。
- 基体压缩强度。
- 纵向剪切强度。
- 横向剪切强度。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DamageInitiation 对象。

**异常**

RangeError。

### 60.32.2 成员

DamageInitiation 对象可以具有以下成员：

**原型**

```
odb_String definition() const;
double feq() const;
double fnn() const;
double fnt() const;
int frequency() const;
double ks() const;
int numberImperfections() const;
bool temperatureDependency() const;
int dependencies() const;
double alpha() const;
double omega() const;
double tolerance() const;
odb_String direction() const;
odb_SequenceSequenceDouble table() const;
odb_DamageEvolution damageEvolution() const;
odb_DamageStabilization damageStabilization() const;
odb_DamageStabilizationCohesive damageStabilizationCohesive() const;
```

*definition*

一个 odb_String，指定损伤起始定义。可能的值为"FLD"和"MSFLD"。默认值为"MSFLD"。

*feq*

一个 Double，指定等效塑性应变变形严重度指数的临界值。默认值为 10.0。

*fnn*

一个 Double，指定与凹槽方向垂直的应变变形严重度指数的临界值。默认值为 10.0。

*fnt*

一个 Double，指定剪切应变变形严重度指数的临界值。默认值为 10.0。

*frequency*

一个整数，指定执行 Marciniak-Kuczynski 分析的频率（以增量为单位）。默认值为 1。

*ks*

一个 Double，指定 Ks 的值。默认值为 0.0。

*numberImperfections*

一个整数，指定用于 Marciniak-Kuczynski 分析评估的缺陷数量。这些缺陷假定在角方向上等距分布。默认值为 4。

*temperatureDependency*

一个布尔值，指定数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定场变量依赖数量。默认值为 0。

*alpha*

一个 Double，指定将乘以 Hashin 纤维起始准则中剪切贡献的系数值。默认值为 0.0。

*omega*

一个 Double，指定用于过滤主应变率比值的因子，用于 MSFLD 损伤起始准则的评估。默认值为 1.0。

*tolerance*

一个 Double，指定损伤起始准则必须满足的容差。默认值为 0.05。

*direction*

一个 odb_String，指定损伤起始方向。可能的值为"NMORI"和"TMORI"。默认值为"NMORI"。

*table*

一个 odb_SequenceSequenceDouble，指定"表数据"部分中描述的项目。

*damageEvolution*

一个 [DamageEvolution](pt02ch60pyo31.md) 对象。

*damageStabilization*

一个 [DamageStabilization](pt02ch60pyo33.md) 对象。

*damageStabilizationCohesive*

一个 [DamageStabilizationCohesive](pt02ch60pyo34.md) 对象。

### 60.32.3 对应的分析关键字

| [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation) |
| --- |
