# *PERMEABILITY









### *PERMEABILITY定义孔隙流体渗透率。

此选项用于在涉及渗流和多孔介质的问题中定义孔隙流体流动的渗透率。

**产品：**Abaqus/Standard  Abaqus/CFD  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["渗透率，" Abaqus Analysis User's Guide第26.6.2节](../usb/usb-link.md#usb-mat-cpermeabil)

### 在Abaqus/Standard分析中定义渗透率

### **可选参数：**

DEPENDENCIES

将此参数设置为渗透率定义中包含的场变量依赖数量。如果省略此参数，则假定渗透率不依赖于场变量。

此参数只能与TYPE=ISOTROPIC、ORTHOTROPIC或ANISOTROPIC结合使用。

TYPE

设置TYPE=ISOTROPIC（默认）以定义完全饱和各向同性渗透率。设置TYPE=ORTHOTROPIC以定义完全饱和正交各向异性渗透率。设置TYPE=ANISOTROPIC以定义完全饱和各向异性渗透率。

设置TYPE=SATURATION以定义；这必须是同一材料的选项重复使用，必须跟在完全饱和渗透率定义之后。定义必须给出在时的值。

设置TYPE=VELOCITY以定义；这必须是同一材料的选项重复使用，必须跟在完全饱和渗透率定义之后。

### **定义完全饱和材料属性时需要的参数：**

SPECIFIC

将此参数设置为润湿液体的比重。实际比重必须给定为非零正值，如果需要总压力解决方案，则必须使用GRAV分布荷载类型来施加重力荷载。

### **定义完全饱和各向同性渗透率的数据行（TYPE=ISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行以定义变化。

### **定义完全饱和正交各向异性渗透率的数据行（TYPE=ORTHOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于3时需要）：**

根据需要重复此组数据行以定义变化。

### **定义完全饱和各向异性渗透率的数据行（TYPE=ANISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数被指定时需要）：**

根据需要重复此组数据行以定义变化。

### **定义润湿液体饱和度渗透率依赖性的数据行（TYPE=SATURATION）：**

**第一行：**

根据需要重复此数据行以定义变化。

### **定义速度系数的数据行（TYPE=VELOCITY）：**

**第一行：**

根据需要重复此数据行以定义变化。

### 在Abaqus/CFD分析中定义渗透率

### **可选参数：**

INERTIAL DRAG COEFFICIENT

将此参数设置为与多孔介质中惯性（二次或形式）阻力成比例的值。默认值为0.142887。

TYPE

设置TYPE=ISOTROPIC（默认）以定义完全饱和各向同性渗透率。

设置TYPE=CARMAN KOZENY以通过Carman-Kozeny关系定义作为孔隙度函数的渗透率。

### **定义完全饱和各向同性渗透率的数据行（TYPE=ISOTROPIC）：**

**第一行：**

根据需要重复此数据行以定义变化。

### **定义Carman-Kozeny渗透率关系的数据行（TYPE=CARMAN KOZENY）：**

**第一行（也是唯一一行）：**