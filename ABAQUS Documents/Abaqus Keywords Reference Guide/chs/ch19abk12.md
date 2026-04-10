# *TRANSPORT VELOCITY





### *TRANSPORT VELOCITY指定角度传输速度。

此选项用于在稳态传输分析期间定义通过可变形体网格传输的材料的角速度，或相对于刚性体参考节点的材料传输速度。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步

##### **参考：**

- ["稳态传输分析," Section 6.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatetransport)
- ["对称模型生成," Section 10.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaximodelgen)
- ["UMOTION," Section 1.1.44 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-umotion)

### **可选参数：**

AMPLITUDE

将此参数设置为幅度曲线（在[*AMPLITUDE](ch01abk09.md)选项中定义）的名称，该曲线给出整个步中速度随时间的变化（["幅度曲线," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)）。

如果省略此参数，则根据[*STEP](ch18abk36.md)选项上AMPLITUDE参数分配的值，参考幅值将在步开始时立即应用或在整个步中线性应用（参见["定义分析," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)）。

USER

包含此参数以指示旋转速度的大小将在用户子程序[`UMOTION`](../sub/sub-link.md#sub-xsl-umotion)中定义。如果使用此参数，则数据行定义的任何大小都可以在用户子程序中重新定义。

### **定义旋转运动的数据行：**

**第一行：**

根据需要重复此数据行，以定义模型不同部分节点上的旋转运动。





