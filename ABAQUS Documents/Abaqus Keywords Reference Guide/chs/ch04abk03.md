# *DAMAGE STABILIZATION





### *DAMAGE STABILIZATION指定纤维增强材料损伤模型、表面基于的内聚行为或富集单元中内聚行为的粘性系数。

此选项用于指定粘性正则化方案中使用的粘性系数，用于纤维增强材料的损伤模型、接触中的基于表面的牵引-分离行为或富集单元中的内聚行为。对于纤维增强材料，您可以将此选项与 [*DAMAGE INITIATION](ch04abk04.md)、CRITERION=HASHIN 和 [*DAMAGE EVOLUTION](ch04abk03.md) 选项结合使用；对于基于表面的牵引-分离行为，您可以将此选项与 [*DAMAGE INITIATION](ch04abk04.md)、CRITERION=MAXS、MAXE、QUADS 或 QUADE 和 [*DAMAGE EVOLUTION](ch04abk03.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["粘性正则化" 位于 "纤维增强复合材料的损伤演化与单元移除，" Abaqus分析用户指南第24.3.3节](../usb/usb-link.md#usb-mat-cdamagefibercomposite-regularize)
- ["基于表面的内聚行为，" Abaqus分析用户指南第37.1.10节](../usb/usb-link.md#usb-cni-acohesivebehavior)
- ["使用扩展有限元方法将不连续性建模为富集特征，" Abaqus分析用户指南第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)

**此选项没有关联的参数。**

### **定义纤维增强材料粘性系数的数据行：**

**第一行：**

### **定义基于表面的牵引-分离行为或富集单元中内聚行为的粘性系数的数据行：**

**第一行（也是唯一一行）：**




