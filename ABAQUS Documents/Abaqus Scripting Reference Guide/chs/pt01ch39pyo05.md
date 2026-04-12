# 39.5 ProbeOptions 对象

ProbeOptions 对象用于存储与探测模型或 *X–Y* 图表相关的设置。ProbeOptions 对象没有构造函数。导入 Visualization 模块时，Abaqus 会创建 *defaultProbeOptions* 和 *probeOptions* 成员。首次启动探测时，*probeOptions* 成员的值使用 *defaultProbeOptions* 成员的值进行初始化。

**访问**

```
import visualization
session.defaultProbeOptions
session.probeOptions
```

### 39.5.1 setValues(...)

此方法修改 ProbeOptions 对象。

**必需参数**

无。

**可选参数**

*options*

 ProbeOptions 对象，指定要复制的值。如果还有其他参数提供给 `setValues`，它们将覆盖 *options* 中的值。默认值为 `None`。

*probeEntity*

 SymbolicConstant，指定当 *probeObject*="ODB" 时被探测的实体。可选值为 NODE 和 ELEMENT。默认值为 ELEMENT。

*probeOutputPosition*

 SymbolicConstant，指定探测场输出结果时的输出位置，当 *probeObject*="ODB" 时有效。可选值为 NODAL、INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL 和 ELEMENT_CENTROID。

当 *probeEntity*=NODE 时，唯一可能的值是 NODAL。当 *probeEntity*=ELEMENT 时，可选值为 INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL 和 ELEMENT_CENTROID，默认值为 INTEGRATION_POINT。

*partInstance*

 Boolean，指定是否显示零件实例信息。当 *probeObject*="ODB" 时此成员有效。默认值为 ON。

*elementID*

 Boolean，指定是否显示单元 ID 信息。当 *probeObject*="ODB" 且 *probeEntity*=ELEMENT 时此成员有效。默认值为 ON。

*elementType*

 Boolean，指定是否显示单元类型信息。当 *probeObject*="ODB" 且 *probeEntity*=ELEMENT 时此成员有效。默认值为 ON。

*elementConnectivity*

 Boolean，指定是否显示单元连通性。当 *probeObject*="ODB" 且 *probeEntity*=ELEMENT 时此成员有效。默认值为 ON。

*elementFieldResults*

 Boolean，指定是否显示单元场输出结果。当 *probeObject*="ODB"、*probeEntity*=ELEMENT 且 *isFieldOutputAvailable*=ON 时此成员有效。默认值为 ON。

*nodeId*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示节点 ID。默认值为 ON。

*baseCoordinates*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示节点的基本坐标。默认值为 ON。

*deformedCoordinates*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示节点的变形坐标。默认值为 ON。

*attachedElements*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示连接到节点的单元。默认值为 ON。

*nodeFieldResults*

 Boolean，指定当 *probeObject*="ODB"、*probeEntity*=NODE 且 *isFieldOutputAvailable*=ON 时是否显示节点场输出结果。默认值为 ON。

*legend*

 Boolean，指定是否显示被探测曲线的图例。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*xValue*

 Boolean，指定是否显示被探测曲线上该点的 *x* 坐标值。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*yValue*

 Boolean，指定是否显示被探测曲线上该点的 *y* 坐标值。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*sequenceID*

 Boolean，指定是否显示被探测曲线上该点的序列 ID。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*interpolateXy*

 Boolean，指定当 *probeObject*="XYPlot" 时是否在线段内插值。当 *interpolateXy*=OFF 时，探测返回曲线上最近的 *X–Y* 数据点。当 *interpolateXy*=ON 时，探测进行插值以返回曲线上最近点的值。默认值为 OFF。

**返回值**

无

**异常**

无。

### 39.5.2 成员

ProbeOptions 对象具有以下成员：

*probeEntity*

 SymbolicConstant，指定当 *probeObject*="ODB" 时被探测的实体。可选值为 NODE 和 ELEMENT。默认值为 ELEMENT。

*probeOutputPosition*

 SymbolicConstant，指定探测场输出结果时的输出位置，当 *probeObject*="ODB" 时有效。可选值为 NODAL、INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL 和 ELEMENT_CENTROID。

当 *probeEntity*=NODE 时，唯一可能的值是 NODAL。当 *probeEntity*=ELEMENT 时，可选值为 INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL 和 ELEMENT_CENTROID，默认值为 INTEGRATION_POINT。

*partInstance*

 Boolean，指定是否显示零件实例信息。当 *probeObject*="ODB" 时此成员有效。默认值为 ON。

*elementID*

 Boolean，指定是否显示单元 ID 信息。当 *probeObject*="ODB" 且 *probeEntity*=ELEMENT 时此成员有效。默认值为 ON。

*elementType*

 Boolean，指定是否显示单元类型信息。当 *probeObject*="ODB" 且 *probeEntity*=ELEMENT 时此成员有效。默认值为 ON。

*elementConnectivity*

 Boolean，指定是否显示单元连通性。当 *probeObject*="ODB" 且 *probeEntity*=ELEMENT 时此成员有效。默认值为 ON。

*elementFieldResults*

 Boolean，指定是否显示单元场输出结果。当 *probeObject*="ODB"、*probeEntity*=ELEMENT 且 *isFieldOutputAvailable*=ON 时此成员有效。默认值为 ON。

*nodeId*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示节点 ID。默认值为 ON。

*baseCoordinates*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示节点的基本坐标。默认值为 ON。

*deformedCoordinates*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示节点的变形坐标。默认值为 ON。

*attachedElements*

 Boolean，指定当 *probeObject*="ODB" 且 *probeEntity*=NODE 时是否显示连接到节点的单元。默认值为 ON。

*nodeFieldResults*

 Boolean，指定当 *probeObject*="ODB"、*probeEntity*=NODE 且 *isFieldOutputAvailable*=ON 时是否显示节点场输出结果。默认值为 ON。

*legend*

 Boolean，指定是否显示被探测曲线的图例。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*xValue*

 Boolean，指定是否显示被探测曲线上该点的 *x* 坐标值。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*yValue*

 Boolean，指定是否显示被探测曲线上该点的 *y* 坐标值。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*sequenceID*

 Boolean，指定是否显示被探测曲线上该点的序列 ID。当 *probeObject*="XYPlot" 时此成员有效。默认值为 ON。

*interpolateXy*

 Boolean，指定当 *probeObject*="XYPlot" 时是否在线段内插值。当 *interpolateXy*=OFF 时，探测返回曲线上最近的 *X–Y* 数据点。当 *interpolateXy*=ON 时，探测进行插值以返回曲线上最近点的值。默认值为 OFF。

*isFieldOutputAvailable*

 Boolean，指定当 *probeObject*="XYPlot" 时场输出是否可用于探测。此成员为只读。

*probeObject*

 String，指定被探测显示对象的类型。可选值为 "ODB" 和 "XYPlot"。此成员为只读。

