# 10.3 Enhancement to the contact detection tool in Abaqus/CAE







**Product: **Abaqus/CAE  

**Benefits: **You can now include model instances when you search for contact pairs involving different regions on the same instance. This enhancement improves the usability of the contact detection tool in Abaqus/CAE.

**Description: **    The contact detection algorithm has been extended to include model instances when you search for contact pairs involving different regions on the same instance.

**Abaqus/CAE Usage: **
```
Interaction module:
    ****Interaction**![](../graphics/images/arrow.gif)**Find contact pairs****: select **Whole model** or select **Instance** and child part instances 
    from the viewport, toggle on **Include pairs with surfaces on the same instance** 
```

**References: **

**Abaqus/CAE User's Guide**
- ["The contact detection algorithm," Section 15.6.2](../usi/usi-link.md#usi-itn-auto-detection-algorithm)
- ["Specifying search criteria for contact detection," Section 15.16.1](../usi/usi-link.md#usi-itn-help-detection-criteria)




