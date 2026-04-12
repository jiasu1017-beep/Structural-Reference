# 23.5 writeFieldReport





此命令将场输出报告写入文件。

### 23.5.1 writeFieldReport(...)

此方法将 FieldOutput 对象写入用户定义的 ASCII 文件。

**路径**

```
session.writeFieldReport
```

**必需参数**

*filename*

一个 String，指定要写入场输出的文件名。

*append*

一个 Boolean，指定是否将场输出追加到现有文件。默认值为 ON。

*sortItem*

一个 String，指定用于对表格值排序的项目。

*odb*

一个 Odb 对象，从中获取场输出值。

*step*

一个 Int（或 stepIndex），指定要从中获取场输出值的步骤。可能的值为 0 ≤ *step* ≤ (*numSteps*  1)。

*frame*

一个 Int（或 frameIndex），指定要从中获取场输出值的帧。可能的值为 0 ≤ *frame* ≤ (*numFramesInStep*  1)。

*outputPosition*

一个 SymbolicConstant，指定获取数据的位置。可能的值为 NODAL、INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL、ELEMENT_CENTROID、WHOLE_ELEMENT、WHOLE_REGION、WHOLE_PART_INSTANCE、WHOLE_MODEL 和 GENERAL_PARTICLE。

*displayGroup*

一个 DisplayGroup 对象，指定要获取数据的模型子集。

*variable*

一个变量描述序列的序列，指定要获取数据的一个或多个场输出变量。每个变量描述序列包含以下元素：
- *element0*：一个 String，指定变量名称。
- *element1*：一个 SymbolicConstant，指定报告数据的位置。可能的值为 ELEMENT_CENTROID、ELEMENT_FACE、ELEMENT_NODAL、GENERAL_PARTICLE、INTEGRATION_POINT、NODAL、WHOLE_ELEMENT、WHOLE_MODEL、WHOLE_PART_INSTANCE 和 WHOLE_REGION。
- *element2*：一个元组序列，每个元组由一个 SymbolicConstant（指定精炼类型 COMPONENT 或 INVARIANT）和一个 String（指定要获取值的分量或不变量名称）组成。如果省略此元素，则为所有分量和不变量（如适用）写入数据。如果包含 *element3*（元组中的下一个元素），则需要此元素。
- *element3*（如适用）：一个 Dictionary，键为 String，值为 String，指定要报告数据的单个截面点。键指定模型中的一个区域；相应的值指定该区域内的截面点。例如：``` {'shell < MAT > < 7 section points >':'SPOS, (fraction = 1.0)'} ```如果省略此元素，则为所有截面点（如适用）写入数据。

**可选参数**

*numericForm*

一个 SymbolicConstant，指定显示包含复数的结果时使用的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_MAG_AT_ANGLE。初始值为 COMPLEX_MAGNITUDE。

*complexAngle*

一个 Float，指定当 *numericForm*=COMPLEX_MAG_AT_ANGLE 时显示包含复数的结果的角度（度）。初始值为 0。

**返回值**

无

**异常**

无。





