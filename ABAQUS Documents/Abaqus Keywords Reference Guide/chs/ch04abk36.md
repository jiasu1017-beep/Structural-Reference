# *DRUCKER PRAGER HARDENING





### *DRUCKER PRAGER HARDENING指定Drucker-Prager塑性模型的硬化。

此选项用于为使用 [*DRUCKER PRAGER](ch04abk34.md) 选项中定义的任何广义Drucker-Prager屈服准则的弹塑性材料指定硬化数据。

此选项还在Abaqus/Standard分析中用于指定测量 [*DRUCKER PRAGER CREEP](ch04abk35.md) 选项中定义的蠕变定律的蠕变试验类型。它必须与 [*DRUCKER PRAGER](ch04abk34.md) 选项结合使用，并且如果Abaqus/Standard分析中包含蠕变材料行为，还必须与 [*DRUCKER PRAGER CREEP](ch04abk35.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["扩展Drucker-Prager模型，" Abaqus分析用户指南第23.3.1节](../usb/usb-link.md#usb-mat-cdruckerprager)
- [*DRUCKER PRAGER](ch04abk34.md)
- [*DRUCKER PRAGER CREEP](ch04abk35.md)

### **可选参数：**

DEPENDENCIES

除了温度之外，将此参数设置为屈服应力定义中包含的场变量依赖项数量。如果省略此参数，则屈服应力仅取决于塑性应变，也可能取决于温度。请参见Abaqus分析用户指南第21.1.2节中的["材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖性"，了解更多详细信息。

RATE

将此参数设置为等效塑性应变率 ![](../graphics/key_eqn00629.gif)，用于此硬化曲线。如果使用了 [*RATE DEPENDENT](ch17abk08.md) 选项或 [*DRUCKER PRAGER CREEP](ch04abk35.md) 选项，则应省略此参数。如果未使用RATE参数、[*RATE DEPENDENT](ch17abk08.md) 选项和 [*DRUCKER PRAGER CREEP](ch04abk35.md) 选项，则假定为与速率无关的行为。

TYPE

设置 TYPE=COMPRESSION（默认）以通过给出单轴压缩屈服应力 ![](../graphics/key_eqn00163.gif) 作为单轴压缩塑性应变 ![](../graphics/key_eqn00630.gif) 的函数来定义硬化行为。

设置 TYPE=TENSION 以通过给出单轴拉伸屈服应力 ![](../graphics/key_eqn00167.gif) 作为单轴拉伸塑性应变 ![](../graphics/key_eqn00631.gif) 的函数来定义硬化行为。

设置 TYPE=SHEAR 以通过给出内聚力 ![](../graphics/key_eqn00632.gif) 作为等效剪切塑性应变 ![](../graphics/key_eqn00633.gif) 的函数来定义硬化行为，其中 ![](../graphics/key_eqn00634.gif) 是剪切中的屈服应力，*K* 是三轴拉伸流动应力与三轴压缩流动应力的比率，![](../graphics/key_eqn00635.gif) 是工程剪切塑性应变。

### **定义Drucker-Prager硬化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将屈服应力对塑性应变的依赖性（以及如果需要）对温度和其他预定义场变量的依赖性定义为函数。




