# 3.1 Sizing optimization







**Product: **Abaqus/CAE  

**Benefits: **You can now create a sizing optimization that optimizes a shell model by modifying the thickness of the shell elements. 

**Description: **In addition to topology and shape optimization, you can now create a sizing optimization. Sizing optimization is applied to shell parts and optimizes the thickness of the shell elements in the design area. When you configure a sizing optimization, you can specify that selected regions should contain “clusters” of shell elements of equal thickness. You can use clustering to generate strengthening ribs or rings in the sheet metal structure you are optimizing or to define borders between regions of equal thickness. Clustered regions can be reproduced in manufacturing using sheets of constant thickness; for example, a vehicle “body in white” formed by welding and stamping individual sheet metal structures.

When you view the results of a sizing optimization, by default the Visualization module displays the thickness of the shell elements.

**Abaqus/CAE Usage: **
```
Optimization module:
    ****Task**![](../graphics/images/arrow.gif)**Create****, **Name:** *optimization task name*, **Type:** **Sizing optimization**
```

**References: **

**Abaqus/CAE User's Guide**
- ["Creating an optimization task," Section 18.6.1](../usi/usi-link.md#usi-opz-topo-taskeditor)
- ["Configuring a sizing optimization task," Section 18.6.4](../usi/usi-link.md#usi-opz-sizing-taskconfigure)

**Abaqus Example Problems Guide**
- ["Sizing optimization of a gear shift control holder," Section 11.3.1](../exa/exa-link.md#exa-opt-gearshift)
- ["Sizing optimization of a car door," Section 11.3.2](../exa/exa-link.md#exa-opt-cardoorsizing)




