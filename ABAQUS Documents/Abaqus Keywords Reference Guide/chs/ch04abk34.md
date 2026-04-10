# *DRUCKER PRAGER





### *DRUCKER PRAGER指定扩展Drucker-Prager塑性模型。

此选项用于为使用扩展Drucker-Prager塑性模型之一的弹塑性材料定义屈服面和流动势参数。它必须与 [*DRUCKER PRAGER HARDENING](ch04abk36.md) 选项结合使用，并且如果Abaqus/Standard分析中包含蠕变材料行为，还必须与 [*DRUCKER PRAGER CREEP](ch04abk35.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["扩展Drucker-Prager模型，" Abaqus分析用户指南第23.3.1节](../usb/usb-link.md#usb-mat-cdruckerprager)
- [*DRUCKER PRAGER HARDENING](ch04abk36.md)
- [*DRUCKER PRAGER CREEP](ch04abk35.md)

### **可选参数：**

DEPENDENCIES

除了温度之外，将此参数设置为材料参数定义中包含的场变量依赖项数量。如果省略此参数，则假定材料参数仅取决于温度。请参见Abaqus分析用户指南第21.1.2节中的["指定场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

ECCENTRICITY

此参数仅与 SHEAR CRITERION=HYPERBOLIC 或 SHEAR CRITERION=EXPONENT FORM 结合使用，或者与 SHEAR CRITERION=LINEAR 结合使用包含蠕变材料属性时。

它用于定义流动势离心率 ![](../graphics/key_eqn00222.gif)。离心率是一个小的正数，定义双曲流动势接近其渐近线的速率。对于指数模型，默认值为 ![](../graphics/key_eqn00223.gif)；并且如果 ![](../graphics/key_eqn00625.gif)，对于双曲模型，它设置为 ![](../graphics/key_eqn00626.gif) 以确保相关流动（术语在["扩展Drucker-Prager模型，" Abaqus分析用户指南第23.3.1节](../usb/usb-link.md#usb-mat-cdruckerprager)中定义）。

SHEAR CRITERION

设置 SHEAR CRITERION=LINEAR（默认）以定义线性屈服准则。如果Abaqus/Standard分析中包含蠕变材料行为，则需要此选项。

设置 SHEAR CRITERION=HYPERBOLIC 以定义双曲屈服准则。

设置 SHEAR CRITERION=EXPONENT FORM 以将指数形式定义为屈服准则。

TEST DATA

此参数仅与 SHEAR CRITERION=EXPONENT FORM 结合使用。

如果指数模型的材料常数由Abaqus从不同围压水平的三轴试验数据计算，则包含此参数。必须使用 [*TRIAXIAL TEST DATA](ch19abk15.md) 选项来实现此目的。

### **定义线性Drucker-Prager塑性模型的数据行（SHEAR CRITERION=LINEAR）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将材料参数对温度和其他预定义场变量的依赖性定义为函数。

### **定义双曲Drucker-Prager塑性模型的数据行（SHEAR CRITERION=HYPERBOLIC）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将材料参数对温度和其他预定义场变量的依赖性定义为函数。

### **使用指数律定义Drucker-Prager塑性模型的数据行（SHEAR CRITERION=EXPONENT FORM）且无试验数据（TEST DATA）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将材料参数对温度和其他预定义场变量的依赖性定义为函数。

### **使用指数律定义Drucker-Prager塑性模型的数据行（SHEAR CRITERION=EXPONENT FORM）且有试验数据（TEST DATA）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将材料参数对温度和其他预定义场变量的依赖性定义为函数。




