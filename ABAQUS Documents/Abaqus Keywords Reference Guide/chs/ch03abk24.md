# *COHESIVE SECTION






### *COHESIVE SECTION为粘聚单元指定单元属性。

此选项用于定义粘聚单元的属性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["粘聚单元：概述，" Abaqus 分析用户指南第 32.5.1 节](../usb/usb-link.md#usb-elm-ecohesiveoverview)
- ["使用连续体方法定义粘聚单元的本构响应，" Abaqus 分析用户指南第 32.5.5 节](../usb/usb-link.md#usb-elm-ecohesivematbehavior)

### **必需参数：**

ELSET

将此参数设置为包含正在为其定义粘聚属性的单元的单元集名称。

MATERIAL

将此参数设置为要与此单元一起使用的材料名称。

RESPONSE

此参数指定定义粘聚单元本构行为的几何假设。

如果响应直接以牵引和分离来定义，则设置 RESPONSE=TRACTION SEPARATION。

设置 RESPONSE=CONTINUUM 以指定粘聚单元对包含一个直接（开口应变）和两个横向剪切分量的应变状态进行建模。

设置 RESPONSE=GASKET 以指定粘聚单元中的应力状态为单轴。

当 RESPONSE=CONTINUUM 或 GASKET 时，单元的本构行为必须使用 Abaqus 中任何可用的材料模型以连续体材料属性来定义（受限于某些模型不适用于一维应力状态）。

### **可选参数：**

CONTROLS

将此参数设置为 [*SECTION CONTROLS](ch18abk01.md) 定义的名称（请参阅 ["截面控制，" Abaqus 分析用户指南第 27.1.4 节](../usb/usb-link.md#usb-elm-esectioncontrol)）。[*SECTION CONTROLS](ch18abk01.md) 选项可用于指定粘聚单元完全失效后是否应将其删除。此选项还可用于指定标量退化（损伤）参数 *D* 的最大值和/或粘性正则化的粘性系数，![](../graphics/key_eqn00195.gif)。

ORIENTATION

将此参数设置为 [*ORIENTATION](ch15abk01.md) 选项的名称（["方向，" Abaqus 分析用户指南第 2.2.5 节](../usb/usb-link.md#usb-int-corientation)），用于为指定单元集中的粘聚单元定义积分点计算的局部坐标系。

STACK DIRECTION

将此参数设置为 1、2、3 或 ORIENTATION，以定义粘聚单元的堆叠方向或厚度方向。指定一个数值选项以选择相应的等参方向作为堆叠或厚度方向。对于三维粘聚单元，默认值为 STACK DIRECTION=3；对于二维和轴对称单元，默认值为 STACK DIRECTION=2。

如果 STACK DIRECTION=ORIENTATION，则还需要 ORIENTATION 参数。

要获得所需的厚度方向，STACK DIRECTION 参数的正确数值取决于单元连接性。对于与网格无关的规范，请使用 STACK DIRECTION=ORIENTATION。

此参数不能与孔隙压力粘聚单元一起使用。

THICKNESS

如果粘聚层的初始本构厚度由单元的节点坐标确定，则设置 THICKNESS=GEOMETRY。

设置 THICKNESS=SPECIFIED 以在下方数据行上指定层的初始本构厚度。如果表示初始本构厚度的数据字段留空或设置为零，则假定厚度为 1。

此参数的默认值取决于 RESPONSE 参数的选择。如果 RESPONSE=TRACTION SEPARATION，默认值为 THICKNESS=SPECIFIED。如果 RESPONSE=CONTINUUM，默认值为 THICKNESS=GEOMETRY。如果 RESPONSE=GASKET，则没有默认值；必须明确指定 THICKNESS 参数。

### **用于定义粘聚单元属性的数据行：**

**第一行（也是唯一行）：**




