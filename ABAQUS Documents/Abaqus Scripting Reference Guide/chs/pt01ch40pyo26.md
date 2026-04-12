# 40.26 PlyStackPlotOptions 对象

PlyStackPlotOptions 对象存储与 [Viewport](pt01ch11pyo04.md) 对象关联的值和属性。PlyStackPlotOptions 对象没有构造函数命令。创建 [Viewport](pt01ch11pyo04.md) 时，Abaqus 会创建 *detailPlotOptions.plyStackPlotPlotOptions* 成员。

**访问**

```
session.viewports[*name*].detailPlotOptions.plyStackPlotOptions
```

### 40.26.1 setValues(...)

此方法修改 PlyStackPlotOptions 对象。

**必需参数**

无。

**可选参数**

*renderStyle*

 SymbolicConstant，指定视口中层的渲染方式。可选值为 WIRE_FRAME、FILLED 和 SHADED。默认值为 SHADED。

*showEdges*

 Boolean，指定是否为层绘制边缘。默认值为 OFF。

*edgeStyle*

 SymbolicConstant，指定边缘线型。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*edgeThickness*

 SymbolicConstant，指定边缘线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*plyDisplay*

 SymbolicConstant，指定以非对称楼梯形式还是对称楼梯形式显示层。可选值为 UNSYMMETRIC 和 SYMMETRIC。默认值为 UNSYMMETRIC。

*startLayer*

 Int，指定起始层。默认值为 1。

*numLayers*

 Int，指定要显示的层数。默认值为 30。

*evenNumPlyColor*

 String，指定偶数编号层的层颜色。编号基于显示的层，而非铺层中的实际层编号。默认值为 "#A2B3FF"。

*oddNumPlyColor*

 String，指定奇数编号层的层颜色。编号基于显示的层，而非铺层中的实际层编号。默认值为 "#ECC9AD"。

*showFibers*

 Boolean，指定是否显示纤维。默认值为 ON。

*fiberColor*

 String，指定纤维颜色。默认值为 "Red"。

*fiberStyle*

 SymbolicConstant，指定纤维样式。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*fiberThickness*

 SymbolicConstant，指定纤维粗细。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*fiberSpacing*

 Float，指定纤维之间的间距。默认值为 0.1。

*showReferencePlane*

 Boolean，指定是否显示参考曲面。默认值为 OFF。

*referenceSurfaceColor*

 String，指定参考曲面颜色。默认值为 "White"。

*translucency*

 Boolean，指定是否设置半透明度。默认值为 OFF。

*translucencyFactor*

 Float，指定当 *translucency*=ON 时的半透明因子。可能的值为 0.0![](../graphics/ker_eqn00013.gif) *translucencyFactor* ![](../graphics/ker_eqn00013.gif) 1.0。默认值为 0.3。

*translucencySort*

 Boolean，指定是否使用深度排序。默认值为 OFF。

*showReferenceOutline*

 Boolean，指定是否显示参考轮廓。默认值为 OFF。

*referenceOutlineColor*

 String，指定参考轮廓颜色。默认值为 "Red"。

*referenceOutlineStyle*

 SymbolicConstant，指定参考轮廓样式。可选值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*referenceOutlineThickness*

 SymbolicConstant，指定参考轮廓粗细。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*allLabelsFont*

 String，指定所有标签的字体。Windows 上的默认值为 "-*-verdana-medium-r-normal-*-*-80-*-*-p-*-*-*"，Linux 平台上为 "-*-verdana-medium-r-normal-*-*-90-*-*-p-*-*-*"。默认值为空字符串。

*showMaterialNames*

 Boolean，指定是否显示材料名称。默认值为 OFF。

*materialNamesColor*

 String，指定材料名称文字颜色。默认值为 "Green"。

*showOrientationNames*

 Boolean，指定是否显示取向名称或纤维角度。默认值为 OFF。

*orientationNamesColor*

 String，指定取向名称纤维角度文字颜色。默认值为 "Orange"。

*showStateBlock*

 Boolean，指定是否显示状态块。默认值为 ON。

*stateBlockColor*

 String，指定状态块文字颜色。默认值为 "White"。

*showPlyNames*

 Boolean，指定是否显示层名称。默认值为 ON。

*plyNamesColor*

 String，指定层名称文字颜色。默认值为 "Yellow"。

*showThicknessLabels*

 Boolean，指定是否显示厚度标签。默认值为 ON。

*thicknessLabelsColor*

 String，指定厚度标签文字颜色。默认值为 "Red"。

*showIntPoints*

 Boolean，指定是否显示厚度积分点。默认值为 OFF。

*intPointsColor*

 String，指定厚度积分点颜色。默认值为 "Blue"。

*sizeX*

 Float，指定层在 X 方向的大小。默认值为 1.5。

*sizeY*

 Float，指定层在 Y 方向的大小。默认值为 1.0。

*sizeZ*

 Float，指定层在 Z 方向的大小。默认值为 0.8。

**返回值**

无

**异常**

无。

### 40.26.2 成员

PlyStackPlotOptions 对象的成员与 [setValues](pt01ch40pyo26.md#ker-plystackplotoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

