# Appendix C: Using Additional Techniques to Create and Analyze a Model in Abaqus/CAE

Appendix B, "Creating and Analyzing a Simple Model in Abaqus/CAE," explains how to create and analyze a very simple model composed of only one part. In this advanced tutorial for the experienced Abaqus user you will create and analyze a more complex model. The model is more complex on two levels:

- It consists of three different parts rather than just one. This tutorial illustrates how you position instances of these parts to create the assembly and how you define contact between surfaces of the assembly.
- It includes parts that you will draw using advanced sketching techniques. You will learn how sketches, datum geometry, and partitions combine to define the features that make up individual parts. You will also learn how you can modify a part by editing a feature and how modified parts are regenerated.

As in Appendix B, "Creating and Analyzing a Simple Model in Abaqus/CAE," you will apply section properties, loads, and boundary conditions to the model; you will also mesh the model, configure the analysis, and run the analysis job. At the end of the tutorial you will view your analysis results. The entire tutorial takes approximately three hours to complete.

This tutorial assumes that you are familiar with the techniques described in Appendix B, "Creating and Analyzing a Simple Model in Abaqus/CAE," including the following:

- Using the view manipulation tools to rotate and zoom an object in the viewport.
- Following the prompts in the prompt area.
- Using the mouse to select menu items, toolbox items, and items within the viewport.

---

## C.1 Overview

During the tutorial you will create an assembly composed of a hinge held together by a pin. The assembled part instances and the final mesh are illustrated in Figure C-1.

![Model used in the hinge tutorial](../graphics/gst-tut2-figure0.png)

The tutorial consists of the following sections:

- "Creating the first hinge piece," Section C.2
- "Assigning section properties to the hinge part," Section C.3
- "Creating and modifying a second hinge piece," Section C.4
- "Creating the pin," Section C.5
- "Assembling the model," Section C.6
- "Defining analysis steps," Section C.7
- "Creating surfaces to use in contact interactions," Section C.8
- "Defining contact between regions of the model," Section C.9
- "Applying boundary conditions and loads to the assembly," Section C.10
- "Meshing the assembly," Section C.11
- "Creating and submitting a job," Section C.12
- "Viewing the results of your analysis," Section C.13

---

## C.2 Creating the first hinge piece

To start the tutorial, you create the first part -- half of the hinge. Abaqus/CAE models are composed of features; you create a part by combining features. This portion of the hinge is composed of the following features:

- A cube -- the base feature, since it is the first feature of the part.
- A flange that extends from the cube. The flange also includes a large-diameter hole through which the pin is inserted.
- A small lubrication hole in one corner of the flange.

### C.2.1 Creating the cube

To create the cube (the base feature), you create a solid, three-dimensional, extruded part and name it. You then sketch its profile (0.04 m x 0.04 m) and extrude the profile over a specified distance (0.04 m) to produce the base feature of the first half of the hinge. The desired cube is shown in Figure C-2.

![The base feature (a cube) is created first](../graphics/gst-tut2-figure1.png)

**Note:** The default render style used throughout Abaqus/CAE is **Shaded**. For clarity, many of the figures in this tutorial use the wireframe or hidden line render styles. For more information, see "Choosing a render style," Section 76.2 of the Abaqus/CAE User's Guide.

**To create the cube:**

1. Start Abaqus/CAE, and create a new model database. Resize your windows so that you can follow the tutorial and see the Abaqus/CAE main window.

   Abaqus/CAE enters the Part module and displays the Model Tree in the left side of the main window.

2. In the Model Tree, double-click the **Parts** container to create a new part.

   The **Create Part** dialog box appears.

   The text in the prompt area asks you to fill out the **Create Part** dialog. Abaqus/CAE always displays prompts in the prompt area to guide you through a procedure.

3. Name the part `Hinge-hole`. Accept the following default settings:
   - A three-dimensional, deformable body
   - A solid extrusion base feature

4. In the **Approximate size** text field, type `0.2`. You will be modeling the hinge using meters for the unit of length, and its overall length is 0.14 meters; therefore, 0.2 meters is a sufficiently large approximate size for the part. Click **Continue** to create the part.

   The Sketcher starts and displays the toolbox between the canvas and the Model Tree. Abaqus/CAE uses the approximate size of the part to compute the default sheet size -- 0.2 meters in this example. In addition, in this example the Sketcher draws 40 gridlines on the sheet, and the distance between each gridline is 0.005 meters. (You probably see fewer than 40 gridlines because the sheet extends beyond your viewport.)

5. From the Sketcher toolbox, select the rectangle tool.

6. Sketch an arbitrary rectangle, and click mouse button 2 in the viewport to exit the rectangle tool.

7. Dimension the top and left edges so that each is `0.04` m long.

   **Important:** To complete this tutorial successfully, it is important that you use the dimensions stated and do not deviate from the example; otherwise, you will find it difficult to assemble the model.

8. Click mouse button 2 to exit the Sketcher.

   **Tip:** Clicking mouse button 2 in the viewport has the same effect as clicking the default button in the prompt area -- **Done** in this instance.

   Abaqus/CAE displays the **Edit Base Extrusion** dialog box.

9. In the dialog box, type a **Depth** of `0.04` and press **[Enter]**.

   Abaqus/CAE exits the Sketcher and displays the base feature, a cube, as shown in Figure C-2. The triad in the lower-left corner of the viewport indicates the orientation of the X-, Y-, and Z-axes. You can turn off this triad by selecting **Viewport** -> **Viewport Annotation Options** from the main menu bar and toggling off the **Show triad** option. (The triad is sometimes turned off for clarity in the figures in this tutorial.)

   **Note:** By default, Abaqus/CAE uses the alphabetical option, x-y-z, for labeling the view orientation triad. In general, this guide adopts the numerical option, 1-2-3, to permit direct correspondence with degree of freedom and output labeling. For more information on labeling of axes, see "Customizing the view triad," Section 5.4 of the Abaqus/CAE User's Guide.

### C.2.2 Adding the flange to the base feature

You will now add a solid feature -- the flange -- to the base feature. You select one face of the cube to define the sketch plane and extrude the sketched profile through half the depth of the cube. The cube and flange are shown in Figure C-3.

![The flange is added to the base feature](../graphics/gst-tut2-figure2.png)

**To add the flange to the base feature:**

1. From the main menu bar, select **Shape** -> **Solid** -> **Extrude**.

2. Select the face at the front of the cube to define the sketching plane, as shown in Figure C-4.

   ![Select the gridded face to define the sketching plane](../graphics/gst-tut2-figure4-nls.png)

   When you stop moving the cursor during a selection procedure, Abaqus/CAE highlights the edges of the entity that it would select at the current cursor position. This highlighting behavior is called "preselection."

   **Note:** Two forms of preselection are available in Abaqus/CAE: one for object selection from the viewport and the other for selection from the Sketcher. For more information, see "Highlighting objects prior to selection," Section 6.3.4 of the Abaqus/CAE User's Guide, and "Turning preselection on or off," Section 20.9.3 of the Abaqus/CAE User's Guide, respectively.

3. Select an edge that will appear vertical and on the right side of the sketch, as shown in Figure C-4.

   Again, Abaqus/CAE uses preselection to aid you in selecting the desired edge.

   The Sketcher starts and displays the outline of the base feature as reference geometry. Abaqus/CAE magnifies the view to fit the sketch plane; the sheet size and grid spacing are also recalculated based on the size of the sketch plane. To change the sheet size and grid spacing back to their original settings and disable their automatic recalculation for the current session, use the options tool, located in the Sketcher toolbox. On the **General** tabbed page, toggle off **Auto** next to the sheet size text field and set the value to `0.2`; toggle off **Auto** next to the grid spacing text field and set the value to `0.005`.

   **Tip:** To retain the original sheet size and grid spacing for all sketches in a part, you can select the options tool while sketching the base feature -- the cube -- and toggle off both **Auto** settings.

   The sketch of the flange that you will create is illustrated in Figure C-5. To duplicate the view in the figure, use the options tool again to double the grid spacing.

   ![Use the Sketcher to create the flange profile](../graphics/gst-tut2-figure5.png)

4. Zoom out to view the area where you will sketch the flange:
   - From the **View Manipulation** toolbar, select the magnify tool.
   - Position the cursor near the center of the viewport.
   - Click mouse button 1 and drag to the left until the cube occupies approximately half of the visible Sketcher space.

   Reducing the view is necessary because the flange is created beyond the edges of the selected sketch plane.

5. As before, the approximate shape of the new feature will be sketched first. From the Sketcher toolbox, select the connected lines tool.

6. Sketch the rectangular portion of the flange by drawing three lines as follows:
   - Starting at any point to the right of the cube, connect the line to the top-right corner of the cube.
   - Continue the next line to the bottom-right corner of the cube. This line is automatically assigned a vertical constraint.
   - The final line extends from the bottom-right corner of the cube to any point to the right of the cube.

   **Tip:** If you make a mistake while sketching, use the Sketcher undo or delete tools to correct your error.

7. Click mouse button 2 in the viewport to exit the connected lines tool.

8. Refine the sketch by defining the following constraints and dimension:
   - Use the constraints tool to constrain the top and bottom lines of the sketch so that each is horizontal.
   - Assign an equal length constraint to these two lines (use **[Shift]+Click** to select both lines).
   - Dimension either line so that it is `0.02` m long.

   The sketch appears as shown in Figure C-6.

   ![Draw the rectangular portion of the flange](../graphics/gst-tut2-figure6.png)

9. Close the profile by adding a semicircular arc using the 3-points circle tool.
   - Select the two vertices at the open end of the rectangle as the endpoints of the arc, starting with the top one. Select any point to the right of the sketch as a point that lies on the arc.
   - Define tangent constraints between the ends of the arc and the horizontal lines to refine the sketch.

10. Click mouse button 2 in the viewport to exit the 3-points circle tool.

    The resulting arc is shown in Figure C-7.

    ![Add the curved portion of the flange](../graphics/gst-tut2-figure7.png)

11. From the Sketcher toolbox, select the center-perimeter circle tool to sketch the flange hole.
    - Place the center of the circle to coincide approximately with the center of the arc created previously. The perimeter point should be placed to the right of the center point. Apply a concentric constraint between the two circular regions.
    - Use the dimension tool to change the value of the radius to `0.01` m.
    - Dimension the vertical distance between the center of each circle and its perimeter point. Edit this dimension so that the distance is `0`. (If the distance is already `0`, you cannot add a vertical dimension.) This will adjust the location of the perimeter point so that it is on the same horizontal plane as the center point.

    **Note:** When you mesh a part, Abaqus/CAE places nodes wherever vertices appear along an edge; therefore, the location of the vertex on the circumference of the circle influences the final mesh. Placing it on the same horizontal plane as the center point results in a high-quality mesh.

