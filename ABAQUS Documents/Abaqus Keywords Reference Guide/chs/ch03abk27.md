# *CONCRETE





### *CONCRETE定义超出弹性范围的混凝土属性。

**警告：**成功分析素混凝土和钢筋混凝土问题在很大程度上取决于对本节中描述的混凝土材料参数做出合理的选择，在钢筋混凝土的情况下，还取决于问题中钢筋的定义。熟悉混凝土建模和钢筋定义相关问题非常重要，请参阅["混凝土弥散裂纹"，Abaqus Analysis User's Guide第23.6.1节](../usb/usb-link.md#usb-mat-cconcrete)；["将钢筋定义为单元属性"，Abaqus Analysis User's Guide第2.2.4节](../usb/usb-link.md#usb-int-erebar)；以及[Abaqus Theory Guide](../stm/stm-link.md#stm)和[Abaqus Example Problems Guide](../exa/exa-link.md#exa)中的相应章节。

[*CONCRETE](ch03abk28.md)选项用于在Abaqus/Standard分析中定义素混凝土在弹性范围之外的属性。它必须与[*TENSION STIFFENING](ch19abk04.md)选项结合使用，也可与[*SHEAR RETENTION](ch18abk12.md)和[*FAILURE RATIOS](ch06abk04.md)选项一起使用。钢筋的属性和位置单独给出（["将钢筋定义为单元属性"，Abaqus Analysis User's Guide第2.2.4节](../usb/usb-link.md#usb-int-erebar)）。

[*BRITTLE CRACKING](ch02abk13.md)选项用于在Abaqus/Explicit分析中分析混凝土（请参见["混凝土裂纹模型"，Abaqus Analysis User's Guide第23.6.2节](../usb/usb-link.md#usb-mat-ccracking)）。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["混凝土弥散裂纹"，Abaqus Analysis User's Guide第23.6.1节](../usb/usb-link.md#usb-mat-cconcrete)
- [*TENSION STIFFENING](ch19abk04.md)
- [*SHEAR RETENTION](ch18abk12.md)
- [*FAILURE RATIOS](ch06abk04.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在压缩屈服应力定义中的场变量依赖项数。如果省略此参数，则假定压缩屈服应力仅取决于塑性应变，也可能取决于温度。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

### **定义混凝土属性的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义压缩屈服应力对塑性应变的依赖关系，以及对温度和其他预定义场变量（如需要）的依赖关系。




