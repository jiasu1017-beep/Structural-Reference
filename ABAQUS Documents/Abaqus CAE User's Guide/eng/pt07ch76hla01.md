# 76.2 Choosing a render style







Render style is the style in which Abaqus/CAE displays your model. You can use the ****View**![](../graphics/images/arrow.gif)**Part Display Options**** and ****View**![](../graphics/images/arrow.gif)**Assembly Display Options**** menu items to display your model in one of three render styles: wireframe, hidden, or shaded; these styles are shown in [Figure 76--1](pt07ch76hla01.md#cae-render). An explanation of these choices follows.

**Figure 76–1** Model showing render style options. From left to right: the wireframe, hidden, and lightsource-shaded render styles.

![](../graphics/cae-render.png)

**Wireframe**

Displays model edges; both interior and exterior edges are potentially visible. Wireframe plots produce a frame-like visual effect in which model faces are not displayed. Wireframe is the most rapidly drawn render style.

**Hidden**

Displays a wireframe plot in which edges obscured by the model are either not shown or are shown as dotted lines, depending on which option you select. (For more information on this option, see ["Controlling edge visibility," Section 76.3](pt07ch76hla02.md).) Hidden plots produce a solid rather than frame-like appearance.

**Shaded**

Displays a filled plot in which a light source appears to be directed at the model. Shaded plots produce a highly three-dimensional visual effect. Edges attached to faces in shaded plots are always drawn in black.

**To control render style:**

1. Locate the **Render Style** options. From the main menu bar, select ****View**![](../graphics/images/arrow.gif)**Part Display Options**** or ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****. In the dialog box that appears, click the **General** tab.
2. From the top of the dialog box, click **Wireframe**, **Hidden**, or **Shaded** to select the style that you want. **Tip:**You can also select the render style using the wireframe ![](../graphics/ico_displayWire.png), hidden ![](../graphics/ico_displayHidden.png) , and shaded ![](../graphics/ico_displayShaded.png) icons located in the **Render Style** toolbar.
3. Click **OK** to implement your changes and to close the dialog box. Abaqus/CAE renders the display in the selected style, and your changes are saved for the duration of the session.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- [Chapter 76, "Customizing geometry and mesh display](pt07ch76.md)"
- ["Choosing a render style," Section 55.2.1](pt05ch55s02hlb01.md)




