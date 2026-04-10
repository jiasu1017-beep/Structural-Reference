# *ELEMENT









### *ELEMENT通过给出节点来定义单元。

此选项用于通过指定节点的直接方式定义单元。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**部件，部件实例，装配

**Abaqus/CAE：**网格模块

##### **参考：**

- ["单元定义，" Abaqus分析用户指南第2.2.1节](../usb/usb-link.md#usb-int-ielement)

### **必需参数：**

TYPE

将此参数设置为单元类型，如Abaqus分析用户指南[第六部分，"单元"](../usb/usb-link.md#usbechapter)中所定义。

对于用户单元，请指定U*n*类型标识（请参见["用户定义单元，" Abaqus分析用户指南第32.15.1节](../usb/usb-link.md#usb-elm-euserelem)）。[*USER ELEMENT](ch20abk07.md)选项也必须出现在同一输入文件中。

对于子结构，请指定Z*n*类型标识（请参见["使用子结构，" Abaqus分析用户指南第10.1.1节](../usb/usb-link.md#usb-anl-asuperelements)）。

### **可选参数：**

ELSET

将此参数设置为这些单元将被分配到的单元集名称。

FILE

此参数仅适用于Abaqus/Standard分析。

此参数仅对子结构有意义。将此参数设置为子结构所在的子结构库的名称（不带扩展名）。请参见["输入语法规则，" Abaqus分析用户指南第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，获取此类库名称的语法。如果未指定名称，则使用默认名称（请参见["使用子结构，" Abaqus分析用户指南第10.1.1节](../usb/usb-link.md#usb-anl-asuperelements)）。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。请参见["输入语法规则，" Abaqus分析用户指南第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，获取此类文件名的语法。如果省略此参数，则假定数据跟随在关键字行之后。

OFFSET

当[*ELEMENT](ch05abk07.md)选项用于在Abaqus/Standard中定义具有非对称变形的轴对称单元的连通性时，将此参数设置为一个正偏移数，用于指定连通性中需要的额外节点（请参见["单元定义，" Abaqus分析用户指南第2.2.1节](../usb/usb-link.md#usb-int-ielement)，获取更多信息）。默认值为OFFSET=100000。

当[*ELEMENT](ch05abk07.md)选项用于在Abaqus/Standard中定义垫片单元或内聚单元的连通性时，将OFFSET参数设置为一个正偏移数，用于在仅明确指定部分单元节点时定义单元的其余节点。如果省略此参数，则必须在数据行上指定整个垫片或内聚单元的连通性（请参见["定义垫片单元的初始几何形状，" Abaqus分析用户指南第32.6.4节](../usb/usb-link.md#usb-elm-egasketinit)，和["定义内聚单元的初始几何形状，" Abaqus分析用户指南第32.5.4节](../usb/usb-link.md#usb-elm-ecohesiveinit)）。

SOLID ELEMENT NUMBERING

此参数仅适用于Abaqus/Standard分析。

此参数仅在[*ELEMENT](ch05abk07.md)选项用于定义垫片单元时使用。使用此参数使用等效实体单元的节点排序来指定垫片单元的连通性。将其设置为对应于垫片单元第一面（SNEG）的等效实体面的面号。如果此参数没有赋值，则假定实体单元的第一面（S1）对应于垫片单元的第一面。

### **定义单元的数据行：**

**第一行：**

每种单元类型的节点顺序（单元的连通性）在Abaqus分析用户指南[第六部分，"单元"](../usb/usb-link.md#usbechapter)中给出。

**续行（仅在前一行以逗号结尾时需要）：**

根据需要重复此组数据行，每行最多16个整数值（最多80个字符）。




