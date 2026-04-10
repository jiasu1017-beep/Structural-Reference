# *SURFACE SMOOTHING





### *SURFACE SMOOTHING定义表面平滑方法。

此选项用于为接触相互作用创建表面平滑定义。它必须与[*CONTACT PAIR](ch03abk68.md)选项一起使用。定义的平滑方法适用于所引用接触对中指定表面区域。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Abaqus/Standard中接触表面平滑," Section 38.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asmoothsurfaces)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此表面平滑定义。

此标签由[*CONTACT PAIR](ch03abk68.md)选项上的GEOMETRIC CORRECTION参数引用。

### **定义应用平滑的表面区域的数据行：**

**在对应（或近似对应）圆弧的二维表面区域上定义平滑的数据行（参见[图18.55-1](ch18abk55.md#msmoothcir2d-surfacesmoothing)）：**

**在对应（或近似对应）旋转曲面的表面区域上定义平滑的数据行（参见[图18.55-2](ch18abk55.md#msmoothcir3d-surfacesmoothing)）：**

**图18.55-2** 三维圆周平滑。

![](../graphics/usb-kws-msmoothcir3d-nls.png)

**在对应（或近似对应）球面截面的表面区域上定义平滑的数据行（参见[图18.55-3](ch18abk55.md#msmoothsph3d-surfacesmoothing)）：**

**图18.55-3** 球面平滑。

![](../graphics/usb-kws-msmoothsph3d-nls.png)

**在对应（或近似对应）环曲面的表面区域上定义平滑的数据行（参见[图18.55-4](ch18abk55.md#msmoothtor3d-surfacesmoothing)）：**

根据需要重复上述数据行，以定义所有需要平滑的表面区域。

**图18.55-4** 三维环面平滑。

![](../graphics/usb-kws-msmoothtor3d-nls.png)





