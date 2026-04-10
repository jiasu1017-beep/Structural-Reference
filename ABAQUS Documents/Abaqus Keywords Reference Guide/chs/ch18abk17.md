# *SHELL SECTION





### *SHELL SECTION指定壳截面。

此选项用于指定壳截面。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)
- ["Using a shell section integrated during the analysis to define the section behavior," Section 29.6.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingshellsection)

### **必需参数：**

ELSET

将此参数设置为包含要定义截面行为的壳单元的单元集名称。

### **必需的互斥参数：**

COMPOSITE

如果壳由几层材料组成，则包含此参数。

MATERIAL

将此参数设置为壳所使用材料的名称。

### **可选参数：**

CONTROLS

在Abaqus/Explicit分析中，将此参数设置为截面控制定义（参见["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)）的名称，用于指定二阶精确单元公式选项、非默认沙漏控制公式选项或比例因子。

在Abaqus/Standard分析中，将此参数设置为截面控制定义的名称，用于指定增强沙漏控制公式（参见["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)），或用于后续的Abaqus/Explicit导入分析。

DENSITY

将此参数设置为壳单位表面积的质量。

如果使用此参数，则壳的质量包括此参数的贡献以及材料定义的任何贡献。

LAYUP

此参数仅在使用COMPOSITE参数时相关。

将此参数设置为复合铺层（参见[Abaqus/CAE User's Guide第23章，"复合铺层"](../usi/usi-link.md#usi-adv-layups)）的名称。Abaqus/CAE使用此名称来标识包含壳截面的复合铺层。

NODAL THICKNESS

包含此参数以指示壳厚度不应从数据行读取，而应从使用[*NODAL THICKNESS](ch14abk08.md)选项在节点处指定的厚度进行插值。对于复合截面，总厚度从节点插值，数据行上指定的层厚度按比例缩放。此参数对连续壳被忽略。

NODAL THICKNESS和SHELL THICKNESS参数是互斥的。

OFFSET

包含此参数以定义从壳中面到参考表面（包含单元节点）的距离（以壳厚度的分数表示）。此参数接受正值或负值、标签SPOS或SNEG，或在Abaqus/Standard分析中接受分布名称。参见["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)。

偏移正值在正法线方向（参见["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)）。当OFFSET=0.5（或SPOS）时，壳的上表面为参考表面。当OFFSET=-0.5（或SNEG）时，壳的下表面为参考表面。默认值为OFFSET=0，表示壳的中面为参考表面。此参数对连续壳被忽略。

在Abaqus/Standard分析中，可以通过将OFFSET设置为分布名称来指定空间变化的偏移。用于定义壳偏移的分布必须具有默认值。默认偏移量由分配给壳截面但未在分布中专门分配值的任何壳单元使用。

ORIENTATION

将此参数设置为方向定义（["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)）的名称，用于此壳截面行为定义中的材料计算。此方向将用于个别层的材料计算和应力输出、截面力输出以及横向剪切刚度。

对于复合壳的个别层，可以通过在每个层定义数据行上引用方向定义或给出方向角（以度为单位，相对于壳局部方向正counterclockwise）来使用不同的方向定义进行材料计算。任何没有方向引用或角度指定的层定义行将使用在此定义的方向。虽然可以使用用分布定义的方向来指定壳截面的整体方向，但不能用分布在复合壳的层上指定方向。

POISSON

包含此参数以定义壳厚度方向行为。

将此参数设置为非零值，以使平面应力条件下厚度方向应变成为膜应变的线性函数。POISSON参数的值必须在-1.0和0.5之间。

设置POISSON=ELASTIC以基于材料定义的初始弹性部分自动选择此参数值。

在Abaqus/Explicit分析中设置POISSON=MATERIAL，以使平面应力条件下厚度方向应变成为膜应变和面内材料性质的函数。

在Abaqus/Standard中默认值为POISSON=0.5；在Abaqus/Explicit中默认值为POISSON=MATERIAL。

SECTION INTEGRATION

设置SECTION INTEGRATION=SIMPSON（默认）以使用Simpson法则进行壳截面积分。

设置SECTION INTEGRATION=GAUSS以使用Gauss积分进行壳截面积分。Gauss积分不能用于传热或热耦合壳单元。

SHELL THICKNESS

将此参数设置为分布（["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)）的名称以定义空间变化的厚度。如果此参数用于非复合截面，则忽略数据行上的厚度。对于复合截面，总厚度由分布定义，数据行上指定的层厚度按比例缩放。此参数对连续壳被忽略。

用于定义壳厚度的分布必须具有默认值。默认厚度由分配给壳截面但未在分布中专门分配值的任何壳单元使用。

NODAL THICKNESS和SHELL THICKNESS参数是互斥的。

STACK DIRECTION

此参数仅对连续壳相关。

将此参数设置为1、2、3或ORIENTATION，以定义连续壳堆叠或厚度方向。指定数值之一以选择元素的相应等参数方向作为堆叠或厚度方向。默认值为STACK DIRECTION=3。

如果STACK DIRECTION=ORIENTATION，则还需要ORIENTATION参数。

要获得所需的厚度方向，STACK DIRECTION参数的适当数值取决于单元连接性。对于与网格无关的规格，请使用STACK DIRECTION=ORIENTATION。如果分配给ORIENTATION参数的方向使用分布定义（["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)），则不支持STACK DIRECTION=ORIENTATION。

SYMMETRIC

此参数仅在使用COMPOSITE参数时相关。

如果复合壳中的层关于中心芯对称，则包含此参数。如果使用分布（["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)）在任何复合层上定义了空间变化的厚度或方向角，则不能使用此参数。

TEMPERATURE

使用此参数选择[*FIELD](ch06abk07.md)、[*INITIAL CONDITIONS](ch09abk18.md)或[*TEMPERATURE](ch19abk01.md)选项上使用的温度和场变量输入模式。

省略TEMPERATURE参数以通过其在壳参考表面上的幅度及其通过厚度的梯度来定义预定义场。

设置TEMPERATURE=*n*，其中*n*是壳中预定义场变量点的数量（如果使用COMPOSITE参数，则为每层中的数量），以在壳截面每层的*n*个等距点上定义预定义场。

在传热分析步或耦合温度-位移分析步中，当使用[*FIELD](ch06abk07.md)选项指定预定义场变量的值时，需要TEMPERATURE参数来指定壳中场变量点的数量。具有温度自由度的壳中温度点的数量由数据行上指定的积分点数量定义。

THICKNESS MODULUS

此参数仅对连续壳相关。

将此参数设置为有效厚度模量。默认有效厚度模量是基于材料定义的初始面内剪切模量的两倍。

### **定义均质壳的数据行（包含MATERIAL参数）：**

**第一行（也是唯一行）：**

### **定义复合壳的数据行（包含COMPOSITE参数）：**

**第一行：**

根据需要重复此数据行。壳的每一层使用一行数据。叠层壳层相对于壳法线正方向的顺序由数据行的顺序定义。如果包含SYMMETRIC参数，则仅指定从底层到中面的一半层。




