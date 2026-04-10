# *CYCLIC







### *CYCLIC为腔体辐射热传递分析定义循环对称。

此选项用于通过关于一点或一条轴的循环重复来定义腔体对称性。[*CYCLIC](ch03abk90.md)选项只能跟在[*RADIATION SYMMETRY](ch17abk05.md)选项之后使用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["腔体辐射，" Abaqus 分析用户指南第 41.1.1 节](../usb/usb-link.md#usb-cni-acavityradiation)
- [*RADIATION SYMMETRY](ch17abk05.md)

### **必需参数：**

NC

将此参数设置为组成该对称结果形成的腔体的循环相似图像的数量。用于创建循环相似图像的旋转角度（关于一点或一条轴）等于360/NC。

TYPE

设置TYPE=POINT，通过绕点*l*旋转模型中定义的腔体表面来创建二维腔体（请参见[图 3.90-1](ch03abk90.md#kcyclic-point)）。模型中定义的腔体表面必须由直线![](../graphics/key_eqn00539.gif)和一条经过点*l*的直线（从模型平面外向内看逆时针测量）与![](../graphics/key_eqn00539.gif)成360/NC角度的直线界定。

设置TYPE=AXIS，通过绕轴线![](../graphics/key_eqn00540.gif)旋转模型中定义的腔体表面来创建三维腔体（请参见[图 3.90-2](ch03abk90.md#kcyclic-axis)）。模型中定义的腔体表面必须由平面![](../graphics/key_eqn00541.gif)和经过线![](../graphics/key_eqn00540.gif且与![](../graphics/key_eqn00541.gif)成360/NC角度（从*l*向*m*看时顺时针测量）的平面界定。直线![](../graphics/key_eqn00539.gif)必须垂直于直线![](../graphics/key_eqn00540.gif)。

### **用于定义二维腔体循环对称的数据行（TYPE=POINT）：**

**第一行（也是唯一一行）：**

### **用于定义三维腔体循环对称的数据行（TYPE=AXIS）：**

**第一行：**

**第二行：**

**图 3.90-1** [*CYCLIC](ch03abk90.md)，TYPE=POINT选项。

![](../graphics/kcyclic-point.png)

**图 3.90-2** [*CYCLIC](ch03abk90.md)，TYPE=AXIS选项。

![](../graphics/kcyclic-axis.png)





