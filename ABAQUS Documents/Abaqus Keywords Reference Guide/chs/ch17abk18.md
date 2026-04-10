# *RIGID BODY







### *RIGID BODY将一组单元定义为刚体并定义刚性单元属性。

此选项用于将一组单元和/或一组节点和/或解析表面绑定到刚体，并将参考节点分配给刚体，该刚体可选择性地声明为完全耦合热应力分析的等温刚体。它还用于为Abaqus/Explicit分析中属于刚体一部分的刚性单元指定密度、厚度和偏移。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**零件，零件实例，装配  

**Abaqus/CAE：**零件模块和相互作用模块

##### **参考：**

- ["刚性单元，" Abaqus Analysis User's Guide第30.3.1节](../usb/usb-link.md#usb-elm-erigid)
- ["解析刚体表面定义，" Abaqus Analysis User's Guide第2.3.4节](../usb/usb-link.md#usb-int-arigidsurf)
- ["刚体定义，" Abaqus Analysis User's Guide第2.4.1节](../usb/usb-link.md#usb-int-arigidoverview)

### **必需参数：**

REF NODE

将此参数设置为刚体参考节点的节点编号或包含刚体参考节点的节点集名称。如果选择节点集名称，则该节点集必须恰好包含一个节点。

### **至少需要以下参数之一：**

ANALYTICAL SURFACE

将此参数设置为要分配给刚体的解析表面名称。

ELSET

将此参数设置为包含要分配给刚体的单元的单元集名称。一个单元不能出现在多个刚体中。

PIN NSET

将此参数设置为包含要分配给刚体的销类型节点的节点集名称。此参数可用于向刚体添加节点或重新定义由ELSET参数包含在刚体中的单元上节点的节点类型。销类型节点只有其平移自由度与刚体相关。一个节点不能出现在多个刚体定义中。

TIE NSET

将此参数设置为包含要分配给刚体的绑定类型节点的节点集名称。此参数可用于向刚体添加节点或重新定义由ELSET参数包含在刚体中的单元上节点的节点类型。绑定类型节点具有其平移和旋转自由度与刚体相关。一个节点不能出现在多个刚体定义中。

### **可选参数：**

ISOTHERMAL

此参数仅用于完全耦合热应力分析。

将此参数设置为YES以指定等温刚体。默认为ISOTHERMAL=NO。

POSITION

如果参考节点的位置由用户定义，则设置POSITION=INPUT（默认）。

如果参考节点位于刚体的质心处，则设置POSITION=CENTER OF MASS。

### **可选参数（仅当指定的单元集包含刚性单元时使用）：**

DENSITY

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为单元集中所有刚性单元的密度。

NODAL THICKNESS

此参数仅适用于Abaqus/Explicit分析。

包含此参数以指示刚性单元的厚度不应从数据行读取，而应从使用[*NODAL THICKNESS](ch14abk08.md)选项在节点处指定的厚度进行插值。

OFFSET

此参数仅适用于Abaqus/Explicit分析。

包含此参数以定义从单元的中面到包含单元节点的参考表面的距离（作为刚性单元厚度的分数）。由于对刚性单元不执行单元级计算，因此指定的偏移仅影响与由刚性单元形成的刚体表面的接触对处理。

此参数接受正值或负值或标签SPOS或SNEG。偏移的正值方向为单元法线方向。当OFFSET=0.5（或SPOS）时，刚性单元的顶面为参考表面。当OFFSET=0.5（或SNEG）时，刚性单元的底面为参考表面。默认为OFFSET=0，表示刚性单元的中面为参考表面。

### **在Abaqus/Standard分析中，此选项没有关联的数据行。**

### **Abaqus/Explicit分析中R2D2单元的数据行：**

**第一行（也是唯一一行）：**

### **Abaqus/Explicit分析中RAX2、R3D3和R3D4单元的数据行：**

**第一行（也是唯一一行）：**
