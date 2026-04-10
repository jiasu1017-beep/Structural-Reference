# *BASE MOTION





### *BASE MOTION为线性、基于特征模态的动态过程定义基础运动。

此选项仅在使用系统自然模态的线性动力学过程中相关（[*STEADY STATE DYNAMICS](ch18abk34.md)不使用DIRECT参数，[*MODAL DYNAMIC](ch13abk18.md)和[*RANDOM RESPONSE](ch17abk07.md)）。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["自然频率提取，" Abaqus Analysis User's Guide第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)
- ["瞬态模态动态分析，" Abaqus Analysis User's Guide第6.3.7节](../usb/usb-link.md#usb-anl-amodaldynamic)
- ["基于模态的稳态动态分析，" Abaqus Analysis User's Guide第6.3.8节](../usb/usb-link.md#usb-anl-asteadystdyn)
- ["随机响应分析，" Abaqus Analysis User's Guide第6.3.11节](../usb/usb-link.md#usb-anl-arandomresponse)

### **必需参数：**

DOF

将此参数设置为定义基础运动的方向（1-6，包括旋转）。此方向始终是全局方向。

将此参数设置为8以获得声学自由度，这仅用于基于SIM的架构中的次级基础运动。

### **[*MODAL DYNAMIC](ch13abk18.md)和[*STEADY STATE DYNAMICS](ch18abk34.md)分析的必需参数：**

AMPLITUDE

将此参数设置为定义运动的时间历史（[*MODAL DYNAMIC](ch13abk18.md)）或频谱（[*STEADY STATE DYNAMICS](ch18abk34.md)）的[*AMPLITUDE](ch01abk09.md)选项的名称。此参数与[*RANDOM RESPONSE](ch17abk07.md)过程无关。DEFINITION=SOLUTION DEPENDENT不能用于此选项引用的[*AMPLITUDE](ch01abk09.md)中。

### **可选参数：**

BASE NAME

如果此基础运动要应用于次级基础，则将此参数设置为基础的名称。基础名称在[*FREQUENCY](ch06abk35.md)步骤中的[*BOUNDARY](ch02abk12.md)选项上的BASE NAME参数定义。

LOAD CASE

将此参数设置为载荷工况编号。此参数用于[*RANDOM RESPONSE](ch17abk07.md)分析中，是[*CORRELATION](ch03abk77.md)选项上载荷工况的交叉引用。

SCALE

将此参数设置为振幅曲线的比例因子。默认值为SCALE=1.0。此参数适用于[*MODAL DYNAMIC](ch13abk18.md)和[*STEADY STATE DYNAMICS](ch18abk34.md)过程。

TYPE

设置TYPE=ACCELERATION（默认）、VELOCITY或DISPLACEMENT。

### **稳态动力学分析的可选、互斥参数：**

IMAGINARY

包含此参数以定义由振幅定义给出的基础运动记录的虚部（异相）部分。

REAL

包含此参数（默认）以定义由振幅定义给出的基础运动记录的实部（同相）部分。

### **除非主基础运动定义关于不是坐标系原点的点的旋转，否则此选项没有数据行。**

### **为指定旋转定义旋转中心的数据行：**

**第一行（也是唯一一行）：**

此数据行仅与[*MODAL DYNAMIC](ch13abk18.md)和[*STEADY STATE DYNAMICS](ch18abk34.md)过程中定义的主基础运动相关。


