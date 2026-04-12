# 17.7 GeometricRestrictionDisplayOptions 对象









GeometricRestrictionDisplayOptions 对象存储指定如何在特定视口中显示装配的设置，当

```
session.viewports[*name*].assemblyDisplay.geometricRestrictions=ON
```

GeometricRestrictionDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].assemblyDisplay.geometricRestrictionOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.geometricRestrictionOptions
```

### 17.7.1 setValues(...)

此方法修改 GeometricRestrictionDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*drillControl*

一个 Boolean，指定是否显示钻孔控制几何约束符号。默认值为 ON。

*fixedRegion*

一个 Boolean，指定是否显示固定区域几何约束符号。默认值为 ON。

*frozenArea*

一个 Boolean，指定是否显示冻结区域几何约束符号。默认值为 ON。

*growth*

一个 Boolean，指定是否显示生长几何约束符号。默认值为 ON。

*penetrationCheck*

一个 Boolean，指定是否显示穿透检查几何约束符号。默认值为 ON。

*shapeDemoldControl*

一个 Boolean，指定是否显示脱模控制（形状）几何约束符号。默认值为 ON。

*designDirection*

一个 Boolean，指定是否显示设计方向几何约束符号。默认值为 ON。

*shapeMemberSize*

一个 Boolean，指定是否显示成员尺寸（形状）几何约束符号。默认值为 ON。

*shapePlanarSymmetry*

一个 Boolean，指定是否显示平面对称（形状）几何约束符号。默认值为 ON。

*shapePointSymmetry*

一个 Boolean，指定是否显示点对称（形状）几何约束符号。默认值为 ON。

*shapeRotationalSymmetry*

一个 Boolean，指定是否显示旋转对称（形状）几何约束符号。默认值为 ON。

*stampControl*

一个 Boolean，指定是否显示冲压控制几何约束符号。默认值为 ON。

*slideRegionControl*

一个 Boolean，指定是否显示滑动区域控制几何约束符号。默认值为 ON。

*topologyCyclicSymmetry*

一个 Boolean，指定是否显示循环对称几何约束符号。默认值为 ON。

*topologyDemoldControl*

一个 Boolean，指定是否显示脱模控制（拓扑）几何约束符号。默认值为 ON。

*topologyMemberSize*

一个 Boolean，指定是否显示成员尺寸（拓扑）几何约束符号。默认值为 ON。

*topologyPlanarSymmetry*

一个 Boolean，指定是否显示平面对称（拓扑）几何约束符号。默认值为 ON。

*topologyPointSymmetry*

一个 Boolean，指定是否显示点对称（拓扑）几何约束符号。默认值为 ON。

*topologyRotationalSymmetry*

一个 Boolean，指定是否显示旋转对称（拓扑）几何约束符号。默认值为 ON。

*turnControl*

一个 Boolean，指定是否显示车削控制几何约束符号。默认值为 ON。

**返回值**

无

**异常**

RangeError。

### 17.7.2 成员

GeometricRestrictionDisplayOptions 对象的成员与 [setValues](pt01ch17pyo07.md#ker-geometricrestrictiondisplayoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。





