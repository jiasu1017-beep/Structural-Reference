# *TENSILE FAILURE





### *TENSILE FAILURE指定拉伸失效模型和准则。

此选项与Mises或Johnson-Cook塑性模型或状态方程模型一起使用，以指定拉伸失效模型和准则。它必须与[*PLASTIC](ch16abk14.md)、HARDENING=ISOTROPIC选项；[*PLASTIC](ch16abk14.md)、HARDENING=JOHNSON COOK选项；或[*EOS](ch05abk27.md)选项一起使用。

**产品：**Abaqus/Explicit

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["状态方程," Section 25.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ceos)
- ["经典金属塑性," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Johnson-Cook塑性," Section 23.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["动态失效模型," Section 23.2.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfailuremodels)
- [*EOS](ch05abk27.md)
- [*PLASTIC](ch16abk14.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括静水截止应力定义中的场变量依赖项数。如果省略此参数，则假定静水截止应力是恒定的或仅取决于温度。有关详细信息，请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖性"。

ELEMENT DELETION

设置ELEMENT DELETION=YES（默认）以允许在满足失效准则时删除元素。

设置ELEMENT DELETION=NO以允许偏应力和静水部分的BRITTLE/DUCTILE型失效。

### **与ELEMENT DELETION=NO一起使用的必需参数：**

PRESSURE

设置PRESSURE=BRITTLE以对压力应力在满足失效准则时必须为压缩的情况进行建模。

设置PRESSURE=DUCTILE以对压力应力将在满足失效准则时受到静水截止应力限制的情况进行建模。

SHEAR

设置SHEAR=BRITTLE以对偏应力将在满足失效准则时设为零的情况进行建模。

设置SHEAR=DUCTILE以对偏应力在满足失效准则时不受影响的情况进行建模。

### **指定拉伸失效模型的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以定义静水截止应力对温度和其他预定义场变量的依赖性。





