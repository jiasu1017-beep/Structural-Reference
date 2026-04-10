# *CONNECTOR DERIVED COMPONENT





### *CONNECTOR DERIVED COMPONENT在连接器单元中指定用户定义的组件。

此选项与[*CONNECTOR FRICTION](ch03abk43.md)和[*CONNECTOR POTENTIAL](ch03abk49.md)选项结合使用，根据需要多次使用，以从编号分量定义用户自定义分量。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["连接器行为"，Abaqus Analysis User's Guide第31.2.1节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["耦合行为的连接器函数"，Abaqus Analysis User's Guide第31.2.4节](../usb/usb-link.md#usb-elm-econnderivedandpotential)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR FRICTION](ch03abk43.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **必需参数：**

NAME

将此参数设置为将用于引用导出分量的标签。

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器导出分量定义中的场变量依赖项数。如果省略此参数，则假定连接器导出分量独立于场变量。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

EXTRAPOLATION

设置EXTRAPOLATION=CONSTANT（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，EXTRAPOLATION=LINEAR）以在独立变量的指定范围外使用常量外推。

设置EXTRAPOLATION=LINEAR以在独立变量的指定范围外使用线性外推。

INDEPENDENT COMPONENTS

设置INDEPENDENT COMPONENTS=POSITION（默认值）以指定导出分量定义中包含的相对位置分量的依赖关系。

设置INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION以指定导出分量定义中包含的本构相对运动分量的依赖关系。

OPERATOR

设置OPERATOR=NORM（默认值）以使用贡献分量平方和的平方根函数。

设置OPERATOR=MACAULEY SUM以使用Macaulay括号函数对每个贡献求和。

设置OPERATOR=SUM以直接对贡献分量求和。

REGULARIZE

此参数仅适用于Abaqus/Explicit分析。

设置REGULARIZE=ON（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，REGULARIZE=OFF）以正则化用户定义的表格连接器导出分量数据。

设置REGULARIZE=OFF以直接使用用户定义的表格连接器导出分量数据而不进行正则化。

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化连接器导出分量数据的容差。

如果省略此参数，默认值为RTOL=0.03，除非在[*CONNECTOR BEHAVIOR](ch03abk35.md)选项上指定了容差。

SIGN

设置SIGN=POSITIVE（默认值）以为导出分量定义提供整体正号。

设置SIGN=NEGATIVE以为导出分量定义提供整体负号。

### **如果省略INDEPENDENT COMPONENTS参数，则定义导出分量的数据行：**

**第一行：**

**后续行：**

不要重复第一数据行。根据需要重复后续数据行，以将导出分量的贡献定义为温度和场变量的函数。

### **如果包含INDEPENDENT COMPONENTS参数，则定义导出分量的数据行：**

**第一行：**

**第二行：**

**第三行：**

**延续行（如需要）：**

不要重复前两个数据行。根据需要重复后续数据行，以将导出分量的贡献定义为连接器相对位置或本构相对运动、温度和场变量的函数。




