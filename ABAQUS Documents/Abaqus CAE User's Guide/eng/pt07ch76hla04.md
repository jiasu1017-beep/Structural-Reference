# 76.5 Defining mesh feature edges







You can specify that only the feature edges of a meshed part are visible, as described in ["Controlling edge visibility," Section 76.3](pt07ch76hla02.md). You use feature edges to mask the detail provided by a mesh; feature edges are typically the physical edges of the part being meshed and do not include all the additional element edges. [Figure 76--5](pt07ch76hla04.md#usi-featangle-partassembly) shows a meshed part displayed at three different feature angles—0, 5, and 20.

**Figure 76–5** Plots showing feature angles of 0, 5, and 20.

![](../graphics/usi-featangle-partassembly.png)

Feature edges are defined as adjacent edges with normals that differ by more than the “feature angle.” You can customize the feature angle when you select **Feature** mesh edge visibility. Larger angles will reduce the number of feature edges; conversely, smaller angles will cause more edges to be visible. The default mesh feature angle is 20.

**To set a mesh feature angle:**

1. Locate the feature angle option. From the main menu bar, select ****View**![](../graphics/images/arrow.gif)**Part Display Options**** or ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****. In the dialog box that appears, click the **General** tab.
2. From the bottom of the dialog box, select **Feature edges** from the list of mesh edges to show. Abaqus/CAE displays an **Angle** data field to the right of **Feature**.
3. Click the **Angle** data entry field, and enter the desired feature angle.
4. Click **OK** to implement your changes and to close the dialog box. Your changes are saved for the duration of the session.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Controlling edge visibility," Section 76.3](pt07ch76hla02.md)
- [Chapter 76, "Customizing geometry and mesh display](pt07ch76.md)"




