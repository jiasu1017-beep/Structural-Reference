# Appendix E: Flow through a bent tube

This co-simulation tutorial for the experienced Abaqus user illustrates how you can use Abaqus/CFD to model fluid flow through a bent tube and use Abaqus/Standard to model structural deformation in the tube. For more information, see "Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide, and "Fluid-to-structural and conjugate heat transfer co-simulation," Section 17.3.2 of the Abaqus Analysis User's Guide.

---

## E.1 Overview

This simulation illustrates how to model fluid flow through a U-shaped tube. The problem consists of a tube that is clamped at both ends and has a U-shaped bend in the middle, as shown in Figure E-1.

**Figure E-1** Bent tube.

![../graphics/gsa-cfd-fluidpart-nls.png](../graphics/gsa-cfd-fluidpart-nls.png)

Both a rigid and a deformable tube are considered. In the pure flow analysis (corresponding to the case of a rigid tube), you can note interesting flow features such as flow separation and reattachment. Net forces on the tube due to flow can also be measured. In the fluid-structure interaction analysis, the deformation modes of the structure and its effect on the fluid flow can be analyzed.

The fluid flow is modeled in Abaqus/CFD, while the structural deformation is modeled in Abaqus/Standard. The interaction between the two is modeled using a co-simulation approach.

This tutorial includes the following sections:

