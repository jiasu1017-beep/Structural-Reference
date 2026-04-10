# *VISCOSITY





### *VISCOSITY指定材料剪切粘度。

此选项用于指定材料的剪切粘度。在Abaqus/Explicit中使用时，必须与[*EOS](ch05abk27.md)选项一起使用。

**产品：**Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["粘度," Section 26.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cviscosity)
- ["状态方程," Section 25.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ceos)
- ["VUVISCOSITY," Section 1.2.24 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuviscosity)

- [*EOS](ch05abk27.md)
- [*TRS](ch19abk16.md)

### **可选参数：**

DEFINITION

使用此参数选择材料的剪切粘度。

设置DEFINITION=CARREAU-YASUDA以定义Carreau-Yasuda粘性剪切行为。

设置DEFINITION=CROSS以定义Cross粘性剪切行为。

设置DEFINITION=ELLIS-METER以定义Ellis-Meter粘性剪切行为。

设置DEFINITION=HERSCHEL-BULKLEY以定义Herschel-Bulkley粘性剪切行为。

设置DEFINITION=NEWTONIAN（默认）以定义牛顿（线性）粘性剪切行为。

设置DEFINITION=POWELL-EYRING以定义Powell-Eyring粘性剪切行为。

设置DEFINITION=POWER LAW以定义幂律粘性剪切行为。

设置DEFINITION=TABULAR以表格形式定义非牛顿粘性剪切行为。

设置DEFINITION=USER（仅限Abaqus/Explicit）以在用户子程序[`VUVISCOSITY`](../sub/sub-link.md#sub-xsl-vuviscosity)中定义粘性剪切行为。

DEPENDENCIES

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为除了温度之外粘度定义中包含的场变量依赖项数。如果省略此参数，则假定粘度仅取决于温度。

PROPERTIES

此参数仅在指定DEFINITION=USER时才能使用。

将此参数设置为在用户子程序[`VUVISCOSITY`](../sub/sub-link.md#sub-xsl-vuviscosity)中所需的数据属性值数量。默认值为0。

### **定义Carreau-Yasuda粘性剪切行为的数据行（DEFINITION=CARREAU-YASUDA）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此组数据行，以将Carreau-Yasuda粘度模型的系数定义为温度和其他预定义场变量的函数。

### **定义Cross粘性剪切行为的数据行（DEFINITION=CROSS）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以将Cross粘度模型的系数定义为温度和其他预定义场变量的函数。

### **定义Ellis-Meter粘性剪切行为的数据行（DEFINITION=ELLIS-METER）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以将Ellis-Meter粘度模型的系数定义为温度和其他预定义场变量的函数。

### **定义Herschel-Bulkley粘性剪切行为的数据行（DEFINITION=HERSCHEL-BULKLEY）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以将Herschel-Bulkley粘度模型的系数定义为温度和其他预定义场变量的函数。

### **定义牛顿粘性剪切行为的数据行（DEFINITION=NEWTONIAN）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将粘度定义为温度和其他预定义场变量的函数。

### **定义Powell-Eyring粘性剪切行为的数据行（DEFINITION=POWELL-EYRING）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将Powell-Eyring粘度模型的系数定义为温度和其他预定义场变量的函数。

### **定义幂律粘性剪切行为的数据行（DEFINITION=POWER LAW）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以将幂律粘度模型的系数定义为温度和其他预定义场变量的函数。

### **以表格形式定义粘性剪切行为的数据行（DEFINITION=TABULAR）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将粘度定义为本有效剪切应变率、温度和其他预定义场变量的函数。

### **为用户定义的粘度模型定义材料属性的数据行（DEFINITION=USER）：**

**如果PROPERTIES参数被省略或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行，以定义材料属性。





