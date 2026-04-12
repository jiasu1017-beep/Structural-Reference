# N







### native mesh

零件实例的网格化表示。您可以使用 Abaqus/CAE Mesh 模块通过离散几何来创建本机网格。您可以使用 Mesh 模块对在装配中定位的本机零件进行网格划分。本机网格及其属性是基于特征的，本机网格保持与其原始零件和装配的关联。
更多信息：- [「什么是基于特征的建模？，」Abaqus/CAE User's Guide 第 11.3 节](../usi/usi-link.md#usi-prt-concepts)

### native part

使用 Abaqus/CAE Part 模块创建的零件。Abaqus/CAE 以有序特征列表的形式存储每个本机零件。定义每个特征的参数——拉伸深度、孔径、扫描路径等——定义了零件的几何。
更多信息：- [「什么是基于特征的建模？，」Abaqus/CAE User's Guide 第 11.3 节](../usi/usi-link.md#usi-prt-concepts)

### NLGEOM

[geometric nonlinearity](gl01gls08.md#gls-geometricnonlinear) 的缩写。

### node set

节点的命名集合。
更多信息：- [「节点定义，」Abaqus Analysis User's Guide 第 2.1.1 节](../usb/usb-link.md#usb-int-inode)

- [第 73 章，「The Set and Surface toolsets，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### non-manifold edge

两个以上外元素面交汇处的外元素边。您可以使用 Abaqus/CAE Mesh 模块中的 Query toolset 来突出显示实体或壳网格中的自由和非流形网格边。非流形边可能表示问题，尤其是在实体网格中。
更多信息：- [「获取网格信息，」Abaqus/CAE User's Guide 第 17.19.2 节](../usi/usi-link.md#usi-mgn-querymesh)

### normal axis

每个本机或孤立网格元素质心处的空间变化方向。[离散方向](gl01gls05.md#gls-discreteorient) 的 normal axis 代表材料方向的主法线方向。Abaqus/CAE 使用 normal axis 和 [primary axis](gl01gls17.md#gls-primaryaxis) 构建右手笛卡尔坐标系。您选择要在结果方向中表示 normal axis 的坐标系轴，并选择拓扑或基准或输入向量值来定义所需的轴。
更多信息：- [「将离散方向用于材料方向和复合铺层方向，」Abaqus/CAE User's Guide 第 12.16 节](../usi/usi-link.md#usi-prp-discrete-orient)



