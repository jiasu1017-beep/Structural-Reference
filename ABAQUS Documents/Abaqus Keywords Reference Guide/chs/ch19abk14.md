# *TRANSVERSE SHEAR STIFFNESS





### *TRANSVERSE SHEAR STIFFNESS定义梁和壳的横向剪切刚度。

此选项必须与[*BEAM GENERAL SECTION](ch02abk05.md)选项、[*BEAM SECTION](ch02abk06.md)选项、[*COHESIVE SECTION](ch03abk24.md)选项、[*SHELL GENERAL SECTION](ch18abk14.md)选项或[*SHELL SECTION](ch18abk15.md)选项一起使用。借此选项定义的横向剪切刚度仅影响其截面属性由紧随其后的截面选项定义的横向剪切柔性单元。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例

**Abaqus/CAE：**Property模块

##### **参考：**

- ["壳截面行为," Section 29.6.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshellsectionbehavior)
- ["选择梁单元," Section 29.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamelem)
- ["使用连续体方法定义内聚单元的构成响应," Section 32.5.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivematbehavior)
- ["使用牵引-分离描述定义内聚单元的构成响应," Section 32.5.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivebehavior)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)
- [*BEAM GENERAL SECTION](ch02abk05.md)
- [*BEAM SECTION](ch02abk06.md)
- [*COHESIVE SECTION](ch03abk24.md)

**此选项没有关联的参数。**

### **与内聚截面、壳截面和[*BEAM GENERAL SECTION](ch02abk05.md)、SECTION=MESHED一起使用时的数据行：**

**第一行（也是唯一行）：**

如果任一值![](../graphics/key_eqn01106.gif)或![](../graphics/key_eqn01107.gif)被省略或为零，则非零值将用于两者。

### **与其他所有梁截面一起使用时的数据行：**

**第一行（也是唯一行）：**

当标签SCF未使用时，如果任一值![](../graphics/key_eqn01111.gif)被省略或为零，则非零值将用于两者。





