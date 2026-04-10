# *NMAP









### *NMAP将节点从一个坐标系映射到另一个坐标系，并旋转、平移或缩放节点坐标。

将节点从一个坐标系映射到另一个坐标系，并旋转、平移或缩放节点坐标。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**模型数据  

**级别：**此选项在基于部件实例装配定义的模型中不支持。

**Abaqus/CAE：**不支持；网格模块中的网格划分技术通常更可取。

##### **参考：**

- ["节点定义，" Abaqus Analysis User's Guide第2.1.1节](../usb/usb-link.md#usb-int-inode)

### **必需参数：**

NSET

将此参数设置为包含要映射的节点的节点集名称。映射的节点是此选项被遇到时属于此集的节点。

TYPE

设置TYPE=ROTATION以引入关于由两点*a*和*b*定义的给定轴的指定角度旋转（或通过这些点的坐标）。旋转原点由第三点*c*给出（或通过该点的坐标）。

设置TYPE=TRANSLATION以引入沿由两个节点*a*和*b*定义的给定轴的平移（或通过这些点的坐标）。

设置TYPE=SCALE以相对于一个节点*a*缩放每个轴（或通过该点的坐标）。

设置TYPE=RECTANGULAR以引入简单的移位或旋转。图中的点*a*定义定义映射的局部笛卡尔坐标系的原点。局部轴由连接点*a*和点*b*的线定义。局部平面由通过点*a*、*b*和*c*的平面定义。

设置TYPE=CYLINDRICAL以从圆柱坐标映射。图中的点*a*定义定义映射的局部圆柱坐标系的原点。通过点*a*和点*b*的线定义局部圆柱坐标系的轴。局部平面由通过点*a*、*b*和*c*的平面定义。

设置TYPE=DIAMOND以从偏斜笛卡尔坐标映射。图中的点*a*定义定义映射的局部菱形坐标系的原点。通过点*a*和点*b*的线定义局部坐标系的轴。通过点*a*和点*c*的线定义局部坐标系的轴。通过点*a*和点*d*的线定义局部坐标系的轴。

设置TYPE=SPHERICAL以从球坐标映射。图中的点*a*定义定义映射的局部球坐标系的原点。通过点*a*和点*b*的线定义局部球坐标系的极轴。通过点*a*并垂直于极轴的平面定义平面。通过点*a*、*b*和*c*的平面定义局部平面。

设置TYPE=TOROIDAL以从环面坐标映射。图中的点*a*定义定义映射的局部环面坐标系的原点。局部环面系统的轴位于由点*a*、*b*和*c*定义的平面中。环面系统的R坐标由点*a*和*b*之间的距离定义。通过点*a*和*b*的线定义位置。对于每个值，坐标在与由点*a*、*b*和*c*定义的平面垂直并与环面系统轴垂直的平面中定义。位于由点*a*、*b*和*c*定义的平面中。

设置TYPE=BLENDED以通过Abaqus/Standard分析中的混合二次映射。

### **可选参数：**

DEFINITION

设置DEFINITION=COORDINATES（默认）通过给出点*a*、*b*、*c*和*d*的坐标（取决于所选类型）来定义局部系统、旋转轴、旋转原点或平移轴。

设置DEFINITION=NODES通过给出点*a*、*b*、*c*和*d*的全局节点编号来定义局部系统、旋转轴、旋转原点或平移轴。此选项不能与TYPE=BLENDED一起使用。

### **TYPE=ROTATION、DEFINITION=COORDINATES的数据行：**

**第一行：**

**第二行：**

**第三行：**

### **TYPE=ROTATION、DEFINITION=NODES的数据行：**

**第一行：**

**第二行：**

**第三行：**

### **TYPE=TRANSLATION、DEFINITION=COORDINATES的数据行：**

**第一行：**

**第二行：**

### **TYPE=TRANSLATION、DEFINITION=NODES的数据行：**

**第一行：**

**第二行：**

### **TYPE=SCALE、DEFINITION=COORDINATES的数据行：**

**第一行：**

**第二行：**

### **TYPE=SCALE、DEFINITION=NODES的数据行：**

**第一行：**

**第二行：**

### **TYPE=RECTANGULAR、CYLINDRICAL、DIAMOND、SPHERICAL或TOROIDAL、DEFINITION=COORDINATES的数据行：**

**第一行：**

**第二行：**

如果指定了TYPE=RECTANGULAR且仅给出了点*a*，则集合中节点的坐标简单地被平移。

**第三行：**

### **TYPE=RECTANGULAR、CYLINDRICAL、DIAMOND、SPHERICAL或TOROIDAL、DEFINITION=NODES的数据行：**

**第一行：**

**第二行：**

如果指定了TYPE=RECTANGULAR且仅给出了点*a*，则集合中节点的坐标简单地被平移。

**第三行：**

### **TYPE=BLENDED的数据行：**

**第一行：**

**第二行：**

继续，最多给出20个控制节点，但至少给出八个角节点。如果混合映射的边要线性映射，则相应的边中控制节点可以从列表中省略。这是通过插入仅包含节点编号0的行（空行）来代替控制节点及其映射坐标的定义来完成的。控制节点不必是有限元模型中的节点——它们可以只是用于网格生成的节点。Abaus在进行分析之前消除分析模型中未使用的任何节点。

**图14.4-1** 坐标系；角度以度为单位。

![](../graphics/knmap-coordsys-nls.png)