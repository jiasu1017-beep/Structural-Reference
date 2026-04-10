# *SOLID SECTION





### *SOLID SECTION为实体、无穷元、声学、粒子和桁架单元指定元素属性。

此选项用于定义实体（连续体）单元、无穷元、声学有限元和无穷元、粒子单元和桁架单元的属性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Solid (continuum) elements," Section 28.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esolidcont)
- ["Infinite elements," Section 28.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-einfinite)
- ["Continuum particle elements," Section 33.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esphelem)
- ["Truss elements," Section 29.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-etruss)

### **必需参数：**

COMPOSITE

此参数仅适用于Abaqus/Standard分析。

此参数仅可用于仅具有位移自由度的三维砖块实体单元。如果实体由几层材料组成，则包含此参数。

COMPOSITE和MATERIAL参数是互斥的。

ELSET

将此参数设置为包含要定义材料行为的单元的单元集名称。

MATERIAL

将此参数设置为要用于这些单元的材料名称。

COMPOSITE和MATERIAL参数是互斥的。

REF NODE

此参数仅对广义平面应变单元和声学无穷元是必需的；对于所有其他单元类型，它被忽略。

将此参数设置为参考节点的节点号或包含参考节点的节点集名称。如果选择节点集名称，则该节点集必须恰好包含一个节点。

### **各向异性材料的必需参数；各向同性材料的可选参数：**

ORIENTATION

将此参数设置为方向定义（["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)）的名称，用于定义此集合中单元材料计算的局部坐标系。当材料是各向异性时需要此参数。

对于复合实体，此方向连同在层数据行上指定的方向角，也可用于定义个别层中的材料方向。或者，可以通过在每个层数据行上引用方向定义来指定材料方向。在这种情况下，将忽略ORIENTATION参数上的引用。任何没有方向引用或角度指定的层定义行将使用在关键字行上定义的截面方向。

### **可选参数：**

CONTROLS

在Abaqus/Explicit分析中，将此参数设置为截面控制定义（参见["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)）的名称，用于指定非默认沙漏控制公式选项或比例因子。[*SECTION CONTROLS](ch18abk01.md)选项可用于为二维和三维实体单元选择沙漏控制和公式精度阶数，以及为8节点砖块单元选择运动学公式。

在Abaqus/Standard分析中，将此参数设置为截面控制定义（参见["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)）的名称，用于指定增强沙漏控制公式或用于后续的Abaqus/Explicit导入分析。

LAYUP

此参数仅在使用COMPOSITE参数时相关。

将此参数设置为复合铺层（参见[Abaqus/CAE User's Guide第23章，"复合铺层"](../usi/usi-link.md#usi-adv-layups)）的名称。Abaqus/CAE使用此名称来标识包含实体截面的复合铺层。

ORDER

此参数仅可用于Abaqus/Explicit中的声学无穷元。它定义将用于解析无穷方向声场变化的九阶多项式的数量。将此参数设置为*N*，以指示将使用九阶多项式集合的前*N*个成员。默认值为ORDER=10，这是Abaqus/Standard中始终使用的值。

STACK DIRECTION

此参数仅适用于Abaqus/Standard分析。

此参数仅可用于复合单元。它定义相对于一对单元面的堆叠方向。将此参数设置为1、2或3。默认值为STACK DIRECTION=3。

SYMMETRIC

此参数仅在使用COMPOSITE参数时相关。

如果复合壳中的层关于中心芯对称，则包含此参数。如果使用分布（["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)）在任何复合层上定义了空间变化的方向角，则不能使用此参数。

### **定义均质实体单元、无穷元、声学元、粒子或桁架元的数据行：**

**第一行（也是唯一行）：**

### **定义复合实体的数据行：**

**第一行：**

根据需要重复此数据行以定义复合实体每层的属性。如果包含SYMMETRIC参数，则仅指定从底层到中面的一半层。




