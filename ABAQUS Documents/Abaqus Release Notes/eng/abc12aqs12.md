# 12.12 Performing display group Boolean operations on linked viewports







**Product: **Abaqus/CAE  

**Benefits: **In the Visualization module you can now perform selected display group operations simultaneously in all linked viewports. You can also display a list of items common between linked viewports when you create display groups.

**Description: **You can now perform selected display group operations simultaneously in all linked viewports. If you select specific items for the display group by names or labels, the same display group operation is performed in all linked viewports that share the items specified. This option applies only in the Visualization module.

When you are creating a display group, you now have the option to display items common to all linked viewports in the **Method** list. For **Part instances**, viewports containing model databases or output databases are considered; for other model components, only viewports containing output databases are considered.

**Abaqus/CAE Usage: **
```
Visualization module:
    ****Viewport**![](../graphics/images/arrow.gif)**Linked Viewports****: toggle **Link viewports**, toggle **Display groups**
    ****Tools**![](../graphics/images/arrow.gif)**Display group**![](../graphics/images/arrow.gif)**Create****: toggle **Show common list between linked viewports**
```

**References: **

**Abaqus/CAE User's Guide**
- ["Linking viewports," Section 4.5.2](../usi/usi-link.md#uss-cnv-link-options)
- ["Creating or editing a display group," Section 78.2.1](../usi/usi-link.md#usv-dgp-hlp-create)




