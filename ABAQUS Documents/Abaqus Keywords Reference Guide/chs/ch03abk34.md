# *CONDUCTIVITY





### *CONDUCTIVITY指定热导率。

此选项用于指定材料的热导率。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["导热性"，Abaqus Analysis User's Guide第26.2.2节](../usb/usb-link.md#usb-mat-cconductivity)

### **可选参数：**

DEPENDENCIES

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

将此参数设置为导热率定义中包含的场变量数。如果省略此参数，则假定导热率为常数或仅取决于温度。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

PORE FLUID

此参数仅适用于Abaqus/Standard分析。

如果正在定义多孔介质中孔隙流体的导热率，则包含此参数。流体的导热率必须是各向同性的；因此，如果包含此参数，则不能使用TYPE=ORTHO和TYPE=ANISO。

TYPE

设置TYPE=ISO（默认值）以定义各向同性导热率。设置TYPE=ORTHO以定义正交各向异性导热率。设置TYPE=ANISO以定义完全各向异性导热率。Abaqus/CFD仅支持不具有场依赖变体的各向同性导热率。

### **定义各向同性热导率的数据行（TYPE=ISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将热导率定义为温度和其他预定义场变量的函数。

### **定义正交各向异性热导率的数据行（TYPE=ORTHO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将热导率定义为温度和其他预定义场变量的函数。

### **定义完全各向异性热导率的数据行（TYPE=ANISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于一时需要）：**

根据需要重复此组数据行，以将热导率定义为温度和其他预定义场变量的函数。




