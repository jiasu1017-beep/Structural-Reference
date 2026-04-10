# *SELECT EIGENMODES





### *SELECT EIGENMODES选择用于模态动态、复特征值提取或子结构生成分析的模式。

此选项选择用于基于模式的动态分析、复特征值提取分析或子结构生成分析的模式。每个步只能使用一个选项。如果在基于模式的动态分析或复特征值提取分析中省略此选项，则将使用在前一个[*FREQUENCY](ch06abk35.md)步中提取的所有模式，包括如果被激活的残余模式。

如果在子结构生成分析中省略此选项，则将不使用在前一个[*FREQUENCY](ch06abk35.md)步中提取的任何模式，包括如果被激活的残余模式。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**仅在子结构生成的Step模块中支持。

##### **参考：**

- ["Implicit dynamic analysis using direct integration," Section 6.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamic)
- ["Complex eigenvalue extraction," Section 6.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acomplexfreqextract)
- ["Transient modal dynamic analysis," Section 6.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amodaldynamic)
- ["Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn)
- ["Subspace-based steady-state dynamic analysis," Section 6.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdynsubspace)
- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)
- ["Response spectrum analysis," Section 6.3.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aresponsespectrum)
- ["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)
- [*MODAL DAMPING](ch13abk17.md)

### **可选参数：**

DEFINITION

设置DEFINITION=MODE NUMBERS（默认）以指示所选模式以模式号集合的形式给出。

设置DEFINITION=FREQUENCY RANGE以指示模式从指定的频率范围（包括频率边界）中选择。频率范围可以是不连续的。

如果[*MODAL DAMPING](ch13abk17.md)和[*SELECT EIGENMODES](ch18abk07.md)选项在同一步中使用，则DEFINITION参数必须在两个选项中设置为相同的值。

GENERATE

如果包含此参数，则每个数据行应给出一个起始模式 ![](../graphics/key_eqn00707.gif)；一个结束模式 ![](../graphics/key_eqn00708.gif)；以及这些模式之间模式号的增量 *i*。然后所有从 ![](../graphics/key_eqn00707.gif) 到 ![](../graphics/key_eqn00708.gif) 以 *i* 为步长的模式将被添加到集合中。*i* 必须是一个整数，使得 ![](../graphics/key_eqn00926.gif) 是一个整数（不是分数）。

此参数只能与DEFINITION=MODE NUMBERS一起使用。

### **如果DEFINITION=MODE NUMBERS且省略GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许16个条目。

### **如果DEFINITION=MODE NUMBERS且包含GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行。

### **如果DEFINITION=FREQUENCY RANGE时的数据行：**

**第一行：**

根据需要重复此数据行。




