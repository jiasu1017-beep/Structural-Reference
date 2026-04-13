# 58.6 Creating expression fields







Select ****Tools**![](../graphics/images/arrow.gif)**Analytical Field**![](../graphics/images/arrow.gif)**Create**** from the main menu bar in the Property module, Interaction module, or Load module to create an analytical field using an expression. Analytical fields defined using mathematical expressions are referred to as expression fields.

**To create an expression field:**

1. Open the **Create Expression Field** dialog box using one of the following methods: - From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Analytical Field**![](../graphics/images/arrow.gif)**Create****. **Tip:**You can also click **Create** in the **Analytical Field Manager**. - From the interaction editor in the Interaction module, click ![](../graphics/ico_analyticalField.png) next to the **Definition** or **Emissivity distribution** field. - From the load, boundary condition, or predefined field editor in the Load module, click ![](../graphics/ico_analyticalField.png) next to the **Distribution** field.
2. Choose **Expression field** as the **Type**, and click **Continue**.
3. In the **Name** text field, enter a name for the expression field. For information on naming objects, see ["Using basic dialog box components," Section 3.2.1](pt01ch03s02s01.md).
4. In the **Description** text field, enter a description for the expression field.
5. If you want to change the local coordinate system for the expression field, click **Edit** and use one of the following methods: - Select an existing datum coordinate system in the viewport. - Select an existing datum coordinate system by name. 1. From the prompt area, click **Datum CSYS List** to display a list of datum coordinate systems. 2. Select a name from the list, and click **OK**. - Click **Use Global CSYS** from the prompt area to revert to the global coordinate system.
6. Build your expression in the expression window of the editor using a combination of the following procedures: - Select a parameter name from the list on the left side of the editor. The parameter names that are available depend on the type of coordinate system that you select: - **Rectangular**: **X**, **Y**, and **Z** are the values on the *X*-, *Y*-, and *Z*-axes, respectively. - **Cylindrical**: **R**, **Th**, and **Z** are the values on the *R*-, ![](../graphics/usi_eqn00065.gif)-, and *Z*-axes, respectively. - **Spherical**: **R**, **Th**, and **P** are the values on the *R*-, ![](../graphics/usi_eqn00065.gif)-, and ![](../graphics/usi_eqn00226.gif)-axes, respectively. The parameter name appears in the expression window. - Select an operation, function, or constant from the **Operators** list on the right side of the editor. For more information, see ["Overview of operations and functions in expressions," Section 58.2.2](pt06ch58s02s02.md). The selected operation, function, or constant appears in the expression window. - Use standard mouse and keyboard editing techniques in the expression window to position the cursor and configure your expression. Parameter names and operators are case sensitive. - Adjust [the syntax of your expression](pt06ch58s01.md) if necessary; parentheses may be needed. - Click **Clear Expression** to clear the entire expression in the expression window.
7. Click **OK** to create the expression field and to exit the editor.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Using the interaction editors," Section 15.13](pt03ch15s13.md)
- ["Using the load editors," Section 16.9](pt03ch16s09.md)
- ["Using the boundary condition editors," Section 16.10](pt03ch16s10.md)
- ["Using the predefined field editors," Section 16.11](pt03ch16s11.md)
- [Chapter 58, "The Analytical Field toolset](pt06ch58.md)"




