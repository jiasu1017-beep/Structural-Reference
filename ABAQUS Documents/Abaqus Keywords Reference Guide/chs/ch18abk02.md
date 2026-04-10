# *SECTION FILE





### *SECTION FILE定义用户定义表面截面上的累积量结果文件请求。

此选项用于控制与用户定义截面相关联的累积量输出到结果文件。根据分析类型，输出可能包括以下一项或多项：与截面相关联的总力、总弯矩、总热通量、总电流、总质量流量或总孔隙流体体积流量。此选项不适用于特征频率提取、特征值屈曲预测、复特征频率提取或线性动力学过程。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步

##### **参考：**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)
- ["Abaqus/Standard output variable identifiers," Section 4.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-houtputvar)

### **必需参数：**

NAME

将此参数设置为用于标识截面输出的标签。同一输入文件中的截面名称必须唯一。

SURFACE

将此参数设置为在[*SURFACE](ch18abk47.md)选项中用于定义表面的名称。

### **可选参数：**

AXES

如果需要在局部坐标系中输出，则设置AXES=LOCAL。设置AXES=GLOBAL（默认）以在全局坐标系中输出量。

FREQUENCY

将此参数设置为输出频率，以增量计。除非FREQUENCY=0，否则输出始终在每个步的最后增量处打印。默认值为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

UPDATE

如果需要在原始局部坐标系中输出，则设置UPDATE=NO。设置UPDATE=YES（默认）以在随表面截面平均刚体运动旋转的局部坐标系中输出量。此参数仅在AXES=LOCAL且步骤中激活NLGEOM参数时相关。

### **可选数据行：**

**第一行：**

将此行留空以允许Abaqus定义锚点。

**第二行：**

将此行留空以允许Abaqus定义轴。

**第三行：**

对于AXES=GLOBAL或允许Abaqus为AXES=LOCAL定义锚点和轴，请省略第一行和第二行。根据需要重复第三行以定义要写入结果文件的变量。如果省略此行，则将输出所有适当的变量（["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)）。

**图18.2-1** 用户定义的局部坐标系。

![](../graphics/oprintfile-localsys-nls.png)




