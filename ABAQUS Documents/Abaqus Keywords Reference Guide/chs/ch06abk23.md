# *FLUID EXCHANGE PROPERTY





### *FLUID EXCHANGE PROPERTY定义流体腔流入或流出的流体交换属性。

此选项用于定义两个流体腔之间或流体腔与其环境之间流动的流体交换属性。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["流体交换定义，" Abaqus Analysis User's Guide第11.5.3节](../usb/usb-link.md#usb-anl-afluidcavityexchange)
- [*FLUID EXCHANGE](ch06abk21.md)

### **必需参数：**

NAME

将此参数设置为用于引用流体交换属性的标签。

TYPE

设置TYPE=BULK VISCOSITY以定义流体交换，其中质量流率与压差由粘性和流体动力学阻力系数相关联。

设置TYPE=ENERGY FLUX以通过明确指定热能流率泄漏来定义流体交换。此参数值仅适用于Abaqus/Explicit分析。

设置TYPE=ENERGY RATE LEAKAGE以通过将热能流率定义为温度差和压力的函数来定义流体交换。此参数值仅适用于Abaqus/Explicit分析。

设置TYPE=FABRIC LEAKAGE以定义由于织物泄漏引起的流体交换。

设置TYPE=MASS FLUX以通过明确指定质量流率泄漏来定义流体交换。

设置TYPE=MASS RATE LEAKAGE以通过将质量流率定义为压差和温度的函数来定义流体交换。

设置TYPE=ORIFICE以定义通过通风孔的流体交换。此参数值仅适用于Abaqus/Explicit分析。

设置TYPE=VOLUME FLUX以通过明确指定体积流率泄漏来定义流体交换。

设置TYPE=VOLUME RATE LEAKAGE以通过将体积流率泄漏定义为压差和温度的函数来定义流体交换。

设置TYPE=USER以指示在Abaqus/Explicit中使用用户子程序[`VUFLUIDEXCH`](../sub/sub-link.md#sub-xsl-vufluidexch)来通过指定质量流率和/或热能流率定义流体交换。

### **可选参数：**

CONSTANTS

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为在用户子程序[`VUFLUIDEXCH`](../sub/sub-link.md#sub-xsl-vufluidexch)中定义流体交换所需的数据常量值数量。默认值为CONSTANTS=0。

DEPENDENCIES

将此参数设置为TYPE参数定义的系数规范中包含的场变量数量。如果省略此参数，则假定系数不依赖于任何场变量。

DEPVAR

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用户子程序[`VUFLUIDEXCH`](../sub/sub-link.md#sub-xsl-vufluidexch)所需的数量。默认值为DEPVAR=0。

### **TYPE=BULK VISCOSITY的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将粘性和流体动力学阻力系数定义平均绝对压力、平均温度和其他预定义场变量的函数。

### **TYPE=ENERGY FLUX的数据行：**

**第一行（唯一行）：**

### **TYPE=ENERGY RATE LEAKAGE的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将热能流率定义为温度差、平均绝对压力、平均温度和其他预定义场变量的函数。

### **TYPE=FABRIC LEAKAGE或TYPE=ORIFICE的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于五时才需要）：**

根据需要重复此组数据行，以将排放系数定义为压力、温度和其他预定义场变量的函数。

### **TYPE=MASS FLUX的数据行：**

**第一行（唯一行）：**

### **TYPE=MASS RATE LEAKAGE的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将质量流率定义为压差、平均绝对压力、平均温度和其他预定义场变量的函数。

### **TYPE=VOLUME FLUX的数据行：**

**第一行（唯一行）：**

### **TYPE=VOLUME RATE LEAKAGE的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将体积流率泄漏定义为压差、平均绝对压力、平均温度和其他预定义场变量的函数。

### **TYPE=USER的数据行：**

**第一行：**

根据需要重复此数据行，以定义所有流体交换常数。