12. The final sketch is shown in Figure C-8.

    ![Final sketch](../graphics/gst-tut2-figure8.png)

13. Click mouse button 2 to exit the Sketcher.

    Abaqus/CAE displays the part in an isometric view showing the base extrusion, your sketched profile, and an arrow indicating the extrusion direction. The default extrusion direction for a solid is always out of the solid. Abaqus/CAE also displays the **Edit Extrusion** dialog box.

    **Tip:** Use the auto-fit view manipulation tool to fit the sketched flange profile and the base extrusion in the viewport.

14. In the **Edit Extrusion** dialog box:
    - Accept the default **Type** selection of **Blind** to indicate that you will provide the depth of the extrusion.
    - In the **Depth** field, type an extrusion depth of `0.02`.
    - Click the flip arrow button to reverse the extrusion direction, as shown in Figure C-9.

      ![Completed flange sketch showing the extrusion direction](../graphics/gst-tut2-flipdirection.png)

    - Toggle on **Keep internal boundaries**. When you toggle this option on, Abaqus/CAE maintains the face that is generated between the extruded solid feature and the existing part. As a result, the extruded flange is maintained as a second cell and is not merged with the cube. (When you mesh the model at the end of the tutorial, the internal boundary allows you to mesh the flange without having to first partition the cell and flange into separate cells.)
    - Click **OK** to create the solid extrusion.

    Abaqus/CAE displays the part composed of the cube and the flange. Use the auto-fit view manipulation tool again to resize the part to fit in the viewport.

### C.2.3 Modifying a feature

Each part is defined by a set of features, and each feature in turn is defined by a set of parameters. For example, the base feature (the cube) and the second feature (the flange) are both defined by a sketch and an extrusion depth. You modify a part by modifying the parameters that define its features. For the hinge example you will change the radius of the hole in the sketch of the flange from 0.01 m to 0.012 m.

**To modify a feature:**

1. In the Model Tree, expand the **Hinge-hole** item underneath the **Parts** container. Then expand the **Features** container that appears.

   A list showing each feature's **Name** appears. In this example you have created two solid extrusion features: the base feature (the cube), **Solid extrude-1**, and the flange, **Solid extrude-2**.

2. Click mouse button 3 on **Solid extrude-2** (the flange) in this list.

   Abaqus/CAE highlights the selected feature in the viewport.

3. From the menu that appears, select **Edit**.

   Abaqus/CAE displays the feature editor. For an extruded solid you can change the extrusion depth, the twist or draft (if specified when the feature was created), and the profile sketch.

4. From the feature editor, click the edit sketch button.

   Abaqus/CAE displays the sketch of the second feature, and the feature editor disappears.

5. From the edit tools in the Sketcher toolbox, select the edit dimension value tool.

6. Select the radial dimension of the circle (`0.010`).

7. In the **Edit Dimension** dialog box, type a new radius of `0.012` and click **OK**.

   Abaqus/CAE closes the dialog box and changes the radius of the circle in the sketch only.

8. Click mouse button 2 to exit the edit dimension value tool. Click mouse button 2 again to exit the Sketcher.

   Abaqus/CAE again displays the feature editor.

9. Click **OK** to regenerate the flange with the modified radius and to exit the feature editor.

   The flange hole is enlarged to the new radius dimension.

   **Note:** In some circumstances regenerating a feature causes dependent features to fail. In such a case Abaqus/CAE asks if you want to save your changes and suppress the features that failed to regenerate, or if you want to revert to the unmodified feature and lose your changes.

### C.2.4 Creating the sketch plane

The flange includes a small hole used for lubrication, as shown in Figure C-10.

![Isometric shaded view of the hinge with the lubrication hole](../graphics/gst-tut2-figure10.png)

Creating the hole in the desired location requires an appropriate datum plane on which to sketch the profile of the extruded cut, as shown in Figure C-11.

