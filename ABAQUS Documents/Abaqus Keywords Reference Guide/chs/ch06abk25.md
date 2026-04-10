# *FLUID FLUX





### *FLUID FLUX改变流体填充腔中的流体量。

此选项用于指定使用静水流体单元建模的流体填充腔中流体量的变化。

**产品：**Abaqus/Standard   Abaqus/Explicit   

**类型：**历史数据  

**级别：**步骤  

##### **参考：**

- ["流体交换定义，" Abaqus Analysis User's Guide第11.5.3节](../usb/usb-link.md#usb-anl-afluidcavityexchange)

### **可选参数：**

AMPLITUDE

将此参数设置为幅值与时间曲线的名称，该曲线定义步骤中质量流率的大小（["幅值曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。如果省略此参数，则无论步骤中使用何种过程，参考幅值都将在步骤开始时立即应用。

OP

对于现有流体通量保持不变，将OP=MOD（默认）设置为此选项定义要添加（对于没有流体通量载荷的腔）或修改（对于有流体通量载荷的腔）的流体通量。

如果应该删除应用于模型的所有现有流体通量，则设置OP=NEW。

### **定义流体质量流率的数据行：**

**第一行（唯一行）：**
