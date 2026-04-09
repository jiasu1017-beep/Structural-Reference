# Appendix B: Creating and Analyzing a Simple Model in Abaqus/CAE

The following section is a basic tutorial for the experienced Abaqus user. It leads you through the Abaqus/CAE modeling process by visiting each of the modules and showing you the basic steps to create and analyze a simple model. To illustrate each of the steps, you will first create a model of a steel cantilever beam and load its top surface (see Figure B-1).

![Figure B-1: A loaded cantilever beam](../graphics/gst-beam.png)

You will then analyze the beam and plot the resulting stresses and displacements. The entire tutorial takes approximately 90 minutes to complete.

The following topics are covered:

- [B.1 Understanding Abaqus/CAE modules](#b1-understanding-abaquscae-modules)
- [B.2 Understanding the Model Tree](#b2-understanding-the-model-tree)
- [B.3 Creating a part](#b3-creating-a-part)
- [B.4 Creating a material](#b4-creating-a-material)
- [B.5 Defining and assigning section properties](#b5-defining-and-assigning-section-properties)
- [B.6 Assembling the model](#b6-assembling-the-model)
- [B.7 Defining your analysis steps](#b7-defining-your-analysis-steps)
- [B.8 Applying a boundary condition and a load to the model](#b8-applying-a-boundary-condition-and-a-load-to-the-model)
- [B.9 Meshing the model](#b9-meshing-the-model)
- [B.10 Creating and submitting an analysis job](#b10-creating-and-submitting-an-analysis-job)
- [B.11 Viewing the results of your analysis](#b11-viewing-the-results-of-your-analysis)
- [B.12 Summary](#b12-summary)

---

## B.1 Understanding Abaqus/CAE modules

Abaqus/CAE is divided into modules, where each module defines an aspect of the modeling process; for example, defining the geometry, defining material properties, and generating a mesh. As you move from module to module, you build the model from which Abaqus/CAE generates an input file that you submit to Abaqus/Standard or Abaqus/Explicit for analysis. For example, you use the **Property** module to define material and section properties and the **Step** module to choose an analysis procedure. The Abaqus/CAE postprocessor is called the **Visualization** module and is also licensed as a separate product called Abaqus/Viewer.

You enter a module by selecting it from the **Module** list in the context bar, as shown in Figure B-2.

![Figure B-2: Selecting a module](../graphics/gst-module-list-nls.png)

For the cantilever beam tutorial, you will enter the following Abaqus/CAE modules and perform the following tasks:

**Part**
Sketch a two-dimensional profile and create a part representing the cantilever beam.

**Property**
Define the material properties and other section properties of the beam.

**Assembly**
Assemble the model and create sets.

**Step**
Configure the analysis procedure and output requests.

**Load**
Apply loads and boundary conditions to the beam.

**Mesh**
Mesh the beam.

**Optimization**
Create an optimization task (not discussed here).

**Job**
Create a job and submit it for analysis.

**Visualization**
View the results of the analysis.

Although the **Module** list in the context bar lists the modules in a logical sequence, you can move back and forth between modules at will. However, certain obvious restrictions apply; for example, you cannot assign section properties to geometry that has not yet been created.

A completed model contains everything that Abaqus/CAE needs to generate an input file and start the analysis. Abaqus/CAE uses a model database to store your models. When you start Abaqus/CAE, the **Start Session** dialog box allows you to create a new, empty model database in memory. After you start Abaqus/CAE, you can save your model database to a disk by selecting **File → Save** from the main menu bar; to retrieve it from a disk, select **File → Open**.

For a complete listing of which module generates a particular keyword, see "Abaqus keyword browser table," Section A.1 of the Abaqus/CAE User's Guide.

---

## B.2 Understanding the Model Tree

The Model Tree provides a visual description of the hierarchy of items in a model. Figure B-3 shows a typical Model Tree.

![Figure B-3: Model Tree](../graphics/uss-int-tree-nls.png)

Items in the Model Tree are represented by small icons; for example, the **Steps** icon. In addition, parentheses next to an item indicate that the item is a container, and the number in the parentheses indicates the number of items in the container. You can click on the "+" and "-" signs in the Model Tree to expand and collapse a container. The right and left arrow keys perform the same operation.

The arrangement of the containers and items in the Model Tree reflects the order in which you are expected to create your model. As noted earlier, a similar logic governs the order of modules in the module menu—you create parts before you create the assembly, and you create steps before you create loads. This arrangement is fixed—you cannot move items in the Model Tree.

The Model Tree provides most of the functionality of the main menu bar and the module managers. For example, if you double-click on the **Parts** container, you can create a new part (the equivalent of selecting **Part → Create** from the main menu bar).

The instructions for the examples that follow will focus on using the Model Tree to access the functionality of Abaqus/CAE. Menu bar actions will be considered only when necessary (e.g., when creating a finite element mesh or postprocessing results).

---

## B.3 Creating a part

You can create parts that are native to Abaqus/CAE, or you can import parts created by other applications either as a geometric representation or as a finite element mesh.

You will start the cantilever beam tutorial by creating a three-dimensional, deformable solid body. You do this by sketching the two-dimensional profile of the beam (a rectangle) and extruding it. Abaqus/CAE automatically enters the Sketcher when you create a part.

Abaqus/CAE often displays a short message in the prompt area indicating what it expects you to do next, as shown in Figure B-4.

![Figure B-4: Messages and instructions are displayed in the prompt area](../graphics/gst-prompt-area-nls.png)

Click the **Cancel** button to cancel the current task. Click the **Previous** button to cancel the current step in the task and return to the previous step.

### To create the cantilever beam:

1. If you did not already start Abaqus/CAE, type `abaqus cae`. Resize your windows so that you can follow the tutorial and see the Abaqus/CAE main window.

2. From the **Create Model Database** options in the **Start Session** dialog box that appears, select **With Standard/Explicit Model**. If you are already in an Abaqus/CAE session, select **File → New** from the main menu bar.

   Abaqus/CAE enters the **Part** module. The Model Tree appears in the left side of the main window. Between the Model Tree and the canvas is the **Part** module toolbox.

3. In the Model Tree, double-click the **Parts** container to create a new part.

   The **Create Part** dialog box appears. Abaqus/CAE also displays text in the prompt area near the bottom of the window to guide you through the procedure.

4. Name the part `Beam`. Accept the default settings of a three-dimensional, deformable body and a solid, extruded base feature. In the **Approximate size** text field, type `300`.

5. Click **Continue** to exit the **Create Part** dialog box.

   Abaqus/CAE automatically enters the Sketcher. The Sketcher toolbox appears in the left side of the main window, and the Sketcher grid appears in the viewport.

   **Tip:** Like all tools in Abaqus/CAE, if you simply position the cursor over a tool in the Sketcher toolbox for a short time, a small window appears that gives a brief description of the tool.

6. To sketch the profile of the cantilever beam, select the rectangle drawing tool.

7. In the viewport, sketch the rectangle using the following steps:

   a. You will first sketch a rough approximation of the beam and then use constraints and dimensions to refine the sketch. Select any two points as the opposite corners of the rectangle.

   b. Click mouse button 2 anywhere in the viewport to exit the rectangle tool.

   **Note:** If you are a Windows user with a 2-button mouse, press both mouse buttons simultaneously whenever you are asked to press mouse button 2.

   c. The Sketcher automatically adds constraints to the sketch (in this case the four corners of the rectangle are assigned perpendicular constraints and one edge is designated as horizontal).

   d. Use the dimension tool to dimension the top and left edges of the rectangle. The top edge should have a horizontal dimension of `200 mm`, and the left edge should have a vertical dimension of `20 mm`.

   e. The final sketch is shown in Figure B-5.

   ![Figure B-5: Sketch of the rectangle](../graphics/gst-sketch-rect.png)

8. If you make a mistake while using the Sketcher, you can delete lines in your sketch:

   a. From the Sketcher toolbox, click the **Delete** tool.

   b. From the sketch, click a line to select it. Abaqus/CAE highlights the selected line in red.

   c. Click mouse button 2 in the viewport to delete the selected line.

   d. Repeat steps b and c as often as necessary.

   **Note:** You can also use the **Undo** tool and the **Redo** tool to undo and redo your previous operations.

9. From the prompt area, click **Done** to exit the Sketcher.

10. Because you are creating an extruded part, Abaqus/CAE displays the **Edit Base Extrusion** dialog box. In the **Depth** field, type a value of `25.0`. Click **OK**.

    Abaqus/CAE displays an isometric view of the new part, as shown in Figure B-6.

    ![Figure B-6: Isometric view of the beam](../graphics/gst-part.png)

11. Before you continue the tutorial, save your model in a model database file.

    a. From the main menu bar, select **File → Save**.

    b. Type a name for the new model database in the **File Name** field, and click **OK**.

---

## B.4 Creating a material

For the cantilever beam tutorial you will create a single linear elastic material with Young's modulus of 209 x 10³ MPa and Poisson's ratio of 0.3.

### To define a material:

1. In the Model Tree, double-click the **Materials** container to create a new material.

   Abaqus/CAE switches to the **Property** module, and the **Edit Material** dialog box appears.

2. Name the material `Steel`. From the material editor's menu bar, select **Mechanical → Elasticity → Elastic**.

   ![Figure B-7: Submenus available under the Mechanical menu](../graphics/prp-buttons-nls.png)

3. Type a value of `209.E3` MPa for Young's modulus and a value of `0.3` for Poisson's ratio, as shown in Figure B-8. Use [Tab] to move between cells.

   ![Figure B-8: Entering data values for the elastic material properties](../graphics/gst-material-editor-nls.png)

4. Click **OK** to exit the material editor.

---

## B.5 Defining and assigning section properties

You define the properties of a part through sections. After you create the section, you can assign the section to the part in the current viewport. For the cantilever beam tutorial you will create a single homogeneous solid section that you will assign to the beam by selecting the beam from the viewport.

### B.5.1 Defining a homogeneous solid section

A homogeneous solid section is the simplest section type that you can define; it includes only a material reference and an optional plane stress/plane strain thickness definition.

### To define the homogeneous solid section:

1. In the Model Tree, double-click the **Sections** container to create a section.

   The **Create Section** dialog box appears.

2. In the **Create Section** dialog box:

   a. Name the section `BeamSection`.

   b. In the **Category** list, accept **Solid** as the default category selection.

   c. In the **Type** list, accept **Homogeneous** as the default type selection.

   d. Click **Continue**.

   The **Edit Section** dialog box appears.

3. In the dialog box:

   a. Accept the default selection of `Steel` for the **Material** associated with the section.

   b. Click **OK**.

### B.5.2 Assigning the section to the cantilever beam

The section `BeamSection` must be assigned to the part.

### To assign the section to the cantilever beam:

1. In the Model Tree, expand the branch for the part named **Beam**.

2. Double-click **Section Assignments** in the list of part attributes that appears.

3. Click anywhere on the beam to select the region to which the section will be applied. Abaqus/CAE highlights the entire beam.

4. Click mouse button 2 in the viewport or click **Done** to accept the selected geometry.

5. Accept the default selection of `BeamSection` as the section, and click **OK**.

   Abaqus/CAE assigns the solid section to the beam, colors the entire beam aqua to indicate that the region has a section assignment.

**Note:** When you assign a section to a region of a part, the region takes on the material properties associated with the section.

---

## B.6 Assembling the model

Each part that you create is oriented in its own coordinate system and is independent of the other parts in the model. Although a model may contain many parts, it contains only one assembly. You define the geometry of the assembly by creating instances of a part and then positioning the instances relative to each other in a global coordinate system.

For the cantilever beam tutorial you will create a single instance of your cantilever beam. Abaqus/CAE positions the instance so that the origin of the sketch that defined the rectangular profile of the beam overlays the origin of the assembly's default coordinate system.

### To assemble the model:

1. In the Model Tree, expand the **Assembly** container. Then double-click **Instances**.

   Abaqus/CAE switches to the **Assembly** module, and the **Create Instance** dialog box appears.

2. In the dialog box, select `Beam` and click **OK**.

   Abaqus/CAE creates an instance of the cantilever beam and displays it using an isometric orientation.

3. In the **View Manipulation** toolbar, click the rotate view manipulation tool.

   When you move the mouse back into the viewport, a circle appears.

4. Drag the mouse in the viewport to rotate the model and examine it from all sides.

   Click mouse button 2 to exit rotate mode.

5. Several other tools (pan, magnify, zoom, and auto-fit) are also available in the **View Manipulation** toolbar to help you examine your model.

---

## B.7 Defining your analysis steps

Now that you have created your part, you can define your analysis steps. For the cantilever beam tutorial the analysis will consist of two steps:

- An initial step, in which you will apply a boundary condition that constrains one end of the cantilever beam.
- A general, static analysis step, in which you will apply a pressure load to the top face of the beam.

Abaqus/CAE generates the initial step automatically, but you must create the analysis step yourself.

### B.7.1 Creating an analysis step

Create a general, static step that follows the initial step of the analysis.

### To create a general, static analysis step:

1. In the Model Tree, double-click the **Steps** container to create a step.

   Abaqus/CAE switches to the **Step** module. The **Create Step** dialog box appears with a list of all the general procedures.

2. Name the step `BeamLoad`.

3. From the list of available general procedures, select **Static, General** and click **Continue**.

4. In the **Description** field, type `Load the top of the beam`.

5. Click the **Incrementation** tab, and accept the default time incrementation settings.

6. Click the **Other** tab to see its contents; you can accept the default values.

7. Click **OK** to create the step.

### B.7.2 Requesting data output

When you submit your job for analysis, Abaqus/Standard or Abaqus/Explicit writes the results of the analysis to the output database.

When you create a step, Abaqus/CAE generates a default output request for the step.

### To examine your output requests:

1. In the Model Tree, click mouse button 3 on the **Field Output Requests** container and select **Manager**.

   The **Field Output Requests Manager** displays an alphabetical list of existing output requests along the left side and the names of all the steps along the top.

2. Review the default output request that Abaqus/CAE generates for the **Static, General** step you created.

3. Click **Edit** to view more detailed information about the output request.

4. Click **Cancel** to close the field output editor, since you do not wish to make any changes.

5. Click **Dismiss** to close the **Field Output Requests Manager**.

6. Review the history output requests in a similar manner.

---

## B.8 Applying a boundary condition and a load to the model

Prescribed conditions, such as loads and boundary conditions, are step-dependent, which means that you must specify the step or steps in which they become active.

### B.8.1 Applying a boundary condition to one end of the cantilever beam

Create a boundary condition that constrains the cantilever beam to be built-in at one end of the beam.

### To apply boundary conditions to one end of the cantilever beam:

1. In the Model Tree, double-click the **BCs** container.

   Abaqus/CAE switches to the **Load** module, and the **Create Boundary Condition** dialog box appears.

2. In the **Create Boundary Condition** dialog box:

   a. Name the boundary condition `Fixed`.

   b. From the list of steps, select `Initial` as the step in which the boundary condition will be activated.

   c. In the **Category** list, accept **Mechanical**.

   d. In the **Types for Selected Step** list, accept **Symmetry/Antisymmetry/Encastre** and click **Continue**.

3. You will fix the face at the left end of the cantilever beam, as shown in Figure B-9.

   ![Figure B-9: Selecting the region on which to apply a boundary condition](../graphics/gst-ambig2.png)

4. Click mouse button 2 in the viewport or click **Done** to indicate that you have finished selecting.

5. In the **Edit Boundary Condition** dialog box:

   a. Toggle on **ENCASTRE**.

   b. Click **OK**.

   Abaqus/CAE displays arrows at each corner and midpoint on the selected face to indicate the constrained degrees of freedom.

6. In the Model Tree, click mouse button 3 on the **BCs** container and select **Manager** to view the **Boundary Condition Manager**.

7. Click **Dismiss** to close the **Boundary Condition Manager**.

### B.8.2 Applying a load to the top of the cantilever beam

Now that you have fixed one end of the cantilever beam, you can apply a distributed load to the top face of the beam.

### To apply a load to the top of the cantilever beam:

1. In the Model Tree, double-click the **Loads** container.

   The **Create Load** dialog box appears.

2. In the **Create Load** dialog box:

   a. Name the load `Pressure`.

   b. From the list of steps, select `BeamLoad` as the step in which the load will be applied.

   c. In the **Category** list, accept **Mechanical**.

   d. In the **Types for Selected Step** list, select **Pressure** and click **Continue**.

3. In the viewport, select the top face of the beam as the surface to which the load will be applied, as shown in Figure B-10.

   ![Figure B-10: Selecting the region on which to apply a pressure load](../graphics/gst-load.png)

4. Click mouse button 2 in the viewport or click **Done**.

5. In the **Edit Load** dialog box:

   a. Enter a magnitude of `0.5` MPa for the load.

   b. Accept the default **Distribution** selection.

   c. Accept the default **Amplitude** selection.

   d. Click **OK**.

   Abaqus/CAE displays downward-pointing arrows along the top face of the beam.

---

## B.9 Meshing the model

You will now generate the finite element mesh. You can choose the meshing technique that Abaqus/CAE will use to create the mesh, the element shape, and the element type.

### B.9.1 Assigning mesh controls

### To assign the mesh controls:

1. In the Model Tree, expand the **Beam** item underneath the **Parts** container and double-click **Mesh**.

   Abaqus/CAE switches to the **Mesh** module.

2. From the main menu bar, select **Mesh → Controls**.

   The **Mesh Controls** dialog box appears. Abaqus/CAE will use structured meshing to mesh your cantilever beam and displays the beam in green.

3. In the dialog box, accept **Hex** as the default **Element Shape** selection.

4. Accept **Structured** as the default **Technique** selection.

5. Click **OK**.

### B.9.2 Assigning an Abaqus element type

### To assign an Abaqus element type:

1. From the main menu bar, select **Mesh → Element Type**.

   The **Element Type** dialog box appears.

2. In the dialog box, accept the following default selections:

   - **Standard** is the default **Element Library** selection.
   - **Linear** is the default **Geometric Order**.
   - **3D Stress** is the default **Family** of elements.

3. Click the **Hex** tab, and choose **Incompatible modes** from the list of formulation options.

   A description of the element type C3D8I appears.

4. Click **OK**.

### B.9.3 Creating the mesh

Basic meshing is a two-stage operation: first you seed the edges of the part instance, and then you mesh the part instance.

### To mesh the model:

1. From the main menu bar, select **Seed → Part** to seed the part instance.

   The **Global Seeds** dialog box appears.

2. Enter an approximate global size of `10.0` and click **OK**.

3. Click **Done** in the prompt area.

   Abaqus/CAE applies the seeds to the part instance, as shown in Figure B-11.

   ![Figure B-11: Seeding the mesh](../graphics/gst-mesh.png)

4. From the main menu bar, select **Mesh → Part** to mesh the part instance.

5. In the prompt area, click **Yes** to confirm that you want to mesh the part instance.

   Abaqus/CAE meshes the part instance and displays the resulting mesh, as shown in Figure B-12.

   ![Figure B-12: Meshing the part](../graphics/gst-meshdone.png)

---

## B.10 Creating and submitting an analysis job

Now that you have configured your analysis, you will create a job that is associated with your model and submit the job for analysis.

### To create and submit an analysis job:

1. In the Model Tree, double-click the **Jobs** container to create a job.

   Abaqus/CAE switches to the **Job** module, and the **Create Job** dialog box appears.

2. Name the job `Deform`.

3. Click **Continue** to create the job.

4. In the **Description** field, type `Cantilever beam tutorial`.

5. Click **OK** to accept all the default job settings.

6. In the Model Tree, expand the **Jobs** container; click mouse button 3 on the job named **Deform**, and select **Submit** to submit your job for analysis.

   The status of the cantilever beam tutorial shows one of the following:

   - **Submitted** while the analysis input file is being generated.
   - **Running** while Abaqus analyzes the model.
   - **Completed** when the analysis is complete.
   - **Aborted** if Abaqus/CAE finds a problem with the input file or the analysis.

7. When the job completes successfully, in the Model Tree click mouse button 3 on the job named **Deform** and select **Results** to enter the **Visualization** module.

---

## B.11 Viewing the results of your analysis

You use the **Visualization** module to read the output database that Abaqus/CAE generated during the analysis and to view the results. Because you named the job `Deform`, Abaqus/CAE names the output database `Deform.odb`.

For the tutorial you will view the undeformed and deformed shapes of the cantilever beam model and create a contour plot.

### To view the results of your analysis:

1. After you select **Results** in the Model Tree, Abaqus/CAE enters the **Visualization** module, opens `Deform.odb`, and displays the undeformed shape of the model, as shown in Figure B-13.

   ![Figure B-13: Undeformed shape plot of model](../graphics/gst-undef-nls.png)

2. From the main menu bar, select **Plot → Deformed Shape** to view a deformed shape plot.

3. Click the auto-fit tool so that the entire plot is rescaled to fit in the viewport, as shown in Figure B-14.

   ![Figure B-14: Deformed shape plot of model](../graphics/gst-def-nls.png)

4. From the main menu bar, select **Plot → Contours → On Deformed Shape** to view a contour plot of the von Mises stress, as shown in Figure B-15.

   ![Figure B-15: Contour plot of Mises stress](../graphics/gst-cont-nls.png)

5. From the main menu bar, select **Result → Field Output** to examine the variables that are available for display.

   By default, the **Mises** invariant of the **Stress components at integration points** variable is selected.

6. Click **Cancel** to close the **Field Output** dialog box.

You have now finished this tutorial.

---

## B.12 Summary

- When you create a part, you name it and choose its type, modeling space, base feature, and approximate size.
- Abaqus/CAE automatically enters the Sketcher when you create or edit a part. You use the Sketcher to draw the two-dimensional profiles of parts.
- Click mouse button 2 in the viewport to indicate you have finished selecting items or using a tool.
- You can create a material and define its properties, and create a section and define its category and type. Since the section refers to the material, the material must be defined first.
- A model contains only one assembly. The assembly is composed of instances of parts positioned in a global coordinate system.
- Abaqus/CAE generates the initial step automatically, but you must create analysis steps. You use the step editor to define each analysis step.
- When you create a step, Abaqus/CAE generates a default output request for the step.
- Prescribed conditions, such as loads and boundary conditions, are step-dependent objects, which means that you must specify the step or steps in which they become active.
- Managers are useful for reviewing and modifying the status of prescribed conditions in each step.
- You create loads and define where the load is applied to the assembly in the **Load** module.
- Although you can create a mesh at any point after creating the assembly, you typically do it after configuring the rest of the model.
- You can assign the element type either before or after you create the mesh.
- You use seeds to define the approximate position of nodes in your final mesh.
- You can use the Model Tree to submit jobs and to monitor the status of a job.
- In the **Visualization** module you read the output database generated by your analysis and view the results.
- You can display the results in several modes—undeformed, deformed, and contour. You can control the appearance of the display in each mode.
