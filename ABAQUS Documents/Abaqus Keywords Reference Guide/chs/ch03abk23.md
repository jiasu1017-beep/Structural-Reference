# *COHESIVE BEHAVIOR






### *COHESIVE BEHAVIOR指定基于表面的粘聚行为属性。

此选项用于在机械接触分析中定义基于表面的粘聚行为。必须与 [*SURFACE INTERACTION](ch18abk50.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["基于表面的粘聚行为，" Abaqus 分析用户指南第 37.1.10 节](../usb/usb-link.md#usb-cni-acohesivebehavior)
- [*SURFACE INTERACTION](ch18abk50.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为在模量定义中包含的场变量依赖项数。如果省略此参数，则假定模量为常数或仅依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

ELIGIBILITY

设置 ELIGIBILITY=CURRENT CONTACTS（默认）以不仅为在步骤开始时与主表面接触的从表面所有节点定义粘聚行为，还为初始未接触但在步骤过程中可能接触的从节点定义粘聚行为。

设置 ELIGIBILITY=ORIGINAL CONTACTS 以将粘聚行为限制为仅在步骤开始时与主表面接触的从表面节点。

设置 ELIGIBILITY=SPECIFIED CONTACTS 以将粘聚行为限制为使用 [*INITIAL CONDITIONS](ch09abk18.md)、TYPE=CONTACT 定义的从节点子集。此参数值仅适用于 Abaqus/Standard 分析。

REPEATED CONTACTS

包含此参数以在已定义渐进损伤时修改默认的失效后行为。默认情况下，一旦在这些节点处发生最终失效，从表面节点上的粘聚行为就不再强制执行。使用 REPEATED CONTACTS 参数可在最终失效后从表面节点的后续接触上强制执行粘聚行为。

TYPE

设置 TYPE=UNCOUPLED（默认）以定义非耦合牵引行为。

设置 TYPE=COUPLED 以定义耦合牵引行为。

### **用于定义非耦合牵引分离行为的数据行（TYPE=UNCOUPLED）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要；仅与定义非耦合牵引行为相关）：**

根据需要重复此数据行集，以将弹性行为定义为温度和其他预定义场变量的函数。

### **用于定义耦合牵引分离行为的数据行（TYPE=COUPLED）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于一时需要）：**

根据需要重复此数据行集，以将弹性行为定义为温度和其他预定义场变量的函数。




