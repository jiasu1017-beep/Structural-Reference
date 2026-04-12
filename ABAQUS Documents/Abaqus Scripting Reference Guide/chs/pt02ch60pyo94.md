# 60.94 Sorption 对象

Sorption 对象用于定义部分饱和多孔介质在耦合润湿液体流动和多孔介质应力分析中的吸收和解吸行为。

**访问**

```
materialApi.materials()[*name*].sorption()
```

### 60.94.1 Sorption(...)

此方法创建一个 Sorption 对象。

**路径**

```
materialApi.materials()[*name*].Sorption
```

**原型**

```
odb_Sorption&
Sorption(const odb_SequenceSequenceDouble& absorptionTable,
         const odb_String& lawAbsorption,
         bool exsorption,
         const odb_String& lawExsorption,
         double scanning,
         const odb_SequenceSequenceDouble& exsorptionTable);
```

**必需参数**

*absorptionTable*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。

**可选参数**

*lawAbsorption*

一个 odb_String，指定吸收行为。可能的值为"LOG"和"TABULAR"。默认值为"TABULAR"。

*exsorption*

一个布尔值，指定是否指定了解吸数据。默认值为 false。

*lawExsorption*

一个 odb_String，指定解吸行为。可能的值为"LOG"和"TABULAR"。默认值为"TABULAR"。

*scanning*

一个 Double，指定扫描线的斜率，![](../graphics/ker_eqn00368.gif]。此斜率必须为正且大于吸收或解吸行为的斜率。默认值为 0.0。

*exsorptionTable*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。默认值为空序列。

**表数据**

如果 *lawAbsorption*=TABULAR 或 *lawExsorption*=TABULAR，则 *absorptionTable* 和 *exsorptionTable* 数据分别指定以下内容：
- 孔隙压力，![](../graphics/ker_eqn00369.gif]。
- 饱和度，![](../graphics/ker_eqn00234.gif]。

如果 *lawAbsorption*=LOG 或 *lawExsorption*=LOG，则 *absorptionTable* 和 *exsorptionTable* 数据分别指定以下内容：
- A。
- B。
- ![](../graphics/ker_eqn00370.gif]。
- ![](../graphics/ker_eqn00371.gif]。

**返回值**

一个 Sorption 对象。

**异常**

RangeError。

### 60.94.2 成员

Sorption 对象的成员与 [Sorption](pt02ch60pyo94.md#ker-sorption-sorption-cpp) 方法的参数具有相同的名称和描述。

### 60.94.3 对应的分析关键字

| [*SORPTION](../key/key-link.md#usb-kws-msorption) |
| --- |
