# *VIEW FACTOR OUTPUT





### *VIEW FACTOR OUTPUT在腔体辐射热传递分析中将辐射视角因子写入结果文件。

此选项用于将腔体辐射元素视角因子矩阵写入结果文件。此选项仅适用于包括腔体辐射的热传递分析。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步

##### **参考：**

- ["腔体辐射," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- ["输出," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **必需参数：**

CAVITY

将此参数设置为此输出请求所针对的腔体名称。

### **可选参数：**

FREQUENCY

将此参数设置为输出频率，以增量为单位。除非FREQUENCY=0，否则输出将始终在每个步的最后一个增量处写入。默认值为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

**此选项没有关联的数据行。**





