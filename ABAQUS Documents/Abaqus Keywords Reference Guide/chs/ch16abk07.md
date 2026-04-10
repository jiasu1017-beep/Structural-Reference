# *PHYSICAL CONSTANTS









### *PHYSICAL CONSTANTS指定物理常数。

此选项用于定义分析所需的物理常数；由于Abaqus没有内置单位，因此没有提供默认值。如果分析所需的物理常数未给出，Abaqus将发出致命错误消息。常数的单位必须与剩余输入数据一致。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**模型属性

##### **参考：**

- ["非耦合热传递分析，" Abaqus Analysis User's Guide第6.5.2节](../usb/usb-link.md#usb-anl-aheattransfer)
- ["质量扩散分析，" Abaqus Analysis User's Guide第6.9.1节](../usb/usb-link.md#usb-anl-amassdiffusion)
- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)
- ["率相关塑性：蠕变和膨胀，" Abaqus Analysis User's Guide第23.2.4节](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["扩散率，" Abaqus Analysis User's Guide第26.4.1节](../usb/usb-link.md#usb-mat-cdiffusivity)
- ["溶解度，" Abaqus Analysis User's Guide第26.4.2节](../usb/usb-link.md#usb-mat-csolubility)
- ["热接触属性，" Abaqus Analysis User's Guide第37.2.1节](../usb/usb-link.md#usb-cni-athermalinteraction)
- ["腔体辐射，" Abaqus Analysis User's Guide第41.1.1节](../usb/usb-link.md#usb-cni-acavityradiation)

### **可选参数：**

ABSOLUTE ZERO

将此参数设置为所选温度标度上的绝对零度。例如，如果分析使用摄氏度，则设置ABSOLUTE ZERO=273.15。

STEFAN BOLTZMANN

将此参数设置为Stefan Boltzmann常数。例如，在SI单位中STEFAN BOLTZMANN=5.669×10^8焦耳每秒平方米开尔文^4。

UNIVERSAL GAS CONSTANT

将此参数设置为通用气体常数。例如，在SI单位中UNIVERSAL GAS CONSTANT=8.31434焦耳每摩尔开尔文。

SPL REFERENCE PRESSURE

将此参数设置为用于计算声压级的参考压力。例如，在SI单位中对于空气SPL REFERENCE PRESSURE=20微帕斯卡。

**此选项没有关联的数据行。**