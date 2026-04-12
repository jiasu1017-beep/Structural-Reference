# 51.6 IntegratedOutputSection 对象

IntegratedOutputSection 对象指定用于集成输出的参数。

**访问**

```
import step
mdb.models[*name*].integratedOutputSections[*name*]
```

### 51.6.1 IntegratedOutputSection(...)

此方法创建一个 IntegratedOutputSection 对象。

**路径**

```
mdb.models[*name*].IntegratedOutputSection
```

**必要参数**

*name*

一个 String，指定仓库键。

**可选参数**

*surface*

一个 [Region](pt01ch45pyo03.md) 对象，指定输出所基于的表面。

*refPoint*

 `None` 或一个 [Region](pt01ch45pyo03.md) 对象，指定计算输出区域积分力矩的锚点，或 SymbolicConstant None（代表全局原点）。默认值为 `None`。

*refPointAtCenter*

一个 Boolean，指定是否调整 *refPoint* 使其与输出区域在初始配置中的中心重合。此参数仅在包含 *refPoint* 参数时有效。默认值为 OFF。

*refPointMotion*

一个 SymbolicConstant，指定如何将 *refPoint* 的运动与输出区域的平均运动相关联。INDEPENDENT 值允许 *refPoint* 独立于输出区域运动。AVERAGE_TRANSLATION 值将 *refPoint* 的位移设置为等于输出区域的平均平移。AVERAGE 值将 *refPoint* 的位移和旋转设置为等于输出区域的平均平移。默认值为 INDEPENDENT。

此参数仅在包含 *refPoint* 参数时有效。

*localCsys*

 `None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定用于表示向量输出的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

*projectOrientation*

一个 Boolean，指定将坐标系投影到 *surface* 上，使1轴垂直于 *surface*。投影到平面 *surface* 时，1轴垂直于表面；投影到非平面 *surface* 时，将使用最小二乘法拟合表面。默认值为 OFF。

**返回的值**

一个 IntegratedOutputSection 对象。

**异常**

无。

### 51.6.2 setValues(...)

此方法修改 IntegratedOutputSection 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [IntegratedOutputSection](pt01ch51pyo06.md#ker-integratedoutputsection-integratedoutputsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回的值**

无。

**异常**

无。

### 51.6.3 成员

IntegratedOutputSection 对象的成员与 [IntegratedOutputSection](pt01ch51pyo06.md#ker-integratedoutputsection-integratedoutputsection-pyc) 方法的参数具有相同的名称和描述。
