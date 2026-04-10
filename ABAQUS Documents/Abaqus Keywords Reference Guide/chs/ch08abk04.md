# *HOURGLASS STIFFNESS






### *HOURGLASS STIFFNESS指定非默认的沙漏刚度。

此选项适用于一阶减缩积分单元； 二阶减缩积分单元类型 M3D9R、S8R5 和 S9R5； 以及改进的四面体和三角形单元。它还可用于为壳单元中与钻孔自由度（关于表面法线的旋转）相关的刚度定义沙漏缩放因子，并修改 C3D4H 单元的压力 Lagrange 乘子自由度的沙漏刚度因子。

[*HOURGLASS STIFFNESS](ch08abk05.md) 选项只能与 [*MEMBRANE SECTION](ch13abk16.md) 选项、[*SOLID SECTION](ch18abk22.md) 选项、[*SHELL SECTION](ch18abk15.md) 选项或 [*SHELL GENERAL SECTION](ch18abk14.md) 选项一起使用。使用此选项定义的沙漏控制仅影响那些其截面特性由紧 preceding 的截面选项定义的单元。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件、零件实例  

**Abaqus/CAE：** Mesh 模块

##### **参考文献：**

- ["截面控制，" Abaqus Analysis User's Guide 第 27.1.4 节](../usb/usb-link.md#usb-elm-esectioncontrol)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)
- [*SOLID SECTION](ch18abk22.md)

**此选项没有关联的参数。**

### **定义非默认沙漏刚度的数据行：**

**第一（也是唯一）行：**




