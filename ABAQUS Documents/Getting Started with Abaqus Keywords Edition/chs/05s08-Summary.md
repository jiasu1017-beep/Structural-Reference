# 5.8 小结

壳单元的横截面行为可以通过壳厚度方向的数值积分（<a rel="xbook" href="../key/key-link.htm#usb-kws-mshellsection"><span class="abqkeywordnostar">*SHELL SECTION</span></a>）来确定，也可以使用在分析开始时计算的横截面刚度（<a rel="xbook" href="../key/key-link.htm#usb-kws-mshellgensect"><span class="abqkeywordnostar">*SHELL GENERAL SECTION</span></a>）来确定。

- <a rel="xbook" href="../key/key-link.htm#usb-kws-mshellgensect"><span class="abqkeywordnostar">*SHELL GENERAL SECTION</span></a> 效率很高，但只能用于线性材料。<a rel="xbook" href="../key/key-link.htm#usb-kws-mshellsection"><span class="abqkeywordnostar">*SHELL SECTION</span></a> 可同时用于线性和非线性材料。
- 数值积分在壳厚度方向的多个截面点处执行。这些截面点是输出单元变量的位置。默认的最外层截面点位于壳的表面上。
- 壳单元法线的方向决定了单元的正负表面。为了正确定义接触和解释单元输出，必须知道哪个表面是哪个表面。壳法线还定义了作用于单元的正压力载荷的方向，并可在 Abaqus/Viewer 中绘制。
- 壳单元使用每个单元局部的材料方向。在大位移分析中，局部材料轴随单元转动。<a rel="xbook" href="../key/key-link.htm#usb-kws-morientation"><span class="abqkeywordnostar">*ORIENTATION</span></a> 可用于定义非默认的局部坐标系。单元变量（如应力和应变）以局部方向输出。
- <a rel="xbook" href="../key/key-link.htm#usb-kws-mtransform"><span class="abqkeywordnostar">*TRANSFORM</span></a> 为节点定义局部坐标系。集中载荷和边界条件施加在局部坐标系中。默认情况下，所有打印的节点输出（如位移）也引用局部坐标系。
- 符号图可以帮助您可视化模拟结果。它们对于可视化结构的运动和载荷路径特别有用。
