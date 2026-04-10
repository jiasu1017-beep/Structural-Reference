# *CONNECTOR DAMAGE INITIATION





### *CONNECTOR DAMAGE INITIATION为连接器单元指定连接器损伤起始准则。

此选项用于为具有相对运动可用分量的连接器单元定义连接器损伤起始准则。它几乎总是与[*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["连接类型库"，Abaqus Analysis User's Guide第31.1.5节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["连接器行为"，Abaqus Analysis User's Guide第31.2.1节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器损伤行为"，Abaqus Analysis User's Guide第31.2.7节](../usb/usb-link.md#usb-elm-econndamagebehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md)
- [*CONNECTOR PLASTICITY](ch03abk48.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **可选参数：**

COMPONENT

将此参数设置为为连接器指定损伤起始准则的相对运动分量。请参见["连接类型库"，Abaqus Analysis User's Guide第31.1.5节](../usb/usb-link.md#usb-elm-econnectortypelibrary)，了解相对运动分量的定义。如果使用此参数，则[*CONNECTOR POTENTIAL](ch03abk49.md)选项不能与[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)选项结合使用。

省略此参数并使用[*CONNECTOR POTENTIAL](ch03abk49.md)选项与[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)选项结合，以指定涉及多个相对运动分量的连接器损伤起始准则。

CRITERION

设置CRITERION=FORCE（默认值）以指定基于连接器中总力/力矩的损伤起始准则。

设置CRITERION=MOTION以指定基于连接器中相对位移/旋转的损伤起始准则。

设置CRITERION=PLASTIC MOTION以指定基于由相关塑性定义定义的等效塑性相对运动的损伤起始准则。如果CRITERION=PLASTIC MOTION，则[*CONNECTOR POTENTIAL](ch03abk49.md)选项不能与[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)选项结合使用。

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器损伤起始准则定义中的场变量依赖项数。如果省略此参数，则假定连接器损伤起始准则独立于场变量。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

EXTRAPOLATION

设置EXTRAPOLATION=CONSTANT（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，EXTRAPOLATION=LINEAR）以在独立变量的指定范围外使用常量外推。

设置EXTRAPOLATION=LINEAR以在独立变量的指定范围外使用线性外推。

RATE FILTER FACTOR

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于过滤等效相对塑性运动率以评估率相关连接器损伤起始数据的因子。默认值为0.9。

RATE INTERPOLATION

此参数仅适用于Abaqus/Explicit分析，仅用于插值率相关连接器损伤起始数据。

设置RATE INTERPOLATION=LINEAR（默认值）以在使用对数率相关损伤起始数据进行插值时，对等效相对塑性运动率使用线性间隔。

设置RATE INTERPOLATION=LOGARITHMIC以在使用对数率相关损伤起始数据进行插值时，对等效相对塑性运动率使用对数间隔。

REGULARIZE

此参数仅适用于Abaqus/Explicit分析。

设置REGULARIZE=ON（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，REGULARIZE=OFF）以正则化用户定义的表格连接器损伤起始数据。

设置REGULARIZE=OFF以直接使用用户定义的表格连接器损伤起始数据而不进行正则化。

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化连接器损伤起始数据的容差。

如果省略此参数，默认值为RTOL=0.03，除非在[*CONNECTOR BEHAVIOR](ch03abk35.md)选项上指定了容差。

### **CRITERION=FORCE的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此数据行集，以将连接器损伤起始极限值定义为温度和其他预定义场变量的函数。

### **CRITERION=MOTION的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此数据行集，以将连接器损伤起始极限值定义为温度和其他预定义场变量的函数。

### **CRITERION=PLASTIC MOTION的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此数据行集，以将连接器损伤起始准则定义为模式混合比、等效塑性运动率、温度和其他预定义场变量的函数。




