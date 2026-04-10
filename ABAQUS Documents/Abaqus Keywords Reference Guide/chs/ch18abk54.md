# *SURFACE SECTION





### *SURFACE SECTION为表面元素指定截面属性。

此选项用于指定表面元素横截面。它必须与[*REBAR LAYER](ch17abk12.md)选项一起使用。在Abaqus/Aqua分析中，表面截面可用于可视化重力波作用下水面行为。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  Abaqus/Aqua

**类型：**模型数据

**级别：**部件、部件实例

**Abaqus/CAE：**Property模块

##### **参考：**

- ["表面元素," Section 32.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esurface)
- ["定义钢筋," Section 2.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-erebarlayer)
- [*REBAR LAYER](ch17abk12.md)

### **必需参数：**

ELSET

将此参数设置为包含正在为其定义截面属性的表面元素的元素集名称。

### **可选的互斥参数：**

AQUAVISUALIZATION

此参数仅适用于Abaqus/Aqua分析。

设置AQUAVISUALIZATION=YES以指定引用的表面元素将用于可视化重力波。

DENSITY

将此参数设置为表面元素截面每单位面积的質量密度。

**此选项没有关联的数据行。**





