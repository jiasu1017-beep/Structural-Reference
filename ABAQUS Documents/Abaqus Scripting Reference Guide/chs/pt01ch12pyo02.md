# 12.2 CDCTerm 对象

CDCTerm 对象用于为 [DerivedComponent](pt01ch12pyo13.md) 对象创建贡献项。

**访问**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*]
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*]
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*]
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*]
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*]
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*]
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*]
```

### 12.2.1 CDCTerm(...)

此方法创建 CDCTerm 对象。

**路径**

```
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.CDCTerm
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.CDCTerm
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.CDCTerm
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.CDCTerm
```

**必需参数**

*intrinsicComponents*

Int 的序列，指定定义贡献项的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *intrinsicComponents* ![](../graphics/ker_eqn00013.gif) 6。如果 DerivedComponent 对象正被 Potential 对象引用，则只能指定可用的分量。如果 DerivedComponent 对象直接被 ConnectorFriction 对象引用，则不是这种情况。默认值为空序列。

*table*

Float 的序列的序列，指定分量号以及温度和场值。表格数据的每个序列指定：
- 第一个固有分量号。
- 如果适用，第二个固有分量号。
- 依此类推。
- 如果适用，第一个独立分量号。
- 如果适用，第二个独立分量号。
- 依此类推。
- 如果适用，温度值。
- 如果适用，第一个场变量的值。
- 如果适用，第二个场变量的值。
- 依此类推。

默认值为空序列。

**可选参数**

*termOperator*

SymbolicConstant，指定组合贡献项的方法：平方和的平方根、直接和或 Macauley 和。可能的值为 RSS、SUM 和 MACAULEY。默认值为 RSS。

*termSign*

SymbolicConstant，指定贡献项的总体符号。可能的值为 POSITIVE 和 NEGATIVE。默认值为 POSITIVE。

*localDependency*

Boolean，指定表格数据是否依赖于相对位置的分量或结构相对运动的分量。默认值为 OFF。

*indepCompType*

SymbolicConstant，指定 localDependency 是指相对位置的分量还是结构相对运动的分量。可能的值为 POSITION 和 MOTION。默认值为 POSITION。

*indepCompType* 参数仅在 *localDependency*=ON 时适用。

*indepComponents*

Int 的序列，指定派生分量定义中包含的独立分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *indepComponents* ![](../graphics/ker_eqn00013.gif) 6。只能指定可用的分量。*indepComponents* 参数仅在 *localDependency*=ON 时适用。默认值为空序列。

*tempDependency*

Boolean，指定表格数据是否依赖于温度。默认值为 OFF。

*fieldDependencies*

Int，指定场变量依赖的数量。默认值为 0。

**返回值**

CDCTerm 对象。

**异常**

ValueError 和 TextError。

### 12.2.2 setValues(...)

此方法修改 CDCTerm 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CDCTerm](pt01ch12pyo02.md#ker-cdcterm-cdcterm-pyc) 方法的参数相同。

**返回值**

无。

**异常**

ValueError。

### 12.2.3 成员

CDCTerm 对象的成员与 [CDCTerm](pt01ch12pyo02.md#ker-cdcterm-cdcterm-pyc) 方法的参数具有相同的名称和描述。

此外，CDCTerm 对象可以具有以下成员：

*options*

[ConnectorOptions](pt01ch12pyo09.md) 对象，指定用于定义此 [ConnectorBehaviorOption](pt01ch12pyo01.md) 的表格选项的 [ConnectorOptions](pt01ch12pyo09.md)。
