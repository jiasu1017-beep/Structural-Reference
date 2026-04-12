# 58.2 CDCTerm 对象







CDCTerm 对象用于为 [DerivedComponent](pt02ch58pyo13.md) 对象创建贡献项。

**访问**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent().cdcTerms(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()\
.cdcTerms(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent().cdcTerms(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent().cdcTerms(*i*)
```

### 58.2.1 CDCTerm(...)

此方法创建 CDCTerm 对象。

**路径**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent().CDCTerm
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()\
.CDCTerm
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent().CDCTerm
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent().CDCTerm
```

**原型**

```
odb_CDCTerm&
CDCTerm(const odb_SequenceInt& intrinsicComponents,
        const odb_SequenceSequenceDouble& table,
        const odb_String& termOperator,
        const odb_String& termSign,
        bool localDependency,
        const odb_String& indepCompType,
        const odb_SequenceInt& indepComponents,
        bool tempDependency,
        int fieldDependencies);
```

**必需参数**

*intrinsicComponents*

一个 odb_SequenceInt，指定定义贡献项的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *intrinsicComponents* ![](../graphics/ker_eqn00013.gif) 6。仅当 DerivedComponent 对象被 Potential 对象引用时，才能指定可用分量。如果 DerivedComponent 对象直接由 ConnectorFriction 对象引用，则不受此限制。默认值为空序列。

*table*

一个 odb_SequenceSequenceDouble，指定分量号以及温度和场值。表数据的每个序列指定：
- 第一个内在分量号。
- 如适用，第二个内在分量号。
- 依此类推。
- 如适用，第一个独立分量号。
- 如适用，第二个独立分量号。
- 依此类推。
- 如适用，温度值。
- 如适用，第一个场变量的值。
- 如适用，第二个场变量的值。
- 依此类推。

默认值为空序列。

**可选参数**

*termOperator*

一个 odb_String，指定组合贡献项的方法：平方和的平方根、直接和或 Macauley 和。可能的值为 "RSS"、"SUM" 和 "MACAULEY"。默认值为 "RSS"。

*termSign*

一个 odb_String，指定贡献项的整体符号。可能的值为 "POSITIVE" 和 "NEGATIVE"。默认值为 "POSITIVE"。

*localDependency*

一个 Boolean，指定表数据是否依赖于相对位置分量或结构相对运动分量。默认值为 false。

*indepCompType*

一个 odb_String，指定 localDependency 是指相对位置分量还是结构相对运动分量。可能的值为 "POSITION" 和 "MOTION"。默认值为 "POSITION"。

*indepCompType* 参数仅在 *localDependency*=true 时适用。

*indepComponents*

一个 odb_SequenceInt，指定派生分量定义中包含的独立分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *indepComponents* ![](../graphics/ker_eqn00013.gif) 6。仅能指定可用分量。*indepComponents* 参数仅在 *localDependency*=true 时适用。默认值为空序列。

*tempDependency*

一个 Boolean，指定表数据是否依赖于温度。默认值为 false。

*fieldDependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

**返回值**

CDCTerm 对象。

**异常**

ValueError 和 TextError。

### 58.2.2 setValues(...)

此方法修改 CDCTerm 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [CDCTerm](pt02ch58pyo02.md#ker-cdcterm-cdcterm-cpp) 方法的参数相同。

**返回值**

None

**异常**

ValueError。

### 58.2.3 成员

CDCTerm 对象具有与 [CDCTerm](pt02ch58pyo02.md#ker-cdcterm-cdcterm-cpp) 方法的参数具有相同名称和描述的成员。

此外，CDCTerm 对象可以具有以下成员：

**原型**

```
odb_ConnectorOptions options() const;
```

*options*

一个 [ConnectorOptions](pt02ch58pyo09.md) 对象，指定用于定义此 [ConnectorBehaviorOption](pt02ch58pyo01.md) 的表格选项的 [ConnectorOptions](pt02ch58pyo09.md)。

