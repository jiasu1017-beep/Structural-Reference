# *DYNAMIC TEMPERATURE-DISPLACEMENT





### *DYNAMIC TEMPERATURE-DISPLACEMENT使用显式积分的动态耦合热应力分析。

此选项用于指示要使用显式积分执行动态耦合热应力分析。

**产品：**Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["全耦合热应力分析，" Abaqus分析用户指南第6.5.3节](../usb/usb-link.md#usb-anl-acouptempdisp)

### **必需参数：**

EXPLICIT

包含此参数以指定显式时间积分。

### **可选、互斥参数：**

DIRECT USER CONTROL

包含此参数以指定此步骤应使用由用户指定的固定时间增量。

ELEMENT BY ELEMENT

包含此参数以指示应使用逐单元稳定时间增量估计的可变自动时间增量。此方法通常需要比全局时间估计器更多的增量 和更多的计算时间。

FIXED TIME INCREMENTATION

包含此参数以指定此步骤应使用固定时间增量，该增量将在步骤开始时由Abaqus/Explicit使用逐单元时间估计器确定。

### **可选参数：**

IMPROVED DT METHOD

设置 IMPROVED DT METHOD=YES（默认）以使用"改进"方法估计由于三维连续体单元和平面应力公式（壳、膜和二维平面应力单元）的机械响应导致的单元稳定时间增量。

设置 IMPROVED DT METHOD=NO 以使用保守方法估计由于三维连续体单元和平面应力公式的机械响应导致的单元稳定时间增量。

SCALE FACTOR

将此参数设置为用于缩放由Abaqus/Explicit计算的时间增量的因子。默认缩放因子为1.0。此参数可用于缩放默认的全局时间估计，并且可以与 ELEMENT BY ELEMENT 和 FIXED TIME INCREMENTATION 参数结合使用。它不能与 DIRECT USER CONTROL 参数结合使用。

### **自动时间增量（全局或逐单元估计）的数据行：**

**第一行（也是唯一一行）：**

### **使用 DIRECT USER CONTROL 的固定时间增量的数据行：**

**第一行（也是唯一一行）：**

### **使用 FIXED TIME INCREMENTATION 的固定时间增量的数据行：**

**第一行（也是唯一一行）：**




