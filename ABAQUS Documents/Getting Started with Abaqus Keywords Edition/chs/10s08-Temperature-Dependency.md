# 10.8 大变形网格设计

我们知道，橡胶支座角落处的单元变形是不可取的。这些区域的结果不可靠；如果增加载荷，分析可能会失败。这些问题可以通过使用更好的网格设计来纠正。[图 10-67](#gss-simulation) 显示了一种改进网格设计的示例，该设计可用于减少橡胶模型左下角的单元变形。

<div class="figure">
<p><a name="gss-simulation"></a><strong>图 10-67</strong> 在仿真过程中最大限度地减少橡胶模型左下角单元变形的改进网格。</p>

![](../graphics/gss-simulation-v.png)
</div>

关于对角处网格变形的问题将在["减少体积锁定的技术"](/ch10s09.html)，第 10.9 节中讨论。左下角区域的单元在初始未变形配置中现在变形得更严重。然而，随着分析的进行和单元的变形，它们的形状实际上得到了改善。变形形状图（见[图 10-68](#gss-displaced)）说明该区域的单元变形程度已减小；然而，橡胶模型右下角的网格变形程度仍然显著。

<div class="figure">
<p><a name="gss-displaced"></a><strong>图 10-68</strong> 改进网格的变形形状。</p>

![](../graphics/gss-displaced-v.png)
</div>

最大主应力的等值线（见[图 10-69](#modified-mesh)）显示，该角落的局部应力仅略有减少。

<div class="figure">
<p><a name="modified-mesh"></a><strong>图 10-69</strong> 改进网格中最大主应力的等值线。</p>

![](../graphics/gss-modified-mesh-v.png)
</div>

大变形问题的网格设计比小位移问题更困难。必须生成在整个分析过程中单元形状都合理的网格，而不仅仅是在开始时。你必须利用经验、手工计算或粗有限元模型的结果来估计模型将如何变形。
