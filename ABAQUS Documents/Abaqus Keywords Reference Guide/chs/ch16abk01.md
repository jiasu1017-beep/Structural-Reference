# *PARAMETER









### *PARAMETER定义输入参数化的参数。

此选项用于定义可用来替代Abaqus输入量的参数。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例、装配、模型、步骤

##### **参考：**

- ["参数化输入，" Abaqus Analysis User's Guide第1.4.1节](../usb/usb-link.md#usb-int-iparinput)
- ["参数化形状变化，" Abaqus Analysis User's Guide第2.1.2节](../usb/usb-link.md#usb-int-iparshapevar)

### **定义表格依赖参数的可选关键字参数（如果指定了其中任何一个，则必须全部指定）：**

DEPENDENT

将此关键字参数设置为此选项中定义的依赖参数列表。该列表必须以括号内的参数名称给出，用逗号分隔；例如，`(depPar1, depPar2, depPar3)`。

INDEPENDENT

将此关键字参数设置为此选项中使用的独立参数列表。该列表必须以括号内的参数名称给出，用逗号分隔；例如，`(indPar1, indPar2, indPar3)`。

TABLE

将此关键字参数设置为由[*PARAMETER DEPENDENCE](ch16abk02.md)选项定义的参数依赖表的名称，该表定义此选项中依赖参数和独立参数之间的关系。

### **如果省略了DEPENDENT、INDEPENDENT和TABLE关键字参数，则定义独立参数或表达式依赖参数的数据行：**

**第一行：**

根据需要重复此数据行以定义独立和表达式依赖参数。此数据行上给出的数据不能被参数化。