# *MAGNETIC PERMEABILITY









### *MAGNETIC PERMEABILITY指定磁导率。

此选项用于为电磁分析或静磁分析中的电磁单元定义磁导率。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["磁导率，" Abaqus Analysis User's Guide第26.5.3节](../usb/usb-link.md#usb-mat-cmagpermeability)
- ["涡流分析，" Abaqus Analysis User's Guide第6.7.5节](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["静磁分析，" Abaqus Analysis User's Guide第6.7.6节](../usb/usb-link.md#usb-anl-amagnetostatic)

### **可选参数：**

DEPENDENCIES

将此参数设置为磁导率定义中包含的场变量数量。如果省略此参数，则假定磁导率不依赖于任何场变量，但可能仍依赖于温度和频率。

DEPENDENCIES参数不能与NONLINEAR参数一起使用。

FREQUENCY

包含此参数以将磁导率指定为频率的函数。

FREQUENCY参数不能与NONLINEAR参数一起使用。

NONLINEAR

如果磁行为是非线性的且以表格形式提供（磁通密度与磁场值的关系），则包含此参数。如果使用此参数，则不需要数据行。磁行为的表格数据（包括依赖场变量的非线性磁特性）必须使用[*NONLINEAR BH](ch14abk14.md)选项提供。

NONLINEAR参数不能与FREQUENCY和DEPENDENCIES参数一起使用。

TYPE

设置TYPE=ISOTROPIC（默认）以定义各向同性磁导率。设置TYPE=ORTHOTROPIC以定义正交各向异性磁导率。设置TYPE=ANISOTROPIC以定义完全各向异性磁导率。

如果还使用了NONLINEAR参数，则TYPE参数只能设置为ISOTROPIC或ORTHOTROPIC。

### **如果省略FREQUENCY和NONLINEAR参数，定义各向同性磁导率的数据行（TYPE=ISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于6时需要）：**

根据需要重复此组数据行，以将各向同性磁导率定义为温度和场变量的函数。

### **如果包含FREQUENCY参数，定义各向同性磁导率的数据行（TYPE=ISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将各向同性磁导率定义为频率、温度和场变量的函数。

### **如果省略FREQUENCY和NONLINEAR参数，定义正交各向异性磁导率的数据行（TYPE=ORTHOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将正交各向异性磁导率定义为温度和场变量的函数。

### **如果包含FREQUENCY参数，定义正交各向异性磁导率的数据行（TYPE=ORTHOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于3时需要）：**

根据需要重复此组数据行，以将正交各向异性磁导率定义为频率、温度和场变量的函数。

### **如果省略FREQUENCY和NONLINEAR参数，定义各向异性磁导率的数据行（TYPE=ANISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于1时需要）：**

根据需要重复此组数据行，以将各向异性磁导率定义为温度和场变量的函数。

### **如果包含FREQUENCY参数，定义各向异性磁导率的数据行（TYPE=ANISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于或等于1时需要）：**

根据需要重复此组数据行，以将各向异性磁导率定义为频率、温度和场变量的函数。

### **如果使用了NONLINEAR参数，则此选项没有关联的数据行。**



