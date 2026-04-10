# *ACOUSTIC MEDIUM





### *ACOUSTIC MEDIUM指定声学介质。

此选项用于定义与声学元素一起使用的声学介质的属性。[*ACOUSTIC MEDIUM](ch01abk02.md)选项必须与[*MATERIAL](ch13abk08.md)选项结合使用。[*ACOUSTIC MEDIUM](ch01abk02.md)选项可以多次使用以指定声学介质的所有属性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["声学介质，" Abaqus Analysis User's Guide第26.3.1节](../usb/usb-link.md#usb-mat-cacousticmed)

### **可选的、互斥的参数：**

BULK MODULUS

包含此参数以定义声学介质的体积模量（默认值）。

CAVITATION LIMIT

此参数仅适用于Abaqus/Explicit分析。

包含此参数以定义声学介质的空化压力极限。当流体绝对压力降至此极限时，声学介质将进行自由体积膨胀或空化，压力不再进一步降低。负的空化极限值表示声学介质能够维持负绝对压力至指定极限值。任何非零的初始声学静态压力值（如由大气压力和/或静水压力引起的）都可以使用[*INITIAL CONDITIONS](ch09abk18.md)，TYPE=ACOUSTIC STATIC PRESSURE选项指定。

如果省略此参数，则即使在任意大的负压力条件下，也假定流体不会空化。

COMPLEX BULK MODULUS

包含此参数以定义声学介质的复体积模量。

COMPLEX DENSITY

包含此参数以定义声学介质的复密度。

POROUS MODEL

此参数仅适用于Abaqus/Standard分析。

设置POROUS MODEL=DELANY BAZLEY（默认值）以使用Delany-Bazley模型计算与频率相关的复密度和复体积模量。

设置POROUS MODEL=MIKI以使用Delany-Bazley-Miki模型计算与频率相关的复密度和复体积模量。

VOLUMETRIC DRAG

包含此参数以定义声学介质的体积拖曳系数。

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外还包括在声学介质定义中的场变量依赖项数。如果省略此参数，则假定声学介质属性是常数或仅取决于温度。有关更多信息，请参见["在材料数据定义中指定场变量依赖性，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

### **定义声学材料体积模量的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于6时需要）：**

根据需要重复此组数据行，以将体积模量定义为温度和其他预定义场变量的函数。

### **定义声学材料空化压力极限的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于6时需要）：**

根据需要重复此组数据行，以将空化压力极限定义为温度和其他预定义场变量的函数。

### **定义声学材料复体积模量的数据行：**

**第一行：**

根据需要重复此数据行，以将复体积模量定义为频率的函数。

### **定义声学材料复密度的数据行：**

**第一行：**

根据需要重复此数据行，以将复密度定义为频率的函数。

### **定义声学材料体积拖曳的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于5时需要）：**

根据需要重复此组数据行，以将体积拖曳定义为频率、温度和其他预定义场变量的函数。

### **当POROUS MODEL=DELANY BAZLEY或POROUS MODEL=MIKI时的数据行：**

**第一行（也是唯一一行）：**