# *ELECTRICAL CONDUCTIVITY









### *ELECTRICAL CONDUCTIVITY指定电导率。

此选项用于在耦合热-电和耦合热-电-结构分析中为耦合热-电和耦合热-电-结构单元定义电导率。此选项还用于在涡流分析中为电磁单元定义电导率。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["电导率，" Abaqus分析用户指南第26.5.1节](../usb/usb-link.md#usb-mat-celectricconduct)
- ["耦合热-电分析，" Abaqus分析用户指南第6.7.3节](../usb/usb-link.md#usb-anl-ajouleheating)
- ["全耦合热-电-结构分析，" Abaqus分析用户指南第6.7.4节](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)
- ["涡流分析，" Abaqus分析用户指南第6.7.5节](../usb/usb-link.md#usb-anl-aeddycurrent)

### **可选参数：**

DEPENDENCIES

将此参数设置为电导率定义中包含的场变量数。如果省略此参数，则假定电导率不依赖于任何场变量，但可能仍取决于温度和频率。有关更多信息，请参见["材料数据定义，" Abaqus分析用户指南第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

FREQUENCY

包含此参数以在涡流分析中将电导率指定为频率的函数。

TYPE

设置 TYPE=ISO（默认）来定义各向同性电导率。设置 TYPE=ORTHO 来定义正交各向异性电导率。设置 TYPE=ANISO 来定义完全各向异性电导率。

### **如果省略FREQUENCY参数，定义各向同性电导率的数据行（TYPE=ISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将各向同性电导率定义为温度和场变量的函数。

### **如果包含FREQUENCY参数，定义各向同性电导率的数据行（TYPE=ISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以将各向同性电导率定义为频率、温度和场变量的函数。

### **如果省略FREQUENCY参数，定义正交各向异性电导率的数据行（TYPE=ORTHO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将正交各向异性电导率定义为温度和场变量的函数。

### **如果包含FREQUENCY参数，定义正交各向异性电导率的数据行（TYPE=ORTHO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以将正交各向异性电导率定义为频率、温度和场变量的函数。

### **如果省略FREQUENCY参数，定义各向异性电导率的数据行（TYPE=ANISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于一时需要）：**

根据需要重复此组数据行，以将各向异性电导率定义为温度和场变量的函数。

### **如果包含FREQUENCY参数，定义各向异性电导率的数据行（TYPE=ANISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于或等于一时需要）：**

根据需要重复此组数据行，以将各向异性电导率定义为频率、温度和场变量的函数。




