# 45.2 Overview of symbol plot options







You can use the symbol plot options to customize the appearance of symbol plots. For data from an output database, use the [**Symbol Variable**](pt05ch42s03hlb05.md) options in the **Field Output** dialog box to select the vector or tensor quantity and optionally the component to plot. 

**Note:**If you selected a model from the current model databases, symbol plots display the primary variable, not the symbol variable. Changing the symbol variable has no effect unless you plot data from an output database.

Select ****Options**![](../graphics/images/arrow.gif)**Symbol**** from the main menu bar or click ![](../graphics/ico_plotSymbolOptions.png) in the toolbox to access the **Symbol Plot Options** dialog box. Click the following tabs to customize the appearance of symbol plots in the current viewport:- **Color & Style**: The **Color & Style** page contains the following tabs: - **Vector**: Choose to customize the appearance of arrows that represent resultant values or selected component values of a vector variable. - **Tensor**: Choose to customize the appearance of arrows that represent all principal components, all direct components, or selected components of a tensor variable.
- **Limits**: The **Limits** page contains the following tabs: - **Vector**: Choose either to specify the minimum and maximum vector values or to have Abaqus/CAE automatically compute these values. - **Tensor**: Choose either to specify the minimum and maximum tensor values or to have Abaqus/CAE automatically compute these values.
- **Labels**: The **Labels** page contains the following tabs: - **Vector**: Choose to display numerical labels for the vector values and to customize the color, font, type size, number format, and number of decimal places used for the vector values. - **Tensor**: Choose to display numerical labels for the tensor values and to customize the color, font, type size, number format, and number of decimal places used for the tensor values.

Other options such as the render style, edge visibility, deformation scale factor, and translucency are located in the [**Common Plot Options**](pt05ch43hla01.md) dialog box. If you choose to plot symbols on both the undeformed and the deformed shape, you can use the [**Superimpose Plot Options**](pt05ch43hla02.md) to customize the appearance of the undeformed shape. To learn how to customize the render style and other display characteristics of your symbol plot, see [Chapter 55, "Customizing plot display](pt05ch55.md).” For more information on tensor and field output variables, see ["Overview of field output variable selection," Section 42.5.1](pt05ch42s03hlb01.md). For more information on selecting the results step, see ["Selecting a specific results step and frame," Section 42.3.1](pt05ch42s01hlb01.md).
![](../graphics/images/black4rule.gif)For information on related topics, click the following item: - ["Customizing symbol plot appearance," Section 45.5](pt05ch45s02.md)




