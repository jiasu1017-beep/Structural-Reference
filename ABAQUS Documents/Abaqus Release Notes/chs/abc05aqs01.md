# 5.1 欧拉单元中材料的局部坐标系定义





**产品：** Abaqus/Explicit

**优势：** 现在可以为欧拉单元中的材料定义局部坐标系。因此，基于方向性的材料可以与欧拉单元一起使用。

**说明：** 在欧拉截面定义中，现在可以为一个或多个材料定义方向。Abaqus/Explicit 会随着材料流过单元面重新映射材料方向。各向异性线弹性材料、正交各向异性线弹性材料、各向异性超弹性材料以及具有 Hill 塑性的材料现在可以与欧拉单元一起使用。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["欧拉分析，" 第 14.1.1 节](../usb/usb-link.md#usb-anl-aeuleriananalysis)

**Abaqus Keywords Reference Guide**
- [*EULERIAN SECTION](../key/key-link.md#usb-kws-meulsection)
- [*ORIENTATION](../key/key-link.md#usb-kws-morientation)
