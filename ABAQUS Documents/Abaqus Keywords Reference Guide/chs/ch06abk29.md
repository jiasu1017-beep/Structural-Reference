# *FLUID INFLATOR PROPERTY





### *FLUID INFLATOR PROPERTY定义流体充气机属性。

此选项用于定义流体充气机属性以建模气囊展开。

**产品：**Abaqus/Explicit   

**类型：**模型数据  

**级别：**部件，部件实例  

##### **参考：**

- ["充气机定义，" Abaqus Analysis User's Guide第11.5.4节](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID INFLATOR](ch06abk26.md)

### **必需参数：**

EFFECTIVE AREA

此参数仅与TYPE=DUAL PRESSURE和TYPE=PRESSURE AND MASS相关。

将此参数设置为充气机孔口的总面积。

NAME

将此参数设置为用于引用流体充气机属性的标签。

TANK VOLUME

此参数仅与TYPE=DUAL PRESSURE或TYPE=TANK TEST相关。

将此参数设置为罐体体积。

TYPE

设置TYPE=DUAL PRESSURE以使用双压力方法获取气体种类的质量流率。

设置TYPE=PRESSURE AND MASS以使用给定的质量流率和充气机压力获取气体温度。

设置TYPE=TANK TEST以使用罐体测试数据获取气体种类的质量流率。

设置TYPE=TEMPERATURE AND MASS以使用给定的质量流率和充气机气体温度获取气体压力。

### **可选参数：**

DISCHARGE COEFFICIENT

此参数仅与TYPE=DUAL PRESSURE和TYPE=PRESSURE AND MASS相关。

将此参数设置为充气机孔口的排放系数。默认值为0.4。

### **TYPE=DUAL PRESSURE的数据行：**

**第一行：**

根据需要重复此数据行，以将充气机压力和罐体压力定义为充气时间的函数。

### **TYPE=PRESSURE AND MASS的数据行：**

**第一行：**

根据需要重复此数据行，以将充气机压力和充气机质量流率定义为充气时间的函数。

### **TYPE=TANK TEST的数据行：**

**第一行：**

根据需要重复此数据行，以将充气机气体温度和罐体压力定义为充气时间的函数。

### **TYPE=TEMPERATURE AND MASS的数据行：**

**第一行：**

根据需要重复此数据行，以将充气机气体温度和充气机质量流率定义为充气时间的函数。
