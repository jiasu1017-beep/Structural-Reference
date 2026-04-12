# 17.11 Light 对象









Light 对象存储控制当 *renderStyle* 设置为 SHADED 时如何照亮对象的设置。

Light 对象没有构造函数；Abaqus 在启动会话时将它们作为 *defaultLightOptions* 和 *lightOptions* 对象的一部分创建。

**访问**

```
session.defaultLightOptions.lights[*i*]
session.viewports[*name*].lightOptions.lights[*i*]
```

### 17.11.1 setValues(...)

此方法修改 Light 对象。

**必需参数**

无。

**可选参数**

*enabled*

一个 Boolean，指定灯是打开还是关闭。默认值为 OFF。

*type*

一个 SymbolicConstant，指定如何计算灯的效果。可能的值为：
- DIRECTIONAL，指定用于从灯到顶点方向的恒定向量的方向。
- POINT，指定将为每个顶点计算从灯到顶点的向量。

默认值为 DIRECTIONAL。

当设置为 *type*=DIRECTIONAL 时，使用从灯到顶点的恒定向量。当 *type*=POINT 时，结果更真实，因为会计算每个顶点从灯到顶点的实际向量。整体性能会下降。

*latitude*

一个 Float，指定灯高于或低于相机的 altitude。可能的值为 -90.0 ≤ *latitude* ≤ 90.0。默认值为 0.0。

*longitude*

一个 Float，指定灯相对于相机的东西位置。可能的值为 -90.0 ≤ *longitude* ≤ 90.0。默认值为 0.0。

*diffuseColor*

一个 String，指定此光源添加到场景的颜色。初始值为 70% 灰色。有效颜色字符串列表在 *session* 对象的 *colors* 映射中。

*specularColor*

一个 String，指定此光源创建的镜面高光的颜色。初始值为 36% 灰色。有效颜色字符串列表在 *session* 对象的 *colors* 映射中。

**返回值**

无

**异常**

RangeError。

### 17.11.2 成员

Light 对象的成员与 [setValues](pt01ch17pyo11.md#ker-light-setvalues-pyc) 方法的参数具有相同的名称和描述。





