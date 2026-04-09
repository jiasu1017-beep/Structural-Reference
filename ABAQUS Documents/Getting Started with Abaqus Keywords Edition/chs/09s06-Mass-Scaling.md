# 9.6 能量平衡

能量输出通常是Abaqus/Explicit分析的重要组成部分。各种能量分量之间的比较可用于评估分析是否产生了适当的响应。

## 9.6.1 能量平衡方程

整个模型的能量平衡可以写成：

![能量平衡公式](../graphics/gsk_eqn00217.gif)

其中，![E_I](../graphics/gsk_eqn00218.gif) 是内能，![E_VD](../graphics/gsk_eqn00219.gif) 是粘性能量耗散，![E_FD](../graphics/gsk_eqn00220.gif) 是摩擦能量耗散，![E_K](../graphics/gsk_eqn00221.gif) 是动能，![E_H](../graphics/gsk_eqn00222.gif) 是内热能，![W_Ext](../graphics/gsk_eqn00223.gif) 是外部施加载荷所做的功，![W_Pen](../graphics/gsk_eqn00224.gif)、![W_Con](../graphics/gsk_eqn00225.gif) 和![W_Mass](../graphics/gsk_eqn00226.gif) 分别是接触罚函数、约束罚函数和推进附加质量所做的功。![E_Ext_H](../graphics/gsk_eqn00227.gif) 是通过外部通量的外部热能。这些能量分量之和为![E_Total](../graphics/gsk_eqn00228.gif)，该值应保持恒定。在数值模型中，![E_Total](../graphics/gsk_eqn00228.gif) 只是近似恒定，通常误差小于1%。

**内能**

内能是以下各项之和：可恢复的弹性应变能 ![E_SE](../graphics/gsk_eqn00229.gif)；通过塑性等非弹性过程耗散的能量 ![E_PD](../graphics/gsk_eqn00230.gif)；通过粘弹性或蠕变耗散的能量 ![E_CD](../graphics/gsk_eqn00231.gif)；人工应变能 ![E_AE](../graphics/gsk_eqn00232.gif)；通过损伤耗散的能量 ![E_DMD](../graphics/gsk_eqn00233.gif)；通过畸变控制耗散的能量 ![E_DC](../graphics/gsk_eqn00234.gif)；以及流体腔能量 ![E_FC](../graphics/gsk_eqn00235.gif)：

![内能公式](../graphics/gsk_eqn00236.gif)

人工应变能包括存储在沙漏阻力和壳单元及梁单元横向剪切中的能量。人工应变能的较大值表明需要网格细化或对网格进行其他更改。

**粘性能量**

粘性能量是通过阻尼机制耗散的能量，包括体积粘性阻尼和材料阻尼。作为全局能量平衡中的基本变量，粘性能量不是通过粘弹性或非弹性过程耗散的能量的一部分。

**施加力的外功**

外功是连续向前积分的，完全由节点力（力矩）和位移（转角）定义。规定的边界条件也会对外功做出贡献。

## 9.6.2 能量平衡的输出

每个能量值都可以请求输出，并且可以绘制为整个模型、特定单元集、单个单元或每个单元内能量密度的时间历程。与整个模型或单元集求和的能量值相关联的变量名称如表9-2所示。

**表9-2** 整体模型能量输出变量。

| 变量名称 | 能量值 |
|----------|--------|
| ALLIE | 内能，![E_I](../graphics/gsk_eqn00218.gif)：ALLIE = ALLSE + ALLPD + ALLCD + ALLAE + ALLDMD + ALLDC + ALLFC |
| ALLKE | 动能，![E_K](../graphics/gsk_eqn00221.gif) |
| ALLVD | 粘性耗散能量，![E_VD](../graphics/gsk_eqn00219.gif) |
| ALLFD | 摩擦耗散能量，![E_FD](../graphics/gsk_eqn00220.gif) |
| ALLCD | 通过粘弹性耗散的能量，![E_CD](../graphics/gsk_eqn00231.gif) |
| ALLWK | 外力做的功，![W_Ext](../graphics/gsk_eqn00223.gif) |
| ALLPW | 接触罚函数做的功，![W_Pen](../graphics/gsk_eqn00224.gif) |
| ALLCW | 约束罚函数做的功，![W_Con](../graphics/gsk_eqn00225.gif) |
| ALLMW | 推进附加质量（由于质量缩放）做的功，![W_Mass](../graphics/gsk_eqn00226.gif) |
| ALLSE | 弹性应变能，![E_SE](../graphics/gsk_eqn00229.gif) |
| ALLPD | 非弹性耗散能量，![E_PD](../graphics/gsk_eqn00230.gif) |
| ALLAE | 人工应变能，![E_AE](../graphics/gsk_eqn00232.gif) |
| ALLIHE | 内热能，![E_H](../graphics/gsk_eqn00222.gif) |
| ALLHF | 通过外部通量的外部热能，![E_Ext_H](../graphics/gsk_eqn00237.gif) |
| ALLDMD | 通过损伤耗散的能量，![E_DMD](../graphics/gsk_eqn00233.gif) |
| ALLDC | 通过畸变控制耗散的能量，![E_DC](../graphics/gsk_eqn00234.gif) |
| ALLFC | 流体腔能量（流体腔所做功的负值），![E_FC](../graphics/gsk_eqn00235.gif) |
| ETOTAL | 能量平衡：![能量平衡公式1](../graphics/gsk_eqn00238.gif) ![能量平衡公式2](../graphics/gsk_eqn00239.gif) |

此外，Abaqus/Explicit可以生成单元级能量输出和能量密度输出，如表9-3所示。

**表9-3** 单元能量输出变量。

| 变量名称 | 单元能量值 |
|----------|-----------|
| ELSE | 弹性应变能 |
| ELPD | 塑性耗散能量 |
| ELCD | 蠕变耗散能量 |
| ELVD | 粘性耗散能量 |
| ELASE | 人工能量 = 钻孔能量 + 沙漏能量 |
| EKEDEN | 单元内的动能密度 |
| ESEDEN | 单元内的弹性应变能密度 |
| EPDDEN | 单元内耗散的塑性能量密度 |
| EASEDEN | 单元内的人工应变能密度 |
| ECDDEN | 单元内耗散的蠕变应变能密度 |
| EVDDEN | 单元内耗散的粘性能量密度 |
| ELDMD | 单元内通过损伤耗散的能量 |
