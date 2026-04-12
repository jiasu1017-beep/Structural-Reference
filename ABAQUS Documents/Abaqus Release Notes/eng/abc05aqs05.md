# 5.5 Enhancements to the XFEM-based crack propagation capability in Abaqus/CAE







**Product: **Abaqus/CAE  

**Benefits: **In Abaqus/CAE you can specify if the stress/strain values at the element centroid, at the crack tip, or the combination of both locations are used to measure the crack propagation criterion, which increases the coverage of Abaqus product functionality.

**Description: **Abaqus/CAE now supports the options for local calculations of the stress and strain fields ahead of the crack tip. You can specify if the stress/strain values at the element centroid, at the crack tip, or the combination of both locations are used to determine if the damage initiation criterion is satisfied and to determine the crack propagation direction (if needed). 

**Abaqus/CAE Usage: **
```
Property module:
    material editor: ****Mechanical**![](../graphics/images/arrow.gif)**Damage for Traction Separation Laws****: 
    **Quade Damage**, **Maxe Damage**, **Quads Damage**, **Maxs Damage**, **Maxpe Damage**, 
    or **Maxps Damage**: ****Position**![](../graphics/images/arrow.gif)**Centroid****, **Crack tip**, or **Combined**
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Defining damage," Section 12.9.3](../usi/usi-link.md#usi-prp-mechanical-damage)




