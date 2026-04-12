# 25.51 Model 对象

以下命令对 Model 对象进行操作。有关 Model 对象的更多信息，请参阅"Model 对象，"第 33.1 节。

**访问**

```
import interaction
```

### 25.51.1 contactDetection(...)

此方法使用接触检测来创建 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md)、[SurfaceToSurfaceContactExp](pt01ch25pyo74.md) 和 [Tie](pt01ch13pyo10.md) 对象。

**必需参数**

无。

**可选参数**

*name*

字符串，指定用于生成存储库键的前缀。默认值为 "CP-"。

*createStepName*

字符串，指定创建 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md)、[SurfaceToSurfaceContactExp](pt01ch25pyo74.md) 和 [Tie](pt01ch13pyo10.md) 对象的步骤名称。默认值为 "Initial"。

*searchDomain*

 SymbolicConstant MODEL 或字符串序列，指定要搜索的实例名称。MODEL 表示搜索整个模型。默认值为 MODEL。

*defaultType*

 SymbolicConstant，指定要创建的对象的默认类型。可能的值为 CONTACT、CONTACT_STANDARD、CONTACT_EXPLICIT 和 TIE。如果使用 CONTACT，则行为由模型中的 [Step](pt01ch49pyo01.md) 类型决定。如果存在 [ExplicitDynamicsStep](pt01ch49pyo11.md) 或 [TempDisplacementDynamicsStep](pt01ch49pyo31.md)，则默认创建 [SurfaceToSurfaceContactExp](pt01ch25pyo74.md)。否则默认创建 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md)。默认值为 CONTACT。

*interactionProperty*

字符串，指定与任何创建的交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

*separationTolerance*

浮点数，指定考虑两个表面为接触候选的最大分离值，其中分离是两个表面上最近点方法之间的最大距离。默认值为模型的函数。

*extendByAngle*

 `None` 或浮点数，指定用于扩展表面定义以包含相邻面的角度。默认值为 20。

*mergeWithinAngle*

 `None` 或浮点数，指定用于合并位于该角度内的相邻接触对的的角度。默认值为 20。

*searchSingleInstances*

布尔值，指定是否包含单个实例内的表面对。默认值为 OFF。

*nameEachSurfaceFound*

布尔值，指定是否为找到的每个表面分配名称。默认值为 ON。

*createUnionOfMasterSurfaces*

布尔值，指定是否创建找到的所有主表面的并集表面。默认值为 OFF。

*createUnionOfSlaveSurfaces*

布尔值，指定是否创建找到的所有从属表面的并集表面。默认值为 OFF。

*createUnionOfMasterSlaveSurfaces*

布尔值，指定是否创建找到的所有主表面和从属表面的并集表面。默认值为 OFF。

*includePlanar*

布尔值，指定是否包含平面几何。默认值为 ON。

*includeCylindricalSphericalToric*

布尔值，指定是否包含圆柱、球面和圆环几何。默认值为 ON。

*includeSplineBased*

布尔值，指定是否包含样条基几何。默认值为 ON。

*includeMeshSolid*

布尔值，指定是否包含实体网格实体。默认值为 ON。

*includeMeshShell*

布尔值，指定是否包含壳网格实体。默认值为 ON。

*includeMeshMembrane*

布尔值，指定是否包含网格膜实体。默认值为 OFF。

*includeOverclosed*

布尔值，指定是否包含过度闭合的对。默认值为 ON。

*includeNonOverlapping*

布尔值，指定是否包含不重叠的相对几何表面。默认值为 OFF。

*meshedGeometrySearchTechnique*

 SymbolicConstant USE_GEOMETRY 或 USE_MESH，指定是使用几何实体还是网格实体来定位网格