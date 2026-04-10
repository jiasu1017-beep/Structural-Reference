# *REBAR LAYER







### *REBAR LAYER在膜、壳、表面和连续单元中定义钢筋层。

此选项用于在膜、壳和表面单元中定义一层或多层钢筋。它必须与[*MEMBRANE SECTION](ch13abk16.md)、[*SHELL SECTION](ch18abk15.md)或[*SURFACE SECTION](ch18abk54.md)选项结合使用。实体（连续）单元中的钢筋层可以通过使用[*EMBEDDED ELEMENT](ch05abk14.md)选项，将具有钢筋层的表面或膜单元集嵌入宿主连续单元集中来定义。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**零件，零件实例  

**Abaqus/CAE：**属性模块；仅支持膜和壳单元。

##### **参考：**

- ["定义钢筋，" Abaqus Analysis User's Guide第2.2.3节](../usb/usb-link.md#usb-int-erebarlayer)
- ["嵌入单元，" Abaqus Analysis User's Guide第35.4.1节](../usb/usb-link.md#usb-cni-pembeddedelement)
- [*EMBEDDED ELEMENT](ch05abk14.md)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*SHELL SECTION](ch18abk15.md)
- [*SURFACE SECTION](ch18abk54.md)

### **可选参数：**

GEOMETRY

使用此参数指定钢筋几何类型。

如果单元中钢筋间距恒定，则设置GEOMETRY=CONSTANT（默认）。间距在数据行上以长度单位给出。

如果钢筋间距作为距圆柱坐标系中旋转轴距离的线性函数而增加，则设置GEOMETRY=ANGULAR。间距在数据行上以角度间距（度）给出。如果此选项与三维膜、壳或表面单元一起使用，则必须定义圆柱方向系统。

如果单元中钢筋间距和方向由轮胎"提升"方程决定，则设置GEOMETRY=LIFT EQUATION。钢筋参数是相对于未硫化或"生"轮胎构型定义的，提升方程将钢筋参数映射到硫化轮胎构型。间距在数据行上以长度单位给出。如果此选项与三维膜、壳或表面单元一起使用，则必须定义圆柱方向系统。

ORIENTATION

此参数仅对一般壳、膜和表面单元中的钢筋有意义。将此参数设置为在数据行上定义钢筋角度方向的方向定义名称。如果省略此参数，则数据行上钢筋的角度方向是相对于默认投影局部表面方向指定的。此参数不允许与轴对称壳、轴对称膜和轴对称表面单元一起使用。

### **定义钢筋层的数据行：**

**第一行：**

根据需要重复此数据行。每行定义一层钢筋。
