# *ENRICHMENT ACTIVATION









### *ENRICHMENT ACTIVATION激活或停用富集特征。

此选项用于在步骤定义中激活或停用富集特征。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["使用扩展有限元法将不连续性建模为富集特征，" Abaqus分析用户指南第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)

### **必需参数：**

NAME

将此参数设置为在[*ENRICHMENT](ch05abk25.md)选项上分配给富集特征的名称。

### **可选参数：**

ACTIVATE

设置 ACTIVATE=ON（默认）以在步骤中激活此富集特征。

设置 ACTIVATE=OFF 以在步骤中停用此富集特征。

设置 ACTIVATE=AUTO OFF 以在此富集中特征的所有预先存在的裂纹（或如果没有预先存在的裂纹，则所有允许的新生裂纹）在步骤内通过给定富集特征的边界传播后自动停用此富集特征。

TYPE

将此参数设置为在[*ENRICHMENT](ch05abk25.md)选项上指定的富集特征类型。目前仅支持 TYPE=PROPAGATION CRACK（默认）。

### **此选项没有关联的数据行。**



