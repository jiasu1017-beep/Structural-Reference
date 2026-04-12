# 17.12 LightOptions 对象









LightOptions 对象存储控制当 *renderStyle* 设置为 SHADED 时如何照亮对象的设置。LightOptions 对象通过以下两种方式之一访问：
- 默认灯光选项。这些设置在您启动会话时使用，也由"灯光选项"对话框上的"默认"按钮使用。
- 与特定视口关联的灯光选项。

LightOptions 对象没有构造函数；Abaqus 在启动会话时创建 *defaultLightOptions* 成员。创建新视口时，*lightOptions* 成员从当前视口复制。

**访问**

```
session.defaultLightOptions
session.viewports[*name*].lightOptions
```

### 17.12.1 setValues(...)

此方法修改 LightOptions 对象。

**必需参数**

无。

**可选参数**

*shading*

一个 SymbolicConstant，指定当 *renderStyle*=SHADED 时用于填充几何体面片的着色技术。网格几何体的面片着色不受此设置影响。可能的值为：
- GOURAUD，指定为面的每个角计算照明值，并插值以填充面的其余部分。
- PHONG，指定为面的每个像素计算照明值。

默认值为 GOURAUD。

当设置为 *shading*=GOURAUD 时，为面的每个角计算照明值，并从角值插值面的其余部分的照明。当 *shading*=PHONG 时，为面的每个像素计算照明值。

**注意：**仅当 [GraphicsOptions](pt01ch17pyo09.md) 的 *shadersAvailable* 成员为 True 时，才能将着色技术设置为 PHONG。

仅当输出格式为光栅且 [GraphicsOptions](pt01ch17pyo09.md) 的 *accelerateOffScreen* 成员为 ON 时，打印输出才包含 Phong 着色。

*renderStyle* 设置是 [AssemblyDisplayOptions](pt01ch17pyo01.md)、[PartDisplayOptions](pt01ch17pyo16.md) 和其他选项对象的一部分，此处未列出，因为它们通常用于网格几何体。

*viewpoint*

一个 SymbolicConstant，指定如何计算镜面高光。可能的值为：
- INFINITE，指定在计算镜面高光时使用从相机到顶点的恒定向量。
- LOCAL，指定在计算镜面高光时计算从相机到每个顶点的向量。

默认值为 INFINITE。

当设置为 *viewpoint*=INFINITE 时，在计算镜面高光时使用从相机（视点）到顶点的恒定向量。当 *viewpoint*=LOCAL 时，结果更真实，因为会计算从相机到每个顶点的实际向量。整体性能会下降。

*ambientColor*

一个 String，指定均匀应用于整个场景的光，不依赖于任何单独的光。初始值为 20% 灰色。有效颜色字符串列表在 *session* 对象的 *colors* 映射中。

*materialShininess*

一个 Float，指定镜面反射的聚焦程度。*materialShininess* 参数越高，镜面高光越集中。可能的值为 0.0 ≤ *polygonOffsetConstant* ≤ 128.0。默认值为 105.0。

**返回值**

无

**异常**

RangeError。

### 17.12.2 成员

LightOptions 对象具有以下成员：

*shading*

一个 SymbolicConstant，指定当 *renderStyle*=SHADED 时用于填充几何体面片的着色技术。网格几何体的面片着色不受此设置影响。可能的值为：
- GOURAUD，指定为面的每个角计算照明值，并插值以填充面的其余部分。
- PHONG，指定为面的每个像素计算照明值。

默认值为 GOURAUD。

当设置为 *shading*=GOURAUD 时，为面的每个角计算照明值，并从角值插值面的其余部分的照明。当 *shading*=PHONG 时，为面的每个像素计算照明值。

**注意：**仅当 [GraphicsOptions](pt01ch17pyo09.md) 的 *shadersAvailable* 成员为 True 时，才能将着色技术设置为 PHONG。

仅当输出格式为光栅且 [GraphicsOptions](pt01ch17pyo09.md) 的 *accelerateOffScreen* 成员为 ON 时，打印输出才包含 Phong 着色。

*renderStyle* 设置是 [AssemblyDisplayOptions](pt01ch17pyo01.md)、[PartDisplayOptions](pt01ch17pyo16.md) 和其他选项对象的一部分，此处未列出，因为它们通常用于网格几何体。

*viewpoint*

一个 SymbolicConstant，指定如何计算镜面高光。可能的值为：
- INFINITE，指定在计算镜面高光时使用从相机到顶点的恒定向量。
- LOCAL，指定在计算镜面高光时计算从相机到每个顶点的向量。

默认值为 INFINITE。

当设置为 *viewpoint*=INFINITE 时，在计算镜面高光时使用从相机（视点）到顶点的恒定向量。当 *viewpoint*=LOCAL 时，结果更真实，因为会计算从相机到每个顶点的实际向量。整体性能会下降。

*materialShininess*

一个 Float，指定镜面反射的聚焦程度。*materialShininess* 参数越高，镜面高光越集中。可能的值为 0.0 ≤ *polygonOffsetConstant* ≤ 128.0。默认值为 105.0。

*lights*

长度为 8 的 [LightArray](pt01ch17pyo11.md) 对象。

*ambientColor*

一个 String，指定均匀应用于整个场景的光，不依赖于任何单独的光。初始值为 20% 灰色。有效颜色字符串列表在 *session* 对象的 *colors* 映射中。





