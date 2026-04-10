# *CONTACT PAIR






### *CONTACT PAIR定义相互接触的表面。

此选项用于定义在分析过程中可能相互接触或相互作用的表面对或节点集与表面对。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的历史数据  

**级别：**Abaqus/Standard 中的模型；Abaqus/Explicit 中的步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["在 Abaqus/Standard 中定义接触对，" Abaqus 分析用户指南第 36.3.1 节](../usb/usb-link.md#usb-cni-acontactpair)
- ["调整 Abaqus/Standard 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.3.5 节](../usb/usb-link.md#usb-cni-aadjustsurfaces)
- ["在 Abaqus/Standard 中定义绑定接触，" Abaqus 分析用户指南第 36.3.7 节](../usb/usb-link.md#usb-cni-atiedcontact)
- ["在 Abaqus/Standard 中调整接触控制，" Abaqus 分析用户指南第 36.3.6 节](../usb/usb-link.md#usb-cni-acontactcontrolsstd)
- ["Abaqus/Standard 中的接触公式，" Abaqus 分析用户指南第 38.1.1 节](../usb/usb-link.md#usb-cni-acontactpairform)
- ["在 Abaqus/Standard 中平滑接触表面，" Abaqus 分析用户指南第 38.1.3 节](../usb/usb-link.md#usb-cni-asmoothsurfaces)
- ["与 Abaqus/Standard 中接触建模相关的常见困难，" Abaqus 分析用户指南第 39.1.2 节](../usb/usb-link.md#usb-cni-acontacttrouble)
- ["在 Abaqus/Explicit 中定义接触对，" Abaqus 分析用户指南第 36.5.1 节](../usb/usb-link.md#usb-cni-aexpcontactpair)
- ["Abaqus/Explicit 中接触对的接触公式，" Abaqus 分析用户指南第 38.2.2 节](../usb/usb-link.md#usb-cni-aexpcontactpairform)
- ["调整 Abaqus/Explicit 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.5.4 节](../usb/usb-link.md#usb-cni-aexpadjustsurfaces)

### 在 Abaqus/Standard 分析中定义接触表面

### **必需参数：**

INTERACTION

将此参数设置为与正在定义的接触对关联的 [*SURFACE INTERACTION](ch18abk50.md) 属性定义名称。

### **可选参数：**

ADJUST

将此参数设置为一个节点集标签或一个值，以调整此选项中指定的表面的初始位置。这些调整在分析开始时进行，不会产生任何应变。此参数是 TIED 接触所必需的。

EXTENSION ZONE

将此参数设置为主表面要延伸的端段或小平面边缘长度的一部分，以避免与接触建模相关的数值舍入误差。给定的值必须介于 0.0 和 0.2 之间。默认值为 0.1。此参数仅影响节点到表面接触。

GEOMETRIC CORRECTION

将此参数设置为由 [*SURFACE SMOOTHING](ch18abk55.md) 定义的表面平滑属性名称。此参数仅影响表面到表面接触。

HCRIT

将此参数设置为从表面上的点必须穿透主表面的距离，之后 Abaqus/Standard 放弃当前增量并使用更小的增量重试。HCRIT 的默认值是从表面上特征单元面长度的一半。此参数不适用于使用有限滑动、表面到表面接触公式的接触对。

MIDFACE NODES

设置 MIDFACE NODES=YES 以自动将形成表面到表面接触对从表面的大多数三维二阶单元类型（无面中节点的作品单元）转换为具有面中节点的单元。

设置 MIDFACE NODES=NO（默认）以避免向表面到表面接触对的从表面底层单元添加面中节点。

此参数只能用于表面到表面接触对。Abaqus/Standard 自动将形成节点到表面接触对从表面的大多数作品单元转换为具有面中节点的单元。

MINIMUM DISTANCE

设置 MINIMUM DISTANCE=YES（默认）以在附近表面最初仅在单点接触时自动激活局部接触阻尼。

设置 MINIMUM DISTANCE=NO 以放弃此自动局部阻尼。

此参数只能与有限滑动、表面到表面接触公式一起使用。

NO THICKNESS

包含此参数以在接触计算中忽略表面厚度效应。此参数仅影响默认考虑表面厚度效应的接触公式（它不影响有限滑动、节点到表面接触）。

SMALL SLIDING

包含此参数以指示应使用小滑动接触公式而非有限滑动接触公式。此参数不允许与自接触一起使用。

SMOOTH

将此参数设置为在有限滑动、节点到表面接触公式中用于基于单元的主表面的平滑度。给定的值必须介于 0.0 和 0.5 之间。默认值为 0.2。此参数不影响具有解析刚性表面或除有限滑动、节点到表面接触公式之外的接触公式的接触对。

SLIDING TRANSITION

设置 SLIDING TRANSITION=ELEMENT ORDER SMOOTHING 以使滑动时节点力重分配的平滑与从表面底层单元的阶数相同。

设置 SLIDING TRANSITION=LINEAR SMOOTHING 以使滑动时节点力重分配具有线性平滑。

设置 SLIDING TRANSITION=QUADRATIC SMOOTHING 以使滑动时节点力重分配具有二次平滑。

此参数只能与表面到表面接触公式一起使用。

SUPPLEMENTARY CONSTRAINTS

设置 SUPPLEMENTARY CONSTRAINTS=SELECTIVE（默认）以使用补充约束的选择性方案。

设置 SUPPLEMENTARY CONSTRAINTS=YES 以在适用时添加补充接触约束。

设置 SUPPLEMENTARY CONSTRAINTS=NO 以放弃补充接触约束。

TIED

包含此参数以指示此 [*CONTACT PAIR](ch03abk68.md) 的表面将在整个模拟期间被"绑定"在一起。使用 TIED 参数时需要 ADJUST 参数。此参数不允许与自接触一起使用。

TRACKING

此参数控制对有限滑动、表面到表面接触使用哪种接触跟踪算法；它对使用其他公式的接触对没有影响。

设置 TRACKING=PATH（默认）以为有限滑动、表面到表面接触调用基于路径的接触跟踪算法。

设置 TRACKING=STATE 以为有限滑动、表面到表面接触调用基于状态的接触跟踪算法。

TYPE

设置 TYPE=NODE TO SURFACE（默认）以根据从节点投影到主表面上那一点处的插值函数生成接触约束系数。

设置 TYPE=SURFACE TO SURFACE 以生成接触约束系数，从而使指定表面类型配对的应力精度最优化。此参数设置将对包含基于节点的表面的接触对被忽略。

### **用于定义形成接触对的表面和节点集的数据行：**

**第一行：**

根据需要重复此数据行，以定义形成接触对的所有表面或节点集。每一数据行定义一个可能相互作用的表面对或节点集与表面。

### 在 Abaqus/Explicit 分析中定义接触表面

### **可选参数：**

CPSET

将此参数设置为要向其添加正在定义的接触对的接触对集合名称。CPSET 名称可用于将接触对与 [*CLEARANCE](ch03abk21.md) 选项或 [*CONTACT CONTROLS](ch03abk57.md) 选项关联，这些选项可用于调整算法控制参数。它也可与 [*CONTACT OUTPUT](ch03abk67.md) 选项一起使用，以指定需要输出数据库结果的接触对。

INTERACTION

将此参数设置为与正在定义的接触对关联的 [*SURFACE INTERACTION](ch18abk50.md) 属性定义名称。

MECHANICAL CONSTRAINT

将此参数设置用于强制接触约束的方法的名称。

设置 MECHANICAL CONSTRAINT=KINEMATIC（默认）以选择运动接触方法。

设置 MECHANICAL CONSTRAINT=PENALTY 以选择惩罚接触方法。

OP

设置 OP=ADD（默认）以将新接触对添加到现有接触对集合。设置 OP=DELETE 以从活动接触对集合中移除此选项使用中给出的接触对。

SMALL SLIDING

包含此参数以指示应使用小滑动接触公式而非有限滑动接触公式。此参数只能用于在模拟第一步中定义的接触对，并使用运动约束方法。

WEIGHT

将此参数设置为接触表面的加权因子。

### **用于定义形成接触对的表面和节点集的数据行：**

**第一行：**

根据需要重复此数据行，以定义形成接触对的所有表面或节点集。每一数据行定义一个可能相互作用的表面对或节点集与表面。




