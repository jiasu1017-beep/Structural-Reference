# *LOW DENSITY FOAM









### *LOW DENSITY FOAM指定低密度泡沫材料的属性。

此选项用于定义低密度泡沫材料的材料系数。[*LOW DENSITY FOAM](ch12abk04.md)选项必须与[*UNIAXIAL TEST DATA](ch20abk04.md)、DIRECTION=TENSION和[*UNIAXIAL TEST DATA](ch20abk04.md)、DIRECTION=COMPRESSION选项结合使用，以分别指定泡沫材料在单轴拉伸和压缩时的应力-应变响应。

**产品：**Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["低密度泡沫，" Abaqus Analysis User's Guide第22.9.1节](../usb/usb-link.md#usb-mat-clowdensfoam)
- [*UNIAXIAL TEST DATA](ch20abk04.md)

### **可选参数：**

LATERAL STRAIN DATA

使用此参数指定是否提供作为材料在拉伸和压缩时单轴响应定义一部分的横向应变数据。

如果未在单轴响应定义中指定横向应变数据，则设置LATERAL STRAIN DATA=NO（默认）。在这种情况下，横向应变假定为零（零泊松比）。

如果横向应变数据在单轴响应定义中指定，则设置LATERAL STRAIN DATA=YES。

STRAIN RATE

使用此参数定义用于本构计算的应变率度量。

设置STRAIN RATE=VOLUMETRIC以使用体积应变率。如果LATERAL STRAIN DATA=NO，这是默认值。

设置STRAIN RATE=PRINCIPAL以使用每个主变形方向的的名义应变率。

设置STRAIN RATE=MAX PRINCIPAL以使用主变形方向上的最大名义应变率。当LATERAL STRAIN DATA=YES时，这是默认且唯一的可用选项。

RATE EXTRAPOLATION

使用此参数指定超过最大指定应变率的率相关单轴应力-应变曲线的外推。

设置RATE EXTRAPOLATION=NO（默认）以防止外推。最大指定应变率对应的曲线将用于大于最大值的应变率。

设置RATE EXTRAPOLATION=YES以使用相对于应变率的斜率触发超过最大指定应变率的外推。

TENSION CUTOFF

包含此参数以指定低密度材料在拉伸时可以承受的最大主应力的拉伸截止值。拉伸截止值必须大于零。

FAIL

此参数仅在使用了TENSION CUTOFF参数时相关。

设置FAIL=NO（默认）以强制最大主应力保持在拉伸截止值以下而不删除单元。

设置FAIL=YES以允许在达到拉伸截止值时删除单元。

### **指定低密度泡沫松弛系数的数据行：**

**第一行（也是唯一一行）：**



