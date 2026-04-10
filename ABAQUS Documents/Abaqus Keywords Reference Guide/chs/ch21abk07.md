# *VISCOUS





### *VISCOUS为双层粘塑性模型指定粘性材料属性。

此选项用于定义双层粘塑性材料模型的粘性属性。它必须与[*ELASTIC](ch05abk03.md)和[*PLASTIC](ch16abk14.md)选项一起使用。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["双层粘塑性," Section 23.2.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cviscous)
- [*ELASTIC](ch05abk03.md)
- [*PLASTIC](ch16abk14.md)
- [*POTENTIAL](ch16abk24.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外材料属性定义中包含的场变量依赖项数。如果省略此参数，则假定材料属性仅取决于温度。请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

LAW

设置LAW=STRAIN（默认）以选择应变硬化幂律。

设置LAW=TIME以选择时间硬化幂律。

设置LAW=USER以使用用户子程序[`CREEP`](../sub/sub-link.md#sub-xsl-creep)输入蠕变定律。

设置LAW=ANAND以选择Anand定律。

设置LAW=DARVEAUX以选择Darveaux定律。

设置LAW=DOUBLE POWER以选择双幂律。

TIME

此参数仅在LAW=TIME时才相关。

设置TIME=CREEP以在时间硬化关系中使用蠕变时间。

设置TIME=TOTAL（默认）以在时间硬化关系中使用总时间。

### **对于LAW=TIME或LAW=STRAIN的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以将粘性常数定义为温度和其他预定义场变量的函数。

### **对于LAW=USER的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于七时需要）：**

根据需要重复此组数据行，以将粘性常数定义为温度和其他预定义场变量的函数。

### **对于LAW=ANAND的数据行：**

**第一行：**

**第二行：**

### **对于LAW=DARVEAUX的数据行：**

**第一行：**

### **对于LAW=DOUBLE POWER的数据行：**

**第一行：**





