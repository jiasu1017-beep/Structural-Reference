# 76.8 Controlling shell thickness display







If you use shell elements to model relatively thin components in your analysis, you can use the ****View**![](../graphics/images/arrow.gif)**Part Display Options**** and the ****View**![](../graphics/images/arrow.gif)**Assembly Display Options**** menu options to view the actual thickness of these shell elements in your model. Displaying shell thickness enables you to examine the thickness of shell geometry relative to the rest of the model. You can apply a scale factor to reduce or increase the display of shell thickness for your session. [Figure 76--7](pt07ch76hla07.md#usv-gen-shellthickness-example) shows the effect of scale factor changes displayed on the stiffened plate model described in ["Example: blast loading on a stiffened plate," Section 10.5 of Getting Started with Abaqus: Interactive Edition](../gsa/gsa-link.md#gsa-mat-exablastload).

**Figure 76–7** From top to bottom: shell thickness scale factor settings of 1 (default), 2, and 4.

![](../graphics/uss-dsp-shellthickness-graphic.png)

Abaqus/CAE renders shell thickness for three-dimensional shell elements only; thickness is not displayed for axisymmetric shell elements, such as SAX1 elements. When shell thickness is displayed, Abaqus/CAE also renders the edges of shell geometry unless a view cut is displayed in the viewport. Abaqus/CAE renders shell thickness according to the current settings for color coding and translucency. When these settings change, the color and translucency of the shell thickness change as well.

If a discrete field has been used to define shell thicknesses or the shell offset, the **Render shell thickness** option has no effect. The shells are always displayed with zero thickness and no offset.

**To control shell thickness display:**

1. Locate the **Render shell thickness** option. From the main menu bar, select ****View**![](../graphics/images/arrow.gif)**Part Display Options**** or ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****. In the dialog box that appears, click the **General** tab.
2. From the bottom of the dialog box, toggle on **Render shell thickness** to display shell thicknesses for the shell sections in your model.
3. If desired, apply a **Scale factor** to the shell thicknesses to increase or decrease their thickness. The default value is 1, which produces a realistic rendering of the shell thickness settings.
4. Click **OK** to implement your changes and to close the dialog box. Abaqus/CAE displays the shell sections in the selected part or assembly with the appropriate thickness. Your changes are saved for the duration of the session.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Defining sections," Section 12.2.3](pt03ch12s02s03.md)
- [Chapter 76, "Customizing geometry and mesh display](pt07ch76.md)"
- ["Controlling shell thickness display," Section 55.12.6](pt05ch55s12hlb06.md)




