# 45.3 Producing a results symbol plot







A symbol plot shows either the magnitude and direction of a vector or tensor variable at a specified step and frame of an output database or the magnitude and direction of model attributes at a specified step of a model in the current model database. Abaqus/CAE represents the values as symbols (for example, arrows) at locations on your model. For more information on tensor and field output variables, see ["Overview of field output variable selection," Section 42.5.1](pt05ch42s03hlb01.md). For more information on selecting the results step, see ["Selecting a specific results step and frame," Section 42.3.1](pt05ch42s01hlb01.md). To learn how to display the minimum and maximum values associated with your symbol plot, see ["Customizing the legend," Section 56.1](pt05ch56s01.md).

**To produce a symbol plot:**

1. [Open the model database or the output database](pt02ch09s06hlb02.md) containing your model data or analysis results.
2. If you are plotting data from a model database, switch to the Visualization module, expand the **Model Database** container of the Results Tree, and select the model you want to use.
3. Select the results [step and frame](pt05ch42s01hlb01.md) to display (or just the step, if the current model database is selected).
4. For output databases, select the [symbol field output variable](pt05ch42s03hlb05.md) to display. For model databases, select the [primary field output variable](pt05ch42s03hlb03.md) as the variable to display. The symbol plot state is activated.
5. Select the plot state--independent and symbol plot [customization](pt05ch40s03s03.md) options you want.
6. If your chosen field output includes complex numbers, select the [**Complex Form**](pt05ch42s04hlb05.md) tab in the **Result Options** dialog box to control the numeric form to display. This option applies only to plots for output databases.
7. For plots of output database data, select ****Plot**![](../graphics/images/arrow.gif)**Symbols**** from the main menu bar to modify whether to plot the symbols on the deformed model shape, the undeformed shape, or both. **Tip:**You can also produce a symbol plot using the deformed ![](../graphics/ico_plotSymbolDeformed.png), undeformed ![](../graphics/ico_plotSymbolUndeformed.png), or superimposed ![](../graphics/ico_plotSymbolDefUndef.png) symbol tools in the toolbox. The current viewport changes to display a customized symbol plot of the specified field output variable at the specified step and frame of the current output database. Abaqus automatically refreshes your symbol plot each time you click **Apply** in the step and frame selector dialog box, plot state--independent options, superimpose plot options (if applicable), or symbol plot options dialog boxes.

![](../graphics/images/black4rule.gif)For information on related topics, click the following item: - ["Overview of symbol plot options," Section 45.2](pt05ch45hla01.md)




