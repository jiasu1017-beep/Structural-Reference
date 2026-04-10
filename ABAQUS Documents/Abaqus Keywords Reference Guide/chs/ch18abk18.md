# *SLIDE LINE





### *SLIDE LINE指定可变形结构可能在其上相互作用的滑线表面。

此选项仅与滑线和管-管接触元素相关。它用于定义滑线并指定哪组接触元素与其相互作用。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**装配

**Abaqus/CAE：**不支持；Interaction模块使用基于表面的接触。

##### **参考：**

- ["Tube-to-tube contact elements," Section 40.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eitt)
- ["Slide line contact elements," Section 40.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-eslidelineelem)

### **必需参数：**

ELSET

将此参数设置为包含与所定义滑线相互作用的滑线或管-管接触元素的单元集名称。

TYPE

设置TYPE=LINEAR以定义由线性段组成的滑线。当一阶单元组成模型时应使用此参数。

设置TYPE=PARABOLIC以定义由抛物线段组成的滑线。当二阶单元组成模型时应使用此参数。在这种情况下，滑线应由奇数个节点组成，其中滑线上的奇数节点与抛物线段的端点相关联。

### **可选参数：**

EXTENSION ZONE

将此参数设置为端段长度的一个分数，开放滑线的任一端将延伸该分数以避免与接触建模相关的数值舍入误差。给定值必须在0.0和0.2之间。默认值为0.1。

GENERATE

包含此参数以允许沿滑线增量生成节点编号。

SMOOTH

将此参数设置为平滑分数 *f*，以圆整滑线段之间线段的不连续性。默认值为0。极限为 ![](../graphics/key_eqn01076.gif)。

### **如果省略GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行以指定形成滑线的节点。每行最多输入16个整数值。

### **如果包含GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行以指定形成滑线的节点。




