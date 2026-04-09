# 6.4 Example: cargo crane

A light-service, cargo crane is shown in [Figure 6–11](#gss-cargo-static). You have been asked to determine the static deflections of the crane when it carries a load of 10 kN. You should also identify the critical members and joints in the structure: i.e., those with the highest stresses and loads. Because this is a static analysis you will analyze the cargo crane using Abaqus/Standard.

**Figure 6–11** Sketch of a light-service cargo crane.

![](../graphics/gss-cargo.png)

The crane consists of two truss structures joined together by cross bracing. The two main members in each truss structure are steel box beams (box cross-sections). Each truss structure is stiffened by internal bracing, which is welded to the main members. The cross bracing connecting the two truss structures is bolted to the truss structures. These connections can transmit little, if any, moment and, therefore, are treated as pinned joints. Both the internal bracing and cross bracing use steel box beams with smaller cross-sections than the main members of the truss structures. The two truss structures are connected at their ends (at point E) in such a way that allows independent movement in the 3-direction and all of the rotations, while constraining the displacements in the 1- and 2-directions to be the same. The crane is welded firmly to a massive structure at points A, B, C, and D. The dimensions of the crane are shown in [Figure 6–12](#gss-cargo-crane-dim). In the following figures, truss A is the structure consisting of members AE, BE, and their internal bracing; and truss B consists of members CE, DE, and their internal bracing.

**Figure 6–12** Dimensions (in m) of the cargo crane.

![](../graphics/gss-cargo-crane-dim-nls.png)

The ratio of the typical cross-section dimension to global axial length in the main members of the crane is much less than 1/15. The ratio is approximately 1/15 in the shortest member used for internal bracing. Therefore, it is valid to use beam elements to model the crane.

## 6.4.1 Coordinate system

You should use the default global rectangular Cartesian coordinate system shown in [Figure 6–11](#gss-cargo-static) and [Figure 6–12](#gss-cargo-crane-dim). Locate the origin of the coordinate system midway between points A and D. If you build your model with a different origin or orientation of the coordinate system, ensure that the input data in your model reflect your coordinate system and not the one shown here.

## 6.4.2 Mesh design

The cargo crane will be modeled with three-dimensional, slender, cubic beam elements (B33). The cubic interpolation in these elements allows us to use a single element for each member and still obtain accurate results under the applied bending load. The mesh that you use in the simulation is shown in [Figure 6–13](#gss-cargo-crane).

**Figure 6–13** Mesh for cargo crane.

![](../graphics/gss-cargo-crane-v.png)

The welded joints in the crane provide complete continuity of the translations and rotations from one element to the next. You, therefore, need only a single node at each welded joint in the model. The bolted joints, which connect the cross bracing to the truss structures, and the connection at the tip of the truss structures are different. Since these joints do not provide complete continuity for all nodal degrees of freedom, separate nodes are needed for each element at the connection. Appropriate constraints between these separate nodes must then be given by using the `*MPC`, `*BOUNDARY`, or `*EQUATION` options. The `*MPC` and `*EQUATION` options are discussed in more detail later.

The node numbers for the various members of the cargo crane model are shown in [Figure 6–14](#gss-crane-model1-v).

**Figure 6–14** Node numbers in crane model.

![](../graphics/gss-crane-model1-v-nls.png)

These are the node numbers from the input file given in "Cargo crane," Section A.4. Separate nodes have been defined on the cross-bracing elements and the truss structures that they connect. Separate nodes are also needed at the end of each truss structure, point E in [Figure 6–11](#gss-cargo-static). The node numbers in your model may be different from those shown here.

The element numbers for the various members of the cargo crane model are shown in [Figure 6–15](#gss-crane-model2-v).

**Figure 6–15** Element numbers in crane model.

![](../graphics/gss-crane-model2-v-nls.png)

These are the element numbers from the input file given in "Cargo crane," Section A.4. The element numbers in your model may be different from those shown here.

## 6.4.3 Preprocessing—creating the model

The full input file for this example is `crane.inp`, and it is available in "Cargo crane," Section A.4. The Abaqus input options used to create the nodes and elements shown on the preceding pages can be found in "Cargo crane," Section A.4. If you wish to create the entire model using Abaqus/CAE, refer to "Example: cargo crane," Section 6.4 of Getting Started with Abaqus: Interactive Edition.

## 6.4.4 Reviewing the input file—the model data

This section describes how the model data are described in the input file for this example. These data include the descriptions for the input file heading, its nodes and elements, beam sections and orientations, constraints, and boundary conditions.

**Heading**

The heading used in this example provides a short description of the model and the units used:

```
*HEADING
44	3-D model of light-service cargo crane
45	S.I. Units (m, kg, N, sec)
```

**Nodal coordinates and element connectivity**

Define the nodal coordinates in a `*NODE` option block. If you decide to do this with an editor, you may want to use the mesh generation commands found in "Cargo crane," Section A.4. In this example, a node set called `ATTACH` is created; this node set contains the nodes at points A, B, C, and D, the points at which the crane is attached to the parent structure.

```
*NSET, NSET=ATTACH
46	100, 107, 200, 207
```

Create elements in your model that correspond to the elements shown in [Figure 6–15](#gss-crane-model2-v), but remember that your numbering may be different. (Having the same numbering will make defining some modeling features easier, however.) There are several element sets that you will need in this simulation. As the elements are defined, they are grouped into following element sets:

```
OUTA	    100, 101, 102, 103, 104, 105, 106
BRACEA	  110, 111, 112, 113, 114
OUTB	    200, 201, 202, 203, 204, 205, 206
BRACEB	  210, 211, 212, 213, 214
CROSSEL	 300, 301, 302, 303, 304, 305, 306, 307
```

where these element numbers refer to those elements shown in [Figure 6–15](#gss-crane-model2-v). The element sets `OUTA` and `OUTB` contain the main outer members for the two truss structures. Element sets `BRACEA` and `BRACEB` contain the elements modeling the internal bracing within each truss structure. Element set `CROSSEL` contains the cross bracing that connects the two truss structures.

**Beam element properties**

Since the material behavior in this simulation is assumed to be linear elastic, use the `*BEAM GENERAL SECTION` option to define the section properties. All of the beams in this structure have a box-shaped cross-section.

A box-section is specified using the parameter `SECTION`=`BOX`. The first data line contains the section dimensions, which are the dimensions *a*, *b*, *t1*, *t2*, *t3*, and *t4* shown in [Figure 6–16](#gss-localbeam) for a box section. The dimensions shown in [Figure 6–16](#gss-localbeam) are for the main members of the two trusses in the crane.

**Figure 6–16** Cross-section geometry and dimensions (in m) of the main members.

![](../graphics/gss-localbeam-nls.png)

The beam section axes for the main members should be oriented such that the beam 1-axis is orthogonal to the plane of the truss structures shown in the elevation view ([Figure 6–12](#gss-cargo-crane-dim)) and the beam 2-axis is orthogonal to the elements in that plane. Specify this orientation by giving the approximate direction of the beam 1-axis (the *n1*-vector) on the second data line of the `*BEAM GENERAL SECTION` option. To get the correct normal, *n*, in this case, you need to provide a very accurate *n1*. It is somewhat easier to provide an approximate direction, which would be the negative 3-direction. However, given the logic that Abaqus uses to determine *n* given *t* and *n1*, the normal *n* is rotated slightly from its proper orientation if we use this approximate *n1*. You can specify the same *n1*-direction for all elements in each of the two truss structures. The third data line contains the elastic and shear moduli, assuming a mild strength steel with *E* = 200.0 GPa, *nu* = 0.25, and *G* = 80.0 GPa. These modeling data are included in the input file in the following option blocks:

```
*BEAM GENERAL SECTION, SECTION=BOX, ELSET=OUTA
51	0.10,0.05,0.005,0.005,0.005,0.005
52	-0.1118, 0.0, -0.9936 
53	200.E9,80.E9
54	*BEAM GENERAL SECTION, SECTION=BOX, ELSET=OUTB
55	0.10,0.05,0.005,0.005,0.005,0.005
56	-0.1118, 0.0, 0.9936 
57	200.E9,80.E9
```

The dimensions of the beam sections for the bracing members are shown in [Figure 6–17](#gss-crosssect-geom). Both the cross bracing and the bracing within each truss structure have the same beam section geometry, but they do not share the same orientation of the beam section axes. Therefore, separate `*BEAM GENERAL SECTION` options must be used. The bracing is made from the same steel as the main members.

**Figure 6–17** Cross-section geometry and dimensions (in m) of the bracing members.

![](../graphics/gss-crosssect-geom-nls.png)

The approximate *n1*-vector for the internal truss bracing is the same as for the main members of the respective truss structures. The following input defines the element properties of this bracing:

```
*BEAM GENERAL SECTION, SECTION=BOX, ELSET=BRACEA
58	0.03,0.03,0.003,0.003,0.003,0.003
59	-0.1118, 0.0, -0.9936
60	200.E9,80.E9
61	*BEAM GENERAL SECTION, SECTION=BOX, ELSET=BRACEB
62	0.03,0.03,0.003,0.003,0.003,0.003
63	-0.1118, 0.0, 0.9936
64	200.E9,80.E9
```

We make some assumptions so that the orientation of the cross bracing is somewhat easier to specify. All of the beam normals (*n*-vectors) should lie approximately in the plane of the plan view of the cargo crane (see [Figure 6–12](#gss-cargo-crane-dim)). This plane is skewed slightly from the global 1–3 plane. Again, a simple method for defining such an orientation is to provide an approximate *n1*-vector that is orthogonal to this plane on the element property options. The vector should be nearly parallel to the global 2-direction. Since the angle between the normals from one element to the next is always greater than 20º, the normals are not averaged at the nodes.

Depending on the exact orientation of the members in the cross bracing, it is possible that we would have to define the normals individually for each of the cross-bracing elements. Such an exercise would be very similar to what you have already done by defining the normals for the two truss structures. Since the square cross-bracing members are subjected to primarily axial loading, their deformation is not sensitive to cross-section orientation. Therefore, we accept the default normals that Abaqus calculates to be correct. The approximate *n1*-vector for the cross bracing is aligned with the *y*-axis. The following option block specifies the cross-bracing:

```
*BEAM GENERAL SECTION, SECTION=BOX, ELSET=CROSSEL
65	0.03,0.03,0.003,0.003,0.003,0.003
66	0.0,1.0,0.0
67	200.E9,80.E9
```

**Beam section orientation**

In this model you will have a modeling error if you provide data that only define the orientation of the approximate *n1*-vector. The averaging of beam normals at the nodes (see "Beam element curvature," Section 6.1.3) causes Abaqus to use incorrect geometry for the cargo crane model. To see this, you can use Abaqus/Viewer to display the beam section axes and beam tangent vectors (see "Postprocessing," Section 6.4.7). However, the normals in the crane model appear to be correct in Abaqus/Viewer; yet, they are, in fact, slightly incorrect. You can also find such modeling mistakes by examining the averaged nodal normals that are printed in the data (`crane.dat`) file. Some of the normals in the incorrect model of the cargo crane are shown in the following output:

![](../graphics/gss-c6-node-def-input-nls.png)

The problem is the normal vector for node 102, which does not match those at the other nodes defining the lower, main member in truss A (see [Figure 6–14](#gss-crane-model1-v)). Four elements (101, 102, 112, and 113) contain node 102. When the averaging of beam normals at nodes produces multiple independent normals, the additional normals at the node are also printed in the data file (see "Beam element curvature," Section 6.1.3, for details). The correct geometry for the crane model requires three independent beam normals at node 102: one each for the bracing elements 112 and 113 and a single normal for elements 101 and 102. The normal shown above for node 102 is not the normal needed for elements 101 and 102. If it were, it would match the normals shown for nodes 100, 101, or 103. Nor is it the correct normal for either of the other two elements, whose normals are printed in the data file, as shown below.

```
                          N O R M A L   D E F I N I T I O N S

 ELEMENT NODE           NORMAL               ELEMENT  NODE              NORMAL

     100  101  -0.1820  0.9831  2.0481E-02       101   101  -0.1820      0.9831  2.0481E-02
     101  102  -0.1820  0.9831  2.0481E-02       102   102  -0.1820      0.9831  2.0481E-02
     102  103  -0.1820  0.9831  2.0481E-02       103   103  -0.1820      0.9831  2.0481E-02
     103  104  -0.1820  0.9831  2.0504E-02       104   105   6.1600E-02 -0.9981 -6.9312E-03
```

In this table element 113 shows no normal for either of its nodes, node 102 and node 105. Thus, the normal shown for node 102 above in the NODE DEFINITIONS table was the average of the normals from elements 101, 102, and 113. Using the Abaqus logic for averaging normals, we could have predicted that the normals at the nodes of element 113 would be averaged with the normals for the adjacent elements. For this problem the important part of the averaging logic is that normals that subtend an angle less than 20º with the reference normal are averaged with the reference normal to define a new reference normal. In the case of the normals at node 102, the original reference normal is the normal for elements 101 and 102. Since the normal for element 113 at node 102 subtends an angle less than 20º with the original reference normal, it is averaged with the normals for elements 101 and 102 at node 102 to define the new reference normal at that node. On the other hand, since the normal for element 112 subtends an angle of approximately 30º with the original reference normal, it has an independent normal at node 102, as shown in the data file.

This incorrect average normal means that elements 101, 102, and 113 have a section geometry that exhibits curvature about the beam axis from one end of the element to the other, which is not the intended geometry. You must use the `*NORMAL` option to define the normals at node 102 for element 113 explicitly. Explicitly specifying the normal directions prevents Abaqus from applying its averaging algorithm. You must also use `*NORMAL` for the corresponding elements on the opposite side of the crane: element 213, node 202 of truss B.

There is also a problem with the normals at nodes 104 and 204 at the tip of each truss structure, again because the angle between elements 103 and 104 is less than 20º. Since we are modeling straight beam elements, the normals are constant at both nodes in each element. Thus, the `*NORMAL` option block that you should put in your input file has six data lines. If you used the numbering scheme shown in [Figure 6–14](#gss-crane-model1-v) and [Figure 6–15](#gss-crane-model2-v), the following option block should be added to your input file:

![](../graphics/gss-c6-node-normal-input-nls.png)

**Multi-point constraints**

The cross bracing, unlike the internal truss bracing, is bolted to the truss members. You can assume that these bolted connections are unable to transmit rotations or torsion. The duplicate nodes that were defined at these locations are needed to define this constraint. In Abaqus such constraints between nodes can be defined using multi-point constraints (MPCs) or constraint equations.

Multi-point constraints allow constraints to be imposed between different degrees of freedom of the model. A large library of MPCs is available in Abaqus. (See "Linear constraint equations," Section 35.2.1 of the Abaqus Analysis User's Guide, for a complete list and a description of each one.) The format of the `*MPC` option is

```
*MPC
<type of MPC>,<node 1 or node set 1>,<node 2 or node set 2>, ......
```

You can define multiple constraints of the same type with just a single data line by using node sets. The MPC type needed to model the bolted connection is PIN. The pinned joint created by this MPC constrains the displacements at two nodes to be equal, but the rotations, if they exist at the nodes, remain independent.

There are many bolted joints in the crane model. The following is the complete `*MPC` option block for the model from "Cargo crane," Section A.4:

```
*MPC
76	PIN,101,301
77	PIN,102,302
78	PIN,103,303
79	PIN,105,305
80	PIN,106,306
81	PIN,201,401
82	PIN,202,402
83	PIN,203,403
84	PIN,205,405
85	PIN,206,406
```

Add a similar option block to your model, changing the node numbers to correspond to those in your model. If all of the nodes on the two truss structures had been grouped into a node set called `TRUSNODE` and all of the nodes on the cross bracing had been grouped into a node set called `CROSNODE`, the option block could have been shortened to the following:

```
*NSET, NSET=TRUSNODE, UNSORTED
86	101,102,103,105,106,201,202,203,205,206
87	*NSET, NSET=CROSNODE, UNSORTED
88	301,302,303,305,306,401,402,403,405,406
89	*MPC
90	PIN, TRUSNODE, CROSNODE
```

If a node set is provided as the first item after the MPC type, the second item can be either another node set or a single node. When the data line of an `*MPC` option contains a node set and then a single node, as shown below, Abaqus creates an MPC constraint between each node in the set and the individual node specified. For example, the following option block would create a pinned joint between node 301 and each node in node set `TRUSNODE`.

```
*MPC
91	PIN, TRUSNODE, 301
```

**Constraint equations**

Constraints between nodal degrees of freedom can also be specified with linear equations by using the `*EQUATION` option. The form of each equation is

![](../graphics/gsk_eqn00075.gif)

where *a*i is the coefficient associated with degree of freedom *i*. Each linear constraint equation requires at least two data lines. The number of terms, *n*, involved in the equation is given on the first data line beneath the `*EQUATION` option. On the subsequent data lines the format is

```
<><><><><><><><><>
```

Exactly four terms must be given on each data line except the final one, which can have fewer terms.

In the crane model the tips of the two trusses are connected together such that degrees of freedom 1 and 2 (the translations in the 1- and 2-directions) of each tip node are equal, while the other degrees of freedom (3–6) at the nodes are independent. We need two linear constraints, one equating degree of freedom 1 at node 104 to degree of freedom 1 at node 204:

![](../graphics/gsk_eqn00088.gif)

and the other equating degree of freedom 2 at node 104 to degree of freedom 2 at node 204:

![](../graphics/gsk_eqn00089.gif)

You may have to change the node numbers if you created this model using a preprocessor. The following option block defines the appropriate constraints at point E in the crane model (see [Figure 6–11](#gss-cargo-static)):

```
*EQUATION
92	2
93	104,1,1.0, 204,1,-1.0
94	2
95	104,2,1.0, 204,2,-1.0
```

The degrees of freedom at the first node defined in an `*MPC` or `*EQUATION` are eliminated from the stiffness matrix. Therefore, these nodes should not appear in other MPCs or constraint equations. Nor should boundary conditions be applied to the eliminated degrees of freedom.

**Boundary conditions**

The crane is attached firmly to the parent structure. The following `*BOUNDARY` option block constrains all of the nodes at the attachment points, which should have been grouped into node set `ATTACH`:

```
*BOUNDARY
96	ATTACH, ENCASTRE
```

## 6.4.5 Reviewing the input file—the history data

The following options specify a static, linear perturbation simulation:

```
*STEP, PERTURBATION
97	Static tip load on crane
98	*STATIC
```

**Loading**

A concentrated load of 10 kN is applied in the negative *y*-direction to node 104. Since there is a constraint equation connecting the *y*-displacement of nodes 104 and 204, the load is carried equally by both nodes. The following `*CLOAD` option block provides an equal load on both nodes:

```
*CLOAD
99	104,2,-1.0E4
```

**Output requests**

Write the displacements (U) and reaction forces and moments (RF) at the nodes, and the section forces and moments (SF) in the elements to the output database for postprocessing with Abaqus/Viewer, as shown in the following option blocks:

```
*OUTPUT, FIELD
100	*NODE OUTPUT
101	U, RF
102	*ELEMENT OUTPUT
103	SF,
104	*END STEP
```

## 6.4.6 Running the analysis

Store the input in a file called `crane.inp`. Run the analysis using the command:

```
abaqus job=crane
```

## 6.4.7 Postprocessing

Start Abaqus/Viewer by typing the following command at the operating system prompt:

```
abaqus viewer odb=crane
```

Abaqus/Viewer plots the undeformed shape of the crane model.

**Plotting the deformed model shape**

To begin this exercise, plot the deformed model shape with the undeformed model shape superimposed on it. Specify a nondefault view using (0, 0, 1) as the *X*-, *Y*-, and *Z*-coordinates of the viewpoint vector and (0, 1, 0) as the *X*-, *Y*-, and *Z*-coordinates of the up vector.

**Tip:** You can also display the model using this view by clicking ![](../graphics/ico_viewFront.png) from the **Views** toolbar.

The undeformed shape of the crane superimposed upon the deformed shape is shown in [Figure 6–18](#gss-displaced-hoist).

**Figure 6–18** Deformed shape of cargo crane.

![](../graphics/gss-displaced-hoist-c.png)

**Using display groups to plot element and node sets**

You can use display groups to plot existing node and element sets; you can also create display groups by selecting nodes or elements directly from the viewport. You will create a display group containing only the elements associated with the main members in truss structure A.

**To create and plot a display group:**

1. In the Results Tree, expand the **Sections** container underneath the output database file named `crane.odb`.

2. To facilitate your selection, change the view back to the default isometric view using the ![](../graphics/ico_viewIso.png) tool in the **Views** toolbar.

   **Tip:** If the **Views** toolbar is not visible, select **View** ![](../images/arrow.gif) **Toolbars** ![](../images/arrow.gif) **Views** from the main menu bar.

3. In succession, click the items in the container until the elements associated with the main members in truss A are highlighted in the viewport. Click mouse button 3 on this item and select **Replace** from the menu that appears.

   Abaqus/Viewer now displays only this group of elements.

4. To save this group, double-click **Display Groups** in the Results Tree; or use the ![](../graphics/ico_displayGroupCreate.png) tool in the **Display Group** toolbar.

   The **Create Display Group** dialog box appears.

5. In the **Create Display Group** dialog box, click **Save As** and enter `MainA` as the name for your display group.

6. Click **Dismiss** to close the **Create Display Group** dialog box.

   This display group now appears underneath the **Display Groups** container in the Results Tree.

**Beam cross-section orientation**

You will now plot the section axes and beam tangents on the undeformed model shape.

**To plot the beam section axes:**

1. From the main menu bar, select **Plot** ![](../images/arrow.gif) **Undeformed Shape**; or use the ![](../graphics/ico_plotUndeformed.png) tool in the toolbox to display only the undeformed model shape.

2. From the main menu bar, select **Options** ![](../images/arrow.gif) **Common**; then, click the **Normals** tab in the dialog box that appears.

3. Toggle on **Show normals**, and accept the default setting of **On elements**.

4. In the **Style** area at the bottom of the **Normals** page, specify the **Length** to be **Long**.

5. Click **OK**.

   The section axes and beam tangents are displayed on the undeformed shape.

The resulting plot is shown in [Figure 6–19](#gss-beamsectaxes). The text annotations in [Figure 6–19](#gss-beamsectaxes) that identify the section axes and beam tangent will not appear in your image. The vector showing the local beam 1-axis, *n1*, is blue; the vector showing the beam 2-axis, *n*, is red; and the vector showing the beam tangent, *t*, is white.

**Figure 6–19** Plot of beam section axes and tangents for elements in display group `MainA`.

![](../graphics/gss-beamsectaxes-v-nls.png)

**Rendering beam profiles**

You will now display an idealized representation of the beam profile and contour the stress results.

**To render beam profiles:**

1. From the main menu bar, select **View** ![](../images/arrow.gif) **ODB Display Options**.

   The **ODB Display Options** dialog box appears.

2. In the **General** tabbed page, toggle on **Render beam profiles** and accept the default scale factor of 1.

3. Click **OK**.

   Abaqus/Viewer displays beam profiles with the appropriate dimensions and in the correct orientations. [Figure 6–20](#usi-prp-cargocrane) shows the beam profiles on the whole model. Your changes are saved for the duration of the session.

4. Click ![](../graphics/ico_plotContourDeformed.png) to contour the Mises stress on the rendered profile.

**Figure 6–20** Cargo crane with beam profiles displayed.

![](../graphics/usi-prp-cargocrane.png)

**Creating a hard copy**

You can save the current image to a file for hard-copy output.

**To create a PostScript file of the current image:**

1. From the main menu bar, select **File** ![](../images/arrow.gif) **Print**.

   The **Print** dialog box appears.

2. From the **Settings** area in the **Print** dialog box, select **Black&White** as the **Rendition** type; and toggle on **File** as the **Destination**.

3. Select **PS** as the **Format**, and enter `beam.ps` as the **File name**.

4. Click ![](../graphics/ico_selectionOptions.png).

   The **PostScript Options** dialog box appears.

5. From the **PostScript Options** dialog box, select **600 dpi** as the **Resolution**; and toggle off **Print date**.

6. Click **OK** to apply your selections and to close the dialog box.

7. In the **Print** dialog box, click **OK**.

   Abaqus/Viewer creates a PostScript file of the current image and saves it in your working directory as `beam.ps`. You can print this file using your system's command for printing PostScript files.

**Displacement summary**

Write a summary of the displacements of all nodes in display group `MainA` to a file named `crane.rpt`. The peak displacement at the tip of the crane in the 2-direction is 0.0188 m.

**Section forces and moments**

Abaqus can provide output for structural elements in terms of forces and moments acting on the cross-section at a given point. These section forces and moments are defined in the local beam coordinate system. Toggle off the rendering of beam profiles, then contour the section moment about the beam 1-axis in the elements in display group `MainA`. For clarity, reset the view so that the elements are displayed in the 1–2 plane.

**To create a "bending moment"-type contour plot:**

1. From the list of variable types on the left side of the **Field Output** toolbar, select **Primary**.

2. From the list of output variables in the center of the toolbar, select **SM**.

   Abaqus/Viewer automatically selects **SM1**, the first component name in the list on the right side of the **Field Output** toolbar, and displays a contour plot of the bending moment about the beam 1-axis on the deformed model shape. The deformation scale factor is chosen automatically since geometric nonlinearity was not considered in the analysis.

3. Open the **Common Plot Options** dialog box, and select a **Uniform** deformation scale factor of `1.0`.

   Color contour plots of this type typically are not very useful for one-dimensional elements such as beams. A more useful plot is a "bending moment"-type plot, which you can produce using the contour options.

4. From the main menu bar, select **Options** ![](../images/arrow.gif) **Contour**; or use the **Contour Options** ![](../graphics/ico_plotContourOptions.png) tool in the toolbox.

   The **Contour Plot Options** dialog box appears; by default, the **Basic** tab is selected.

5. In the **Contour Type** field, toggle on **Show tick marks for line elements**.

6. Click **OK**.

   The plot shown in [Figure 6–21](#gss-beambending) appears. The magnitude of the variable at each node is now indicated by the position at which the contour curve intersects a "tick mark" drawn perpendicular to the element. This "bending moment"-type plot can be used for any variable (not just bending moments) for any one-dimensional element, including trusses and axisymmetric shells as well as beams.

**Figure 6–21** Bending moment diagram (moment about beam 1-axis) for elements in display group `MainA`. The locations with the highest stress (created by the bending of the elements) are indicated.

![](../graphics/gss-beambending-c.png)
