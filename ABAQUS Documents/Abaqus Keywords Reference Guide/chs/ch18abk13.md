# *SHEAR TEST DATA





### *SHEAR TEST DATA用于提供剪切试验数据。

此选项只能与[*VISCOELASTIC](ch21abk04.md)选项配合使用。如果使用了[*COMBINED TEST DATA](ch03abk25.md)选项，则[*SHEAR TEST DATA](ch18abk13.md)选项不能用于粘弹性材料。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Time domain viscoelasticity," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- [*VISCOELASTIC](ch21abk04.md)

### 使用剪切试验数据定义粘弹性材料

### **可选参数：**

SHRINF

要指定蠕变试验数据，请将此参数设置为长期归一化剪切柔量 ![](../graphics/key_eqn00196.gif) 的值。

要指定松弛试验数据，请将此参数设置为长期归一化剪切模量 ![](../graphics/key_eqn00197.gif) 的值。剪切柔量和剪切模量通过 ![](../graphics/key_eqn00198.gif) 相关联。拟合程序将在约束 ![](../graphics/key_eqn00199.gif) 中使用指定值。

### **指定蠕变试验数据的数据行：**

**第一行：**

根据需要重复此数据行以提供柔量-时间数据。

### **指定松弛试验数据的数据行：**

**第一行：**

根据需要重复此数据行以提供模量-时间数据。




