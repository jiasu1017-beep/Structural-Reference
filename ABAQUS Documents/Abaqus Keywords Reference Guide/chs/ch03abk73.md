# *CONTACT STABILIZATION






### *CONTACT STABILIZATION为通用接触定义接触稳定化控制。

可以使用此选项的多个实例来为 Abaqus/Standard 中的通用接触定义接触稳定化控制。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["Abaqus/Standard 中通用接触的稳定化，" Abaqus 分析用户指南第 36.2.5 节](../usb/usb-link.md#usb-cni-agenlcontstabilize)
- [*CONTACT](ch03abk54.md)

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中定义接触稳定化随时间变化的缩放因子的幅值曲线名称。如果省略此参数，缩放因子将在步骤中从 1 线性减少到 0。

RANGE

将此参数设置为稳定化变为零的间隙值；当表面之间的分离超过此值时，不应用任何接触稳定化。默认情况下，此间隙由 Abaqus/Standard 根据接触表面上的小平面尺寸计算。

REDUCTION PER INCREMENT

将此参数设置为一个因子，Abaqus/Standard 将使用该因子每增量减少接触稳定化系数。对于此选项数据行上指定相互作用的默认值为 0.1。

RESET

包含此参数以取消涉及先前步骤中出现的非默认幅值的接触稳定化规范的结转效果。此参数不能与任何其他参数结合使用。如果包含此参数，则没有数据行。

SCALE FACTOR

将此参数设置为一个因子，Abaqus/Standard 将使用该因子缩放接触稳定化系数。对于此选项数据行上指定的相互作用的默认值为 1。

设置 SCALE FACTOR=USER ADAPTIVE 以根据数据行上指定的模式，在每个增量内的迭代过程中按因子减少接触稳定化系数。

TANGENT FRACTION

将此参数设置为一个因子，该因子仅在切向方向缩放接触稳定化系数。默认值为零，这样在切向方向不应用接触稳定化。

### **如果省略了 RESET 参数时的数据行：**

**第一行：**

根据需要重复此数据行。

### **如果 SCALE FACTOR=USER ADAPTIVE 时的数据行：**

**第一行：**




