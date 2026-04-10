# *UNLOADING DATA





### *UNLOADING DATA为连接器中的单轴行为模型提供卸载数据，或为织物提供单轴和剪切试验的卸载数据。

此选项用于在与[*CONNECTOR BEHAVIOR](ch03abk35.md)、[*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md)和[*LOADING DATA](ch12abk03.md)选项结合使用时，定义连接器单元单轴行为的卸载响应。

此选项用于在与[*FABRIC](ch06abk01.md)、[*UNIAXIAL](ch20abk03.md)和[*LOADING DATA](ch12abk03.md)选项结合使用时，定义织物材料单轴或剪切试验的卸载响应。织物单轴试验沿指定纱线方向以递增应变指定。织物剪切试验随着纬纱和经纱相互旋转，以递增剪切应变指定。

**产品：**Abaqus/Explicit

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["连接器单轴行为," Section 31.2.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnuniaxialbehav)
- ["织物材料行为," Section 23.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfabric)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md)
- [*FABRIC](ch06abk01.md)
- [*LOADING DATA](ch12abk03.md)
- [*UNIAXIAL](ch20abk03.md)

### 定义连接器中单轴行为的卸载响应

### **必需参数：**

DEFINITION

设置DEFINITION=COMBINED以基于指定的卸载曲线和过渡斜率定义卸载路径，从加载过渡到卸载曲线。

设置DEFINITION=EXPONENTIAL以定义指数卸载路径。

设置DEFINITION=INTERPOLATED CURVE以基于指定卸载曲线之间的插值定义卸载路径。

设置DEFINITION=QUADRATIC以定义二次卸载路径。

设置DEFINITION=SHIFTED CURVE以基于将指定的卸载曲线移动到卸载点来定义卸载路径。

### **可选参数：**

RATE DEPENDENT

包含此参数以定义率相关卸载数据。如果省略此参数，则假定数据是率无关的。此参数仅在加载数据是弹性和率相关时才能使用。

### **对于DEFINITION=COMBINED的数据行，用于定义不依赖于独立分量的率无关卸载行为：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

不要重复第一数据行。根据需要重复后续数据行，以定义卸载曲线数据。

### **对于DEFINITION=COMBINED的数据行，用于定义依赖于独立分量的率无关卸载行为：**

**第一行：**

**第二行：**

不要重复第一数据行。根据需要重复后续数据行，以定义卸载曲线数据。

### **对于DEFINITION=EXPONENTIAL和DEFINITION=QUADRATIC的数据行：**

**第一行（也是唯一行）：**

### **对于DEFINITION=INTERPOLATED CURVE和DEFINITION=SHIFTED CURVE的数据行，用于定义不依赖于独立分量的率无关卸载行为（省略RATE DEPENDENT参数）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义卸载曲线数据。

### **对于DEFINITION=INTERPOLATED CURVE和DEFINITION=SHIFTED CURVE的数据行，用于定义依赖于独立分量的率无关卸载行为（省略RATE DEPENDENT参数）：**

**第一行：**

根据需要重复此组数据行，以定义卸载曲线数据。

### **对于DEFINITION=INTERPOLATED CURVE的数据行，用于定义不依赖于独立分量的率相关卸载行为（包含RATE DEPENDENT参数）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以定义卸载曲线数据。

### **对于DEFINITION=INTERPOLATED CURVE的数据行，用于定义依赖于独立分量的率相关卸载行为（包含RATE DEPENDENT参数）：**

**第一行：**

根据需要重复此组数据行，以定义卸载曲线数据。

### 定义织物材料单轴试验的卸载响应数据

### **必需参数：**

DEFINITION

设置DEFINITION=COMBINED以基于指定的卸载曲线和过渡斜率定义卸载路径，从加载过渡到卸载曲线。

设置DEFINITION=EXPONENTIAL以定义指数卸载路径。

设置DEFINITION=INTERPOLATED CURVE以基于指定卸载曲线之间的插值定义卸载路径。

设置DEFINITION=QUADRATIC以定义二次卸载路径。

设置DEFINITION=SHIFTED CURVE以基于将指定的卸载曲线移动到卸载点来定义卸载路径。

可用的卸载路径类型取决于分配给测试数据的行为类型（如[*LOADING DATA](ch12abk03.md)选项所定义）。

### **可选参数：**

RATE DEPENDENT

包含此参数以定义率相关卸载数据。如果省略此参数，则假定数据是率无关的。此参数仅在加载数据是弹性和率相关时才能使用。

### **对于DEFINITION=COMBINED的数据行：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

不要重复第一数据行。根据需要重复后续数据行，以定义卸载曲线数据。

### **对于DEFINITION=EXPONENTIAL和DEFINITION=QUADRATIC的数据行：**

**第一行（也是唯一行）：**

### **对于DEFINITION=INTERPOLATED CURVE和DEFINITION=SHIFTED CURVE的数据行，用于定义单轴率无关卸载行为（省略RATE DEPENDENT参数）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义卸载曲线数据。

### **对于DEFINITION=INTERPOLATED CURVE的数据行，用于定义单轴率相关卸载行为（包含RATE DEPENDENT参数）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以定义卸载曲线数据。





