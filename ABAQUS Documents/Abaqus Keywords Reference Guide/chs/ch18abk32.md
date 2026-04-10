# *STEADY STATE CRITERIA





### *STEADY STATE CRITERIA指定终止准静态单向模拟的稳态准则。

此选项用于指定必须满足的范数，以基于达到稳态条件来终止准静态单向模拟。它必须与[*STEADY STATE DETECTION](ch18abk33.md)选项配合使用。

**产品：**Abaqus/Explicit

**类型：**历史数据

**级别：**步

##### **参考：**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- ["Steady-state detection," Section 11.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatedetection)
- [*STEADY STATE DETECTION](ch18abk33.md)

**此选项没有关联的参数。**

### **定义稳态检测范数SSPEEQ和SSSPRD的数据行：**

**第一行：**

根据需要重复此数据行。每一行定义一个必须满足才能达到稳态的准则。

### **定义稳态检测范数SSFORC和SSTORQ的数据行：**

**第一行：**

根据需要重复此数据行。每一行定义一个必须满足才能达到稳态的准则。




