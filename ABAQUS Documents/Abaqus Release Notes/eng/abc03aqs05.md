# 3.5 Additional criteria for creating soft elements







**Product: **Abaqus/CAE  

**Benefits: **During a topology optimization, Abaqus creates soft elements that have a negligible influence on the stiffness of the resulting structure but are still relevant for the number of degrees of freedom of the structure. Choosing to delete soft elements is recommended when you are optimizing a nonlinear model because those elements would otherwise degenerate or collapse and prevent Abaqus from converging on a solution. Additional criteria have been added that define when an element is considered soft.

**Description: **You specify the criteria for creating soft elements when you create a topology optimization task. The additional criteria are:
- Maximum shear strain
- Minimum principal strain
- Maximum elastoplastic strain
- Volume compression

In addition, if you choose the standard or aggressive criteria, you can prevent isolated soft elements from being removed by choosing to delete only soft elements that have neighboring soft elements.

**Abaqus/CAE Usage: **
```
Optimization module:
    ****Task**![](../graphics/images/arrow.gif)**Create****, **Name:** *task name*, **Type:** **Topology optimization**, **Advanced** 
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Configuring advanced options" in "Configuring a topology optimization task," Section 18.6.2](../usi/usi-link.md#usi-opz-topo-taskconfigure-general-advanced)




