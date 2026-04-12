# 36.20 ShapeTask 对象

ShapeTask 对象定义形状任务。

ShapeTask 对象派生自 [OptimizationTask](pt01ch36pyo01.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*]
```

### 36.20.1 ShapeTask(...)

此方法创建 ShapeTask 对象。

**路径**

```
mdb.models[*name*].ShapeTask
```

**必要参数**

*name*

一个字符串，指定优化任务仓库键。

**可选参数**

*absoluteStepSizeControl*

一个 SymbolicConstant，指定是通过平均优化位移还是最小优化位移来控制允许的绝对步长。可能的值为 MINIMUM 和 AVERAGE。默认值为 MINIMUM。

*constrainedLaplacianConvergenceLevel*

一个 SymbolicConstant，指定约束拉普拉斯收敛级别。可能的值为 NORMAL、CONSERVATIVE 和 AGGRESSIVE。默认值为 NORMAL。

*curvatureSmoothingEdgeLength*

一个 Float，指定移动向量的边长。默认值为 5.0。

*equalityConstraintTolerance*

一个 Float，指定等式约束公差。默认值为 10–3。

*featureRecognitionAngle*

一个 Float，指定用于边缘和角落的网格平滑特征识别角度。默认值为 30.0。

*filterExponent*

一个 Float，指定取决于半径的权重，当指定了 *filterMaxRadius* 时使用。默认值为 1.0。

*filterMaxRadius*

`None` 或一个 Float，指定等效应力的最大影响半径。默认值为 `None`。

*filterRadiusReduction*

`None` 或一个 Float，指定取决于表面弯曲的半径减少，当指定了 *filterMaxRadius* 时使用。默认值为 `None`。

*firstCycleDeletedVolumeTechnique*

一个 SymbolicConstant，指定在第一个设计循环中可立即删除的体积的指定方法。可能的值为 OFF、PERCENTAGE 和 ABSOLUTE。默认值为 OFF。

*freezeBoundaryConditionRegions*

一个布尔值，指定是否将具有边界条件的单元排除在优化之外。默认值为 OFF。

*frozenBoundaryConditionRegion*

SymbolicConstant MODEL 或 [Region](pt01ch45pyo03.md) 对象，指定冻结边界条件区域的区域，或 SymbolicConstant MODEL，与 *freezeBoundaryConditionRegions* 一起使用。默认值为 MODEL。

*geometricRestrictionEvaluationFrequency*

一个 SymbolicConstant，指定在网格平滑期间评估几何约束的频率。可能的值为 LOW、MEDIUM 和 HIGH。默认值为 LOW。

*growthScaleFactor*

一个 Float，指定对具有生长的节点的优化位移应用的缩放因子。默认值为 1.0。

*haltUponViolation*

一个布尔值，指定当质量标准不满足时是否停止优化。默认值为 OFF。

*layerReferenceRegion*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定当 *meshSmoothingRegionMethod* 为 TASK_REGION_LAYERS 时用于指定网格平滑的第一个节点层的区域。默认值为 `None`。

*meshSmoothingRegionMethod*

一个 SymbolicConstant，指定用于确定网格平滑区域的方法。REGION 值使用 *smoothingRegion*。NUMBER_OF_LAYERS 值使用 *layerReferenceRegion*。TASK_REGION_LAYERS 值将使用任务区域平滑六层。可能的值为 TASK_REGION_LAYERS、REGION 和 NUMBER_OF_LAYERS。默认值为 TASK_REGION_LAYERS。

*meshSmoothingStrategy*

一个 SymbolicConstant，指定网格平滑策略方法。可能的值为 CONSTRAINED_LAPLACIAN 和 LOCAL_GRADIENT。默认值为 CONSTRAINED_LAPLACIAN。

*midsideInterpolation*

一个 SymbolicConstant，指定在优化期间处理中节点位置的方法。POSITIONS 表示中节点位置按位置线性插值。OPTIMIZATION_DISPLACEMENT 表示它们按角节点优化位移插值。可能的值为 POSITIONS 和 OPTIMIZATION_DISPLACEMENT。默认值为 POSITIONS。

*numFreeNodeLayers*

SymbolicConstant FIX_NONE 或 Int，指定与任务区域相邻的在网格平滑期间保持自由的节点层数。值为 0 表示没有层是自由的，所有层都是固定的。默认值为 0。

*numSmoothedElementLayers*

`None` 或 Int，当 *meshSmoothingRegionMethod* 为 NUMBER_OF_LAYERS 时指定网格平滑的层数。默认值为 `None`。

*presumeFeasibleBCRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略自动冻结的边界条件区域。此参数与 *freezeBoundaryConditionRegions* 一起使用。默认值为 ON。

*quadMaxAngle*

一个 Float，指定网格平滑期间四边形单元的最大角度。默认值为 160.0。

*quadMinAngle*

一个 Float，指定网格平滑期间四边形单元的最小角度。默认值为 20.0。

*quadSkew*

一个 Float，指定网格平滑期间四边形单元的偏斜角度，与 *reportQualityViolation* 一起使用。默认值为 30.0。

*quadTaper*

一个 Float，指定网格平滑期间四边形单元的锥度，与 *reportQualityViolation* 一起使用。默认值为 0.5。

*region*

SymbolicConstant MODEL 或 [Region](pt01ch45pyo03.md) 对象，指定应用优化任务的区域。默认值为 MODEL。

*reportPoorQualityElements*

一个布尔值，指定在网格平滑期间是否报告劣质单元。默认值为 OFF。

*reportQualityViolation*

一个布尔值，指定在网格平滑期间是否报告质量标准违反。默认值为 OFF。

*shrinkScaleFactor*

一个 Float，指定对具有收缩的节点的优化位移应用的缩放因子。默认值为 1.0。

*smoothingRegion*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定网格平滑区域，当 *meshSmoothingRegionMethod* 为 REGION 时使用。默认值为 `None`。

*targetMeshQuality*

一个 SymbolicConstant，指定网格平滑的目标网格质量。可能的值为 NONE、LOW、MEDIUM 和 HIGH。默认值为 LOW。

*tetAspectRatio*

一个 Float，指定网格平滑期间四面体单元的纵横比。默认值为 100.0。

*tetMaxAspect*

一个 Float，指定网格平滑期间最大四面体单元纵横比。默认值为 8.0。

*tetMinAspect*

一个 Float，指定网格平滑期间最小四面体单元纵横比。默认值为 0.222。

*tetSkew*

一个 Float，指定网格平滑期间四面体单元的偏斜值。默认值为 100.0。

*triMaxAngle*

一个 Float，指定网格平滑期间三角形单元的最大角度。默认值为 140.0。

*triMinAngle*

一个 Float，指定网格平滑期间三角形单元的最大角度。默认值为 20.0。

*updateShapeBasisVectors*

一个 SymbolicConstant，指定是在第一个设计循环还是每个设计循环更新形状基向量。可能的值为 EVERY_CYCLE 和 FIRST_CYCLE。默认值为 LOW。

**返回值**

ShapeTask 对象。

**异常**

无。

### 36.20.2 setValues(...)

此方法修改 ShapeTask 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [ShapeTask](pt01ch36pyo20.md#ker-shapetask-shapetask-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.20.3 成员

ShapeTask 对象具有与 [ShapeTask](pt01ch36pyo20.md#ker-shapetask-shapetask-pyc) 方法的参数名称和描述相同的成员。

此外，ShapeTask 对象可以具有以下成员：

*designResponses*

[DesignResponse](pt01ch36pyo04.md) 对象的仓库。

*objectiveFunctions*

[ObjectiveFunction](pt01ch36pyo11.md) 对象的仓库。

*optimizationConstraints*

[OptimizationConstraint](pt01ch36pyo12.md) 对象的仓库。

*geometricRestrictions*

[GeometricRestriction](pt01ch36pyo08.md) 对象的仓库。

*stopConditions*

[StopCondition](pt01ch36pyo34.md) 对象的仓库。
