# 6.3 蠕变模型增强





**产品：** Abaqus/Standard

**优势：** 通过引入三个新的蠕变模型（Anand、Darveaux 和双幂律）增强了经典偏应力蠕变行为。这三个蠕变定律特别适合建模电子封装中焊料合金的行为，并已被证明可在各种温度和应变率下产生准确的结果。

**说明：** 三个新的蠕变模型（Anand、Darveaux 和双幂律）已在 Abaqus/Standard 中实现。这些模型可用于定义金属蠕变行为以及两层粘塑性材料的粘性行为。

双幂律模型由两个项组成，引入两种蠕变机制的效应：攀移（低应力）和组合滑移/攀移（高应力）。

Darveaux 模型同时考虑了一次和二次蠕变。二次蠕变由标准双曲正弦定律描述，该定律经过修改以包含一次蠕变效应。温度依赖性通过 Arrhenius 型项引入。

Anand 模型使用双曲正弦模型描述蠕变应变，该模型通过引入单个内部变量（变形阻力）进行修改。该变量表示对非弹性变形的各向同性阻力，其演化由单独的速度方程定义。温度依赖性由 Arrhenius 型项描述，并通过使初始变形阻力成为温度的函数以及硬化/软化参数成为温度和蠕变应变率的函数来实现。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["率相关塑性：蠕变和膨胀，" 第 23.2.4 节](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["两层粘塑性，" 第 23.2.11 节](../usb/usb-link.md#usb-mat-cviscous)

**Abaqus Keywords Reference Guide**
- [*CREEP](../key/key-link.md#usb-kws-mcreep)
- [*VISCOUS](../key/key-link.md#usb-kws-mviscous)