- ["Creating the model for the fluid flow analysis," Section E.2](#e2-creating-the-model-for-the-fluid-flow-analysis)
- ["Creating a CFD analysis job for the fluid flow analysis," Section E.3](#e3-creating-a-cfd-analysis-job-for-the-fluid-flow-analysis)
- ["Running and monitoring the CFD analysis," Section E.4](#e4-running-and-monitoring-the-cfd-analysis)
- ["Viewing the CFD analysis results," Section E.5](#e5-viewing-the-cfd-analysis-results)
- ["Creating the fluid model for the fluid-structure interaction analysis," Section E.6](#e6-creating-the-fluid-model-for-the-fluid-structure-interaction-analysis)
- ["Creating the structural model for the fluid-structure interaction analysis," Section E.7](#e7-creating-the-structural-model-for-the-fluid-structure-interaction-analysis)
- ["Creating a co-simulation job for the fluid-structure interaction analysis," Section E.8](#e8-creating-a-co-simulation-job-for-the-fluid-structure-interaction-analysis)
- ["Running and monitoring the fluid-structure co-simulation analysis," Section E.9](#e9-running-and-monitoring-the-fluid-structure-co-simulation-analysis)
- ["Viewing the fluid-structure co-simulation analysis results," Section E.10](#e10-viewing-the-fluid-structure-co-simulation-analysis-results)

---

## E.2 Creating the model for the fluid flow analysis

You will first create the model for the fluid flow analysis. In this case the tube is assumed rigid. This scenario can be modeled only with a Computational Fluid Dynamics (CFD) analysis since the fluid boundaries do not deform.

### E.2.1 Creating the CFD model

Start Abaqus/CAE (if you are not already running it). You will first perform a pure flow analysis in which the tube is assumed rigid. After that analysis you will perform a fluid-structure interaction analysis in which the tube is considered deformable.

In the Model Tree, double-click **Models**. In the **Edit Model Attributes** dialog box, enter `fluid-cfd` as the name and select **CFD** as the type. Click **OK**.

This tutorial discusses how to use Abaqus/CAE to create the entire model for this simulation. Abaqus provides scripts that replicate the complete analysis model for this problem. If you encounter difficulties following the instructions given below or if you wish to check your work, you can run the plug-in script for this example, which is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins** → **Abaqus** → **Getting Started**; highlight **Flow through a bent tube**; and click **Run**. For more information about the Getting Started plug-ins, see "Running the Getting Started with Abaqus examples," Section 82.1 of the Abaqus/CAE User's Guide.

### E.2.2 Defining the part

The first step in creating the model is to define its geometry. You will create a three-dimensional part using a swept solid base feature.

**To create a part:**

1. In the Model Tree, under the model `fluid-cfd`, double-click **Parts** to create a new part. In the **Create Part** dialog box, name the part `fluid`, select **Swept solid** as the base feature, and **0.5** as the approximate size. Click **Continue**.

2. Sketch the sweep path for the part. Use the dimensions given in Figure E-2 to sketch a sweep path.

**Figure E-2** Sweep path for the fluid part.

![../graphics/gsa-cfd-sweeppath.png](../graphics/gsa-cfd-sweeppath.png)

3. Click **Done** in the prompt area.

4. Create a section sketch that will be swept along the sketched path to create a part. Enter **0.1** as the maximum scale for the section sketch.

5. Create the profile for the circular section as shown in Figure E-3. Place the center of the circle at the origin and the perimeter point along the *Y*- or *Z*-axis.

**Figure E-3** Section for the fluid part.

![../graphics/gsa-cfd-fluid-part-section.png](../graphics/gsa-cfd-fluid-part-section.png)

6. Click **Done** in the prompt area.

   Abaqus/CAE creates the part representing the fluid domain, as shown in Figure E-4. The inlet and outlet faces are indicated in the figure.

**Figure E-4** Fluid part.

![../graphics/gsa-cfd-fluidpart-inletoutlet-nls.png](../graphics/gsa-cfd-fluidpart-inletoutlet-nls.png)

### E.2.3 Partitioning the part

To ensure that the part can be meshed using hexahedral elements, we will partition it appropriately to permit a combination of structured and swept meshing.

**To partition the part:**

1. In the Model Tree, expand the **fluid** item under the **Parts** container, and double-click **Mesh** in the menu that appears to switch to the Mesh module.

   The part is initially colored orange, which means that it cannot be meshed using the default hexahedral element shape.

2. Use the **Partition Face: Sketch** tool to create a sketch of a circular section that will partition the inlet face. Place the center of the circle at the origin and the perimeter point along the *Y*- or *Z*-axis. The dimensions of the sketch are shown in Figure E-5.

**Figure E-5** Face partition sketch.

![../graphics/gsa-cfd-face-partition.png](../graphics/gsa-cfd-face-partition.png)

3. Create a partition cutting midway through the entire part in the *X-Y* plane, as shown in Figure E-6.

**Figure E-6** Partition along *X-Y* plane.

![../graphics/gsa-cfd-partition-xyplane.png](../graphics/gsa-cfd-partition-xyplane.png)

   a. Click the **Partition Cell: Define Cutting Plane** tool, and select **Normal To Edge** in the prompt area to specify the cutting plane.

   b. When prompted to select an edge, select the outer circular edge at the inlet.

   c. When prompted to select a point on the edge, select a point on the edge on the vertical *Y*-axis.

   d. Click **Create Partition** in the prompt area to complete the first partition.

4. Use the circular partition on the inlet face to make a swept cut along the entire length of the tube, as shown in Figure E-7.

**Figure E-7** Partition of cylindrical core.

![../graphics/gsa-cfd-partition-core.png](../graphics/gsa-cfd-partition-core.png)

   a. Click and hold the **Partition Cell** tool to reveal additional tools, and select the **Partition Cell: Extrude/Sweep Edges** tool.

   b. Select the entire part, and click **Done** in the prompt area.

   c. In the prompt area, choose the **by edge angle** selection technique. Accept the default angle of `20.0`.

   d. Select the circular edge created by the face partition on the inlet face, and click **Done**.

   e. Click **Sweep Along Edge** as the sweep method. Select the top edge of the straight section containing the inlet. This edge was created by the partition in the previous step.

   f. Click **Create Partition**.

   Abaqus/CAE adds a cylindrical core in the straight section of the tube. Repeat the process four more times to extend the cylindrical core throughout the entire length of the tube.

5. Create additional partitions along the length of the tube.

   a. Click the **Partition Cell: Define Cutting Plane** tool.

   b. Select the entire part, and click **Done** in the prompt area.

   c. Click **Point & Normal** in the prompt area to specify the cutting plane.

   d. When prompted to select a point, select the point on the outer circumferential edge between the straight section containing the outlet and its adjacent curved section, as shown in Figure E-8.

   e. Click **Create Partition** in the prompt area.

   f. When prompted to select an edge, select the straight edge indicated in Figure E-8.

**Figure E-8** Partition using straight edge to define normal.

![../graphics/gsa-cfd-partition-straightedge.png](../graphics/gsa-cfd-partition-straightedge.png)

   g. Repeat the procedure for the straight section attached to the inlet.

   h. For the curved section in the center of the part, use the **3 Points** method to define a cutting plane, as indicated in Figure E-9.

**Figure E-9** Partition using 3 points method.

![../graphics/gsa-cfd-partition-3pts.png](../graphics/gsa-cfd-partition-3pts.png)

6. Partition the curved sections in the center of the part using the **Normal to Edge** method. Select the outer circular edge and the point midway along the edge to define the plane. The partition is shown in Figure E-10.

### E.2.4 Creating sets and surfaces

You will now create sets and surfaces that will be utilized to define section properties and boundary conditions. Sets and surfaces identify the regions where analysis attributes are applied.

**To define sets:**

1. In the Model Tree, expand the container for the part named **fluid** and double-click **Sets**.

2. In the **Create Set** dialog box, name the set `all` and click **Continue**.

3. Select the entire geometry in the viewport, and click **Done** in the prompt area.

   Abaqus/CAE creates a set that contains the entire part.

4. Repeat this procedure to create a set named `fixed` containing the faces at the inlet and outlet sections of the fluid domain, as shown in Figure E-10.

**Figure E-10** Set `fixed`.

![../graphics/gsa-cfd-set-fixed.png](../graphics/gsa-cfd-set-fixed.png)

5. Create a set named `seed-1` containing the straight edges running radially through the tube between the central core and the outer surface, as indicated in Figure E-11 and Figure E-12. This set will be used to assign mesh seeds.

   **Tip:** Switch to the wireframe view to facilitate your selections.

**Figure E-11** Set `seed-1`.

![../graphics/gsa-cfd-set-seed1.png](../graphics/gsa-cfd-set-seed1.png)

**Figure E-12** Close-up view of set `seed-1`.

![../graphics/gsa-cfd-set-seed1-closeup.png](../graphics/gsa-cfd-set-seed1-closeup.png)

6. Create a set named `seed-2` containing the straight edges running axially through the tube, as indicated in Figure E-13. This set will also be used to assign mesh seeds.

**Figure E-13** Set `seed-2`.

![../graphics/gsa-cfd-set-seed2.png](../graphics/gsa-cfd-set-seed2.png)

**To define surfaces:**

1. In the Model Tree, expand the container for the part named **fluid** and double-click **Surfaces**.

2. In the **Create Surface** dialog box, name the surface `inlet` and click **Continue**.

3. In the prompt area, select **by angle** as the selection technique. Select the faces at the inlet of the tube (Figure E-14 depicts the location of the surface).

4. Click **Done** in the prompt area.

5. Repeat the previous steps to create a surface named `outlet` at the outlet of the tube.

6. Repeat the previous steps to create a surface named `wall` representing the outer surface of the tube (excluding the inlet and outlet).

**Figure E-14** Surface definitions for the tube.

![../graphics/gsa-cfd-surfaces-nls.png](../graphics/gsa-cfd-surfaces-nls.png)

### E.2.5 Material and section properties

The next step in creating the model involves defining and assigning material and section properties to the fluid part. Each region of the model must refer to a section property. In this model we assume the fluid is a Newtonian fluid with density 1000 kg/m³ and a viscosity of 0.001 Pa·s (i.e., water).

**To define material properties:**

1. In the Model Tree, double-click **Materials** to create a new material named `fluid`.

2. From the material editor, select **General** → **Density** and specify a density value of `1000` kg/m³.

3. From the material editor, select **Mechanical** → **Viscosity** and specify a viscosity value of `0.001` Pa·s.

4. Click **OK**.

   Abaqus/CAE creates the material definition.

**To define the CFD section:**

1. In the Model Tree, double-click **Sections** to create a new section named `fluid`. Accept the default selection of a homogeneous fluid section, and click **Continue**.

2. In the **Edit Section** dialog box, select **fluid** as the material and click **OK**.

   Abaqus/CAE creates a fluid section definition.

**To assign the CFD section:**

1. In the Model Tree, expand the **Parts** container and the **fluid** container under it, then double-click **Section Assignments**.

2. In the prompt area, click **Sets**. In the **Region Selection** dialog box, choose **all** and click **Continue**.

3. Click **OK** in the section assignment editor.

### E.2.6 Meshing the fluid domain

You will now mesh the fluid domain.

**To mesh the fluid domain:**

1. In the Model Tree, expand the container for the part named **fluid** and double-click **Mesh**. Note that the core partition of the tube is colored yellow, while the outside cells are colored green; these color cues mean that the core can be meshed with a sweep meshing technique, while the outside cells can be meshed using a structured meshing technique.

2. Before meshing the part, assign mesh seeds. This seeding method creates a mesh that is finer near the walls of the tube and becomes coarser radially inward.

   First create seeds for the outside cells.

   a. Click the **Seed Edges** tool, and then click **Sets/Surfaces** in the prompt area (if necessary).

   b. In the **Region Selection** dialog box, select **seed-1** as the set and click **Continue**.

   c. In the **Local Seeds** dialog box, select **By size** as the method, **Single** as the bias type, and enter `0.0004` as the minimum size and `0.001` as the maximum size.

   d. Zoom in to ensure that the seeds are concentrated near the wall. You can verify seed placement by confirming that the arrow indicating the bias direction points radially outward for each edge in the selected set.

   e. If any arrow points radially inward, you can flip it by clicking **Select** next to **Flip bias** and selecting the edges where the bias direction needs to be flipped.

3. Create seeds along the length of the tube.

   a. Follow the steps outlined above to create biased seeds that ensure coarser seeding at the inlet and outlet and finer seeds at the sections where the straight tube sections transition to the curved sections.

   b. In the **Region Selection** dialog box, select **seed-2** as the set and click **Continue**.

   c. In the **Local Seeds** dialog box, select **By size** as the method, **Single** as the bias type, and enter `0.0035` as the minimum size and `0.01` as the maximum size.

   d. Ensure that each arrow points axially inward on both the inlet as well as the outlet sides of the tube. Flip the direction of any arrow that violates this condition.

4. Set the global seed size.

   a. Click the **Seed Part** tool. In the **Global Seeds** dialog box, enter `0.0025` as the approximate global size.

   b. Accept all other default values, and click **OK**.

   Abaqus/CAE sets the global seed size for the entire part.

5. Use the medial axis algorithm for the swept mesh regions of the part.

   a. Use the **Display Group** toolbar to display only the inner core of the tube (colored yellow).

      **Tip:** Choose **Cells** as the selection method, and remove the outer regions of the part.

   b. Click the **Mesh Controls** tool, and assign the **Medial axis** mesh algorithm.

   c. Restore the visibility of all part regions.

6. Click the **Mesh Part** tool, and click **Yes** in the prompt area to create the part mesh.

   Abaqus/CAE displays the mesh, creating approximately 9000 elements.

### E.2.7 Assembling the parts

An assembly contains all the geometry included in the model. Each Abaqus/CAE model contains a single assembly. The assembly is initially empty, even when you have created a part. You will create an instance of the part in the assembly to include it in your model.

**To instance a part:**

1. In the Model Tree, expand the **Assembly** container and double-click **Instances** in the list that appears to create an instance of the part.

2. In the **Create Instance** dialog box, select **fluid** from the **Parts** list and click **OK**.

### E.2.8 Defining steps and output requests

You will now define the analysis steps. Attributes such as boundary conditions and output requests can be step dependent, so an analysis step must be defined before these items can be specified.

**To define an incompressible turbulent flow analysis step:**

1. In the Model Tree, double-click **Steps**.

2. In the **Create Step** dialog box, accept **Flow** as the default procedure type and the default step name (`Step-1`). Click **Continue**.

3. From the **Basic** tabbed page of the step editor, do the following:

   a. Enter `Flow in a rigid hose` as the description.

   b. Enter `0.8` sec as the time period.

4. From the **Incrementation** tabbed page of the step editor, do the following:

   a. Accept **Automatic** (**Fixed CFL**) as the default time incrementation type.

   b. Enter `0.001` as the initial time increment.

   c. Enter `2.0` as the **Maximum CFL number**.

5. From the **Solvers** tabbed page of the step editor, accept the default settings on the **Momentum Equation**, **Pressure Equation**, and **Transport Equation** tabbed pages.

6. From the **Turbulence** tabbed page of the step editor, select **Spalart-Allmaras** as the turbulence model. Abaqus/CAE will use the Spalart-Allmaras turbulence model for turbulent flow calculations.

7. Click **OK** to close the **Create Step** dialog box.

**To define output requests:**

1. In the Model Tree, expand the **Field Output Requests** container. Note that a default field output request named **F-Output-1** was created automatically at the time the step was created.

2. Double-click **F-Output-1**. Note that the output is requested at 20 evenly spaced time intervals.

3. Delete the preselected output, and select the following output variables: **V**, **PRESSURE**, **DIV**, **TURBNU**, and **VORTICITY**.

4. Click **OK** to close the output request editor.

### E.2.9 Defining boundary and initial conditions

You will now define boundary conditions and a predefined field for turbulence. We are solving a transient turbulent flow problem so specification of initial turbulence at time = 0 is required.

**To define boundary conditions:**

1. Define an inlet boundary condition at the inlet surface.

   a. In the Model Tree, double-click **BCs**.

   b. Name the boundary condition `inlet`, and select **Step-1** as the step.

   c. Select **Fluid** as the category and **Fluid inlet/outlet** as the type.

   d. Select `fluid-1.inlet` as the surface to which the boundary condition will be applied (click **Surfaces** in the prompt area if necessary).

   e. From the **Momentum** tabbed page of the boundary condition editor, toggle on **Specify** and select **Velocity**.

   f. Set the *X*-velocity component **V1** to `1`. Set the *Y*- and *Z*-velocity components **V2** and **V3** to `0`.

   g. From the **Turbulence** tabbed page, toggle on **Kinematic eddy viscosity** and enter a value of `5e-6`. Abaqus/CAE sets the inlet turbulence of the flow.

   h. Click **OK** to create the boundary condition and to close the boundary condition editor.

2. Define an outlet boundary condition at the outlet surface.

   a. In the Model Tree, double-click **BCs**.

   b. Name the boundary condition `outlet`, and select **Step-1** as the step.

   c. Select **Fluid** as the category and **Fluid inlet/outlet** as the type.

   d. Select `fluid-1.outlet` as the surface to which the boundary condition will be applied.

   e. From the **Momentum** tabbed page of the boundary condition editor, toggle on **Specify** and select **Pressure**.

   f. Set the pressure to `0`.

   g. Click **OK** to create the boundary condition and to close the boundary condition editor.

3. Define a no-slip/no-penetration boundary condition at the cylinder surface.

   a. In the Model Tree, double-click **BCs**.

   b. Name the boundary condition `noSlip`, and select **Step-1** as the step.

   c. Select **Fluid** as the category and **Fluid wall condition** as the type.

   d. Select `fluid-1.wall` as the surface to which the boundary condition will be applied.

   e. Select **No slip** as the condition.

   f. Click **OK** to close the boundary condition editor.

   Abaqus/CAE creates the no-slip/no-penetration boundary condition.

**To specify a predefined field for the turbulent viscosity:**

1. In the Model Tree, double-click **Predefined Fields**.

2. Name the initial condition `initial turbulence`, and select **Initial** as the step.

3. Select **Fluid** as the category and **Fluid turbulence** as the type.

4. Set the **Kinematic eddy viscosity** to `5e-6`.

5. Click **OK** to close the predefined field editor.

   Abaqus/CAE creates the predefined field for turbulent viscosity.

### E.2.10 Specifying surface output requests

Surface output quantities in fluid flow analyses are required because they provide important insight into the adequacy and correctness of the CFD simulation. For example, measuring the inlet and outlet mass flow rates can give us a good sense of the mass balance. Proper mass balance should be ensured for accurate CFD results. In addition, a measure of the nondimensional wall distance (Y⁺) indicates if the mesh at the walls is suitable to resolve essential turbulent flow features. For more information about fluid dynamics at a wall, see "Incompressible fluid dynamic analysis," Section 6.6.2 of the Abaqus Analysis User's Guide.

You will now request surface output quantities. Since these are not supported through the Abaqus/CAE interface, they will be included using the keywords editor.

**To request surface output quantities:**

1. In the Model Tree, click mouse button 3 on the **fluid-cfd** model and select **Edit Keywords** from the menu that appears.

   The keywords editor appears.

2. Scroll down, and click in the `*Output, field` option block.

3. Click **Add After**, and enter the following:

   ```
   *Surface output, surface=fluid-1.wall
    yplus
   ```

4. Navigate to the `*Output, history` option block, and change the output frequency to `1`.

5. Click **Add after**, and enter the following:

   ```
   *Surface output, surface=fluid-1.inlet
    massflow,
   *Surface output, surface=fluid-1.outlet
    massflow,
   ```

6. Click **OK** to close the keywords editor.

   Abaqus/CAE modifies the selected output requests.

---

## E.3 Creating a CFD analysis job for the fluid flow analysis

In this section you will define a job for the fluid flow analysis.

**To create a CFD analysis job:**

1. In the Model Tree, expand the **Analysis** container.

2. Double-click **Jobs**.

3. In the **Create Job** dialog box, select the model **fluid-cfd** and name the job `fluid-cfd`.

   Abaqus/CAE creates the new analysis job.

---

## E.4 Running and monitoring the CFD analysis

Now that the model setup is complete, you will run the CFD analysis job.

**To run the job:**

1. In the Model Tree, expand the **Jobs** container.

2. Click mouse-button 3 on the job named **fluid-cfd**, and select **Submit** from the menu that appears.

Abaqus/CAE runs the analysis job. While the job is running, you can monitor its progress; click mouse button 3 on the job in the Model Tree, and select **Monitor** from the menu that appears. Note that Abaqus/CAE updates divergence (RMS) and kinetic energy every time increment.

---

## E.5 Viewing the CFD analysis results

Once the job **fluid-cfd** completes, perform the steps in this section to display contour plots and *X-Y* plots of the output data.

**To view the CFD analysis results:**

1. Click mouse button 3 on the job named **fluid-cfd**, and select **Results** from the menu that appears.

   The output database file `fluid-cfd.odb` opens in the Visualization module.

2. Create pressure and velocity contour plots.

   a. In the toolbox, click the **View Cut** tool to activate a view cut.

   b. Click the **View Cut Manager** icon.

   c. In the **View Cut Manager**, select the **Z-Plane**.

      Abaqus/CAE creates a view cut of the fluid domain showing the interior.

   d. From the **Views** toolbar, select the front view.

   e. In the toolbox, click the **Contour Plot** tool to create a contour plot.

   f. From the main menu bar, select **Result** → **Field Output**. In the **Field Output** dialog box, select **PRESSURE** as the output variable and click **OK**.

   g. In the toolbox, click the **Common Plot Options** tool. Toggle on **Feature edges** for the visible edges, and click **OK**.

      Abaqus/CAE hides the mesh feature lines in the model.

   h. In the toolbox, click the **Contour Plot Options** tool. Toggle on **Continuous under Contour Intervals**, and click **Apply**.

      Abaqus/CAE creates a smooth pressure contour plot, as shown in Figure E-15.

**Figure E-15** Pressure contour plot.

![../graphics/gsa-cfd-contour-pressure.png](../graphics/gsa-cfd-contour-pressure.png)

   i. Using the **Field Output** toolbar, select **V** as the output variable to plot.

      A contour plot of the velocity magnitude appears, as shown in Figure E-16.

**Figure E-16** Velocity magnitude contour plot.

![../graphics/gsa-cfd-contour-velocity.png](../graphics/gsa-cfd-contour-velocity.png)

   j. In the toolbox, click the **Animation** tool to create a time history animation. Select an output variable (velocity, pressure, etc.) to animate the results.

3. Plot the turbulence variables.

   a. Using the **Field Output** toolbar, select **TURBNU** as the output variable.

      Abaqus/CAE displays a smooth contour plot of turbulent viscosity, as shown in Figure E-17.

**Figure E-17** Turbulent viscosity contour plot.

![../graphics/gsa-cfd-contour-viscosity.png](../graphics/gsa-cfd-contour-viscosity.png)

   b. Toggle off the view cut by clicking the **View cut** tool.

   c. From the **Views** toolbar, select the isometric view.

   d. Using the **Field Output** toolbar, select **YPLUS** as the output variable.

      Abaqus/CAE creates a smooth contour plot of nondimensional wall distance on the wall surface, as shown in Figure E-18.

**Figure E-18** YPLUS contour plot.

![../graphics/gsa-cfd-contour-yplus.png](../graphics/gsa-cfd-contour-yplus.png)

4. Verify the mass balance.

   a. Select **Tools** → **XY Data** → **Create**.

   b. In the **Create XY Data** dialog box that appears, select **ODB history output** as the source, and click **Continue**.

   c. In the **History Output** dialog box, select the **MASSFLOW** output at the inlet and outlet and click **Plot**, as shown in Figure E-19.

**Figure E-19** Mass flow rates at inlet and outlet.

![../graphics/gsa-cfd-massflow-inletoutlet.png](../graphics/gsa-cfd-massflow-inletoutlet.png)

   d. In the **History Output** dialog box, click **Save As**.

   e. In the **Save XY Data As** dialog box, select **sum** as the **Save Operation**, name the new *X-Y* data object `mass-balance`, and click **OK**.

      Abaqus/CAE creates a plot representing the sum of mass flow rates at the inlet and the outlet surfaces, as shown in Figure E-20. The plot verifies that inlet and outlet mass flow rates are balanced.

**Figure E-20** Sum of mass flow rates.

![../graphics/gsa-cfd-massflow-sum.png](../graphics/gsa-cfd-massflow-sum.png)

---

## E.6 Creating the fluid model for the fluid-structure interaction analysis

You will now create models to perform the fluid-structure interaction analysis of fluid flow inside a deformable tube. Two models must be created: one for the fluid flow and another for the structural response of the tube. You will first create the fluid model that is used in the fluid-structure interaction analysis.

### E.6.1 Defining the fluid model

In this section you copy the previously created fluid model to a new model that will be used in the fluid-structure interaction analysis.

**To create the fluid model:**

1. In the Model Tree, click mouse button 3 on the model named **fluid-cfd**.

2. From the menu that appears, select **Copy Model**.

3. Name the new model `fluid`, and click **OK**.

Abaqus/CAE creates the fluid model. Make all subsequent changes to this model.

### E.6.2 Modifying the analysis step and output requests

You will now modify the total analysis time for the fluid-structure interaction analysis.

**To modify the analysis step and its output requests:**

1. Modify the CFD analysis step in the model named `fluid`.

   a. In the Model Tree, expand the **Steps** container and double-click **Step-1**.

      The step editor appears.

   b. From the **Basic** tabbed page, do the following:

      i. Modify the description to read `Flow in a deformable hose`.

      ii. Set the time period of the step to `0.2` sec.

2. Modify the output requests.

   a. In the Model Tree, expand the **Field Output Requests** container.

   b. Double-click **F-Output-1**.

   c. Select **Every x units of time** as the frequency, and enter `0.02` as the time interval.

   d. Click **OK**.

   Abaqus/CAE makes the specified changes to the analysis.

### E.6.3 Modifying the boundary conditions

You will now modify the boundary conditions. The no-slip/no-penetration wall boundary condition on the tube wall surface is suppressed because the fluid velocities and mesh displacements are dictated by the coupled solution. Therefore, it is not necessary to specify this boundary condition.

In addition, since the Arbitrary Lagrangian-Eulerian (ALE) method is activated to accommodate the displacements of the tube, appropriate boundary conditions are required for the mesh deformation solution.

**To modify the boundary conditions:**

1. Suppress the no-slip/no-penetration wall boundary condition on the tube wall surface.

   a. In the Model Tree, expand the container for the **fluid** model and expand its **BCs** container.

   b. Click mouse button 3 on the boundary condition named **noSlip**, and select **Suppress** from the menu that appears.

   Abaqus/CAE suppresses the wall boundary condition on the fluid surface.

2. Create the mesh displacement boundary conditions by defining a fixed-mesh condition at the inlet and outlet boundaries.

   a. In the Model Tree, double-click **BCs** to create a new boundary condition named `fix-mesh`.

   b. Select **Mechanical** as the category and **Displacement/Rotation** as the type, and click **Continue**.

   c. Select `fluid-1.fixed` as the set to which the boundary condition will be applied.

   d. Set **U1, U2,** and **U3** to `0`.

   e. Click **OK** to close the boundary condition editor.

### E.6.4 Defining the fluid-structure interaction

The CFD model includes a surface definition representing the region of the fluid that interacts with the tube surface. This surface is used to define the co-simulation interaction with the structural model.

**To define a fluid-structure interaction:**

1. In the Model Tree, double-click **Interactions**.

2. Name the interaction `fsi`.

3. Select **Step-1** as the step in which it will be defined, and accept **Fluid-Structure Co-simulation boundary** as the type.

4. Select `fluid-1.wall` as the surface to which the interaction will be applied.

5. Click **OK** to close the interaction editor.

### E.6.5 Specifying CFD analysis controls for co-simulation

The recommended practice to improve convergence behavior is to specify the ratio of the solid-to-fluid density. This specification is particularly important when the ratio is close to one, as is the case in this analysis (as shown below, the density of the tube is 1100 kg/m³, implying a ratio of 1.1).

You can specify the ratio of solid-to-fluid density in Abaqus/CAE using the keywords editor.

**To specify CFD analysis controls:**

1. In the Model Tree, click mouse button 3 on the **fluid** model and select **Edit Keywords** from the menu that appears.

   The keywords editor appears.

2. Scroll down and click in the option block just prior to the `*Co-simulation` option block, and click **Add After**.

3. Enter the following:

   ```
   *Controls, type=FSI
    , , , 1.1
   ```

4. Click **OK**.

   Abaqus/CAE saves your changes to the CFD analysis controls.

---

## E.7 Creating the structural model for the fluid-structure interaction analysis

You will now create the structural model for the tube.

### E.7.1 Defining the model

In the Model Tree, double-click **Models**. In the **Edit Model Attributes** dialog box, enter `solid` as the name and select **Standard & Explicit** as the model type. Click **OK**.

### E.7.2 Defining the part

The structural part will be based on the existing part used to define the fluid. You will modify the structural part to represent the U-shaped tube by deleting the existing features of the part and creating a shell from the solid.

**To define the part:**

1. From the main menu bar, select **Model** → **Copy Objects**. In the **Copy Objects** dialog box, select **fluid** as the **From model** and **solid** as **To model**.

2. Expand the **Parts** container, and select the **fluid** part.

3. Click **OK**.

   Abaqus/CAE copies the **fluid** part from the **fluid** model into the **solid** model.

4. Rename the part. In the Model Tree, expand the **Parts** container underneath the **solid** model. Click mouse button 3 on the **fluid** part, and select **Rename** from the menu that appears.

5. In the **Rename Part** dialog box, enter `solid` as the new name and click **OK**.

**To delete the existing features of the solid part:**

1. In the Model Tree, expand the **Section Assignments** container under the **solid** part.

2. Click mouse button 3 on the section **fluid** (which is no longer relevant), and select **Delete** from the menu that appears. Click **Yes** to confirm the operation.

3. Expand the **Sets** container under the **solid** part.

4. Select all the sets, click mouse button 3 on the selections, and select **Delete** from the menu that appears. Click **Yes** to confirm the operation.

5. Repeat this process to delete all the surfaces and all the face and cell partitions.

**To create a shell from the solid:**

1. From the main menu bar in the Part module, select **Tools** → **Geometry Edit**. In the **Geometry Edit** dialog box, select **Face** as the category and **Remove** as the method.

2. Select the faces representing the inlet and the outlet.

3. Click **Done** in the prompt area.

4. Click **OK** when prompted to delete faces.

5. Close the **Geometry Edit** dialog box.

6. Click mouse button 3 on the **solid** part, and select **Update Validity** from the menu that appears. Abaqus/CAE updates the features of the part.

### E.7.3 Defining partitions

To assign biased meshing to the part, we will first partition it.

**To partition the part:**

1. In the Model Tree, expand the **solid** item under the Parts container and double-click **Mesh** in the menu that appears.

2. Create a datum plane by clicking the **Create Datum Plane: Offset From Principal Plane** tool.

3. Click **XY Plane** in the prompt area. Accept the default offset of `0.0`, and press **[Enter]**.

4. Click the **Partition Face: Use Datum Plane** tool to create a partition running along the length of the tube.

5. Select all the faces of the tube in the viewport, and click **Done** in the prompt area.

6. Select the datum plane created in the previous step, and click **Create Partition** in the prompt area.

### E.7.4 Creating sets and surfaces

You will now create sets and surfaces that will be utilized to define section properties and boundary conditions.

**To define sets:**

1. In the Model Tree, expand the container for the **solid** part.

2. Double-click **Sets**. In the **Create Set** dialog box, name the set `all` and click **Continue**.

3. Select the entire geometry in the viewport, and click **Done** in the prompt area.

   Abaqus/CAE creates a set containing the entire part.

4. Repeat this procedure to create a set named `ends` containing the edges at the inlet and outlet regions of the tube.

**To define surfaces:**

1. In the Model Tree, expand the container for the **solid** part.

2. Double-click **Surfaces**. In the **Create Surface** dialog box, name the surface `inner` and click **Continue**.

3. In the prompt area, select **by angle** as the selection technique. Select the surface of the tube.

4. In the prompt area, select the color associated with the inner surface of the tube (purple).

5. Repeat the previous steps to create a surface named `outer` by selecting the outer surface (brown) of the shell.

### E.7.5 Specifying material and section properties

The next step in creating the model involves defining and assigning material and section properties to the structural part. Each region of the model must refer to a section property. In this model we are modeling a flexible rubber material using a linear elastic material model. The material properties include a density of 1100 kg/m³, an elastic modulus of 1 MPa, and a Poisson's ratio of 0.45. The tube thickness is assumed to be 2 mm.

**To define material properties:**

1. In the Model Tree, double-click **Materials** to create a new material named `elastic`.

2. From the **General** menu of the material editor, select **Density** and enter a value of `1100` kg/m³.

3. From the **Mechanical** menu of the material editor, select **Elasticity** → **Elastic**.

4. Enter a value of `1.e6` Pa as the **Young's Modulus** and `0.45` as the **Poisson's Ratio**.

5. Click **OK**.

**To define a shell section:**

1. In the Model Tree, double-click **Sections** to create a new section named `shell`.

2. Select **Shell** as the category and **Homogeneous** as the type. Click **Continue**.

3. In the **Edit Section** dialog box, enter `0.002` as the value of the constant shell thickness.

4. Select **elastic** as the material.

5. Click **OK**.

**To assign the shell section:**

1. In the Model Tree, expand the **Parts** container. Expand the container for the part named **solid**.

2. Double-click **Section Assignments**.

3. In the prompt area, click **Sets**. In the **Region Selection** dialog box, choose **all** and click **Continue**.

4. Click **Done** in the prompt area.

5. In the section assignment editor, choose the **shell** section created earlier and click **OK**.

### E.7.6 Creating the mesh

You will now create a mesh for the tube structure.

**To create the mesh:**

1. In the Model Tree, expand the **solid** item under the **Parts** container and double-click **Mesh** in the menu that appears.

   Note that the entire tube is colored pink, which means that the part can be meshed with the default free meshing technique.

2. Change the meshing technique to sweep.

   a. From the main menu bar, select **Mesh** → **Controls**.

   b. Select the entire part in the viewport to assign new controls, and click **Done** in the prompt area.

   c. In the **Mesh Controls** dialog box, select **Sweep** as the technique and click **OK**.

   Abaqus/CAE changes the part's color to yellow in the current viewport.

3. Assign mesh seeds. You create biased seeds for the inlet and outlet regions of the tube. This seeding method creates a mesh that is coarser axially at the inlet and outlet and finer in the middle sections of the tube.

   a. Click the **Seed Edges** tool, and click **Select in Viewport** in the prompt area (if necessary).

   b. In the viewport, select the straight edges in the inlet and outlet regions running along the midplane and click **Done**.

   c. In the **Local Seeds** dialog box, select **By size** as the method, **Single** as the bias type, and enter `0.0045` as the minimum size and `0.01` as the maximum size.

   d. Ensure that the seeding bias is such that seeds are concentrated away from inlet and outlet regions of the tube (i.e., each arrow should point axially inward). Flip the direction of any arrow that violates this condition.

4. Set the global seed size.

   a. Click the **Seed Part** tool.

   b. In the **Global Seeds** dialog box, enter `0.004` as the approximate global size.

   c. Accept all the other default values, and click **OK**.

   Abaqus/CAE sets the global seed size for the part.

5. Mesh the part.

   a. Click the **Mesh Part** tool.

   b. Click **Yes** in the prompt area.

   Abaqus/CAE creates a mesh for the part with approximately 950 shell elements.

### E.7.7 Create the assembly

You will now create an instance of the part in the assembly to include it in your model.

**To instance a part:**

1. In the Model Tree, expand the **Assembly** container and double-click **Instances** in the list that appears to create an instance of the part.

2. In the **Create Instance** dialog box, select **solid** from the **Parts** list and click **OK**.

### E.7.8 Specifying steps and output requests

You will now define the analysis step. An implicit dynamic procedure is used to model the structural response of the tube.

**To define an implicit dynamic analysis step:**

1. In the Model Tree, double-click **Steps**.

2. In the **Create Step** dialog box, accept the default procedure type (**General**) and the default name (`Step-1`). From the list of available procedures, select **Dynamic, Implicit** and click **Continue**.

3. From the **Basic** tabbed page of the step editor, do the following:

   a. Enter `deformation of the tube` as the description.

   b. Enter `0.2` sec as the time period.

   c. Toggle on **Nlgeom**.

   d. Select **Transient fidelity** as the application type.

4. From the **Incrementation** tabbed page of the step editor, do the following:

   a. Enter `1000` as the maximum number of increments.

   b. Enter `0.001` as the initial increment size.

   c. Enter `2.e-6` as the minimum increment size.

   d. Toggle on **Suppress calculation** for the **Half-increment Residual**.

5. Click **OK** to create the step.

**To define output requests:**

1. In the Model Tree, expand the **Field Output Requests** container.

2. Double-click **F-Output-1**.

3. Select **Every x units of time** as the output frequency, and enter `0.02` as the time interval.

4. Accept the default output variables, and click **OK**.

### E.7.9 Defining boundary conditions

The tube is secured at each end, so you need to define an encastre boundary condition for the set definition that includes the ends of the tube.

**To define the boundary conditions:**

1. In the Model Tree, double-click **BCs** underneath the **solid** model.

2. In the **Create Boundary Condition** dialog box, name the boundary condition `fixed-ends` and select **Initial** as the step.

3. Accept **Mechanical** as the category, and select **Symmetry/Antisymmetry/Encastre** as the type.

4. Click **Sets** in the prompt area.

5. In the **Region Selection** dialog box, select the set named **solid-1.ends** and click **Continue**.

6. In the **Edit Boundary Condition** dialog box, select **Encastre** and click **OK**.

   Abaqus/CAE creates the boundary condition.

### E.7.10 Creating a fluid-structure interaction

The structural model includes a surface definition representing the regions of the tube that interact with the fluid. This surface is used to define the co-simulation interaction with the Abaqus/CFD model.

**To create a fluid-structure interaction:**

1. In the Model Tree, double-click **Interactions**.

2. Name the interaction `fsi`.

3. In the **Create Interaction** dialog box, select **Step-1** as the step and **Fluid-Structure Co-simulation boundary** as the type. Click **Continue**.

4. In the **Region Selection** dialog box, select **solid-1.inner** as the surface to which the interaction will be applied and click **Continue**.

5. In the interaction editor, click **OK**.

   Abaqus/CAE creates the fluid-structure interaction.

---

## E.8 Creating a co-simulation job for the fluid-structure interaction analysis

To perform the fluid-structure interaction analysis, the Abaqus/Standard and Abaqus/CFD jobs need to execute simultaneously. A co-simulation is performed where the two solvers exchange information at each co-simulation target time. The co-simulation target time is chosen automatically as the minimum of the time increments required by either the structural or CFD solver. To facilitate the co-simulation of the two analyses, a co-execution job procedure is used. A co-execution job creates the two analysis jobs and runs them simultaneously. It also automatically provides the command line options needed for communication between the two analysis jobs. You will now create a co-simulation job.

**To create a co-simulation job:**

1. In the Model Tree, expand the **Analysis** container.

2. Double-click **Co-executions**, and create a co-execution named `uhose`.

3. In the **Edit Co-execution** dialog box:

   a. Select **fluid** as the first model. Accept the default job name.

   b. Select **solid** as the second model. Accept the default job name.

4. Click **OK**.

In the Model Tree, expand the **Co-executions** container and then expand the **uhose** container. Expand the **Jobs** container under **uhose**. Two analyses jobs have been created: one representing the Abaqus/Standard model and the other representing the Abaqus/CFD model.

---

## E.9 Running and monitoring the fluid-structure co-simulation analysis

You will now run the co-execution job from within Abaqus/CAE.

**To run the co-execution job:**

1. Click mouse button 3 on the co-execution job **uhose**.

2. From the menu that appears, select **Submit**.

   Abaqus/CAE launches the co-execution job. Both the Abaqus/Standard and Abaqus/CFD jobs are launched.

   While the co-execution is running, you can monitor its progress by clicking mouse button 3 on the CFD analysis job **uhose-fluid** and selecting **Monitor** from the menu that appears. Note that Abaqus/CAE updates divergence (RMS) and kinetic energy every time increment.

   You can also monitor the progress of the Abaqus/Standard job **uhose-solid**.

---

## E.10 Viewing the fluid-structure co-simulation analysis results

You can display the results of the fluid-structure co-simulation analysis.

**To view fluid-structure co-simulation analysis results:**

1. Click mouse button 3 on the co-execution named **uhose**.

2. From the menu that appears, select **Results**.

   The output database files `uhose-solid.odb` and `uhose-fluid.odb` are opened simultaneously in the Visualization module and are overlaid in the viewport.

3. Select **View** → **Overlay Plot**. In the **Overlay Plot Layer Manager**, select the layer containing the solid material and click **Plot Single**.

4. Contour the displacement magnitude, as shown in Figure E-21.

**Figure E-21** Deformation of the tube.

![../graphics/gsa-cfd-hose-deform.png](../graphics/gsa-cfd-hose-deform.png)

---

*This document is auto-generated from ABAQUS Getting Started with Abaqus: Interactive Edition (6.14)*
