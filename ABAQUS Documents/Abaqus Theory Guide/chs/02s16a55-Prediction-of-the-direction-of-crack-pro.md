# 2.16.4 裂纹扩展方向预测

### 2.16.4 裂纹扩展方向预测

**产品：** Abaqus/Standard

![](../graphics/stm_eqn02707.gif)![](../graphics/stm_eqn02707.gif)![](../graphics/stm_eqn02641.gif)![](../graphics/stm_eqn02708.gif)已经提出了各种标准来预测预存裂纹将扩展的角度。这些标准包括最大切向应力准则（[Erdogan and Sih, 1963](07s01a01-References.md)）、最大主应力准则（[Maiti and Smith, 1983](07s01a01-References.md)）、最大能量释放率准则（[Palaniswamy and Knauss, 1978](07s01a01-References.md), 和 [Hussain, Pu, and Underwood, 1974](07s01a01-References.md)）、最小弹性能量密度准则（[Sih, 1973](07s01a01-References.md)）和T准则（[Theocaris, 1982](07s01a01-References.md)）。这些标准预测初始裂纹扩展的角度略有不同，但它们都有这样的含义：当裂纹扩展时在裂纹尖端处![](../graphics/stm_eqn02707.gif)[Cotterell and Rice, 1980](07s01a01-References.md)）。在Abaqus/Standard中，我们为均匀、各向同性线弹性材料提供了三个准则：最大切向应力准则、最大能量释放率准则和![](../graphics/stm_eqn02707.gif)则。在下文中不考虑![](../graphics/stm_eqn02641.gif)因为对于![](../graphics/stm_eqn02709.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn02709.gif)中*r*和![](../graphics/stm_eqn02710.gif)![](../graphics/stm_eqn02711.gif)裂纹扩展方向可以使用条件![](../graphics/stm_eqn02710.gif)![](../graphics/stm_eqn02711.gif)得；即，

![](../graphics/stm_eqn02712.gif)![](../graphics/stm_eqn02713.gif)![](../graphics/stm_eqn02714.gif)![](../graphics/stm_eqn02715.gif)![](../graphics/stm_eqn02716.gif)![](../graphics/stm_eqn02717.gif)![](../graphics/stm_eqn02718.gif)![](../graphics/stm_eqn02712.gif)中裂纹扩展角度![](../graphics/stm_eqn02714.gif)示"直前方"方向的裂纹扩展。![](../graphics/stm_eqn02713.gif)考虑长度为*a*的裂纹段，以角度![](../graphics/stm_eqn02719.gif)![](../graphics/stm_eqn02720.gif)![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02640.gif)![](../graphics/stmfracmech-crack-direct-crit.png) 当*a*与所有其他几何长度（包括主裂纹的长度）相比无限小时，假设裂纹尖端的应力强度因子![](../graphics/stm_eqn02719.gif)![](../graphics/stm_eqn02720.gif)以表示为主裂纹 kink 前存在的应力强度因子![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02721.gif)![](../graphics/stm_eqn02713.gif)![](../graphics/stm_eqn02722.gif)![](../graphics/stm_eqn02721.gif)数![](../graphics/stm_eqn02722.gif)的![](../graphics/stm_eqn02713.gif)依赖性由[Hayashi and Nemat-Nasser (1981)](07s01a01-References.md)和[He and Hutchinson (1989)](07s01a01-References.md)给出。

对于裂纹段，我们也有关系

![](../graphics/stm_eqn02723.gif)![](../graphics/stm_eqn02723)

![](../graphics/stm_eqn02724.gif)最大能量释放率准则假定主裂纹沿使![](../graphics/stm_eqn02724.gif)大化的方向初始扩展。
### KII = 0准则

![](../graphics/stm_eqn02725.gif)该准则简单地假定裂纹将沿使![](../graphics/stm_eqn02725.gif)方向初始扩展。

![](../graphics/stm_eqn02707.gif)从图2.16.4-1可以看出，最大能量释放率准则和![](../graphics/stm_eqn02707.gif)则预测大致相同的裂纹扩展角度。相比之下，最大切向应力准则预测较小的裂纹扩展角度。
### 参考

### 参考

"Abaqus Analysis User's Guide"第11.4.2节"轮廓积分评估"
