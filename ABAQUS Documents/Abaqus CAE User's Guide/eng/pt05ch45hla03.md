# 45.4 Producing a symbol plot of free body nodal forces







You can create a symbol plot that shows the summation of free body nodal forces at individual nodes in your model. The symbol field output variable FREEBODY is the sum of the individual NFORC*n* components at a node, but with the vector’s direction reversed. The FREEBODY output variable also takes into account the displayed elements by default; in contrast, contour plots of NFORC1 consider the whole model.

The FREEBODY symbol plot is a representation of the unbalanced forces acting on the object that is represented by the current display group. This sensitivity to current display group is not exhibited in any other context, such as contour plots. 

**To produce a symbol plot displaying nodal forces as free body cuts:**

1. [Open the output database](pt02ch09s06hlb02.md) containing your analysis results with NFORC data included.
2. Select the results [step and frame](pt05ch42s01hlb01.md) to display.
3. If desired, focus in on a subset of your model [using a display group](pt07ch78s02hlb01.md).
4. Select **FREEBODY** as the [symbol field output variable](pt05ch42s03hlb05.md) to display. The symbol plot state is activated.
5. Select the plot state--independent and symbol plot [customization](pt05ch40s03s03.md) options you want.
6. From the main menu bar, select ****Plot**![](../graphics/images/arrow.gif)**Symbols**** to modify whether to plot the symbols on the deformed model shape, the undeformed shape, or both. **Tip:**You can also produce a symbol plot using the deformed ![](../graphics/ico_plotSymbolDeformed.png), undeformed ![](../graphics/ico_plotSymbolUndeformed.png), or superimposed ![](../graphics/ico_plotSymbolDefUndef.png) symbol tools in the toolbox. The current viewport changes to display a customized symbol plot of free body nodal forces at the specified step and frame of the current output database for the current display group. Abaqus automatically refreshes your symbol plot each time you click **Apply** in the step and frame selector dialog box, plot state--independent options, superimpose plot options (if applicable), or symbol plot options dialog boxes.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Selecting the symbol field output variable," Section 42.5.5](pt05ch42s03hlb05.md)
- ["Overview of symbol plot options," Section 45.2](pt05ch45hla01.md)
- ["Resultant forces and moments on free body cuts in Abaqus/CAE," Section 67.1](pt06ch67s01.md)




