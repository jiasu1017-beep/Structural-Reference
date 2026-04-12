# 39.3 FreeBody 对象

FreeBody 对象定义计算合力和力矩的截面。

**访问**

```
import visualization
session.freeBodies[*name*]
```

### 39.3.1 FreeBodyFromEdges(...)

此方法创建 FreeBody 对象并将其放入 freeBodies 存储库。

**Path**

```
session.FreeBodyFromEdges
```

**必需参数**

*name*

字符串，指定自由体的名称。

*edges*

 [DisplayGroup](pt01ch16pyo01.md) 叶子对象，指定自由体的物理组成。

**可选参数**

*summationLoc*

 SymbolicConstant，指定求和点的位置。可选值为 CENTROID、NODAL_AVERAGE 和 SPECIFY。默认值为 CENTROID。

*summationPoint*

 3 个 float 的元组，指定求和点。

*componentResolution*

 SymbolicConstant，指定分量分辨率。可选值为 NORMAL_TANGENTIAL 和 CSYS。默认值为 NORMAL_TANGENTIAL。

*csysName*

字符串，指定坐标系的名称。

**返回值**

FreeBody 对象。

**异常**

无。

### 39.3.2 FreeBodyFromFaces(...)

此方法创建 FreeBody 对象并将其放入 freeBodies 存储库。

**Path**

```
session.FreeBodyFromFaces
```

**必需参数**

*name*

字符串，指定自由体的名称。

*faces*

 [DisplayGroup](pt01ch16pyo01.md) 叶子对象，指定自由体的物理组成。

**可选参数**

*summationLoc*

 SymbolicConstant，指定求和点的位置。可选值为 CENTROID、NODAL_AVERAGE 和 SPECIFY。默认值为 CENTROID。

*summationPoint*

 3 个 float 的元组，指定求和点。

*componentResolution*

 SymbolicConstant，指定分量分辨率。可选值为 NORMAL_TANGENTIAL 和 CSYS。默认值为 NORMAL_TANGENTIAL。

*csysName*

字符串，指定坐标系的名称。

**返回值**

FreeBody 对象。

**异常**

无。

### 39.3.3 FreeBodyFromNodesElements(...)

此方法创建 FreeBody 对象并将其放入 freeBodies 存储库。

**Path**

```
session.FreeBodyFromNodesElements
```

**必需参数**

*name*

字符串，指定自由体的名称。

*elements*

 [DisplayGroup](pt01ch16pyo01.md) 叶子对象，指定自由体的物理组成。

*nodes*

 [DisplayGroup](pt01ch16pyo01.md) 叶子对象，指定自由体的物理组成。

**可选参数**

*summationLoc*

 SymbolicConstant，指定求和点的位置。可选值为 CENTROID、NODAL_AVERAGE 和 SPECIFY。默认值为 CENTROID。

*summationPoint*

 3 个 float 的元组，指定求和点。

*componentResolution*

 SymbolicConstant，指定分量分辨率。可选值为 NORMAL_TANGENTIAL 和 CSYS。默认值为 NORMAL_TANGENTIAL。

*csysName*

字符串，指定坐标系的名称。

**返回值**

FreeBody 对象。

**异常**

无。

### 39.3.4 成员

FreeBody 对象没有成员。

