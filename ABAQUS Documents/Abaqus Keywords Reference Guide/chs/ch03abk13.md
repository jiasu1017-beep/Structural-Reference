# *CFD






### *CFD计算流体动力学分析。

此选项用于在瞬态和稳态流体流动问题中控制动量、能量、温度、物种和其他标量变量的传输。

**产品：**Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **步骤模块

##### **参考：**

- ["不可压缩流体动力学分析，" Abaqus 分析用户指南第 6.6.2 节](../usb/usb-link.md#usb-anl-aifluiddyn)

### **必需参数：**

INCOMPRESSIBLE NAVIER STOKES

包含此参数以指定不可压缩流动分析。

### **可选参数：**

ENERGY EQUATION

设置 ENERGY EQUATION=NO ENERGY（默认）以指定等温流动问题。

设置 ENERGY EQUATION=TEMPERATURE 以指定以温度为主要传输标量变量的热（热量）传输问题。

INCREMENTATION

此参数仅对瞬态流动问题有效。

设置 INCREMENTATION=FIXED CFL（默认）以设置时间步进固定的 Courant-Friedrichs-Lewy（CFL）数。Abaqus/CFD 根据指定的 CFL 数自动确定稳定时间步长。

设置 INCREMENTATION=FIXED STEP SIZE 以设置固定时间步长进行时间步进。

STEADY STATE

此参数仅对稳态流动问题有效。

### **INCREMENTATION=FIXED CFL 的数据行：**

**第一行：**

**第二行：**

### **INCREMENTATION=FIXED STEP SIZE 的数据行：**

**第一行：**

**第二行：**

### **稳态流动的数据行：**

**第一行（也是唯一行）：**




