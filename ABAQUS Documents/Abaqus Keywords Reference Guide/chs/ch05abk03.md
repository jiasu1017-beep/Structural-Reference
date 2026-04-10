# *ELASTIC









### *ELASTIC定义弹性材料属性。

此选项用于定义线性弹性模量。在Abaqus/Standard分析中，可以使用分布（["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)）为实体连续体单元定义空间变化的各向同性、正交各向异性（包括工程常数和层合板）或各向异性线性弹性模量。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["线性弹性行为，" Abaqus分析用户指南第22.2.1节](../usb/usb-link.md#usb-mat-clinearelastic)

### **可选参数：**

COMPRESSION FACTOR

此参数仅在非耦合牵引-分离弹性行为中有意义。

将此参数设置为弹性模量 ![](../graphics/key_eqn00641.gif) 在压缩时必须缩放的因子。使用与1.0不同的因子会导致拉伸和压缩具有不同的弹性模量。

DEPENDENCIES

将此参数设置为模量定义中包含的场变量依赖项数。如果省略此参数，则假定模量为常数或仅取决于温度。有关更多信息，请参见["材料数据定义，" Abaqus分析用户指南第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

如果在Abaqus/Standard分析中使用分布定义空间变化的弹性模量，则此参数不相关。请参见["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)。

MODULI

此参数仅在[*ELASTIC](ch05abk03.md)选项与[*VISCOELASTIC](ch21abk04.md)选项结合使用时适用。

设置 MODULI=INSTANTANEOUS 以指示弹性材料常数定义瞬时行为。此参数值不适用于Abaqus/Standard分析中的频域粘弹性。

设置 MODULI=LONG TERM（默认）以指示弹性材料常数定义长期行为。

TYPE

设置 TYPE=ANISOTROPIC 以定义完全各向异性行为。

设置 TYPE=COUPLED TRACTION 以定义内聚单元的耦合牵引行为。

设置 TYPE=ENGINEERING CONSTANTS 通过给出"工程常数"（主方向上的广义杨氏模量、泊松比和剪切模量）来定义正交各向异性行为。

设置 TYPE=ISOTROPIC（默认）来定义各向同性行为。

设置 TYPE=LAMINA 来定义平面应力中的正交各向异性材料。

设置 TYPE=ORTHOTROPIC 通过直接给出弹性刚度矩阵来定义正交各向异性行为。

设置 TYPE=SHEAR 来定义（各向同性）剪切弹性模量。此参数设置仅在与Abaqus/Explicit中的[*EOS](ch05abk27.md)选项结合使用时适用。

设置 TYPE=SHORT FIBER 来为每个壳单元中的每一层定义层合板材料属性。此参数设置仅在使用Abaqus/Standard与**abaqus moldflow**执行程序结合时适用。给出的任何数据行都将被忽略。材料属性将从标识为*jobid*`.shf`的ASCII中性文件读取。请参见["将Moldflow数据转换到Abaqus输入文件，" Abaqus分析用户指南第3.2.37节](../usb/usb-link.md#usb-int-dmflabaproc)，获取更多信息。

设置 TYPE=TRACTION 来定义翘曲单元的正交各向异性剪切行为或内聚单元的非耦合牵引行为。

使用分布定义弹性模量时，必须使用TYPE参数来指示弹性行为的各向异性水平。各向异性水平必须与分布中定义的一致。请参见["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)。

### **直接定义完全各向异性弹性的数据行（TYPE=ANISOTROPIC）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **为内聚单元定义耦合牵引-分离行为的数据行（TYPE=COUPLED TRACTION）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于一时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **用模量定义正交各向异性弹性的数据行（TYPE=ENGINEERING CONSTANTS）：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **定义各向同性弹性的数据行（TYPE=ISOTROPIC）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **定义平面应力正交各向异性弹性的数据行（TYPE=LAMINA）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于一时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **直接定义正交各向异性弹性的数据行（TYPE=ORTHOTROPIC）：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **定义各向同性弹性剪切行为的数据行（TYPE=SHEAR）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将弹性剪切模量定义为温度和其他预定义场变量的函数。

### **为翘曲单元定义正交各向异性剪切行为或为内聚单元定义非耦合牵引行为的数据行（TYPE=TRACTION）：**

**第一行（定义翘曲单元正交各向异性剪切行为的唯一行；在这种情况下，数据不能定义为温度和/或场变量的函数）：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要；仅与内聚单元的非耦合牵引行为定义相关）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **在Abaqus/Standard分析中使用分布为实体连续体单元定义空间变化弹性行为的数据行。（分布支持TYPE=ISOTROPIC、TYPE=ENGINEERING CONSTANTS、TYPE=LAMINA、TYPE=ORTHOTROPIC和TYPE=ANISOTROPIC）：**

**第一行：**




