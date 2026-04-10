# *GAS SPECIFIC HEAT






### *GAS SPECIFIC HEAT为点火和生长状态方程定义反应产物的比热。

此选项用于为点火和生长状态方程指定反应气体产物的比热。当使用 [*EOS](ch05abk27.md), TYPE=IGNITION AND GROWTH 选项时需要此选项。[*GAS SPECIFIC HEAT](ch07abk07.md) 选项应紧跟在 [*EOS](ch05abk27.md) 或 [*REACTION RATE](ch17abk10.md) 选项之后。

**产品：** Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["状态方程，" Abaqus Analysis User's Guide 第 25.2.1 节](../usb/usb-link.md#usb-mat-ceos)

### **可选参数：**

DEPENDENCIES

将此参数设置为反应产物比热定义中包含的场变量数量。如果省略此参数，则假定反应产物的比热是常量或仅取决于温度。

### **指定反应产物比热的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于六时需要）：**

根据需要重复此组数据行，以将比热定义为温度和其他预定义场变量的函数。




