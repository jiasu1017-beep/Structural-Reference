# 6.7 总结

*Getting Started with Abaqus: Keywords Edition*

梁单元的行为可以通过截面的数值积分来确定（使用 `*BEAM SECTION` 或 `*BEAM GENERAL SECTION`），也可以直接通过面积、惯性矩和扭转常数来给定（使用 `*BEAM GENERAL SECTION`）。

当使用数值积分的 `*BEAM GENERAL SECTION` 时，计算在模拟开始时进行一次，并假定为弹性行为。

Abaqus 包含许多标准截面形状。其他形状，只要是"薄壁"的，可以使用 `SECTION`=`ARBITRARY` 进行建模。

截面的方向必须通过指定第三个节点或作为单元属性定义的一部分来定义向量来指定。方向可以在 Abaqus/Viewer 中绘制。

梁截面可以相对于定义梁的节点进行偏移。此方法可用于在壳上建模加筋肋。

线性和二次梁单元包含剪切变形的影响。Abaqus/Standard 中的三次梁单元不考虑剪切柔性。Abaqus/Standard 中的开口截面梁单元能够正确地模拟薄壁开口截面中的扭转和翘曲（包括翘曲约束）的影响。

多点约束、约束方程和连接器可用于连接节点处的自由度，以建模铰接连接、刚性连接等。

"弯矩"类型绘图允许轻松可视化一维单元（如梁）的结果。

显示选项允许您渲染梁截面轮廓，以增强对未变形和变形图形表示。

可以以 PostScript (PS)、封装 PostScript (EPS)、标签图像文件格式 (TIFF)、便携式网络图形 (PNG) 和可缩放矢量图形 (SVG) 格式获取 Abaqus/Viewer 图形的硬拷贝。
