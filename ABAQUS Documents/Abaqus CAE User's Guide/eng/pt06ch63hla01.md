# 63.2 Creating discrete fields







The Discrete Field toolset is available in the Property module, Interaction module, and Load module. Select ****Tools**![](../graphics/images/arrow.gif)**Discrete Field**![](../graphics/images/arrow.gif)**Create**** from the main menu bar to create a discrete field. 

**To create a discrete field:**

1. From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Discrete Field**![](../graphics/images/arrow.gif)**Create****. **Tip:**You can also click **Create** in the **Discrete Field Manager**.
2. In the **Name** text field, enter a name for the discrete field. For information on naming objects, see ["Using basic dialog box components," Section 3.2.1](pt01ch03s02s01.md).
3. In the **Description** text field, enter a description for the discrete field.
4. Choose **Elements** or **Nodes** to specify the type of location to which the field will be applied.
5. Choose the data type. - Choose **Scalar** to enter scalar field data. - The **Orientation** option is available for fields associated with elements. Choose **Orientation**, and do the following: 1. Choose the coordinate system type---**Cartesian**, **Cylindrical**, or **Spherical**. 2. Toggle on **Supplied orientation directions are defined in part space** to specify that the orientation directions are defined at the part or part instance level. When you define the orientations in the part space, Abaqus transforms the orientation values from the part's coordinate system into the assembly coordinate system using the part instance transformation. Toggle off this option to specify that the orientation directions are defined at the assembly level. - Choose **Prescribed condition** to include degree of freedom values in the field data.
6. Enter the default component value or values. For information on how Abaqus uses the default values, see ["Evaluating discrete fields," Section 63.3](pt06ch63hla02.md). Scalar discrete fields require one default component value. Orientation discrete fields require six default component values. Prescribed condition discrete fields require six default component values and up to six degree of freedom values.
7. In the **Field Data** table, enter the following values: - Element or node number and its associated component value or values. When creating discrete fields that will be used with assembly-level or history objects, such as loads or interactions, you must specify the complete name of the node or element numbers, as described in ["Naming conventions" in "Defining an assembly," Section 2.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ipartassy-naming). For example, you would specify the part instance name and element id using the notation *Part_instance_name.EID*, such as `PART-2--1.20`. - For prescribed condition discrete fields, enter the degree of freedom values. Click mouse button 3 on the table to see a menu that allows you to do the following:- Cut, copy, and paste values - Insert and delete rows - Clear a table cell or the entire table - Read from or write to a comma-separated file For more information, see ["Entering tabular data," Section 3.2.7](pt01ch03s02s07.md).
8. Click **OK** to create the discrete field and to exit the editor.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Defining sections," Section 12.2.3](pt03ch12s02s03.md)
- [Chapter 23, "Composite layups](pt04ch23.md)"




