# 3.6 New design responses







**Product: **Abaqus/CAE  

**Benefits: **You can now create scaled element centroidal von Mises stress and energy stiffness measure design responses. 

**Description: **The energy stiffness measure design response is now available when you create general topology and sizing optimizations. In addition, the scaled, element centroidal, von Mises stress design response is now available when you create a general topology optimization. The energy stiffness measure has no physical meaning but can be used as an objective function or a constraint to optimize the stiffness of a structure that is subjected to both external loading and prescribed displacements.  

**Abaqus/CAE Usage: **
```
Optimization module:
    ****Design Response**![](../graphics/images/arrow.gif)**Create****, **Name:** *design response name*,     **Type:** **Single-term**, **Variable**: **Stress** or **Energy stiffness measure** 
```

**Reference: **

**Abaqus Analysis User's Guide**
- ["Design responses," Section 13.2.1](../usb/usb-link.md#usb-anl-aoptdesignresponses)




