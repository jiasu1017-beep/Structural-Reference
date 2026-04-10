# *TRIAXIAL TEST DATA





### *TRIAXIAL TEST DATA提供三轴试验数据。

如果用于定义[*DRUCKER PRAGER](ch04abk34.md)选项指数形式的某些或全部材料参数需要从三轴试验数据校准，则需要此选项。此选项只能作为[*DRUCKER PRAGER](ch04abk34.md)选项的子选项使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["扩展Drucker-Prager模型," Section 23.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdruckerprager)

### **可选参数：**

A

如果材料常数*a*已知并保持在输入值，则将此参数设置为等于该值。如果*a*要从校准中获得，则省略此参数及其值。

B

如果材料常数*b*已知并保持在输入值，则将此参数设置为等于该值。如果*b*要从校准中获得，则省略此参数及其值。

PT

如果材料常数![](../graphics/key_eqn01112.gif)已知并保持在输入值，则将此参数设置为等于该值。如果![](../graphics/key_eqn01112.gif)要从校准中获得，则省略此参数及其值。

### **指定三轴试验数据的数据行：**

**第一行：**

根据需要重复此数据行，以给出不同围压水平下的屈服应力。





