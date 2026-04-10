# *TURBULENCE MODEL





### *TURBULENCE MODEL为流体分析指定湍流模型。

此选项只能作为[*CFD](ch03abk13.md)选项的子选项使用，以启用流体流动模拟的湍流建模。

**产品：**Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["不可压缩流体动力学分析," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)
- [*CFD](ch03abk13.md)

### **必需参数：**

TYPE

设置TYPE=SPALART ALLMARAS以指定Spalart-Allmaras湍流模型。

设置TYPE=RNG KEPSILON以指定![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00849.gif)重整化群湍流模型。

设置TYPE=KEPSILON REALIZABLE以指定![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00849.gif)可实现湍流模型。

设置TYPE=KOMEGA SST以指定![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00018.gif)剪切应力传输湍流模型。

### **TYPE=SPALART ALLMARAS的数据行：**

**第一行：**

**第二行：**

**第三行（除非在关联的[*CFD](ch03abk13.md)选项中使用ENERGY EQUATION=TEMPERATURE，否则输入空行）：**

### **TYPE=RNG KEPSILON的数据行：**

**第一行：**

**第二行（除非在关联的[*CFD](ch03abk13.md)选项中使用ENERGY EQUATION=TEMPERATURE，否则输入空行）：**

### **TYPE=KEPSILON REALIZABLE的数据行：**

**第一行：**

**第二行：**

**第三行（除非在关联的[*CFD](ch03abk13.md)选项中使用ENERGY EQUATION=TEMPERATURE，否则输入空行）：**

### **TYPE=KOMEGA SST的数据行：**

**第一行：**

**第二行（除非在关联的[*CFD](ch03abk13.md)选项上使用ENERGY EQUATION=TEMPERATURE，否则输入空行）：**





