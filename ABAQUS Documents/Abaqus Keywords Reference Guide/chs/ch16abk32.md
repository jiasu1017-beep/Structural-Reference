# *PSD-DEFINITION







### *PSD-DEFINITION定义随机响应载荷的交叉谱密度频率函数。

此选项用于定义频率函数，以便在[*CORRELATION](ch03abk77.md)选项中引用，从而在[*RANDOM RESPONSE](ch17abk07.md)分析过程中定义随机载荷的频率依赖性。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**模型  

##### **参考：**

- ["随机响应分析，" Abaqus Analysis User's Guide第6.3.11节](../usb/usb-link.md#usb-anl-arandomresponse)
- ["UPSD，" Abaqus User Subroutines Reference Guide第1.1.48节](../sub/sub-link.md#sub-rtn-uupsd)
- [*CORRELATION](ch03abk77.md)
- [*RANDOM RESPONSE](ch17abk07.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此频率函数。

### **可选参数：**

DB REFERENCE

将此参数设置为参考功率值，单位为（载荷单位）^2。当频率函数以分贝单位给出时（TYPE=DB），需要此参数。

G

将此参数设置为参考重力加速度；例如，9.81 m/s^2。默认为G=1.0。此参数只能与TYPE=BASE一起使用。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。请参阅["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟在关键字行之后。

TYPE

如果此频率函数将用于定义基础运动，则设置TYPE=BASE。

如果此频率函数直接以功率单位给出，则设置TYPE=FORCE（默认）。

如果此频率函数以分贝单位定义（见下文），则设置TYPE=DB。此选项不能与USER参数一起使用。

USER

如果频率函数在用户子程序[`UPSD`](../sub/sub-link.md#sub-xsl-upsd)中定义，则包含此参数。如果包含此参数，则不需要数据行。

### **TYPE=BASE或TYPE=FORCE的数据行：**

**第一行：**

根据需要重复此数据行以定义频率函数。

### **TYPE=DB的数据行：**

**第一行：**

根据需要重复此数据行以分贝为单位定义频率函数。

### **通过用户子程序定义频率函数（包含USER参数）：**

如果指定了USER参数，则此选项不使用数据行。相反，必须使用用户子程序[`UPSD`](../sub/sub-link.md#sub-xsl-upsd)来定义频率函数。
