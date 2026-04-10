# *JOINTED MATERIAL






### *JOINTED MATERIAL指定节理材料模型。

此选项用于为单个节理系统或节理材料弹塑性模型中的体材料失效定义失效面和流动参数，或者用于定义张开节理中的剪切保留。最多可以为每个材料点定义三个节理系统。

**产品：** Abaqus/Standard  

**类型：** 模型数据  

**级别：** 模型  

##### **参考文献：**

- ["节理材料模型，" Abaqus Analysis User's Guide 第 23.5.1 节](../usb/usb-link.md#usb-mat-cjointedmat)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外模型参数定义中包含的场变量依赖数量。如果省略此参数，则假定参数仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

JOINT DIRECTION

将此参数设置为用于定义节理系统方向的 [*ORIENTATION](ch15abk01.md) 的名称。此 [*ORIENTATION](ch15abk01.md) 选项的使用不影响应力和应变分量的输出——它仅在原始配置中定义节理方向。省略此参数以给出体材料失效参数。JOINT DIRECTION 参数不能与 SHEAR RETENTION 参数一起使用。

NO SEPARATION

包含此参数以防止节理张开。此参数必须与 JOINT DIRECTION 参数一起使用。

SHEAR RETENTION

包含此参数以定义张开节理中的剪切保留。如果省略此参数，则假定为零剪切保留。SHEAR RETENTION 参数不能与 JOINT DIRECTION 参数一起使用。

### **定义失效面和流动参数的数据行（SHEAR RETENTION 省略）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于四时需要）：**

根据需要重复此组数据行，以将失效和表面流动参数定义为温度和其他预定义场变量的函数。

### **定义张开节理中剪切 retention 的数据行（SHEAR RETENTION 包含）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于六时需要）：**

根据需要重复此组数据行，以将剪切保留定义为温度和其他预定义场变量的函数。




