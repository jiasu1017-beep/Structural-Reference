# 5.2.2 孔隙压力接触中的压力和流体流动

### 5.2.2 孔隙压力接触中的压力和流体流动

**产品：** Abaqus/Standard

Abaqus/Standard提供了用于建模完全饱和多孔介质的基于表面的能力。基于表面的能力可用于小滑动或有限滑动。仅考虑垂直于表面的流动；无法模拟切向流动。

### 无限界面渗透率的接触界面孔隙流体约束
![](../graphics/stm_eqn07652.gif)![](../graphics/stm_eqn07653.gif)
设和是界面两侧的孔隙压力。如果界面渗透率被认为是无限的（即对流体流动没有阻力），则要求界面两侧的孔隙压力始终相等：
![](../graphics/stm_eqn07654.gif)![](../graphics/stm_eqn05787.gif)![](../graphics/stm_eqn05788.gif)![](../graphics/stm_eqn07655.gif)
类似地，设和是垂直于界面两侧的体积流率密度，并设是界面法向方向上两侧的相对速度。

假设界面充满流体至分离阈值。因此，连续性要求
![](../graphics/stm_eqn07656.gif)
而差值对应于穿过界面的流量的两倍。
![](../graphics/stm_eqn07657.gif)
是未定的，在无限渗透率情况下应被视为独立变量。翻转这些方程得
![](../graphics/stm_eqn07658.gif)
### 有限界面渗透率的接触界面孔隙流体约束

![](../graphics/stm_eqn02390.gif)对于有限间隙渗透率，直接穿过界面的体积流率密度为

![](../graphics/stm_eqn07659.gif)假设界面充满流体至分离阈值。因此，连续性要求

垂直于界面两侧的体积流率密度为

![](../graphics/stm_eqn07660.gif)其中

和是底层材料渗透率。

![](../graphics/stm_eqn07661.gif)### 瞬态方程

![](../graphics/stm_eqn07662.gif)![](../graphics/stm_eqn07663.gif)![](../graphics/stm_eqn07664.gif)界面虚功方程及其线性化形式首先以包括有限滑动的通用形式获得。然后将方程专门化到Abaqus中实现的各种公式。

由于我们希望在界面两侧实现力和体积流率平衡，并在孔隙压力中获得连续性，我们将以下积分添加到虚功方程：

其中是任意拉格朗日乘子，是界面面积。消除和使用对的合适选择，

我们得到
![](../graphics/stm_eqn07665.gif)![](../graphics/stm_eqn02890.gif)![](../graphics/stm_eqn01047.gif)![](../graphics/stm_eqn05787.gif)![](../graphics/stm_eqn05788.gif)![](../graphics/stm_eqn02890.gif)
其中
![](../graphics/stm_eqn07666.gif)
由于Abaqus使用位移（而不是速度）和在上的积分的通量，方程可以乘以得到
![](../graphics/stm_eqn07667.gif)
其中是沿界面法向方向增量的变化。线性化得
![](../graphics/stm_eqn07668.gif)![](../graphics/stm_eqn00883.gif)![](../graphics/stm_eqn00883.gif)
### 闭合接触
![](../graphics/stm_eqn07669.gif)![](../graphics/stm_eqn07670.gif)![](../graphics/stm_eqn07404.gif)
如果两侧局部处于接触状态，和；因此，虚功简化为
![](../graphics/stm_eqn07671.gif)
类似地，线性化形式简化为

![](../graphics/stm_eqn07672.gif)![](../graphics/stm_eqn06487.gif)### 稳态方程

![](../graphics/stm_eqn07673.gif)对于稳态分析，可以省略瞬态项，而流体流动项以速率形式编写。在这种情况下，我们可以假设界面位移消失，这导致简化的虚功贡献

![](../graphics/stm_eqn07674.gif)及其线性化形式

### 小滑动

当使用小滑动接触公式时，线性化虚功方程中的项、、、将消失。
![](../graphics/stm_eqn07675.gif)
### 参考
![](../graphics/stm_eqn07676.gif)
### 参考

![](../graphics/stm_eqn07677.gif)![](../graphics/stm_eqn07678.gif)![](../graphics/stm_eqn07679.gif)![](../graphics/stm_eqn07680.gif)"Abaqus Analysis User's Guide"第37.4.1节"孔隙流体接触属性"
