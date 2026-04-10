# *EOS









### *EOS指定状态方程模型。

此选项用于以状态方程的形式定义流体动力学材料模型。

**产品：**Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["状态方程，" Abaqus分析用户指南第25.2.1节](../usb/usb-link.md#usb-mat-ceos)

### **必需参数：**

TYPE

设置 TYPE=IDEAL GAS 以使用理想气体状态方程。

设置 TYPE=IGNITION AND GROWTH 以使用点火和生长状态方程；如果使用此状态方程，则需要[*REACTION RATE](ch17abk10.md)选项和[*GAS SPECIFIC HEAT](ch07abk07.md)选项。

设置 TYPE=JWL 以使用炸药状态方程；如果使用此状态方程，则需要[*DETONATION POINT](ch04abk18.md)选项。

设置 TYPE=TABULAR 以使用能量线性关系的状态方程表。

设置 TYPE=USER 以使用在用户子程序[`VUEOS`](../sub/sub-link.md#sub-xsl-vueos)中定义的用户定义状态方程。

设置 TYPE=USUP 以使用线性 ![](../graphics/key_eqn00657.gif) 状态方程。

### **可选参数：**

DETONATION ENERGY

此参数只能与TYPE=IGNITION AND GROWTH结合使用。

将此参数设置为引爆能量。默认值为0.0。

PROPERTIES

此参数只能在使用USER参数时指定。

将此参数设置为用户子程序[`VUEOS`](../sub/sub-link.md#sub-xsl-vueos)中所需属性值的数据个数。默认值为0。

### **理想气体状态方程的数据行（TYPE=IDEAL GAS）：**

**第一行（也是唯一一行）：**

### **点火和生长状态方程的数据行（TYPE=IGNITION AND GROWTH）：**

**第一行：**

未反应炸药状态方程中使用的材料常数。

**第二行：**

反应产物状态方程中使用的材料常数。

### **炸药状态方程的数据行（TYPE=JWL）：**

**第一行（也是唯一一行）：**

### **状态方程表的数据行（TYPE=TABULAR），其中体积应变值必须按降序排列：**

**第一行：**

根据需要重复此数据行，以定义 ![](../graphics/key_eqn00674.gif) 和 ![](../graphics/key_eqn00675.gif) 对体积应变的依赖关系。

### **线性状态方程的数据行（TYPE=USUP）：**

**第一行（也是唯一一行）：**

### **定义用户定义状态方程的材料属性的数据行（TYPE=USER）：**

**如果省略PROPERTIES参数或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行以定义材料属性。




