# *UNIAXIAL





### *UNIAXIAL通过加载和卸载试验数据表征织物材料。

此选项用于指示沿特定方向开始剪切或单轴试验数据，以定义织物材料的行为。它必须与[*FABRIC](ch06abk01.md)选项一起使用。

**产品：**Abaqus/Explicit

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["织物材料行为," Section 23.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfabric)
- [*FABRIC](ch06abk01.md)
- [*LOADING DATA](ch12abk03.md)
- [*UNLOADING DATA](ch20abk05.md)

### **必需参数：**

COMPONENT

设置COMPONENT=1以定义"纬向"方向织物纤维的单轴行为。

设置COMPONENT=2以定义"经向"方向织物纤维的单轴行为。

设置COMPONENT=SHEAR以定义织物的剪切响应。

**此选项没有关联的数据行。**
