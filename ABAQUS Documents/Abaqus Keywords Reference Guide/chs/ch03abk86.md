# *CREEP STRAIN RATE CONTROL






### *CREEP STRAIN RATE CONTROL基于最大等效蠕变应变率控制载荷。

此选项用于基于在指定单元集中计算的最大等效蠕变应变率来控制载荷。

**产品：**Abaqus/Standard  

**类型：**历史数据 

**级别：**步骤

##### **参考：**

- ["率相关塑性：蠕变和膨胀，" Abaqus 分析用户指南第 23.2.4 节](../usb/usb-link.md#usb-mat-cratedepcreep)

### **必需参数：**

AMPLITUDE

将此参数设置为被控制的载荷引用的 [*AMPLITUDE](ch01abk09.md) 名称（类型为 DEFINITION=SOLUTION DEPENDENT）（["幅值曲线，" Abaqus 分析用户指南第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。

ELSET

将此参数设置为其上进行最大等效蠕变应变率搜索的单元集名称。[*CREEP](ch03abk85.md) 选项必须是集中某些单元的 [*MATERIAL](ch13abk08.md) 定义（["材料数据定义，" Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata)）的一部分。

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度和蠕变应变之外还包括在目标蠕变应变率定义中的场变量依赖项数。如果省略此参数，则假定目标蠕变应变率仅依赖于等效蠕变应变，也可能依赖于温度。每个温度下的蠕变应变依赖曲线必须始终从零等效蠕变应变开始。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

OP

设置 OP=MOD（默认）以保留现有的目标 [*CREEP STRAIN RATE CONTROL](ch03abk86.md) 定义，此选项定义要添加或修改的目标蠕变应变率。

设置 OP=NEW 以移除先前步骤中定义的所有目标蠕变应变率。

### **用于定义载荷控制参数的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以定义目标应变率对蠕变应变、温度和其他预定义场变量的依赖性。