![Two-dimensional view of the datum plane's position with respect to the hinge piece](../graphics/gst-tut2-datumplane-nls.png)

You sketch a circle on the datum plane, which is tangent to the flange, and Abaqus/CAE extrudes the circle normal to the datum plane and normal to the flange to create the lubrication hole.

There are three operations involved in creating the datum plane:

- Creating a datum point on the circumference of the flange.
- Creating a datum axis running between two datum points.
- Creating a datum plane through the datum point on the circumference and normal to the datum axis.

**To create the sketch plane:**

1. From the main menu bar, select **Tools** -> **Datum**.

   Abaqus/CAE displays the **Create Datum** dialog box.

2. Create a datum point along the curved edge of the flange through which the datum plane will pass. From the **Create Datum** dialog box, choose the **Point** datum type.

3. From the list of methods, click **Enter parameter**.

4. Select the curved edge, as shown in Figure C-12. Note the direction of the arrow indicating an increasing edge parameter from 0.0 to 1.0. You cannot change the direction of this arrow.

   ![Create a datum point along the curved edge of the flange](../graphics/gst-tut2-figure12-nls.png)

5. In the text box in the prompt area, enter a normalized edge parameter and press **[Enter]**. If the arrow direction is the same as in Figure C-12, enter `0.25` as the normalized edge parameter; if the arrow points in the opposite direction, enter `0.75` as the normalized edge parameter.

   Abaqus/CAE creates a datum point along the selected edge.

6. Create a datum axis that will define the normal to the datum plane. From the **Create Datum** dialog box, choose the **Axis** datum type. Click the **2 points** method.

   Abaqus/CAE highlights the points that can be used to create the datum axis.

7. Select the point at the center of the hole (created when you sketched the hole's profile) and the datum point on the curved edge.

   Abaqus/CAE displays a datum axis passing through the two points, as shown in Figure C-13.

   ![Create a datum axis defined by two datum points](../graphics/gst-tut2-figure13.png)

8. The final step is to create the datum plane normal to the datum axis. From the **Create Datum** dialog box, choose the **Plane** datum type. Click the **Point and normal** method.

9. Select the datum point on the curved edge as the point through which the datum plane will pass.

10. Select the datum axis as the edge that will be normal to the datum plane.

    Abaqus/CAE creates the datum plane, as shown in Figure C-14.

    ![Create a datum plane normal to the datum axis](../graphics/gst-tut2-figure14.png)

### C.2.5 Sketching the lubrication hole

The next operation creates the lubrication hole on the flange by extruding a circle from the datum plane that you just created. First, you need to create a datum point on the flange that indicates the center of the hole, as illustrated in Figure C-15.

![A datum point indicates the center of the lubrication hole](../graphics/gst-tut2-datumpoint-nls.png)

**To create the datum point at the center of the lubrication hole:**

1. Create a datum point along the second curved edge of the flange. From the **Create Datum** dialog box, choose the **Point** datum type.

2. From the list of methods, click **Enter parameter**.

3. Select the second curved edge of the flange, as shown in Figure C-16.

   ![Select the second edge](../graphics/gst-tut2-second-edge-nls.png)

4. Note the direction of the arrow indicating an increasing edge parameter from 0.0 to 1.0. Enter a normalized edge parameter of `0.75` (or `0.25` if the sense of the arrow is opposite that shown in Figure C-16), and press **[Enter]**.

   Abaqus/CAE creates a datum point along the selected edge.

5. From the list of methods in the **Create Datum** dialog box, select **Midway between 2 points**.

6. Select the datum point along the first curved edge.

7. Select the datum point along the second curved edge.

   Abaqus/CAE creates a datum point halfway across the flange.

8. Close the **Create Datum** dialog box.

   This exercise illustrates how you can use feature-based modeling to capture your design intent. The datum point is a feature that Abaqus/CAE defines to be midway between the datum points along the edges of the flange. As a result, if you change the thickness of the flange, the lubrication hole remains in the center.

**To sketch the lubrication hole:**

1. From the main menu bar, select **Shape** -> **Cut** -> **Extrude**.

2. Click the boundary of the datum plane to select it as the plane on which to sketch.

3. Select the top rear edge of the cube as the edge that will appear vertical and on the right side of the sketch, as shown in Figure C-17.

   ![Select the indicated edge to position the part correctly in the Sketcher grid](../graphics/gst-tut2-figure15-nls.png)

   The Sketcher starts with the vertices, datums, and edges of the part projected onto the sketch plane as reference geometry.

   **Tip:** If you are unsure of the relative orientation of the sketch plane and the part, use the view manipulation tools to rotate and pan them. Use the reset view tool to restore the original view.

4. From the Sketcher toolbox, select the circle tool.

5. Select the datum point on the center of the flange to indicate the center of the circle.

6. Select any other point, and click mouse button 1.

7. Dimension the radius of the hole. The radius of the circle should be changed to 0.003 m.

8. Dimension the vertical distance between the circle's center and perimeter points. Set this distance to zero. As noted earlier, this will improve the quality of the mesh.

9. Exit the Sketcher.

   Abaqus/CAE displays the hinge in an isometric view showing the base part and flange, your sketched hole profile, and an arrow indicating the direction for the extruded cut. Abaqus/CAE also displays the **Edit Cut Extrusion** dialog box.

10. From the **Type** menu in the **Edit Cut Extrusion** dialog box, select **Up to Face** and click **OK**.

11. Select the cylindrical inner surface of the hole in the part to indicate the face to which to extrude, as illustrated in Figure C-18.

    ![Select the face to which to extrude](../graphics/gst-tut2-inside1-nls.png)

    Abaqus/CAE extrudes the sketch from the datum plane to the hole in the flange.

12. From the **Render Style** toolbar, select the shaded display tool if necessary, and use the rotation tool to see how the part and its features are oriented, as shown in Figure C-19. (For clarity, the datum geometry has been removed from the view in Figure C-19 by selecting **View** -> **Part Display Options** -> **Datum**.)

    ![Isometric view of the first hinge](../graphics/gst-tut2-figure19.png)

    **Tip:** After you rotate the part, use the cycle views tool to step through the previous views (up to a maximum of eight) and to restore the original view.

13. Now that you have created the first part of your model, it is a good idea to save your model in a model database:
    - From the main menu bar, select **File** -> **Save**. The **Save Model Database As** dialog box appears.
    - Type a name for the new model database in the **File Name** field, and click **OK**. You do not need to include the file extension; Abaqus/CAE appends `.cae` automatically to the file name.

    Abaqus/CAE stores the model database in a new file and returns to the Part module. The name of your model database appears in the main window title bar.

    If you find you need to interrupt this tutorial, you can save the model database at any time and exit Abaqus/CAE. You can then start a new Abaqus/CAE session and open the saved model database by selecting **Open Database** from the **Start Session** dialog box. The model database will contain any parts, materials, loads, etc. that you created, and you will be able to continue the tutorial.

---

## C.3 Assigning section properties to the hinge part

The process of assigning section properties to a part is divided into three tasks:

- Creating a material.
- Creating a section that includes a reference to the material.
- Assigning the section to the part or to a region of the part.

### C.3.1 Creating a material

You will create a material named `Steel` that has a Young's modulus of 209 GPa and a Poisson's ratio of 0.3.

**To define the material:**

1. In the Model Tree, double-click the **Materials** container to create a new material.

   The **Edit Material** dialog box appears.

2. Name the material `Steel`.

3. From the editor's menu bar, select **Mechanical** -> **Elasticity** -> **Elastic**.

   Abaqus/CAE displays the **Elastic** data form.

4. In the respective fields in the **Elastic** data form, type a value of `209.E9` for Young's modulus and a value of `0.3` for Poisson's ratio.

5. Click **OK** to exit the material editor.

### C.3.2 Defining a section

Next, you will create a section that includes a reference to the material `Steel`.

**To define the section:**

1. In the Model Tree, double-click the **Sections** container to create a section.

   The **Create Section** dialog box appears.

2. In the **Create Section** dialog box:
   - Name the section `SolidSection`.
   - In the **Category** list, accept **Solid** as the default selection.
   - In the **Type** list, accept **Homogeneous** as the default selection, and click **Continue**.

   The section editor appears.

3. In the editor, accept `Steel` as the material selection and click **OK**.

   If you had defined other materials, you could click the arrow next to the **Material** text box to see a list of available materials and to select the material of your choice.

### C.3.3 Assigning the section

You will now assign the section `SolidSection` to the hinge part.

**To assign the section to the hinge part:**

1. In the Model Tree, expand the **Hinge-hole** item underneath the **Parts** container and double-click **Section Assignments** in the list that appears.

2. Drag a rectangle around the hinge piece to select the entire part.

   Abaqus/CAE highlights all the regions of the part.

3. Click mouse button 2 to indicate that you have finished selecting the regions to be assigned the section.

   The **Edit Section Assignment** dialog box appears containing a list of existing sections. `SolidSection` is selected by default since there are no other sections currently defined.

4. In the **Edit Section Assignment** dialog box, accept the default selection of `SolidSection`, and click **OK**.

   Abaqus/CAE assigns the section to the part and colors the entire part aqua to indicate that the region has a section assignment.

---

## C.4 Creating and modifying a second hinge piece

The model contains a second hinge piece similar to the first except that the lubrication hole is not present. You will create a copy of the first hinge piece and delete the features that form the lubrication hole.

### C.4.1 Copying the hinge

First you will create an exact copy of the hinge piece.

**To copy the hinge:**

1. In the Model Tree, click mouse button 3 on **Hinge-hole** underneath the **Parts** container and select **Copy** from the menu that appears.

   Abaqus/CAE displays the **Part Copy** dialog box.

2. In the text box in the **Part Copy** dialog box, type `Hinge-solid`, and click **OK**.

   Abaqus/CAE creates a copy of the hinge piece and names the copy **Hinge-solid**. The copy of the hinge piece includes the section from the original hinge piece.

### C.4.2 Modifying the copy of the hinge

Now you will create a solid hinge piece by deleting the features that form the lubrication hole.

**To modify the copy of the hinge:**

1. In the Model Tree, double-click **Hinge-solid** underneath the **Parts** container to make it current.

   Abaqus/CAE displays the part in the current viewport. Look at the viewport title bar to see which part is being displayed.

2. Expand the **Features** container underneath **Hinge-solid**.

3. Click mouse button 3 on **Datum pt-1** in the list of part features.

   Abaqus/CAE highlights the point, as shown in Figure C-20.

   ![Delete the datum point and its children](../graphics/gst-tut2-removehole-nls.png)

4. From the menu that appears, select **Delete**. When you delete a selected feature, Abaqus/CAE asks whether you also want to delete any features that depend on the feature being deleted. The feature being deleted is called the "parent" feature, and its dependent features are called "children." Abaqus/CAE highlights all the features that it will delete if the parent feature is deleted. From the buttons in the prompt area, click **Yes** to delete the datum point and all its children.

   Abaqus/CAE deletes the datum point. Because they were dependent on the datum point, Abaqus/CAE also deletes the datum axis, the datum plane, and the lubrication hole.

   **Important:** You cannot recover deleted features; however, you can temporarily remove a feature by suppressing it.

---

## C.5 Creating the pin

The final assembly consists of instances of the two hinge pieces that are free to rotate about a pin. You will model the pin as a three-dimensional, revolved analytical rigid surface. First you create the pin and assign the rigid body reference point; then you constrain the pin by applying constraints to this rigid body reference point.

### C.5.1 Creating the pin

You will now create the pin -- a three-dimensional, revolved analytical rigid surface.

**To create the pin:**

1. In the Model Tree, double-click the **Parts** container to create a new part.

   The **Create Part** dialog box appears.

2. Name the part `Pin`. Choose a three-dimensional body as before, but change the type to **Analytical rigid** and the base feature shape to **Revolved shell**.

3. Accept the approximate size of `0.2`, and click **Continue**.

   The Sketcher starts and displays the axis of revolution as a green dashed line with a fixed position constraint; your sketch cannot cross this axis.

4. From the Sketcher toolbox, select the connected lines tool. Sketch a vertical line to the right of the axis.

5. Dimension the horizontal distance from the line to the axis, and change the distance to `0.012`.

6. Dimension the vertical length of the line, and change the length to `0.06`.

7. Click mouse button 2 to exit the Sketcher.

   The sketch and the resulting shaded part are shown in Figure C-21.

   ![Create the pin by revolving an analytical rigid surface about an axis](../graphics/gst-tut2-figure19a.png)

### C.5.2 Assigning the rigid body reference point

You need to assign a rigid body reference point to the pin. Because you will not assign mass or rotary inertia to the pin, the rigid body reference point can be placed anywhere in the viewport. You use the Load module to apply constraints to the reference point or to define its motion. Motion or constraints that you apply to the rigid body reference point are applied to the entire rigid surface.

You can either select the reference point from the part in the viewport, or you can enter its coordinates. For the tutorial you will select the reference point from the viewport, as shown in Figure C-22.

![Create a rigid body reference point on the pin](../graphics/gst-tut2-refpoint.png)

**To assign the reference point:**

1. From the main menu bar, select **Tools** -> **Reference Point**.

2. Select one of the vertices on the circumference of the pin.

   Abaqus/CAE labels the vertex **RP** to indicate that the reference point has been assigned to it.

---

## C.6 Assembling the model

Your next task is to create instances of your parts. A part instance can be thought of as a representation of the original part; an instance is not a copy of a part. You can then position these part instances in a global coordinate system to create the assembly.

An instance maintains its association with the original part. If the geometry of a part changes, Abaqus/CAE automatically updates all instances of the part to reflect these changes. You cannot edit the geometry of a part instance directly. The assembly can contain multiple instances of a single part; for example, a rivet that is used repeatedly in a sheet metal assembly.

An instance may be classified as independent or dependent. Independent part instances are meshed individually, while the mesh of a dependent part instance is associated with the mesh of the original part. Part meshing is discussed further in "Meshing the assembly," Section C.11. By default, part instances are dependent.

When you create a part instance, Abaqus/CAE positions it so that the origin of the sketch that defined the base feature overlays the origin of the assembly's global coordinate system. In addition, the sketch plane is aligned with the X-Y plane of the global coordinate system.

When you create the first part instance, the Assembly module displays a graphic indicating the origin and the orientation of the global coordinate system. You can use this graphic to help you decide how to position a selected instance relative to the global coordinate system. For the tutorial you will keep the hinge with the lubrication hole fixed and move the second hinge and the pin relative to it.

### C.6.1 Creating instances of your parts

First, you need to create the following instances:

- An instance of the hinge piece with the lubrication hole -- `Hinge-hole`.
- An instance of the hinge piece with the lubrication hole removed -- `Hinge-solid`.
- An instance of the pin -- `Pin`.

**To create an instance of the hinge piece with the lubrication hole:**

1. In the Model Tree, expand the **Assembly** container. Then double-click **Instances** in the list that appears to create a new part instance.

   The **Create Instance** dialog box appears containing a list of all the parts in the current model -- the two hinge pieces and the pin in this example.

2. In the dialog box, select `Hinge-hole`.

   Abaqus/CAE displays a temporary image of the selected part.

3. In the dialog box, click **Apply**.

   **Note:** What is the difference between the **OK** and **Apply** buttons? When you click **OK**, the **Create Instance** dialog box closes once the part is instanced. When you click **Apply**, the **Create Instance** dialog box remains open while you create the instance and is available for you to create the next instance. Click **OK** if you want to create only a single part instance; click **Apply** if you want to create several part instances before moving on to a new procedure.

   Abaqus/CAE creates a dependent instance of the hinge piece and displays a graphic indicating the origin and orientation of the global coordinate system. Abaqus/CAE names the instance `Hinge-hole-1` to indicate that it is the first instance of a part called `Hinge-hole`.

   **Note:** The default position of a part instance is such that the origin and the X- and Y-axes of the sketch of the base feature align with the origin and the X- and Y-axes of the global coordinate system. For example, the base feature of the hinge piece is the original cube you created. Abaqus/CAE positions instances of the hinge piece so that the origin of the cube sketch is located at the origin of the global coordinate system and the X- and Y-axes align.

### C.6.2 Creating an instance of the solid hinge piece

You will now create an instance of the solid hinge piece. To separate the solid hinge piece from the instance of the hinge piece with the lubrication hole, you ask Abaqus/CAE to offset the new instance along the X-axis.

**To create an instance of the solid hinge piece:**

1. From the **Create Instance** dialog box, toggle on **Auto-offset from other instances**.

   The auto-offset function prevents new part instances from overlapping existing instances.

2. From the **Create Instance** dialog box, select **Hinge-solid** and click **OK**.

   Abaqus/CAE closes the dialog box, creates the new dependent instance, and applies an offset along the X-axis that separates the two hinges, as shown in Figure C-23. (For clarity the datum geometry has been removed from the shaded view in Figure C-23 and subsequent figures by selecting **View** -> **Assembly Display Options** -> **Datum**.)

   ![Create an instance of each hinge piece, and apply an offset to position them in the viewport](../graphics/gst-tut2-figure20a.png)

### C.6.3 Positioning the solid hinge piece

In addition to the simple translate and rotate procedures, the Assembly module provides a set of tools that allow you to position a selected part instance by defining the relationship between selected faces or edges. You can select a face (or an edge) of the instance to move, called the movable part instance, and a face (or an edge) of the instance that remains fixed, called the fixed part instance, and choose one of the following position constraints:

**Parallel Face:** The movable instance moves until the two selected faces are parallel.

**Face to Face:** The movable instance moves until the two selected faces are parallel and a specified clearance from each other.

**Parallel Edge:** The movable instance moves until the two selected edges are parallel.

**Edge to Edge:** The movable instance moves until the two selected edges are colinear or a specified distance from each other.

**Coaxial:** The movable instance moves until the two selected faces are coaxial.

**Coincident Point:** The movable instance moves until the two selected points are coincident.

**Parallel CSYS:** The movable instance moves until the two selected datum coordinate systems are parallel.

Abaqus/CAE stores position constraints as features of the assembly, and they can be edited, deleted, and suppressed. In contrast, translations and rotations are not stored and do not appear in the list of features. Although position constraints are stored as features, they have no knowledge of each other; as a consequence, a new position constraint may override a previous position constraint.

In this example you will move the solid hinge piece while the hinge piece with the lubrication hole will remain fixed. You will apply three types of position constraints to position the two hinge pieces correctly.

**To position the solid hinge piece:**

1. First, constrain the solid hinge piece so that the two flanges face each other. From the main menu bar, select **Constraint** -> **Face to Face**.

2. From the movable part instance, select the face of the solid hinge piece shown in Figure C-24.

   ![Select a face on the movable part instance](../graphics/gst-tut2-facetoface-nls.png)

3. From the fixed part instance, select the face of the hinge piece with the lubrication hole shown in Figure C-25. Abaqus/CAE highlights the face on the movable part instance in red and the face on the fixed part instance in magenta.

   ![Select a face on the fixed instance](../graphics/gst-tut2-facetofaceb-nls.png)

   Abaqus/CAE displays red arrows on each selected face; the movable instance will be positioned so that the arrows point in the same direction. You can change the direction of the arrow on the movable instance if necessary.

4. From the prompt area, click **Flip** to change the direction of the arrow. Click **OK** when the arrows point toward each other.

5. In the text box that appears in the prompt area, type the clearance (0.04) that will remain between the two parts, as measured along the normal to the selected face of the fixed part, and press **[Enter]**.

   Abaqus/CAE rotates the solid hinge piece so that the two selected faces are parallel to each other and 0.04 meters apart, as shown in Figure C-26.

   ![Position 1: Constrain the flange of the solid hinge piece to face the flange of the hinge piece with the lubrication hole](../graphics/gst-tut2-facetofacec.png)

   The two pieces overlap because the position of the solid hinge piece is not fully determined by the position constraint you have applied. You will need to apply two more position constraints to obtain the desired position.

6. Next, align the two flange holes. From the main menu bar, select **Constraint** -> **Coaxial**.

7. Select the flange hole on the solid hinge piece, as shown in Figure C-27. (You may find it helpful to display the wireframe view of the two pieces.)

   ![Select a cylindrical face on the movable instance](../graphics/gst-tut2-coaxiala-nls.png)

8. Select the flange hole on the hinge piece with the lubrication hole, as shown in Figure C-28.

   ![Select a cylindrical face on the fixed instance](../graphics/gst-tut2-coaxialb-nls.png)

   Abaqus/CAE displays red arrows on each selected face.

9. From the prompt area, click **Flip** to change the direction of the arrow on the movable part instance. Click **OK** when the arrow points downward.

   Abaqus/CAE positions the two hinge pieces so that the two flange holes are coaxial.

10. Use the rotate tool to look at the top view of the two pieces. Notice that the two flanges are now overlapping, as shown in Figure C-29.

    ![Position 2: Constrain the two flange holes to lie along the same axis](../graphics/gst-tut2-coaxialc.png)

11. Finally, add a constraint to eliminate the overlap between the two flanges. From the main menu bar, select **Constraint** -> **Edge to Edge**.

12. Select the straight edge on the solid hinge piece shown in Figure C-30.

    ![Select a straight edge on the movable instance](../graphics/gst-tut2-edgea-nls.png)

13. Select the corresponding edge of the hinge piece with the lubrication hole, as shown in Figure C-31.

    ![Select a straight edge on the fixed instance](../graphics/gst-tut2-edgeb-nls.png)

    Abaqus/CAE displays red arrows on each selected face.

14. If necessary, flip the arrows so they point in the same direction; then click **OK** to apply the constraint.

    Abaqus/CAE positions the two hinge pieces so that the two selected edges are colinear, as shown in Figure C-32.

    ![Final position: Constrain an edge of each hinge piece to lie along the same line](../graphics/gst-tut2-edgec.png)

### C.6.4 Creating and positioning an instance of the pin

You will now create an instance of the pin and position it symmetrically in the flange holes using constraints and translation vectors. To define the translation vector, you can select vertices from the assembly or you can enter the coordinates. You can determine the translation vector using the **Query** tool.

**To position the pin:**

1. In the Model Tree, double-click **Instances** underneath the **Assembly** container.

2. In the **Create Instance** dialog box, toggle off **Auto-offset from other instances** and create an instance of the pin.

3. Constrain the pin to lie along the same axis as the two flange holes. Use the **Constraint** -> **Coaxial** menu as you did when you aligned the two flange holes in the previous section. (You can select either of the flange holes as the cylindrical surface of the fixed instance, and the direction of the arrows is not important.)

   Abaqus/CAE will position the pin as shown in Figure C-33.

   ![Align the pin to be coaxial with the two flange holes](../graphics/gst-tut2-pincoax.png)

4. From the main menu bar, select **Tools** -> **Query**.

   The **Query** dialog box appears.

5. Select **Distance** from the list of **General Queries**.

6. The **Distance** query allows you measure the X-, Y-, and Z-components of the vector connecting two selected points. You need to determine the distance between the end of the pin and the hinge containing the lubrication hole; the two points to select are illustrated in Figure C-34.

   ![Determining the position of the pin](../graphics/gst-tut2-distance-nls.png)

   - To define one end of the vector, select a point on the circumference of the hole in the flange containing the lubrication hole.
   - To define the other end of the vector, select the vertex on the pin that is inside the hinge containing the lubrication hole.

   Abaqus/CAE displays the vector distance between the two selected points along with the X-, Y-, and Z-components of the vector in the message area. You will translate the pin along the Z-axis; the Z-component of the distance is 0.01 meters. You want to position the pin symmetrically between the hinges, so you will translate it 0.02 meters.

7. From the main menu bar, select **Instance** -> **Translate**.

8. Select the pin as the part instance to move, and click **Done** to indicate that you have finished selecting instances to move.

9. In the text boxes in the prompt area, enter a start point for the translation vector of `0,0,0` and an end point of `0,0,0.02`.

   Abaqus/CAE translates the pin a distance of 0.02 along the Z-axis and displays a temporary image of the new position of the pin.

   **Note:** If the position of a temporary image (colored red) is not correct, you can use the buttons in the prompt area to correct the problem. Click either the **Cancel** button to cancel the procedure or the **Previous** button to step back through the procedure.

10. From the prompt area, click **OK**.

    The finished assembly is shown in Figure C-35.

    ![Shaded view of the finished assembly](../graphics/gst-tut2-assydone.png)

11. Before proceeding, convert all position constraints to absolute positions. From the main menu bar, select **Instance** -> **Convert Constraints**. Select all part instances, and click **Done** in the prompt area.

---

## C.7 Defining analysis steps

Before you apply loads or boundary conditions to the model or define contact within the model, you must define the different steps in the analysis. Once the steps are created, you can specify in which steps loads, boundary conditions, and interactions should be applied.

When you create a step, Abaqus/CAE selects a default set of output variables corresponding to the analysis procedure and selects a default rate at which the variables are written to the output database. In this tutorial you will edit the default output frequency for the first step and edit the list of default output variables for the second step.

### C.7.1 Creating the analysis steps

The analysis that you perform on the hinge model will consist of an initial step and two general analysis steps:

- In the initial step you apply boundary conditions to regions of the model and define contact between regions of the model.
- In the first general analysis step you allow contact to become established.
- In the second general analysis step you modify two of the boundary conditions applied to the model and apply a pressure load to one of the hinge pieces.

Abaqus/CAE creates the initial step by default, but you must create the two analysis steps.

**To create the analysis steps:**

1. In the Model Tree, double-click the **Steps** container to create a new step.

   The **Create Step** dialog box appears.

2. In the **Create Step** dialog box:
   - Name the step `Contact`.
   - Accept the default procedure type (**Static, General**), and click **Continue**.

   The step editor appears.

3. In the **Description** field, type `Establish contact`.

4. Click the **Incrementation** tab, and delete the value of `1` that appears in the **Initial** text field. Type a value of `0.1` for the initial increment size.

5. Click **OK** to create the step and to exit the editor.

   The `Contact` step appears underneath the **Steps** container in the Model Tree.

6. Use the same technique to create a second general, static step named `Load`. Enter `Apply load` in the description field and an initial increment size of `0.1`.

   The `Load` step appears underneath the **Steps** container in the Model Tree.

### C.7.2 Requesting output

You use field output requests to request output of variables that should be written at relatively low frequencies to the output database from the entire model or from a large portion of the model. Field output is used to generate deformed shape plots, contour plots, and animations from your analysis results. Abaqus/CAE writes every component of the variables to the output database at the selected frequency.

You use history output requests to request output of variables that should be written to the output database at a high frequency from a small portion of the model; for example, the displacement of a single node. History output is used to generate X-Y plots and data reports from your analysis results. When you create a history output request, you must select the individual components of the variables that will be written to the output database.

The default field output variables for the `Contact` and `Load` steps include the following:

- **S** (Stress components)
- **PE** (Plastic strain components)
- **PEEQ** (Equivalent plastic strain)
- **PEMAG** (Plastic strain magnitude)
- **LE** (Logarithmic strain components)
- **U** (Translations and rotations)
- **RF** (Reaction forces and moments)
- **CF** (Concentrated forces and moments)
- **CSTRESS** (Contact stresses)
- **CDISP** (Contact displacements)

By default, Abaqus/CAE writes the default field output variables from a static, general procedure to the output database after every increment of a step. In the following procedure you will change the output frequency during the `Contact` step so that data are written to the output database once -- at the last increment of the step. In addition, you will delete the request for `CDISP` during the `Load` step, since it is not needed for postprocessing.

**To edit an output request and to specify the output frequency during the Load step:**

1. In the Model Tree, click mouse button 3 on the **Field Output Requests** container and select **Manager** from the menu that appears.

   The **Field Output Requests Manager** appears. The **Field Output Requests Manager** is a step-dependent manager. The types of objects that appear in step-dependent managers are those that you can create, modify, and deactivate in particular analysis steps. Step-dependent managers display information concerning the history of each object listed in the manager. In this example Abaqus/CAE named the default field output request that you created in the `Contact` step **F-Output-1**. In addition Abaqus/CAE propagated the output request into the `Load` step. For more information, see "Managing objects," Section 3.4 of the Abaqus/CAE User's Guide.

2. From the **Field Output Requests Manager**, select the **F-Output-1** output request in the `Contact` step. From the buttons on the right side of the manager, click **Edit**.

   The **Edit Field Output Request** editor appears for the `Contact` step.

3. Select **Last increment** as the output frequency to generate output only during the last increment of the step.

4. Select **Exterior only** to restrict field output to nodes and elements that belong to the exterior of the model.

5. Click **OK** to modify the output request.

6. From the **Field Output Requests Manager**, select the **F-Output-1** output request in the `Load` step and click **Edit**.

   The **Edit Field Output Request** editor appears for the `Load` step.

7. Set the output frequency to `1` to generate output during every increment of the step.

8. From the list of output categories, click the arrow to the left of **Contact**.

   A list of the contact output variables available appears along with a description of each.

9. Click the check box next to **CDISP** to deselect this variable for output.

   The check box next to **Contact** remains light gray with a dark gray check mark to indicate that not all variables in this category will be output. The **Edit Field Output Request** editor also indicates the following:

   - Output will be generated for the whole model.
   - Output will be generated at default section points.
   - Output will include local coordinate transformations (when available).

10. Click **OK** to modify the output request.

    In the **Field Output Requests Manager** the status of the output request changes to **Modified** for the `Load` step.

11. At the bottom of the **Field Output Requests Manager**, click **Dismiss** to close the dialog box.

### C.7.3 Selecting a degree of freedom to monitor

You can define sets that contain only selected portions of your model. Once you create a set, you can use it to perform the following tasks:

- Assign section properties in the Property module.
- Create contact pairs with contact node sets and surfaces in the Interaction module.
- Define loads and boundary conditions in the Load module.
- Request output to either the output database or the status file from specific regions of the model in the Step module. Output to the status file is also reported back to the Job module in the form of a continuously updated X-Y plot.
- Display results for specific regions of the model in the Visualization module.

In this example you will define a set consisting of a single point. You will then be able to monitor the results for one degree of freedom at that point when you submit your job for analysis later in this tutorial.

**To create a set and monitor a particular degree of freedom:**

1. In the Model Tree, expand the **Assembly** container and double-click the **Sets** item.

   The **Create Set** dialog box appears.

2. Name the set `Monitor`, and click **Continue**.

3. Select the vertex of the solid hinge piece shown in Figure C-36.

   ![Monitor a degree of freedom on the solid hinge piece](../graphics/gst-tut2-monitor-nls.png)

4. Click **Done** to indicate that you have finished selecting the geometry for the set.

   Abaqus/CAE creates a node set with the name `Monitor` that contains the node you selected.

5. From the main menu bar of the Step module, select **Output** -> **DOF Monitor**.

   The **DOF Monitor** dialog box appears.

6. Toggle on **Monitor a degree of freedom throughout the analysis**.

7. Click the select button, then click **Points** in the prompt area and choose the set **Monitor** from the **Region Selection** dialog box.

8. Type `1` in the **Degree of freedom** text field, and click **OK**.

---

## C.8 Creating surfaces to use in contact interactions

Now you will define contact between regions of the model. There are two approaches that can be adopted to define contact interactions. The first is a manual approach that requires you to identify which surfaces will form part of the contact interactions and to define the individual contact pairs. An alternative approach is to let Abaqus/CAE automatically identify and define all potential contact pairs. The latter approach is desirable for complicated models containing many contact interactions. The automatic contact definition option is available only for three-dimensional Abaqus/Standard models.

In "Defining contact between regions of the model," Section C.9, you will be given the option to define the contact interactions either manually (where you will use the surfaces defined in the following instructions) or automatically (in which case the surfaces defined below are not used; Abaqus/CAE will choose the surfaces automatically). For instructional purposes, however, you are encouraged to complete the surface definition instructions that follow regardless of the approach you choose to define the contact interactions.

When manually defining contact interactions, the first step is to create the surfaces that you will include later in interactions. It is not always necessary to create your surfaces in advance; if the model is simple or the surfaces easy to select, you can indicate the master and slave surfaces directly in the viewport as you create the interactions. However, in this tutorial it is easier to define the surfaces separately and then refer to the names of those surfaces when you create the interactions. You will define the following surfaces:

- A surface named `Pin` that includes the outside surface of the pin.
- Two surfaces named `Flange-h` and `Flange-s` that include the two flange faces that contact each other.
- Two surfaces named `Inside-h` and `Inside-s` that include the inside surfaces of the flanges that contact the pin.

### C.8.1 Defining a surface on the pin

In this section you will define the outside surface of the pin. You will find it helpful to display only one part instance at a time while you select the surfaces to be defined.

**To hide part instances in the assembly:**

1. In the Model Tree, expand the **Instances** container underneath the **Assembly**.

2. Select the hinge pieces, and click mouse button 3.

3. Choose **Hide** from the menu that appears.

   The hinge pieces disappear from the view.

**To define a surface on the pin:**

1. In the Model Tree, expand the **Assembly** container and double-click the **Surfaces** item.

   The **Create Surface** dialog box appears.

2. In the dialog box, name the surface `Pin` and click **Continue**.

3. In the viewport, select the pin.

4. Click mouse button 2 in the viewport to indicate that you have finished selecting regions for the surface.

   Each side of the hollow cylinder representing the pin has a different color associated with it. In Figure C-37 the outside of the pin is colored brown and the inside of the pin is colored purple. The colors may be reversed on your model, depending on how you created the original sketch for the pin.

   ![Select the region to be defined as the surface Pin](../graphics/gst-tut2-pinarrow.png)

5. You must choose whether the surface consists of the inside or the outside of the cylinder. The outside surface contacts the two hinges and is the desired choice. From the buttons in the prompt area, click the color (**Brown** or **Purple**) associated with the outside surface.

   Abaqus/CAE creates the desired surface called `Pin` and displays it underneath the **Surfaces** container in the Model Tree.

### C.8.2 Defining the surfaces on the hinge pieces

In this section you will define the surfaces on the hinge pieces needed to define contact between the two hinge pieces and between the hinge pieces and the pin.

**To define the surfaces on the hinge pieces:**

1. Resume the visibility of part instance `Hinge-hole-1`, and suppress the visibility of `Pin-1` (in the **Instances** container, click mouse button 3 on the instance name, and select **Show** or **Hide** as appropriate).

   Abaqus/CAE displays only the hinge piece with the lubrication hole in the viewport.

2. In the Model Tree, double-click **Surfaces** underneath the **Assembly** container.

   The **Create Surface** dialog box appears.

3. In the dialog box, name the surface `Flange-h` and click **Continue**.

4. On the instance with the lubrication hole, select the face of the flange that contacts the other flange, as shown by the gridded face in Figure C-38. (You may need to rotate the view to see this face clearly.)

   ![Select the region to be defined as the surface Flange-h](../graphics/gst-tut2-flange1.png)

5. When you have selected the desired face, click mouse button 2 to confirm your selection.

   Abaqus/CAE creates the desired surface called `Flange-h` and displays it underneath the **Surfaces** container in the Model Tree.

6. Create a surface called `Inside-h` that includes the cylindrical inner surface of the hinge piece with the lubrication hole, as shown in Figure C-39. (You may need to zoom in on the view to select this face.)

   ![Select the region to be defined as the surface Inside-h](../graphics/gst-tut2-inside1-nls.png)

7. Change the visibility settings so that only `Hinge-solid-1` is visible.

8. Use similar techniques to create a surface called `Flange-s` that contains the corresponding face of the solid hinge piece's flange.

9. Finally, create a surface called `Inside-s` that includes the cylindrical inner surface of the solid hinge piece.

10. Return to the default visibility settings (select the three part instance names in the **Instances** container, and click mouse button 3; from the menu that appears, select **Show**).

---

## C.9 Defining contact between regions of the model

Interactions are objects that you create to model mechanical relationships between surfaces that are in contact or closely spaced. Mere physical proximity of two surfaces on an assembly is not enough to indicate any type of interaction between the surfaces.

You will define the following interactions:

- An interaction called `HingePin-hole` that defines the contact between the part instance `Hinge-hole-1` and the pin.
- An interaction called `HingePin-solid` that defines the contact between the part instance `Hinge-solid-1` and the pin.
- An interaction called `Flanges` that defines the contact between the two flanges.

Each of these interactions requires a reference to an interaction property. Interaction properties are collections of information that help you to define certain types of interactions. You will create a mechanical interaction property that describes the tangential and normal behavior between all surfaces as frictionless. You will name this property `NoFric` and use it in all three of the interactions.

### C.9.1 Creating an interaction property

In this procedure you will create a mechanical contact interaction property.

**To create the interaction property:**

1. In the Model Tree, double-click the **Interaction Properties** container to create a contact property.

   The **Create Interaction Property** dialog box appears.

2. In the **Create Interaction Property** dialog box:
   - Name the property `NoFric`.
   - In the **Type** list, accept **Contact** as the default selection.
   - Click **Continue**.

   The **Edit Contact Property** dialog box appears.

3. From the dialog box's menu bar, select **Mechanical** -> **Tangential Behavior** and accept **Frictionless** for the friction formulation.

4. Click **OK** to save your settings and to close the **Edit Contact Property** dialog box.

### C.9.2 Creating the interactions

In this section you will create three mechanical surface-to-surface contact interactions. Each interaction will refer to the interaction property that you just created. You are given the option to define the interactions either automatically or manually. Please follow the instructions for one method or the other. If you choose to try both, be sure to delete or suppress any duplicate contact interactions that result.

**To create the interactions automatically:**

1. From the main menu bar, select **Interaction** -> **Find contact pairs**.

2. In the **Find Contact Pairs** dialog box, click **Find Contact Pairs**.

   Five potential contact pairs are identified.

3. In the **Contact Pairs** region of the dialog box:
   - Click the name of each contact pair to highlight it in the viewport. This will allow you to familiarize yourself with the contact interactions that have been chosen.
   - Contact pairs are defined between the rounded end of each hinge flange and the flat face opposite it. These contact pairs are not necessary. Thus, delete them (to delete a contact pair, select it and click mouse button 3; from the menu that appears, select **Delete**).
   - Identify the contact pair between the hinge with the hole and the pin. Rename the interaction `HingePin-hole`.
   - Identify the contact pair between the solid hinge and the pin. Rename the interaction `HingePin-solid`.
   - Rename the remaining interaction `Flanges`. If necessary, switch the master and slave surface designations so that the surface associated with the hinge with the hole is the master surface and the one associated with the solid hinge piece is the slave surface (click mouse button 3 on the surface name; from the menu that appears, select **Switch surfaces**).

   **Tip:** You can view the master and slave instance names to aid in the surface designation. Click mouse button 3 anywhere on the table, and select **Edit Visible Columns**. From the dialog box that appears, toggle on **Master instance name** and **Slave instance name**.

   - Accept all default settings except for the contact discretization. Select the column heading labeled **Discretization**, and click mouse button 3. From the menu that appears, select **Edit Cells**. In the dialog box that appears, select **Node-to-surface**, and click **OK**.
   - Click **OK** to save the interactions and to close the dialog box.

**To create the interactions manually:**

1. In the Model Tree, click mouse button 3 on the **Interactions** container and select **Manager** from the menu that appears.

   The **Interaction Manager** appears.

2. From the lower-left corner of the **Interaction Manager**, click **Create**.

   The **Create Interaction** dialog box appears.

3. In the dialog box:
   - Name the interaction `HingePin-hole`.
   - Select `Initial` from the list of steps.
   - In the **Types for Selected Step** list, accept the default selection of **Surface-to-surface contact (Standard)**.
   - Click **Continue**.

   The **Region Selection** dialog box appears containing a list of the surfaces that you defined earlier.

   **Note:** If the **Region Selection** dialog box does not appear automatically, click the **Surfaces** button on the far right side of the prompt area.

4. In the **Region Selection** dialog box, select `Pin` as the master surface, and click **Continue**.

5. From the buttons in the prompt area, select **Surface** as the slave type.

6. In the **Region Selection** dialog box, select `Inside-h` as the slave surface, and click **Continue**.

   The **Edit Interaction** dialog box appears.

7. In the dialog box:
   - Accept the default **Sliding formulation** selection of **Finite sliding**.
   - Change the discretization method to **Node to surface**.
   - Accept the default **Slave Adjustment** selection of **No adjustment**.
   - Accept `NoFric` as the interaction property. (If more properties were defined, you could click the arrow next to the **Contact interaction property** field to see the list of available properties and select the property of your choice.)
   - Click **OK** to save the interaction and to close the dialog box.

   The interaction that you created appears in the **Interaction Manager**.

8. Use the same techniques explained in the previous steps to create a similar interaction called `HingePin-solid`. Use `Pin` as the master surface, `Inside-s` as the slave surface, and `NoFric` as the interaction property.

9. Create a similar interaction called `Flanges`. Use `Flange-h` as the master surface, `Flange-s` as the slave surface, and `NoFric` as the interaction property.

10. From the **Interaction Manager**, click **Dismiss** to close the manager.

---

## C.10 Applying boundary conditions and loads to the assembly

You will apply the following boundary conditions and load to the hinge model:

- A boundary condition called `Fixed` that constrains all degrees of freedom at the end of the hinge piece with the lubrication hole, as shown in Figure C-40.

  ![One end of the hinge is constrained](../graphics/gst-tut2-fixhole-nls.png)

- A boundary condition called `NoSlip` that constrains all degrees of freedom of the pin while contact is established during the first analysis step. You will modify this boundary condition in the second analysis step (the step in which the load is applied) so that degrees of freedom 1 and 5 are unconstrained. Figure C-41 illustrates this boundary condition applied at the reference point.

  ![The pin is constrained](../graphics/gst-tut2-fixpin.png)

- A boundary condition called `Constrain` that constrains all degrees of freedom of a point on the solid hinge piece during the first analysis step. You will modify this boundary condition in the second analysis step so that degree of freedom 1 is unconstrained when the load is applied.

- A load called `Pressure` that you apply to the end of the solid hinge piece during the second analysis step. Figure C-42 illustrates the constraint and the pressure load applied to the solid hinge.

  ![The second hinge is constrained and loaded](../graphics/gst-tut2-loadsolid-nls.png)

### C.10.1 Constraining the hinge piece with the lubrication hole

You will apply a boundary condition to the face at the end of the hinge piece with the lubrication hole to fix the hinge piece in place during the analysis.

**To constrain the hinge piece with the lubrication hole:**

1. In the Model Tree, click mouse button 3 on the **BCs** container and select **Manager** from the menu that appears.

   The **Boundary Condition Manager** dialog box appears.

2. In the **Boundary Condition Manager**, click **Create**.

   The **Create Boundary Condition** dialog box appears.

3. In the **Create Boundary Condition** dialog box:
   - Name the boundary condition `Fixed`.
   - Select `Initial` from the list of steps.
   - Accept **Mechanical** as the default **Category** selection.
   - Select **Displacement/Rotation** as the type of boundary condition for the selected step.
   - Click **Continue**.

   The **Region Selection** dialog box appears.

4. From the right side of the prompt area, click **Select in Viewport** to select the object directly from the viewport.

   The **Region Selection** dialog box closes.

5. Select the gridded face shown in Figure C-43 as the region where the boundary condition will be applied. You may need to rotate the view in order to select this face.

   ![Apply a boundary condition to the end of the hinge piece with the lubrication hole](../graphics/gst-tut2-fixed.png)

6. Click mouse button 2 to indicate that you have finished selecting regions.

   The **Edit Boundary Condition** dialog box appears.

7. In the dialog box:
   - Toggle on the buttons labeled **U1**, **U2**, and **U3** to constrain the end of the hinge in the 1-, 2-, and 3-directions. You do not need to constrain the rotational degrees of freedom of the hinge because solid elements (which have only translational degrees of freedom) will be used to mesh the hinge.
   - Click **OK** to close the dialog box.

   The boundary condition that you just created appears in the **Boundary Condition Manager**, and arrows appear on the nodes of the face indicating the constrained degrees of freedom. The **Boundary Condition Manager** shows that the boundary condition remains active in all steps of the analysis.

   **Tip:** To suppress the display of boundary condition arrows, click the **Attribute** tab in the **Assembly Display Options** dialog box to access the boundary condition display options.

### C.10.2 Constraining the pin

In the first general step of the analysis you will establish contact between the two hinge pieces and between the hinge pieces and the pin. To fix the pin during this step, you must apply a boundary condition to the pin that constrains all its degrees of freedom.

**To apply a boundary condition to the pin:**

1. In the **Boundary Condition Manager**, click **Create**.

   The **Create Boundary Condition** dialog box appears.

2. In the **Create Boundary Condition** dialog box:
   - Name the boundary condition `NoSlip`.
   - Accept `Initial` in the **Step** text field.
   - Accept **Mechanical** as the default **Category** selection.
   - Select **Displacement/Rotation** as the type of boundary condition for the selected step.
   - Click **Continue**.

3. In the viewport, select the rigid body reference point on the pin as the region where the boundary condition will be applied.

4. Click mouse button 2 to indicate that you have finished selecting regions.

   The **Edit Boundary Condition** dialog box appears.

5. In the dialog box:
   - Toggle on all the buttons to constrain all the degrees of freedom of the pin.
   - Click **OK**.

   The new boundary condition appears in the **Boundary Condition Manager**.

### C.10.3 Modifying the boundary condition applied to the pin

Objects that you can create and modify in certain steps -- such as boundary conditions, loads, and interactions -- have special managers that allow you to modify objects and change their status in different analysis steps.

In this section you will use the boundary condition manager to modify the boundary condition `NoSlip` so that translation in the 1-direction and rotation about the 2-axis are unconstrained during the loading step.

Currently the **Boundary Condition Manager** displays the names of the two boundary conditions that you have created as well as their status in each step: both boundary conditions are `Created` in the initial step and `Propagated` through the following analysis steps.

**To modify a boundary condition:**

1. In the **Boundary Condition Manager**, click the cell labeled `Propagated` that lies in the row labeled `NoSlip` and in the column labeled `Load`, as shown in Figure C-44. That cell becomes highlighted.

   ![Select boundary conditions to edit in the Boundary Condition Manager](../graphics/gst-tut2-bcman-nls.png)

2. On the right side of the manager, click **Edit** to indicate that you want to edit the `NoSlip` boundary condition in the `Load` step.

   The **Edit Boundary Condition** dialog box appears, and Abaqus/CAE displays a set of arrows on the model indicating where the boundary condition is applied and which degrees of freedom are constrained.

3. In the editor, toggle off the buttons labeled **U1** and **UR2** so that the pin is allowed to translate in the 1-direction and rotate about the 2-axis. Click **OK** to close the dialog box.

   In the **Boundary Condition Manager**, the status of the `NoSlip` boundary condition in the `Load` step changes to `Modified`.

### C.10.4 Constraining the solid hinge piece

In the first analysis step, in which contact is established, you will constrain a single node of the solid hinge piece in all directions. These constraints, along with contact with the pin, are enough to prevent rigid body motion of the solid piece. In the second analysis step, in which the load is applied to the model, you will remove the constraint in the 1-direction.

**To constrain the solid hinge piece:**

1. Create a displacement boundary condition in the `Initial` step, and call it `Constrain`.

2. Apply the boundary condition to the vertex selected from the solid hinge piece, as shown in Figure C-45.

   ![Apply a boundary condition to a vertex of the solid hinge piece](../graphics/gst-tut2-constrain-nls.png)

3. Constrain the vertex in the 1-, 2-, and 3-directions.

4. In the `Load` step, modify the boundary condition so that the hinge is unconstrained in the 1-direction.

5. When you have finished creating boundary conditions, click **Dismiss** to close the **Boundary Condition Manager**.

### C.10.5 Applying a load to the solid hinge

Next, you apply a pressure load to the face at the end of the solid hinge. You apply the load in the 1-direction during the second analysis step.

**To apply a load to the solid hinge:**

1. In the Model Tree, double-click the **Loads** container to create a new load.

   The **Create Load** dialog box appears.

2. In the **Create Load** dialog box:
   - Name the load `Pressure`.
   - Accept `Load` as the default selection in the **Step** text field.
   - From the **Category** list, accept **Mechanical** as the default selection.
   - From the **Types for Selected Step** list, select **Pressure**.
   - Click **Continue**.

3. In the viewport, select the face at the end of the solid hinge piece as the surface to which the load will be applied, as shown by the gridded surface in Figure C-46.

   ![Apply a load to the solid hinge piece](../graphics/gst-tut2-pressure.png)

4. Click mouse button 2 to indicate that you have finished selecting regions.

   The **Edit Load** dialog box appears.

5. In the dialog box, enter a magnitude of `-1.E6` for the load, and click **OK**.

   Arrows appear on the face indicating the applied load. The arrows are pointing out of the face because you applied a negative pressure.

---

## C.11 Meshing the assembly

Meshing the assembly is divided into the following operations:

- Making sure the part instances can be meshed and creating additional partitions where necessary.
- Assigning mesh attributes to the part instances.
- Seeding the part instances.
- Meshing the part instances.

### C.11.1 Deciding what needs to be partitioned

When you enter the Mesh module, Abaqus/CAE color codes regions of the model according to the methods it will use to generate a mesh:

- Green indicates that a region can be meshed using structured methods.
- Yellow indicates that a region can be meshed using sweep methods.
- Orange indicates that a region cannot be meshed using the default element shape assignment (hexahedral) and must be partitioned further. (Alternatively, you can mesh any model by assigning tetrahedral elements to the model and using the free meshing technique.)

For the tutorial Abaqus/CAE indicates that the hinge with the lubrication hole needs to be partitioned to be meshed using hexahedral-shaped elements. Specifically, areas surrounding the hole in the flange must be partitioned. The partitioned hinges are shown in Figure C-47.

![The partitioned hinges](../graphics/gst-tut2-partmodel.png)

Use the following techniques to help you select faces and vertices during the partitioning process:

- Use a combination of the view manipulation tools, the display option tools in the **View Options** toolbar, and the tools in the **Views** toolbar to resize and reposition the model as necessary. (To display the **Views** toolbar, select **View** -> **Toolbars** -> **Views** from the main menu bar.)
- Toggle off the closest object tool in the **Selection** toolbar to cycle through the possible selections using the **Next** and **Previous** buttons in the prompt area.
- You will probably find the 3D compass and/or the magnification tool and the rotation tool especially useful.
- When necessary, click the **Iso** tool in the **Views** toolbox to return the model to its original size and position in the viewport.
- Recall that part instances are classified as dependent by default. All dependent instances of a part must possess identical geometry (including partitions) and meshes. To satisfy this requirement, all partitions must be created in the original part and all mesh attributes must be assigned to the original part. You will need to examine the parts individually to determine what action (if any) needs to be taken to create a mesh using hexahedral elements.

  **Note:** The advantage of dependent part instances is that if you create multiple instances of the same part, you need only manipulate and mesh the original part; these features are automatically inherited by the dependent instances. Since you created only one instance of each part in this tutorial, you could have created independent part instances and worked with them just as easily. This would have allowed you to create partitions and assign mesh attributes at the assembly level rather than at the part level. You can make a dependent part instance independent by clicking mouse button 3 on its name underneath the **Instances** container in the Model Tree and selecting **Make independent**. In what follows, we assume the part instances remain dependent.

**To decide what needs to be partitioned:**

1. In the Model Tree, expand **Hinge-hole** underneath the **Parts** container and double-click **Mesh** in the list that appears.

   **Note:** If the part instance were independent, you would instead expand the instance name underneath the **Instances** container and click **Mesh** in the list that would appear.

   Abaqus/CAE displays the hinge piece with the lubrication hole. The cube portion of the hinge piece is colored green to indicate that it can be meshed using the structured meshing technique; the flange with the lubrication hole is colored orange to indicate that it needs to be partitioned to be meshed using hexahedral elements, as shown in Figure C-48. The partitioning procedure is described in "Partitioning the flange with the lubrication hole," Section C.11.2.

   ![The flange with the lubrication hole cannot be meshed](../graphics/gst-tut2-meshcolor.png)

2. Use the **Object** field that appears in the context bar to display the solid hinge in the viewport. Abaqus/CAE displays the solid hinge. As before, the cube portion of the solid hinge piece is colored green to indicate that it can be meshed using the structured meshing technique. The flange without the lubrication hole is colored yellow to indicate that it can be meshed using a swept mesh.

3. Select the pin from the **Object** field in the context bar. Abaqus/CAE displays the pin in orange because it is an analytical rigid surface and cannot be meshed.

   Thus, the hinge piece with the lubrication hole needs to be partitioned to be meshed with hexahedral elements; the solid hinge and the pin require no further action.

### C.11.2 Partitioning the flange with the lubrication hole

For Abaqus/CAE to mesh the flange with the lubrication hole, it must be partitioned into the regions shown in Figure C-49.

![Shaded view of the partitioned flange](../graphics/gst-tut2-figure32.png)

**To partition the flange with the lubrication hole:**

1. Make the hinge piece with the lubrication hole current in the viewport.

2. From the main menu, select **Tools** -> **Partition**.

   The **Create Partition** dialog box appears.

3. You want to partition the entire cell that makes up the flange. From the **Create Partition** dialog box, select **Cell** as the **Type** of partition and click **Define cutting plane** as the partition **Method**.

4. Select the flange of the hinge with the lubrication hole. Click **Done** to indicate you have finished selecting cells.

   Abaqus/CAE provides three methods for specifying the cutting plane:
   - Select a point and a normal. The cutting plane passes through the selected point, normal to the selected edge.
   - Select three non-colinear points. The cutting plane passes through each point.
   - Select an edge and a point along the edge. The cutting plane passes through the selected point, normal to the selected edge.

   The cutting plane need not be defined in the cell being partitioned. The plane extends infinitely and partitions the selected cell anywhere there is an intersection.

5. From the buttons in the prompt area, select **3 points**.

   Abaqus/CAE highlights points that you can select.

6. Select three points that cut the flanges in half with a vertical partition, as shown in Figure C-50.

   **Tip:** You may find it easier to select the desired points if you magnify, rotate, and pan the model to obtain a more convenient view.

   ![Select three points to use in partitioning the flanges](../graphics/gst-tut2-figure25.png)

7. From the prompt area, click **Create Partition**.

   Abaqus/CAE creates the desired partitions.

   The flange regions are colored yellow, indicating that no additional partitions are required to create a hexahedral mesh. Thus, the partitioning operation is complete.

8. Select **Assembly** in the **Object** field of the context bar to display the model assembly in the viewport. The model assembly with all the partitions is shown in Figure C-51.

   ![The partitioned model](../graphics/gst-tut2-mesh-partdone.png)

   **Tip:** If you did not previously convert the positioning constraints to absolute positions, this partition may invalidate the coaxial constraints created earlier. If necessary, return to the Assembly module and define new coaxial constraints between the hinge pieces and between the hinge and the pin using the technique described earlier. It is also possible that the partition may invalidate the surfaces used for the contact interactions. Review these and correct them as necessary.

### C.11.3 Assigning mesh controls

In this section you will use the **Mesh Controls** dialog box to examine the techniques that Abaqus/CAE will use to mesh the parts and the shape of the elements that Abaqus/CAE will generate.

You cannot mesh an analytical rigid surface. As a result you cannot apply mesh controls to an analytical rigid surface; neither can you seed it or assign an element type to it. Thus, you need only concern yourself with the hinge pieces. Since the instances are dependent on the original part definition, you must assign mesh attributes (controls, type, and seed size) to each hinge piece individually. For convenience, you will begin with the hinge piece with the lubrication hole.

**To assign the mesh controls:**

1. Make the hinge piece with the hole current in the viewport. From the main menu bar, select **Mesh** -> **Controls**.

2. Drag a square around the part to select all regions of the part, and click **Done** to indicate your selection is complete.

   The hinge piece appears red in the viewport to indicate that you have selected it, and Abaqus/CAE displays the **Mesh Controls** dialog box.

3. In the dialog box, accept **Hex** as the default **Element Shape** selection.

4. Select **Sweep** as the meshing technique that Abaqus/CAE will apply.

5. Select **Medial axis** as the meshing algorithm.

6. Click **OK** to assign the mesh controls and to close the dialog box.

   The entire hinge will appear in yellow, indicating that it will be meshed using the swept meshing technique.

7. Repeat the above steps for the solid hinge piece.

### C.11.4 Assigning the Abaqus element type

In this section you will use the **Element Type** dialog box to examine the element types that are assigned to each part. For convenience, you will begin with the hinge piece with the lubrication hole.

**To assign an Abaqus element type:**

1. Make the hinge piece with the hole current in the viewport. From the main menu bar, select **Mesh** -> **Element Type**.

2. Select the hinge piece using the same technique described in the mesh controls procedure, and click **Done** to indicate your selection is complete.

   Abaqus/CAE displays the **Element Type** dialog box.

3. In the dialog box, accept **Standard** as the **Element Library** selection.

4. Accept **Linear** as the **Geometric Order** selection.

5. Accept **3D Stress** as the default **Family** of elements.

6. Click the **Hex** tab, and select **Reduced Integration** as the formulation if it is not already selected.

   A description of the default element type, C3D8R, appears at the bottom of the dialog box. Abaqus/CAE will now associate C3D8R elements with the elements in the mesh.

7. Click **OK** to assign the element type and to close the dialog box.

8. Click **Done** in the prompt area.

9. Repeat the above steps for the solid hinge piece.

### C.11.5 Seeding the part instances

The next step of the meshing process is to seed each of the part instances. Seeds represent the approximate locations of nodes and indicate the target density of the mesh you would like to generate. You can select seeding based on the number of elements to generate along an edge or on the average element size, or you can bias seed distribution toward one end of an edge. For the tutorial you will seed the parts so that the hinge pieces have an average element size of 0.004. For convenience, you will begin with the hinge piece with the lubrication hole.

**To seed the parts:**

1. Make the hinge piece with the hole current in the viewport. From the main menu bar, select **Seed** -> **Part**.

2. In the **Global Seeds** dialog box that appears, enter an approximate global element size of `0.004`, and click **OK**.

   Seeds appear on all the edges.

   **Note:** If you are using the Abaqus Student Edition, using a global seed size of 0.004 results in a mesh that exceeds the model size limits of the product. Use a global seed size of 0.008 instead.

3. Repeat the above steps for the solid hinge piece.

You are now ready to mesh the parts.

### C.11.6 Meshing the assembly

In this section you will mesh the parts. For convenience, you will begin with the hinge piece with the lubrication hole.

**To mesh the assembly:**

1. Make the hinge piece with the hole current in the viewport. From the main menu bar, select **Mesh** -> **Part**.

2. Click **Yes** in the prompt area to create the mesh.

   Abaqus/CAE meshes the part.

3. Repeat the above steps for the solid hinge piece.

The meshing operations are now complete. Display the model assembly in the viewport to see the final mesh, as illustrated in Figure C-52.

![Final view of the meshed model](../graphics/gst-tut2-mesh-done.png)

---

## C.12 Creating and submitting a job

Now that you have configured your analysis, you will create a job that is associated with your model and submit the job for analysis.

**To create and submit an analysis job:**

1. In the Model Tree, double-click the **Jobs** container to create a job.

   The **Create Job** dialog box appears.

2. Name the job `PullHinge`, and click **Continue**.

   The job editor appears.

3. In the **Description** field, type `Hinge tutorial`.

   Click the tabs to see the contents of the job editor, and review the default settings. Click **OK** to accept all the default job settings.

4. In the Model Tree, click mouse button 3 on the job named **PullHinge** and select **Submit** from the menu that appears to submit your job for analysis.

5. In the Model Tree, click mouse button 3 on the job name and select **Monitor** from the menu that appears to monitor the analysis as it runs.

   A warning may appear indicating that the surfaces associated with the hinge piece with a hole are no longer available. This is due to the partition created earlier. If this occurs, do one of the following before submitting the job:

   - If the contact pairs were defined manually, redefine the surfaces associated with the flange face and the flange hole.
   - If the contact pairs were defined automatically, simply delete the contact pairs and redefine the interactions as before.

   A dialog box appears with the name of your job in the title bar and a status chart for the analysis. Messages appear in the lower panel of the dialog box as the job progresses. Click the **Errors** and **Warnings** tabs to check for problems in the analysis.

   Once the analysis is underway, an X-Y plot of the values of the degree of freedom that you selected to monitor earlier in the tutorial appears in a separate window in the viewport. (You may need to resize the viewport windows to see it.) You can follow the progression of the node's displacement over time in the 1-direction as the analysis runs.

6. When the job completes successfully, the status of the job appearing in the Model Tree changes to `Completed`. You are now ready to view the results of the analysis with the Visualization module. In the Model Tree, click mouse button 3 on the job name and select **Results** from the menu that appears.

   Abaqus/CAE enters the Visualization module, opens the output database created by the job, and displays the undeformed shape of the model.

   **Note:** You can also enter the Visualization module by clicking **Visualization** in the **Module** list located in the context bar. However, in this case Abaqus/CAE requires you to open the output database explicitly using the **File** menu.

---

## C.13 Viewing the results of your analysis

You will view the results of your analysis by drawing a contour plot of the deformed model. You will then use display groups to display one of the hinge pieces; by displaying just a portion of the model you can view results that are not visible when you display the whole model.

### C.13.1 Displaying and customizing a contour plot

In this section you will display a contour plot of the model and adjust the deformation scale factor.

**To display a contour plot of the model:**

1. From the main menu bar, select **Plot** -> **Contours** -> **On Deformed Shape**.

   Abaqus/CAE displays a contour plot of von Mises stress superimposed on the deformed shape of the model at the end of the last increment of the loading step, as indicated by the following text in the state block:

   ```
   Step: Load, Apply load
   Increment     6: Step Time =   1.000
   ```

   By default, all surfaces with no results (in this case, the pin) are displayed in white.

   The deformation is exaggerated because of the default deformation scale factor that Abaqus/CAE selects.

2. To remove the white surfaces from the display, do the following:
   - In the Results Tree, expand the **Surface Sets** container underneath the output database file named `PullHinge.odb`.
   - Select all the surfaces that appear in the list.
   - Click mouse button 3, and select **Remove** from the menu that appears.

   The white surfaces disappear from the view.

3. To reduce the deformation scale factor, do the following:
   - From the main menu bar, select **Options** -> **Common**.

     The **Common Plot Options** dialog box appears.
   - From the **Deformation Scale Factor** options, choose **Uniform**.
   - In the **Value** text field, type a value of `100`; and click **OK**.

   Abaqus/CAE displays the contour plot with a deformation scale factor of 100, as shown in Figure C-53.

   ![Contour plot of von Mises stress with a reduced deformation scale factor](../graphics/gst-tut2-highdeform-nls.png)

4. Use the view manipulation tools to examine the deformed model. Note where the pin appears to be exerting the most pressure against the insides of the flanges. Also note how the two flanges have twisted away from each other.

5. By default, the contour plot displays the von Mises stresses in the model; you can view other variables by selecting them from the **Field Output** toolbar. Select **S11** from the list of components and invariants on the right side of the **Field Output** toolbar.

   Abaqus/CAE replaces the default von Mises plot with a contour plot of the stresses in the 1-direction.

6. Select **Max. Principal** from the list of components and invariants to see the maximum principal stresses on the model.

7. Select any other variables of interest from the **Field Output** toolbar.

8. Click the field output button tool in the toolbar to display the **Field Output** dialog box. On the **Primary Variable** tab, select **S** as the output variable, select **Mises** as the invariant, and click **OK** to display the von Mises stresses again and to close the dialog box.

   The **Field Output** dialog box offers some controls and access to other dialog boxes, such as the **Section Points** dialog box, that cannot be accessed from the **Field Output** toolbar.

### C.13.2 Using display groups

You will now create a display group that includes only the element sets that make up the hinge piece that includes the lubrication hole. By removing all other element sets from the display, you will be able to view results for the surface of the flange that contacts the other hinge.

**To create the display group:**

1. In the Results Tree, expand the **Instances** container underneath the output database named `PullHinge.odb`.

2. From the list of available part instances, select **HINGE-HOLE-1**. Click mouse button 3, and select **Replace** from the menu that appears to replace the current display group with the selected elements. Click the auto-fit tool, if necessary, to fit the model in the viewport.

   The contour plot of the entire model is replaced by a plot of only the selected hinge piece, as shown in Figure C-54.

   ![Use display groups to view a contour plot of the von Mises stress in the hinge piece with the lubrication hole](../graphics/gst-tut2-displayop-nls.png)

3. Use the view manipulation tools to view the hinge at different angles. You can now see results for surfaces on the hinge that were hidden by the solid hinge.

4. From the main menu bar, select **Result** -> **Field Output**.

5. From the top of the **Primary Variable** tabbed page, toggle on **List only variables with results:** and choose **at surface nodes** from the menu.

6. From the list of variables that appears, select **CPRESS**, and click **Apply**.

   Abaqus/CAE displays a contour plot of the contact pressures in the flange hole.

For more information about using the Visualization module, see the following sections:

- "Viewing the results of your analysis," Section B.11
- Appendix D, "Viewing the Output from Your Analysis"

You have now completed this tutorial and learned how to:

- create and modify features;
- use datum geometry to add features to a model;
- use position constraints to assemble a model composed of more than one part;
- define contact interactions between regions of a model;
- monitor the progress of an analysis job; and
- use display groups to view results for individual parts of a model.

---

## C.14 Summary

- When you create a part, you can create a deformable part, a discrete rigid surface, or an analytical rigid surface. You can subsequently change the type of the part.
- You can create parts by adding features to the base feature. When you add a feature, you must select a face on which to sketch the profile of the feature. When you delete a feature from a part, Abaqus/CAE also deletes any features that depend on the feature being deleted. These dependent features are called children.
- You can edit features by modifying the sketch of the feature or a parameter associated with the feature, such as an extrusion depth. Editing features can cause dependent features to fail during regeneration.
- The **Datum** toolset allows you to create datum points, axes, and planes. Datum geometry that you create on a part can also be used by the Sketcher. For example, if a suitable sketch plane does not exist, you can use the **Datum** toolset to create one.
- Click **OK** in a dialog box to perform the selected operation and to close the dialog box; click **Apply** to leave the dialog box open while performing the selected operation. Click **Cancel** to close the dialog box without performing an operation.
- You can use the tools in the **View Manipulation** toolbar to change the view of the model to a more convenient one. Use mouse button 2 to stop any view manipulation. If you rotate or pan the sketch, use the cycle view manipulation tool to restore the original view.
- You should save the model database at regular intervals.
- When you create a part instance, the default position is based on the sketch of the base feature. You can ask Abaqus/CAE to offset the new instance along the X-axis so that it does not overlap any existing instances. A graphic indicates the origin and the orientation of the global coordinate system in the Assembly module.
- You position part instances relative to each other in the Assembly module using a sequence of constraint operations.
- Part instances can be classified as either dependent or independent.
- You use the step editor to control the time incrementation during the step.
- You can use managers to display a list of the entities you have defined -- for example, steps -- and to help you perform repeated operations.
- By default, Abaqus/CAE propagates interactions or prescribed conditions defined in one step to all subsequent steps.
- Abaqus/CAE color codes the model to indicate how a region will be meshed. Green indicates that a region can be meshed with structured methods, yellow indicates that a region can be meshed with sweep methods, and orange indicates that a region cannot be meshed.
- You use the **Partition** toolset to divide the model into regions that Abaqus/CAE can mesh.
- When you create and name a job, Abaqus/CAE uses the same name for the input file it generates. Consequently, all files associated with the analysis (for example, the output database, the message file, and the status file) use the same name.
- You can view the progression of a degree of freedom over the course of an analysis that you have chosen to monitor before submitting the job.
- When you first open an output database, Abaqus/CAE displays an undeformed plot of the model.
- You use display groups to display selected regions of your model. A display group can be composed of any combination of selected part instances, geometry (cells, faces, or edges), elements, nodes, or surfaces.

---

*This document is auto-generated from ABAQUS Getting Started with Abaqus: Interactive Edition (6.14)*
