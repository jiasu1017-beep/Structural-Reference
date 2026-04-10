# *NODAL THICKNESS









### *NODAL THICKNESS在节点处定义壳或膜厚度。

此选项用于在节点基础上定义可变的壳或膜厚度。除非在[*SHELL GENERAL SECTION](ch18abk14.md)或[*SHELL SECTION](ch18abk15.md)选项（对于壳单元）或[*MEMBRANE SECTION](ch13abk16.md)选项（对于膜单元）上包含了NODAL THICKNESS参数，否则此选项定义的厚度数据将被忽略。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["节点厚度，" Abaqus Analysis User's Guide第2.1.3节](../usb/usb-link.md#usb-int-inodalthickness)
- ["膜单元，" Abaqus Analysis User's Guide第29.1.1节](../usb/usb-link.md#usb-elm-emembrane)
- ["使用在分析期间集成的壳截面定义截面行为，" Abaqus Analysis User's Guide第29.6.5节](../usb/usb-link.md#usb-elm-eusingshellsection)
- ["使用通用壳截面定义截面行为，" Abaqus Analysis User's Guide第29.6.6节](../usb/usb-link.md#usb-elm-eusingshellgensect)
- ["用于建模壳中部分穿透裂纹的线弹簧单元，" Abaqus Analysis User's Guide第32.9.1节](../usb/usb-link.md#usb-elm-elinespring)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)

### **可选参数：**

GENERATE

包含此参数以在两个边界节点或节点集之间插值厚度。边界节点或节点集的厚度必须先前已定义。如果节点集具有不同数量的节点，则忽略较长集合中的额外节点。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。如果省略此参数，则假定数据在关键字行之后。

### **省略GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行以定义壳或膜厚度的变化。

### **包含GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行以定义厚度的变化。