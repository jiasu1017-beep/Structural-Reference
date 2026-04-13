# 63.4 Creating discrete fields for material volume fractions







The volume fraction tool is used to create discrete fields representing the overlap between two part instances on an element-by-element basis. One of the part instances must be a meshed Eulerian part. The other part instance acts as reference geometry. The discrete field that is created associates each element in the Eulerian part with a volume fraction based on the amount of space that the reference part instance occupies within that element. This discrete field can be used to assign materials in an Eulerian model (see ["Assigning materials to Eulerian part instances," Section 28.4](pt04ch28s04.md)). For an overview on using the volume fraction tool in Eulerian models, refer to ["The volume fraction tool," Section 28.5](pt04ch28s05.md).

The volume fraction tool is available in the Interaction module and the Load module. Select ****Tools**![](../graphics/images/arrow.gif)**Discrete Field**![](../graphics/images/arrow.gif)**Volume Fraction Tool**** from the main menu bar to create a discrete field using the volume fraction tool.

**To create a discrete field for material volume fractions:**

1. From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Discrete Field**![](../graphics/images/arrow.gif)**Volume Fraction Tool****.
2. In the viewport, select a meshed Eulerian part instance. The discrete field that is created will be associated with the elements in this Eulerian part. **Warning:**You should not regenerate or edit the Eulerian part mesh after using the volume fraction tool. Any changes to the mesh---including regenerating it from replay or journal files---may invalidate the created discrete field.
3. In the viewport, select a reference part instance that intersects the previously selected Eulerian part instance. This part instance must be a three-dimensional solid or a three-dimensional shell. The reference part instance cannot contain free edges or interior dividing faces (free or non-manifold edges). **Note:**If the reference instance consists of meshed geometry, Abaqus/CAE always uses the meshed representation of the part instance to calculate volume fractions. If the reference instance is partially meshed, only the meshed portion of the part is considered in the volume fraction calculations. The **Volume Fraction Tool** dialog box appears.
4. In the **Name** text field, enter a name for the discrete field. For information on naming objects, see ["Using basic dialog box components," Section 3.2.1](pt01ch03s02s01.md).
5. In the **Description** text field, enter a description for the discrete field.
6. To change the Eulerian instance or reference instance, click **Edit**, and select a new part instance in the viewport.
7. Specify the **Accuracy** (**Low**, **Medium**, or **High**) for the volume fraction calculations. A lower accuracy results in faster performance for the tool.
8. Specify the **Material location**: - Selecting **Inside reference instance** implies that the material will be assigned to the region that is occupied or enclosed by the reference instance. A nonzero value is assigned to all Eulerian elements within this region. - Selecting **Outside reference instance** implies that the material will be assigned to the region that is not occupied or enclosed by the reference instance. A nonzero value is assigned to all elements that are not fully occupied or enclosed by the reference instance.
9. Specify a **Scale factor** between zero and one. All values in the discrete field are multiplied by this scale factor. By default, the scale factor is one.
10. To create a set of all nodes connected to elements with nonzero volume fractions in the discrete field, toggle on **Node set**, and enter a name for the set.
11. To create a set of all elements connected to elements with nonzero volume fractions in the discrete field, toggle on **Element set**, and enter a name for the set.
12. Click **OK** to create the discrete field and to close the **Volume Fraction Tool** dialog box.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Assigning materials to Eulerian part instances," Section 28.4](pt04ch28s04.md)
- ["The volume fraction tool," Section 28.5](pt04ch28s05.md)
- ["Using the Discrete Field toolset," Section 63.1](pt06ch63s01.md)




