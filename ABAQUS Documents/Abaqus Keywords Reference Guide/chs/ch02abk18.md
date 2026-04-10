# *BUCKLING LENGTH





### *BUCKLING LENGTH为具有PIPE截面的框架单元的屈曲strut响应定义屈曲长度数据。

此选项用于定义ISO方程中使用的两组系数，该方程预测具有屈曲strut响应的框架单元的![](../graphics/key_eqn00138.gif)。对于用户定义的屈曲包络线，它只能与[*FRAME SECTION](ch06abk34.md)，SECTION=PIPE，YIELD STRESS=![](../graphics/key_eqn00128.gif)选项和[*BUCKLING ENVELOPE](ch02abk17.md)选项配合使用。对于默认屈曲包络线，它只能与[*FRAME SECTION](ch06abk34.md)，BUCKLING，SECTION=PIPE，YIELD STRESS=![](../graphics/key_eqn00128.gif)选项（无论是否带有PINNED参数）配合使用。

**产品：**Abaqus/Standard

**类型：**模型数据

**级别：**部件、部件实例

##### **参考：**

- ["框架截面行为，" Abaqus Analysis User's Guide第29.4.2节](../usb/usb-link.md#usb-elm-eusingframesection)
- [*BUCKLING ENVELOPE](ch02abk17.md)
- [*FRAME SECTION](ch06abk34.md)

**此选项没有参数。**

### **定义屈曲长度系数的数据行：**

**第一行（也是唯一数据行）：**


