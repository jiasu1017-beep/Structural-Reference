# *SURFACE





### *SURFACE定义模型中的表面或区域。

此选项用于定义接触模拟、约束约束、紧固件和耦合的表面，以及分布式表面载荷、声辐射、声阻抗和表面上积分量输出的区域。在Abaqus/Standard中，它还用于定义腔体辐射分析和装配载荷的表面。在Abaqus/Explicit中，此选项也可用于在自适应网格域上定义边界区域。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、装配

**Abaqus/CAE：**基于元素的表面由Surface工具集支持。基于节点的表面不受支持；如果基于节点的表面被导入到Abaqus/CAE，它们将被视为集合。

##### **参考：**

- ["Surfaces: overview," Section 2.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-asurfoverview)
- ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["Node-based surface definition," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)
- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)
- ["Eulerian surface definition," Section 2.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-aeulsurf)
- ["Operating on surfaces," Section 2.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-acombinedsurf)
- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["Contact interaction analysis: overview," Section 36.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactoverview)
- ["RSURFU," Section 1.1.16 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ursurfu)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **必需参数：**

NAME

将此参数设置为将用于引用表面的标签。

### **腔体辐射模拟的必需参数：**

PROPERTY

此参数仅适用于Abaqus/Standard分析。

将此参数设置为与此表面关联的[*SURFACE PROPERTY](ch18abk52.md)定义名称。参见["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)。

### **可选参数：**

COMBINE

设置COMBINE=UNION以基于两个或更多同类型表面的并集创建表面。

设置COMBINE=INTERSECTION以基于两个同类型表面的交集创建表面。

设置COMBINE=DIFFERENCE以基于两个同类型表面的差集创建表面（第二个表面从第一个表面减去）。

只有NAME参数和腔体辐射模拟中的PROPERTY参数可与此参数一起使用。

CROP

包含此参数以创建仅包含现有表面中位于指定矩形框内节点的面的新表面。

只有NAME参数和腔体辐射模拟中的PROPERTY参数可与此参数一起使用。

DEFINITION

此参数仅对使用TYPE=CUTTING SURFACE定义的表面相关。

设置DEFINITION=COORDINATES（默认）以通过给出切割平面上一点的坐标和切割平面的法向来定义切割平面。

设置DEFINITION=NODES以通过给出切割平面上点*a*的全局节点号和位于切割平面外的点*b*（切割平面法线由从*a*到*b*的向量确定）来定义切割平面。

FILLET RADIUS

此参数可与TYPE=SEGMENTS、TYPE=CYLINDER或TYPE=REVOLUTION一起使用，以定义曲率半径来圆整相邻直线段、相邻圆弧段以及相邻直线和圆弧段之间的不连续性。

INTERNAL

Abaqus/CAE使用INTERNAL参数来标识内部创建的表面。INTERNAL参数仅用于以部件实例装配定义的模型。默认是省略INTERNAL参数。

REGION TYPE

此参数仅对在自适应网格域边界上定义的表面相关。在自适应网格域内部定义的表面将独立于材料移动，除非表面受到网格约束约束。参见["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains)。

设置REGION TYPE=LAGRANGIAN以创建拉格朗日边界区域。拉格朗日边界区域的边缘将跟随材料，同时允许沿边缘和区域内部进行自适应网格划分。

设置REGION TYPE=SLIDING（默认）以创建滑动边界区域。滑动边界区域的边缘将滑过材料。网格自适应将发生在边缘和区域内部。网格约束通常应用于滑动边界区域的边缘以将其空间固定。

设置REGION TYPE=EULERIAN以在自适应网格域中创建欧拉边界区域。此选项用于创建材料可以流过的边界区域。必须垂直于欧拉边界区域使用网格约束以允许材料流过该区域。如果没有应用网格约束，则欧拉边界区域的行为将与滑动边界区域相同。

TRIM

设置TRIM=YES以调用开放自由表面的修剪。设置TRIM=NO以抑制表面修剪。默认值为TRIM=YES，除非表面在Abaqus/Standard中用作有限滑动接触公式中的主表面，或表面在Abaqus/Explicit中与接触对算法一起使用。TRIM=YES在Abaqus/Explicit中与接触对算法一起使用的表面上没有影响。

TYPE

设置TYPE=ELEMENT（默认）以自动为指定单元定义自由表面，或使用单元面标识符在单元上定义表面。

设置TYPE=NODE通过指定节点列表或节点集标签来定义表面。

设置TYPE=SEGMENTS以通过定义连接线段在平面模型的 ![](../graphics/key_eqn01033.gif) 平面或轴对称模型的 ![](../graphics/key_eqn01034.gif) 平面中创建二维解析表面。

设置TYPE=CYLINDER以通过沿指定生成向量扫过在局部(*x*, *y*)平面中定义的连接线段来创建三维解析表面。

设置TYPE=REVOLUTION以通过提供在 ![](../graphics/key_eqn01034.gif) 平面中给出的连接线段绕轴旋转来创建三维解析表面。

设置TYPE=CUTTING SURFACE以使用穿过元素集的切割平面生成内部基于元素的表面。生成的表面是切割平面的近似。

设置TYPE=EULERIAN MATERIAL以在欧拉材料实例的外部边界上定义表面。此选项仅适用于Abaqus/Explicit。

设置TYPE=USER以在Abaqus/Standard中通过用户子程序[`RSURFU`](../sub/sub-link.md#sub-xsl-rsurfu)定义解析表面。

设置TYPE=XFEM为扩展有限元方法富集的裂纹单元生成裂纹表面。生成的表面仅支持分布式压力载荷的应用。此选项仅适用于Abaqus/Standard。

### **Abaqus/Explicit中接触对分析的其他可选参数：**

MAX RATIO

将此参数设置为小平面接触厚度与其最小边缘（或对角线）长度之比的上限。此比率在将SCALE THICK参数应用于接触厚度后计算。如果必要，将调整单个小平面的接触厚度以符合此最大比率。

如果省略此参数，则不强制执行上限。如果包含此参数但未指定值，则默认值为0.6。

NO OFFSET

包含此参数以指示此表面将忽略形成表面的任何壳、膜或刚性单元的中面偏移。

NO THICK

包含此参数以指示此表面将忽略形成表面的任何壳、膜或刚性单元的厚度。使用此参数定义的表面不能用于定义双侧表面或自接触。

SCALE THICK

此参数仅在表面与[*CONTACT PAIR](ch03abk68.md)选项一起使用时适用。

将此参数设置为缩放底层单元厚度以计算接触厚度的量。默认值为1.0（即不缩放）。

### **COMBINE=UNION的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许16个条目。

### **COMBINE=INTERSECTION或COMBINE=DIFFERENCE的数据行：**

**第一行（也是唯一行）：**

对于COMBINE=DIFFERENCE，第二个表面从第一个表面减去。

### **包含CROP参数时定义表面的数据行：**

**第一行：**

**第二行：**

**第三行（可选）：**

### **使用TYPE=ELEMENT参数使用单元或单元集定义表面的数据行：**

**第一行：**

根据需要重复此数据行以定义表面。

### **使用TYPE=NODE参数使用节点或节点集定义表面的数据行：**

**第一行：**

根据需要重复此数据行以定义表面。

### **当TYPE=CUTTING SURFACE，DEFINITION=COORDINATES时，使用切割给定单元集的平面定义表面的数据行：**

**第一行：**

**第二行：**

根据需要重复此数据行。每行最多允许16个条目。

### **当TYPE=CUTTING SURFACE，DEFINITION=NODES时，使用切割给定单元集的平面定义表面的数据行：**

**第一行：**

**第二行：**

根据需要重复此数据行。每行最多允许16个条目。

### **使用TYPE=EULERIAN MATERIAL创建的表面的数据行：**

**第一行：**

### **使用TYPE=XFEM创建的裂纹表面的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许16个条目。

### **TYPE=USER不需要数据行。**

### **使用TYPE=SEGMENTS创建的表面的数据行：**

**第一行：**

第二行和后续数据行定义形成解析表面轮廓的各种线、圆和抛物线段（参见下文了解其格式）。

### **使用TYPE=CYLINDER创建的表面的数据行：**

**第一行（如果在部件或部件实例内定义此表面，则留空）：**

**第二行（如果在部件或部件实例内定义此表面，则留空）：**

**第三行：**

第四行和后续数据行定义形成解析表面轮廓的各种线、圆和抛物线段（参见下文了解其格式）。

### **使用TYPE=REVOLUTION创建的表面的数据行：**

**第一行（如果在部件或部件实例内定义此表面，则留空）：**

**第二行：**

第三行和后续数据行定义形成解析表面轮廓的各种线、圆和抛物线段（参见下文了解其格式）。

### **定义TYPE=SEGMENTS、TYPE=CYLINDER和TYPE=REVOLUTION解析表面的线段的数据行：**

**定义直线段的数据行：**

**定义圆弧段的数据行（弧必须小于179.74°）：**

**定义抛物线弧段的数据行：**

对于使用TYPE=SEGMENTS创建的表面，*x*-和*y*-坐标是全局*X*-和*Y*-坐标或*r*-和*z*-坐标。对于使用TYPE=CYLINDER创建的表面，*x*-和*y*-坐标是局部*x*-和*y*-坐标。对于使用TYPE=REVOLUTION创建的表面，*x*-和*y*-坐标是局部*r*-和*z*-坐标。

**图18.47-1** [*SURFACE](ch18abk47.md)，TYPE=CYLINDER。

![](../graphics/krigidsurface-cylinder-nls.png)

**图18.47-2** [*SURFACE](ch18abk47.md)，TYPE=REVOLUTION。

![](../graphics/krigidsurface-rev-nls.png)




