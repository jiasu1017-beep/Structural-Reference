# *CONNECTOR BEHAVIOR





### *CONNECTOR BEHAVIOR开始连接器行为的规范。

此选项用于指示连接器行为定义的开始。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["连接器行为"，Abaqus Analysis User's Guide第31.2.1节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- [*CONNECTOR SECTION](ch03abk50.md)

### **必需参数：**

NAME

将此参数设置为[*CONNECTOR SECTION](ch03abk50.md)选项上引用的行为名称。同一输入文件中的连接器行为名称必须唯一。

### **可选参数：**

EXTRAPOLATION

此处定义的插值选择适用于连接器行为的所有子选项，除非在子选项上重新定义。

设置EXTRAPOLATION=CONSTANT（默认值）以在独立变量的指定范围外使用常量外推。

设置EXTRAPOLATION=LINEAR以在独立变量的指定范围外使用线性外推。

INTEGRATION

此参数仅适用于Abaqus/Explicit分析。

设置INTEGRATION=IMPLICIT（默认值）以使用隐式时间积分进行连接器行为积分。

设置INTEGRATION=EXPLICIT以使用显式时间积分进行连接器行为积分。

REGULARIZE

此参数仅适用于Abaqus/Explicit分析。此处定义的正则化选择适用于连接器行为的所有子选项，除非在子选项上重新定义。

设置REGULARIZE=ON（默认值）以正则化用户定义的表格连接器行为数据。

设置REGULARIZE=OFF以直接使用用户定义的表格连接器行为数据而不进行正则化。

RTOL

此参数仅适用于Abaqus/Explicit分析。此处定义的正则化容差适用于连接器行为的所有子选项，除非在子选项上重新定义。

将此参数设置为用于正则化连接器行为数据的容差。默认值为RTOL=0.03。

**此选项没有关联的数据行。**




