# *SPECTRUM





### *SPECTRUM定义或创建响应谱。

此选项用于将动态事件转换为用于[*RESPONSE SPECTRUM](ch17abk15.md)分析的响应谱。您可以使用作为频率和阻尼函数的*S*值来定义响应谱，或从描述动态事件的用户指定幅值创建响应谱。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Amplitude工具集；仅支持用于定义响应谱。

##### **参考：**

- ["Response spectrum analysis," Section 6.3.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aresponsespectrum)
- [*RESPONSE SPECTRUM](ch17abk15.md)

### 使用作为频率和阻尼函数的S值定义响应谱

### **必需参数：**

NAME

将此参数设置为将用于引用响应谱的标签。此标签用于在[*RESPONSE SPECTRUM](ch17abk15.md)选项上交叉引用响应谱。

### **可选参数：**

G

将此参数设置为重力加速度值。此参数仅在指定TYPE=G时使用。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。有关此类文件名的语法，请参见["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。如果省略此参数，则假定数据跟随在关键字行之后。

TYPE

设置TYPE=DISPLACEMENT、TYPE=VELOCITY或TYPE=ACCELERATION（默认）以定义响应谱定义的单位。

设置TYPE=G以输入以*g*为单位的加速度谱。然后参数G定义重力加速度。

### **使用作为频率和阻尼函数的*S*值定义响应谱的数据行：**

**第一行：**

根据需要重复此数据行，以在每个阻尼值的所有频率处定义响应谱。

### 从用户指定的幅值创建响应谱

### **必需参数：**

CREATE

使用此参数来调用从用户指定幅值提供的动态事件构建响应谱。

AMPLITUDE

将此参数设置为描述用于创建响应谱的动态事件的幅值名称。

NAME

将此参数设置为将用于引用此创建响应谱的标签。此标签用于在[*RESPONSE SPECTRUM](ch17abk15.md)选项上交叉引用响应谱。

TIME INCREMENT

将此参数设置为用于构建此响应谱的隐式时间积分方案的时间增量。

### **可选参数：**

G

将此参数设置为重力加速度值。当指定TYPE=G或EVENT TYPE=G时使用此参数。

TYPE

设置TYPE=DISPLACEMENT、TYPE=VELOCITY或TYPE=ACCELERATION（默认）以定义创建响应谱的单位。

设置TYPE=G以创建以*g*为单位的加速度谱。然后参数G定义重力加速度。

ABSOLUTE

此参数仅与加速度谱相关。使用此参数请求创建绝对加速度谱（如果省略ABSOLUTE和RELATIVE参数，则为默认）。

RELATIVE

此参数仅与加速度谱相关。使用此参数请求创建相对加速度谱。

DAMPING GENERATE

使用此参数请求生成包含将创建响应谱的临界阻尼比例的列表。

EVENT TYPE

设置EVENT TYPE=DISPLACEMENT、EVENT TYPE=VELOCITY或EVENT TYPE=ACCELERATION（默认）以定义幅值定义的单位。

设置EVENT TYPE=G以输入以*g*为单位的加速度幅值。然后参数G定义重力加速度。

FILE

将此参数设置为包含创建响应谱数据的备用输出文件名称。此数据文件的每一行将包含响应谱的幅值、使用此幅值的频率（以每时间周期计）以及以临界阻尼比例给出的相关阻尼。有关此类文件名的语法，请参见["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。如果省略此参数，则假定创建的响应谱只能用于相同或重启作业的后续响应谱过程。

### **从用户指定幅值创建响应谱的数据行：**

**第一行：**

**如果省略DAMPING GENERATE参数时的第二行：**

**如果包含DAMPING GENERATE参数时的第二行：**




