# *ADJUST





### *ADJUST调整用户指定的节点坐标以使其位于给定曲面上。

此选项用于调整用户指定的节点坐标，以使节点位于给定曲面上。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**Part、Part instance、Assembly

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["调整节点坐标，" Abaqus Analysis User's Guide第2.1.6节](../usb/usb-link.md#usb-int-madjust)

### **必需参数：**

NODE SET

将此参数设置为包含要调整的节点的节点集名称。

SURFACE

将此参数设置为节点要调整到的曲面名称。

### **可选参数：**

ORIENTATION

将此参数设置为方向定义的名称（参见["方向，" Abaqus Analysis User's Guide第2.2.5节](../usb/usb-link.md#usb-int-corientation)），该定义给出了调整节点的方向。如果省略此参数，节点将沿指定曲面的法线方向调整。仅支持矩形、圆柱形和球形方向定义。作为方向定义一部分的额外旋转将被忽略。

**此选项没有关联的数据行。**