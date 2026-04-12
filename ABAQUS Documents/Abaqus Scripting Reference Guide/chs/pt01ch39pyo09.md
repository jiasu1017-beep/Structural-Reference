# 39.9 Stream 对象

Stream 对象在流体力学中定义一组流线。

**访问**

```
import visualization
session.streams[*name*]
```

### 39.9.1 Stream(...)

此方法创建 Stream 对象并将其放入 streams 存储库。

**Path**

```
session.Stream
```

**必需参数**

*name*

字符串，指定流的名称。

*numPointsOnRake*

整数，指定沿耙的点数。

**可选参数**

*pointA*

 3 个 float 的元组，指定耙的起点。或者，字符串，表示视口中选择的节点。

*pointB*

 3 个 float 的元组，指定耙的终点。或者，字符串，表示视口中选择的节点。

*path*

 [Path](pt01ch39pyo01.md) 对象，指定耙。

**返回值**

Stream 对象。

**异常**

无。

### 39.9.2 成员

Stream 对象没有成员。

