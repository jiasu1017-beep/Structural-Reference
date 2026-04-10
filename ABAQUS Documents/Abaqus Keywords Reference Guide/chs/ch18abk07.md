# *SELECT CYCLIC SYMMETRY MODES





### *SELECT CYCLIC SYMMETRY MODES在循环对称结构的特征值分析中指定循环对称模式。

此选项用于指定在特征值分析中应使用哪些循环对称模式。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Analysis of models that exhibit cyclic symmetry," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- [*CYCLIC SYMMETRY MODEL](ch03abk92.md)
- [*TIE](ch19abk06.md)

### **可选参数：**

EVEN

包含此参数以仅请求偶数循环对称模式。如果省略此参数，则将在NMIN、NMAX范围内使用所有循环对称模式。

NMIN

将此参数设置为最低循环对称模式号。默认值为0。

NMAX

将此参数设置为最高循环对称模式号。默认值是[*CYCLIC SYMMETRY MODEL](ch03abk92.md)选项中给出的扇区数所能实现的最高编号。

**此选项没有关联的数据行。**




