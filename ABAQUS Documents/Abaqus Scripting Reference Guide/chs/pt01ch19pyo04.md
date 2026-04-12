# 19.3 ContourIntegral 对象









ContourIntegral 对象定义区域上的轮廓积分对象。当前仅支持装配区域。

ContourIntegral 对象派生自 [Crack](pt01ch19pyo04.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.cracks[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.cracks[*name*]
```

### 19.3.1 ContourIntegral(...)

此方法创建 ContourIntegral 对象。尽管构造函数可用于部件和装配，但 ContourIntegral 对象目前仅在装配下支持。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.ContourIntegral
mdb.models[*name*].rootAssembly.engineeringFeatures.ContourIntegral
```

**必需参数**

*name*

一个 String，指定存储库键。

*crackFront*

一个 [RegionArray](pt01ch45pyo03.md) 对象，指定应用轮廓积分的裂缝前缘区域。如果裂缝前缘由单个区域组成，则可以指定 [Region](pt01ch45pyo03.md) 对象而不是包含单个项目的序列。

*crackTip*

一个 [RegionArray](pt01ch45pyo03.md) 对象，指定应用轮廓积分的裂缝尖端区域。如果裂缝尖端由单个区域组成，则可以指定 [Region](pt01ch45pyo03.md) 对象而不是包含单个项目的序列。

*extensionDirectionMethod*

一个 SymbolicConstant，指定虚拟裂缝扩展方向向量的定义方式。可能的值为 CRACK_NORMAL 和 Q_VECTORS。

**可选参数**

*symmetric*

一个 Boolean，指定裂缝是在关于对称平面的半模型上定义，还是在整个模型上定义。默认值为 OFF。

*listOfRegions*

一个 Boolean，指定 *crackFront* 和 *crackTip* 指定的区域是使用单个区域还是区域对象元组指定。默认值为 OFF。

*crackFrontName*

一个 String，指定从指定裂缝前缘区域的区域元组生成的裂缝前缘区域的名称。此参数仅在 *listOfRegions* 为 ON 时有效。默认值为 *name*+"Front"。

*crackTipName*

一个 String，指定从指定裂缝尖端区域的区域元组生成的裂缝尖端区域的名称。此参数仅在 *listOfRegions*=ON 时有效。默认值为 *name*+"Tip"。

*crackNormal*

一个 Float 序列的序列，指定描述裂缝正常方向的向量两个点。每个点由两个或三个坐标的元组定义其位置。此参数仅在 *extensionDirectionMethod*=CRACK_NORMAL 时是必需的。默认值为空序列。

*qVectors*

一个 Float 序列的序列的序列，指定指示裂缝扩展方向集合的向量。每个向量由两个点描述，每个点由两个或三个坐标的元组描述其位置。此参数仅在 *extensionDirectionMethod*=Q_VECTORS 时是必需的。默认值为空序列。

*midNodePosition*

一个 Float，指定沿从裂缝尖端辐射的二阶元素边缘的中点节点位置。可能的值为 0.0 ≤ *midNodeParameter* ≤ 1.0。默认值为 0.5。

*collapsedElementAtTip*

一个 SymbolicConstant，指定裂缝尖端奇异性。可能的值为 NONE、SINGLE_NODE 和 DUPLICATE_NODES。默认值为 NONE。

**返回值**

一个 ContourIntegral 对象。

**异常**

无。

### 19.3.2 setValues(...)

此方法修改 ContourIntegral 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ContourIntegral](pt01ch19pyo03.md#ker-contourintegral-contourintegral-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.3.3 成员

ContourIntegral 对象具有与 [ContourIntegral](pt01ch19pyo03.md#ker-contourintegral-contourintegral-pyc) 方法的参数相同的名称和描述的成员。

此外，ContourIntegral 对象还有以下成员：

*suppressed*

一个 Boolean，指定裂缝是否被抑制。默认值为 OFF。

### 19.3.4 对应的分析关键字

| [*CONTOUR INTEGRAL](../key/key-link.md#usb-kws-hcontintegral) |
| --- |





