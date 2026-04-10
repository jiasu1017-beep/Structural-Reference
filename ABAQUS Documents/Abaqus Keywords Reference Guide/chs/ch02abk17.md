# *BUCKLING ENVELOPE





### *BUCKLING ENVELOPE为具有PIPE截面的框架单元的屈曲 strut响应定义非默认屈曲包络线。

此选项用于定义表征框架单元屈曲strut响应的屈曲strut包络线的系数。它可以与[*FRAME SECTION](ch06abk34.md)，SECTION=PIPE，YIELD STRESS=![](../graphics/key_eqn00128.gif)选项（无论是否带有PINNED参数）配合使用。

**产品：**Abaqus/Standard

**类型：**模型数据

**级别：**部件、部件实例

##### **参考：**

- ["框架截面行为，" Abaqus Analysis User's Guide第29.4.2节](../usb/usb-link.md#usb-elm-eusingframesection)
- [*FRAME SECTION](ch06abk34.md)

**此选项没有参数。**

### **定义屈曲strut包络线的数据行：**

**第一行（也是唯一数据行）：**

在上述数据行中，*A*是横截面积，![](../graphics/key_eqn00128.gif)是屈服应力值，*E*是杨氏模量，*L*是单元长度，*D*是外管道直径，*t*是管道壁厚。


