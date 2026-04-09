10&nbsp;Materials

## 10.&nbsp;Materials

The material library in Abaqus allows most engineering materials to be modeled, including metals, plastics, rubbers, foams, composites, granular soils, rocks, and plain and reinforced concrete. This guide discusses only three of the most commonly used material models: linear elasticity, metal plasticity, and rubber elasticity. All of the material models are discussed in detail in Part V, &#8220;Materials,&#8221; of the Abaqus Analysis User's Guide.

### 10.1&nbsp;Defining materials in Abaqus

You can use any number of different materials in your simulation. Each material definition is given a name. Different regions in a model are associated with different material definitions through the assignment of section properties that refer to the material name.

### 10.2&nbsp;Plasticity in ductile metals

Many metals have approximately linear elastic behavior at low strain magnitudes (see [Figure 10&#8211;1](ch10s02.html#gss-stress-strain)), and the stiffness of the material, known as the Young's or elastic modulus, is constant.

> **Figure:**

Figure 10&#8211;1 Stress-strain behavior for a linear elastic material, such as steel, at small strains.

At higher stress (and strain) magnitudes, metals begin to have nonlinear, inelastic behavior (see [Figure 10&#8211;2](ch10s02.html#gss-nominal)), which is referred to as plasticity.

> **Figure:**

Figure 10&#8211;2 Nominal stress-strain behavior of an elastic-plastic material in a tensile test.

### 10.2.1&nbsp;Characteristics of plasticity in ductile metals

The plastic behavior of a material is described by its yield point and its post-yield hardening. The shift from elastic to plastic behavior occurs at a certain point, known as the elastic limit or yield point, on a material's stress-strain curve (see [Figure 10&#8211;2](ch10s02.html#gss-nominal)). The stress at the yield point is called the yield stress. In most metals the initial yield stress is 0.05 to 0.1% of the material's elastic modulus.

The deformation of the metal prior to reaching the yield point creates only elastic strains, which are fully recovered if the applied load is removed. However, once the stress in the metal exceeds the yield stress, permanent (inelastic) deformation begins to occur. The strains associated with this permanent deformation are called plastic strains. Both elastic and plastic strains accumulate as the metal deforms in the post-yield region.

The stiffness of a metal typically decreases dramatically once the material yields (see [Figure 10&#8211;2](ch10s02.html#gss-nominal)). A ductile metal that has yielded will recover its initial elastic stiffness when the applied load is removed (see [Figure 10&#8211;2](ch10s02.html#gss-nominal)). Often the plastic deformation of the material increases its yield stress for subsequent loadings: this behavior is called work hardening.

Another important feature of metal plasticity is that the inelastic deformation is associated with nearly incompressible material behavior. Modeling this effect places some severe restrictions on the type of elements that can be used in elastic-plastic simulations.

A metal deforming plastically under a tensile load may experience highly localized extension and thinning, called *necking*, as the material fails (see [Figure 10&#8211;2](ch10s02.html#gss-nominal)). The engineering stress (force per unit undeformed area) in the metal is known as the *nominal stress*, with the conjugate *nominal strain* (length change per unit undeformed length). The nominal stress in the metal as it is necking is much lower than the material's ultimate strength. This material behavior is caused by the geometry of the test specimen, the nature of the test itself, and the stress and strain measures used. For example, testing the same material in compression produces a stress-strain plot that does not have a necking region because the specimen is not going to thin as it deforms under compressive loads. A mathematical model describing the plastic behavior of metals should be able to account for differences in the compressive and tensile behavior independent of the structure's geometry or the nature of the applied loads. This goal can be accomplished if the familiar definitions of nominal stress, , and nominal strain, , where the subscript 0 indicates a value from the undeformed state of the material, are replaced by new measures of stress and strain that account for the change in area during the finite deformations.### 10.2.2&nbsp;Stress and strain measures for finite deformations

Strains in compression and tension are the same only if considered in the limit as ; i.e.,

and

where *l* is the current length,  is the original length, and  is the *true strain* or *logarithmic strain*.

The stress measure that is the conjugate to the true strain is called the *true stress* and is defined as

where *F* is the force in the material and *A* is the current area. A ductile metal subjected to finite deformations will have the same stress-strain behavior in tension and compression if true stress is plotted against true strain.### 10.2.3&nbsp;Defining plasticity in Abaqus

When defining plasticity data in Abaqus, you must use *true stress* and *true strain*. Abaqus requires these values to interpret the data correctly.

Quite often material test data are supplied using values of nominal stress and strain. In such situations you must use the expressions presented below to convert the plastic material data from nominal stress-strain values to true stress-strain values.

The relationship between true strain and nominal strain is established by expressing the nominal strain as

Adding unity to both sides of this expression and taking the natural log of both sides provides the relationship between the true strain and the nominal strain:

The relationship between true stress and nominal stress is formed by considering the incompressible nature of the plastic deformation and assuming the elasticity is also incompressible, so

The current area is related to the original area by

Substituting this definition of *A* into the definition of true stress gives

where

can also be written as

Making this final substitution provides the relationship between true stress and nominal stress and strain:

These relationships are valid only prior to necking.

The classical metal plasticity model in Abaqus defines the post-yield behavior for most metals. Abaqus approximates the smooth stress-strain behavior of the material with a series of straight lines joining the given data points. Any number of points can be used to approximate the actual material behavior; therefore, it is possible to use a very close approximation of the actual material behavior. The plastic data define the true yield stress of the material as a function of true plastic strain. The first piece of data given defines the initial yield stress of the material and, therefore, should have a plastic strain value of zero.

The strains provided in material test data used to define the plastic behavior are not likely to be the plastic strains in the material. Instead, they will probably be the total strains in the material. You must decompose these total strain values into the elastic and plastic strain components. The plastic strain is obtained by subtracting the elastic strain, defined as the value of true stress divided by the Young's modulus, from the value of total strain (see [Figure 10&#8211;3](ch10s02.html#gss-total-strain)).

> **Figure:**

Figure 10&#8211;3 Decomposition of the total strain into elastic and plastic components.

This relationship is written

where

is true plastic strain,

is true total strain,

is true elastic strain,

is true stress, and

*E*

is Young's modulus.

**Example of converting material test data to Abaqus input**

The nominal stress-strain curve in [Figure 10&#8211;4](ch10s02.html#gss-elastoplast) will be used as an example of how to convert the test data defining a material's plastic behavior into the appropriate input format for Abaqus. The six points shown on the nominal stress-strain curve will be used to determine the plastic data.

> **Figure:**

Figure 10&#8211;4 Elastic-plastic material behavior.

The first step is to use the equations relating the true stress to the nominal stress and strain and the true strain to the nominal strain (shown earlier) to convert the nominal stress and nominal strain to true stress and true strain. Once these values are known, the equation relating the plastic strain to the total and elastic strains (shown earlier) can be used to determine the plastic strains associated with each yield stress value. The converted data are shown in [Table 10&#8211;1](ch10s02.html#gss-chp-mat-stress-table).

Table 10&#8211;1 Stress and strain conversions.

| | Nominal Stress (Pa) | Nominal Strain | True Stress (Pa) | True Strain | Plastic Strain

| | 200E6 | 0.00095 | 200.2E6 | 0.00095 | 0.0

| | 240E6 | 0.025 | 246E6 | 0.0247 | 0.0235

| | 280E6 | 0.050 | 294E6 | 0.0488 | 0.0474

| | 340E6 | 0.100 | 374E6 | 0.0953 | 0.0935

| | 380E6 | 0.150 | 437E6 | 0.1398 | 0.1377

| | 400E6 | 0.200 | 480E6 | 0.1823 | 0.1800

While there are few differences between the nominal and true values at small strains, there are very significant differences at larger strain values; therefore, it is extremely important to provide the proper stress-strain data to Abaqus if the strains in the simulation will be large.

**Data regularization in Abaqus/Explicit**

When performing an analysis, Abaqus/Explicit may not use the material data exactly as defined by the user; for efficiency, all material data that are defined in tabular form are automatically regularized. Material data can be functions of temperature, external fields, and internal state variables, such as plastic strain. For each material point calculation, the state of the material must be determined by interpolation, and, for efficiency, Abaqus/Explicit fits the user-defined curves with curves composed of equally spaced points. These regularized material curves are the material data used during the analysis. It is important to understand the differences that might exist between the regularized material curves used in the analysis and the curves that you specified.

To illustrate the implications of using regularized material data, consider the following two cases. [Figure 10&#8211;5](ch10s02.html#gxi-regularized-data) shows a case in which the user has defined data that are not regular.

> **Figure:**

Figure 10&#8211;5 Example of user data that can be regularized exactly.

In this example Abaqus/Explicit generates the six regular data points shown, and the user's data are reproduced exactly. [Figure 10&#8211;6](ch10s02.html#gxi-dif-regularize) shows a case where the user has defined data that are difficult to regularize exactly. In this example it is assumed that Abaqus/Explicit has regularized the data by dividing the range into 10 intervals that do not reproduce the user's data points exactly.

> **Figure:**

Figure 10&#8211;6 Example of user data that are difficult to regularize.

Abaqus/Explicit attempts to use enough intervals such that the maximum error between the regularized data and the user-defined data is less than 3%; however, you can change this error tolerance. If more than 200 intervals are required to obtain an acceptable regularized curve, the analysis stops during the data checking with an error message. In general, the regularization is more difficult if the smallest interval defined by the user is small compared to the range of the independent variable. In [Figure 10&#8211;6](ch10s02.html#gxi-dif-regularize) the data point for a strain of 1.0 makes the range of strain values large compared to the small intervals defined at low strain levels. Removing this last data point enables the data to be regularized much more easily.

**Interpolation between data points**

Abaqus interpolates linearly between the data points provided (or, in Abaqus/Explicit, regularized data) to obtain the material's response and assumes that the response is constant outside the range defined by the input data, as shown in [Figure 10&#8211;7](ch10s02.html#gss-mat-svpe). Thus, the stress in this material will never exceed 480&nbsp;MPa; when the stress in the material reaches 480&nbsp;MPa, the material will deform continuously until the stress is reduced below this value.

> **Figure:**

Figure 10&#8211;7 Material curve used by Abaqus.

**Material calibration in Abaqus/CAE**

Abaqus/CAE allows you to calibrate a material model from test data. With this capability, you can import material test data into Abaqus/CAE, process the data, and derive elastic and plastic isotropic material behaviors from the data. This feature is discussed further in &#8220;Creating material calibrations,&#8221;  Section 12.17 of the Abaqus/CAE User's Guide.

### 10.3&nbsp;Selecting elements for elastic-plastic problems

The incompressible nature of plastic deformation in metals places limitations on the types of elements that can be used for an elastic-plastic simulation. The limitations arise because modeling incompressible material behavior adds kinematic constraints to an element; in this case the limitations constrain the volume at the element's integration points to remain constant. In certain classes of elements the addition of these incompressibility constraints makes the element overconstrained. When these elements cannot resolve all of these constraints, they suffer from volumetric locking, which causes their response to be too stiff. Volumetric locking is indicated by a rapid variation of hydrostatic pressure stress from element to element or integration point to integration point.

The fully integrated, second-order, solid elements available in Abaqus/Standard are very susceptible to volumetric locking when modeling incompressible material behavior and, therefore, should not be used in elastic-plastic simulations. The fully integrated, first-order, solid elements in Abaqus/Standard do not suffer from volumetric locking because Abaqus actually uses a constant volume strain in these elements. Thus, they can be used safely in plasticity problems.

Reduced-integration solid elements have fewer integration points at which the incompressibility constraints must be satisfied. Therefore, they are not overconstrained and can be used for most elastic-plastic simulations. The second-order reduced-integration elements in Abaqus/Standard should be used with caution if the strains exceed 20&#8211;40% because at this magnitude they can suffer from volumetric locking. This effect can be reduced with mesh refinement.

If you have to use fully integrated, second-order elements in Abaqus/Standard, use the hybrid versions, which are designed to model incompressible behavior; however, the additional degrees of freedom in these elements will make the analysis more computationally expensive.

A family of modified second-order triangular and  tetrahedral elements is available that provides improved performance over the first-order triangular and tetrahedral elements and that avoids some of the problems that exist for conventional second-order triangular and tetrahedral elements. In particular, these elements exhibit minimal shear and volumetric locking. These elements are available in addition to fully integrated and hybrid elements in Abaqus/Standard; they are the only second-order continuum (solid) elements available in Abaqus/Explicit.

### 10.4&nbsp;Example: connecting lug with plasticity

You have been asked to investigate what happens if the steel connecting lug from Chapter 4, &#8220;Using Continuum Elements,&#8221; is subjected to an extreme load (60&nbsp;kN) caused by an accident. The results from the linear analysis indicate that the lug will yield. You need to determine the extent of the plastic deformation in the lug and the magnitude of the plastic strains so that you can assess whether or not the lug will fail. You do not need to consider inertial effects in this analysis; thus, you will use Abaqus/Standard to examine the static response of the lug.

The only inelastic material data available for the steel are its yield stress (380&nbsp;MPa) and its strain at failure (0.15). You decide to assume that the steel is perfectly plastic: the material does not harden, and the stress can never exceed 380&nbsp;MPa (see [Figure 10&#8211;8](ch10s04.html#gss-steel)).

> **Figure:**

Figure 10&#8211;8 Stress-strain behavior for the steel.

In reality some hardening will probably occur, but this assumption is conservative; if the material hardens, the plastic strains will be less than those predicted by the simulation.

Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in &#8220;Connecting lug with plasticity,&#8221;  Section A.8. Instructions on how to fetch the script and run it within Abaqus/CAE are given in Appendix A, &#8220;Example Files.&#8221;

-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select Plug-insAbaqusGetting Started; highlight Connecting lug with plasticity; and click Run. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: connecting lug with plasticity,&#8221;  Section 10.4 of Getting Started with Abaqus: Keywords Edition.### 10.4.1&nbsp;Modifications to the model

Open the model database file Lug.cae, and copy the model Elastic to a model named Plastic.

**Material definition**

For the Plastic model, you will specify the post-yield behavior of the material using the classical metal plasticity model in Abaqus. The initial yield stress at zero plastic strain is 380&nbsp;MPa. Since you are modeling the steel as perfectly plastic, no other yield stresses are required. You will perform a general, nonlinear simulation because of the nonlinear material behavior in the model.

**To add plasticity data to the material model:**

-

In the Model Tree, expand the Materials container and double-click Steel.

-

In the material editor, select MechanicalPlasticityPlastic to invoke the classical metal plasticity model. Enter an initial yield stress of 380.E6 with a corresponding initial plastic strain of 0.0.

**Step definition and output requests**

Edit the step definition and output requests. In the Basic tabbed page of the Edit Step dialog box, accept the total time period of 1.0 and assume that the effects of geometric nonlinearity will not be important in this simulation. In the Incrementation tabbed page, specify an initial increment size that is 20% of the total step time (0.2). This simulation is a static analysis of the lug under extreme loads; you do not know in advance how many increments this simulation may require. The default maximum of 100 increments, however, is reasonably large and should be sufficient for this analysis.

Open the Field Output Requests Manager. Edit the current output request to request the preselected defaults at every increment.

**Loading**

The load applied in this simulation is twice what was applied in the linear elastic simulation of the lug (60&nbsp;kN vs. 30&nbsp;kN). Therefore, in the Model Tree, double-click Pressure load underneath the Loads container, and double the magnitude of the pressure applied to the lug (i.e., change the magnitude to 10.0E7).

**Job definition**

In the Model Tree, create a job named PlasticLugNoHard, and enter the following job description: Elastic-Plastic Steel Connecting Lug. Remember to save your model database file.

Submit the job for analysis, and monitor the solution progress. Correct any modeling errors, and investigate the source of any warning messages. This analysis should terminate prematurely; the reasons are discussed in the following section.### 10.4.2&nbsp;Job monitor and diagnostics

You can monitor the progress of your analysis while it is running by looking at the Job Monitor.

**Job Monitor**

When Abaqus/Standard has finished the simulation, the Job Monitor will contain information similar to that shown in [Figure 10&#8211;9](ch10s04.html#gsi-plasticlug-nohard-monitor).

> **Figure:**

Figure 10&#8211;9 Job Monitor: perfectly plastic connecting lug.

Abaqus/Standard was able to apply only 94% of the prescribed load to the model. The Job Monitor shows that Abaqus/Standard reduced the size of the time increment, shown in the last (right-hand) column, many times during the simulation and stopped the analysis in the fourteenth increment. The information on the Errors tabbed page (see [Figure 10&#8211;9](ch10s04.html#gsi-plasticlug-nohard-monitor)) indicates that the analysis terminated. Click the Message File tab to view the error details in the message file, as shown in [Figure 10&#8211;10](ch10s04.html#gsi-plasticlug-nohard-message-nls). The error indicates that the analysis terminated because the size of the time increment is smaller than the value allowed for this analysis. This is a classic symptom of convergence difficulties and is a direct result of the continued reduction in the time increment size. To begin diagnosing the problem, click the Warnings tab in the  Job Monitor dialog box. As shown in [Figure 10&#8211;11](ch10s04.html#gsi-plasticlug-nohard-warnings), many warning messages concerning large strain increments and problems with the plasticity calculations are found here. These warnings are related since problems with the plasticity calculations are typically the result of excessively large strain increments and often lead to divergence. Thus, we suspect that numerical problems with the plasticity calculations caused Abaqus/Standard to terminate the analysis early.

> **Figure:**

Figure 10&#8211;10 Message File: error description.

> **Figure:**

Figure 10&#8211;11 Warnings: perfectly plastic connecting lug.

**Job diagnostics**

Enter the Visualization module, and open the file PlasticLugNoHard.odb. Open the Job Diagnostics dialog box to examine the convergence history of the job. Looking at the information for the first increment in the analysis (see [Figure 10&#8211;12](ch10s04.html#gsi-plasticlug-nohard-inc1)), you will discover that the model's initial behavior is determined to be linear.

> **Figure:**

Figure 10&#8211;12 Convergence history for Increment 1.

This judgement is based on the fact that the magnitude of the residual, , is less than 108 (the time average force); the displacement correction criterion is ignored in this case. The model's behavior is also linear in the second increment (see [Figure 10&#8211;13](ch10s04.html#gsi-plasticlug-nohard-inc2)).

> **Figure:**

Figure 10&#8211;13 Convergence history for Increment 2.

Abaqus/Standard requires several iterations to obtain a converged solution in the third increment, which indicates that nonlinear behavior occurs in the model during this increment. The only nonlinearity in the model is the plastic material behavior, so the steel must have started to yield somewhere in the lug at this applied load magnitude. The summary of the final (converged) iteration for the third increment is shown in [Figure 10&#8211;14](ch10s04.html#gsi-plasticlug-nohard-inc3).

> **Figure:**

Figure 10&#8211;14 Convergence history for Increment 3.

Abaqus/Standard attempts to find a solution in the fourth increment using an increment size of 0.3, which means it is applying 30% of the total load, or 18&nbsp;kN, during this increment. After several iterations, Abaqus/Standard abandons the attempt and reduces the size of the time increment to 25% of the value used in the first attempt. This reduction in increment size is called a cutback. With the smaller increment size, Abaqus/Standard finds a converged solution in just a few iterations.

Look more closely at the information for the first attempt of the fourth increment (this is where the convergence difficulties first appear). For this attempt Abaqus/Standard detects large strain increments at the integration points of a number of elements, as shown in [Figure 10&#8211;15](ch10s04.html#gsi-plasticlug-nohard-inc4-att1-iter4).

> **Figure:**

Figure 10&#8211;15 Convergence history for Increment 4.

&#8220;Large&#8221; strain increments are those that exceed the strain at initial yield by 50 times; some of these increments are also considered &#8220;excessive,&#8221; which implies the plasticity calculations are not even attempted at the affected integration points. Thus, we see that the onset of the convergence difficulties is directly related to the large strain increments and problems with the plasticity calculations.

Abaqus/Standard encounters renewed convergence difficulties in subsequent increments until finally it terminates the job. In many of these increments Abaqus/Standard cuts back the time increment size because the strain increments are so large that the plasticity calculations are not even performed. Thus, we conclude the overall convergence difficulties are indeed the result of numerical problems with the plasticity calculations.

This check on the magnitude of the total strain increment is an example of the many automatic solution controls Abaqus/Standard uses to ensure that the solution obtained for your simulation is both accurate and efficient. The automatic solution controls are suitable for almost all simulations. Therefore, you do not have to worry about providing parameters to control the solution algorithm: you only have to be concerned with the input data for your model.

An interesting observation is made using the Job Diagnostics dialog box: in virtually all attempts where convergence problems are encountered, the elements with large or excessive strain increments are in the vicinity of the built-in end of the lug (where yielding begins) while the node with the largest displacement correction is in the vicinity of the loaded end of the lug. This implies that the loaded end wants to deform more than the built-in end can support. Deformed model shape plots can help you pursue this observation further.### 10.4.3&nbsp;Postprocessing the results

Look at the results in the Visualization module to understand what caused the excessive plasticity.

**Plotting the deformed model shape**

Create a plot of the model's deformed shape, and check that this shape is realistic.

The default view is isometric. You can set the view shown in [Figure 10&#8211;16](ch10s04.html#gss-hardening) by using the options in the View menu or the tools in the View Manipulation toolbar; in this figure perspective is also turned off.

> **Figure:**

Figure 10&#8211;16 Deformed model shape using results for the simulation without hardening.

The displacements and, particularly, the rotations of the lug shown in the plot are large but do not seem large enough to have caused all of the numerical problems seen in the simulation. Look closely at the information in the plot's title for an explanation. The deformation scale factor used in this plot is 0.02; i.e., the displacements are scaled to 2% of their actual values. (Your deformation scale factor may be different.)

Abaqus/CAE always scales the displacements in a geometrically linear simulation such that the deformed shape of the model fits into the viewport. (This is in contrast to a geometrically nonlinear simulation, where Abaqus/CAE does not scale the displacements and, instead, adjusts the view by zooming in or out to fit the deformed shape in the plot.) To plot the actual displacements, set the deformation scale factor to 1.0. This will produce a plot of the model in which the lug has deformed until it is almost parallel to the vertical (global Y) axis.

The applied load of 60 kN exceeds the limit load of the lug, and the lug collapses when the material yields at all the integration points through its thickness. The lug then has no stiffness to resist further deformation because of the perfectly plastic post-yield behavior of the steel. This is consistent with the pattern observed earlier concerning the locations of the large strain increments and maximum displacement corrections.### 10.4.4&nbsp;Adding hardening to the material model

The connecting lug simulation with perfectly plastic material behavior predicts that the lug will suffer catastrophic failure caused by the collapse of the structure. We have already mentioned that the steel would probably exhibit some hardening after it has yielded. You suspect that including hardening behavior would allow the lug to withstand this 60&nbsp;kN load because of the additional stiffness it would provide. Therefore, you decide to add some hardening to the steel's material property definition. Assume that the yield stress increases to 580&nbsp;MPa at a plastic strain of 0.35, which represents typical hardening for this class of steel. The stress-strain curve for the modified material model is shown in [Figure 10&#8211;17](ch10s04.html#gss-modified).

> **Figure:**

Figure 10&#8211;17 Modified stress-strain behavior of the steel.

Modify your plastic material data so that it includes the hardening data. Edit the material definition to add a second row of data to the plastic data form. Enter a yield stress of 580.E6 with a corresponding plastic strain of 0.35.### 10.4.5&nbsp;Running the analysis with plastic hardening

Create a job named PlasticLugHard. Submit the job for analysis, and monitor the solution progress. Correct any modeling errors, and investigate the source of any warning messages.

**Job Monitor**

The summary of the analysis in the Job Monitor, shown in [Figure 10&#8211;18](ch10s04.html#gsi-plasticlug-monitor), indicates that Abaqus/Standard found a converged solution when the full 60&nbsp;kN load was applied. The hardening data added enough stiffness to the lug to prevent it from collapsing under the 60&nbsp;kN load.

There are no convergence-related warnings issued during the analysis, so you can proceed directly to postprocessing the results.

> **Figure:**

Figure 10&#8211;18 Job Monitor: connecting lug with plastic hardening.

### 10.4.6&nbsp;Postprocessing the results

Enter the Visualization module, and open the file PlasticLugHard.odb.

**Deformed model shape and peak displacements**

Plot the deformed model shape with these new results, and change the deformation scale factor to 2 to obtain a plot similar to [Figure 10&#8211;19](ch10s04.html#gss-plot). The displayed deformations are double the actual deformations.

> **Figure:**

Figure 10&#8211;19 Deformed model shape for the simulation with plastic hardening.

**Contour plot of Mises stress**

Contour the Mises stress in the model. Create a filled contour plot using ten contour intervals on the actual deformed shape of the lug (i.e., set the deformation scale factor to 1.0) with the plot title and state blocks suppressed. Use the view manipulation tools to position and size the model to obtain a plot similar to that shown in [Figure 10&#8211;20](ch10s04.html#gss-von-mises).

> **Figure:**

Figure 10&#8211;20 Contour of Mises stress.

Do the values listed in the contour legend surprise you? The maximum stress is greater than 580 MPa, which should not be possible since the material was assumed to be perfectly plastic at this stress magnitude. This misleading result occurs because of the algorithm that Abaqus/CAE uses to create contour plots for element variables, such as stress. The contouring algorithm requires data at the nodes; however, Abaqus/Standard calculates element variables at the integration points. Abaqus/CAE calculates nodal values of element variables by extrapolating the data from the integration points to the nodes. The extrapolation order depends on the element type; for second-order, reduced-integration elements Abaqus/CAE uses linear extrapolation to calculate the nodal values of element variables. To display a contour plot of Mises stress, Abaqus/CAE extrapolates the stress components from the integration points to the nodal locations within each element and calculates the Mises stress. If the differences in Mises stress values fall within the specified averaging threshold, nodal averaged Mises stresses are calculated from each surrounding element's invariant stress value. Invariant values exceeding the elastic limit can be produced by the extrapolation process.

Try plotting contours of each component of the stress tensor (variables S11, S22, S33, S12, S23, and S13). You will see that there are significant variations in these stresses across the elements at the built-in end. This causes the extrapolated nodal stresses to be higher than the values at the integration points. The Mises stress calculated from these values will, therefore, also be higher.

Note:&nbsp;

Element type C3D10I does not suffer from this extrapolation problem. The integration points of this element type are located at the nodes, resulting in improved surface stress visualization.

The Mises stress at an integration point can never exceed the current yield stress of the element's material; however, the extrapolated nodal values reported in a contour plot may do so. In addition, the individual stress components may have magnitudes that exceed the value of the current yield stress; only the Mises stress is required to have a magnitude less than or equal to the value of the current yield stress.

You can use the query tools in the Visualization module to check the Mises stress at the integration points.

**To query the Mises stress:**

-

From the main menu bar, select ToolsQuery; or use the  tool in the Query toolbar.

The Query dialog box appears.

-

In the Visualization Module Queries field, select Probe values.

The Probe Values dialog box appears.

-

Make sure that Elements and the output position Integration Pt are selected.

-

Use the cursor to select elements near the constrained end of the lug.

Abaqus/CAE reports the element ID and type by default and the value of the Mises stress at each integration point starting with the first integration point. The Mises stress values at the integration points are all lower than the values reported in the contour legend and also below the yield stress of 580&nbsp;MPa. You can click mouse button 1 to store probed values.

-

Click Cancel when you have finished probing the results.

The fact that the extrapolated values are so different from the integration point values indicates that there is a rapid variation of stress across the elements and that the mesh is too coarse for accurate stress calculations. This extrapolation error will be less significant if the mesh is refined but will always be present to some extent. Therefore, always use nodal values of element variables with caution.

**Contour plot of equivalent plastic strain**

The equivalent plastic strain in a material (PEEQ) is a scalar variable that is used to represent the material's inelastic deformation. If this variable is greater than zero, the material has yielded. Those parts of the lug that have yielded can be identified in a contour plot of PEEQ by selecting Primary from the list of variable types on the left side of the Field Output toolbar and selecting PEEQ from the list of output variables. Any areas in the model plotted in a dark color in Abaqus/CAE  still have elastic material behavior (see [Figure 10&#8211;21](ch10s04.html#gss-plastic-strain)).

> **Figure:**

Figure 10&#8211;21 Contour of equivalent plastic strain (PEEQ).

It is clear from the plot that there is gross yielding in the lug where it is attached to its parent structure. The maximum plastic strain reported in the contour legend is about 10%. However, this value may contain errors from the extrapolation process. Use the query tool  to check the integration point values of PEEQ in the elements with the largest plastic strains. You will find that the largest equivalent plastic strains in the model are about 0.087 at the integration points. This does not necessarily indicate a large extrapolation error since there are strain gradients present in the vicinity of the peak plastic deformation.

**Creating a variable-variable (stress-strain) plot**

The X&#8211;Y plotting capability in Abaqus/CAE was introduced earlier in this guide. In this section you will learn how to create X&#8211;Y plots showing the variation of one variable as a function of another. You will use the stress and strain data saved to the output database (.odb) file (in the form of field output rather than history output) to create a stress-strain plot for one of the integration points in an element adjacent to the constrained end of the lug.

Consider the shaded element shown in [Figure 10&#8211;22](ch10s04.html#gss-crnelem).

> **Figure:**

Figure 10&#8211;22 Element where stress and strain histories will be studied.

We will plot the stress and strain histories at an integration point in this element. The selected integration point should be as close as possible to the top surface of the lug but not adjacent to the constrained nodes. The numbering of the integration points depends on the element's nodal connectivity. Thus, you will need to identify the element's label as well as its nodal connectivity to determine which integration point to use.

**To determine the integration point number:**

-

In the Display Group toolbar, select the Replace Selected  tool and click the shaded element shown in [Figure 10&#8211;22](ch10s04.html#gss-crnelem).

-

Plot the undeformed shape of this element with the node labels made visible. Click the auto-fit tool  to obtain a plot similar to [Figure 10&#8211;23](ch10s04.html#gss-integration).

> **Figure:**

Figure 10&#8211;23 Location of integration point near the top surface.

-

Use the Query tool to obtain the nodal connectivity for this corner element (select Element, and click the element in the viewport). The nodal connectivity will be printed to the message area; you are interested in only the first four nodes.

-

Compare the nodal connectivity list with the undeformed model shape plot to determine which is the 1&#8211;2&#8211;3&#8211;4 face on your C3D20R element, as defined in &#8220;Three-dimensional solid element library,&#8221;  Section 28.1.4 of the Abaqus Analysis User's Guide. For example, in [Figure 10&#8211;23](ch10s04.html#gss-integration) the 276&#8211;552&#8211;313&#8211;79 face corresponds to the 1&#8211;2&#8211;3&#8211;4 face. Thus, the integration points are numbered as shown in the figure. We are interested in the point that corresponds to integration point 5.

In the following discussion, assume that the element label is 41 and that integration point&nbsp;5 of this element satisfies the requirements stated above. Your element and/or integration point numbers may differ.

**To create history curves of stress and direct strain along the lug:**

-

In the Results Tree, double-click XYData.

The Create XY Data dialog box appears.

-

In this dialog box, select ODB field output as the source and click Continue.

The  XY Data from ODB Field Output dialog box appears; the Variables tabbed page is open by default.

-

In this dialog box, expand the following lists: S: Stress components and E: Strain components.

-

From the list of available stress and strain components, select Mises and E11, respectively.

The Mises stress, rather than the component of the true stress tensor, is used because the plasticity model defines plastic yield in terms of Mises stress. The E11 strain component is used because it is the largest component of the total strain tensor at this point; using it clearly shows the elastic, as well as the plastic, behavior of the material at this integration point.

-

Click the Elements/Nodes tab.

-

Accept Pick from viewport as the selection method, and click Edit Selection.

-

In the viewport, click on the shaded element shown in [Figure 10&#8211;22](ch10s04.html#gss-crnelem); then click Done in the prompt area.

-

Click Save to save the data followed by Dismiss to close the dialog box.

Sixteen curves are created (one for each variable at each integration point), and default names are given to the curves. The curves appear in the XYData container. Each of the curves is a history (variable versus time) plot. You must combine the plots for the integration point of interest, eliminating the time dependence, to produce the desired stress-strain plot.

**To combine history curves to produce a stress-strain plot:**

-

In the Results Tree, double-click XYData.

The Create XY Data dialog box appears.

-

Select Operate on XY data, and click Continue.

The Operate on XY Data dialog box appears. Expand the Name field to see the full name of each curve.

-

From the Operators listed, select combine(X,X).

combine( ) appears in the text field at the top of the dialog box.

-

In the XY Data field, select the stress and strain curves for the integration point of interest.

-

Click Add to Expression. The expression combine("E:E11 ...", "S:MISES ...") appears in the text field. In this expression "E:E11 ..." will determine the X-values and "S:MISES ..." will determine the Y-values in the combined plot.

-

Save the combined data object by clicking Save As at the bottom of the dialog box.

The Save XY Data As dialog box appears. In the Name text field, type SVE11; and click OK to close the dialog box.

-

To view the combined stress-strain plot, click Plot Expression at the bottom of the dialog box.

-

Click Cancel to close the dialog box.

-

Click  in the prompt area to cancel the current procedure.

This X&#8211;Y plot would be clearer if the limits on the X- and Y-axes were changed.

**To customize the stress-strain curve:**

-

Double-click either axis to open the Axis Options dialog box.

-

Set the maximum value of the X-axis (E11 strain) to 0.09, the maximum value of the Y-axis (MISES stress) to 500 MPa, and the minimum value to 0.0 MPa.

-

Switch to the Title tabbed page, and customize the X- and Y-axis labels as shown in [Figure 10&#8211;24](ch10s04.html#gss-e11).

> **Figure:**

Figure 10&#8211;24 Mises stress vs. direct strain (E11) along the lug in the corner element.

-

Click Dismiss to close the Axis Options&nbsp;dialog box.

-

It will also be helpful to display a symbol at each data point of the curve. Open the Curve Options dialog box.

-

From the Curves field, select the stress-strain curve (SVE11).

The SVE11 data object is highlighted.

-

Toggle on Show symbol. Accept the defaults, and click Dismiss at the bottom of the dialog box.

The stress-strain plot appears with a symbol at each data point of the curve.

You should now have a plot similar to the one shown in [Figure 10&#8211;24](ch10s04.html#gss-e11). The stress-strain curve shows that the material behavior was linear elastic for this integration point during the first two increments of the simulation. In this plot it appears that the material remains linear during the third increment of the analysis; however, it does yield during this increment. This illusion is created by the extent of strain shown in the plot. If you limit the maximum strain displayed to 0.01 and set the minimum value to 0.0, the nonlinear material behavior in the third increment can be seen more clearly (see [Figure 10&#8211;25](ch10s04.html#gss-mises-stress)).

> **Figure:**

Figure 10&#8211;25 Mises stress vs. direct strain (E11) along the lug in the corner element. Maximum strain 0.01.

This stress-strain curve contains another apparent error. It appears that the material yields at 250&nbsp;MPa, which is well below the initial yield stress. However, this error is caused by the fact that Abaqus/CAE connects the data points on the curve with straight lines. If you limit the increment size, the additional points on the graph will provide a better display of the material response and show yield occurring at exactly 380&nbsp;MPa.

The results from this second simulation indicate that the lug will withstand this 60&nbsp;kN load if the steel hardens after it yields. Taken together, the results of the two simulations demonstrate that it is very important to determine the actual post-yield hardening behavior of the steel. If the steel has very little hardening, the lug may collapse under the 60&nbsp;kN load. Whereas if it has moderate hardening, the lug will probably withstand the load although there will be extensive plastic yielding in the lug (see [Figure 10&#8211;21](ch10s04.html#gss-plastic-strain)). However, even with plastic hardening, the factor of safety for this loading will probably be very small.

### 10.5&nbsp;Example: blast loading on a stiffened plate

The previous example illustrated some of the convergence difficulties that may be encountered when solving problems involving a nonlinear material response using implicit methods. We will now focus on solving a problem involving plasticity using explicit dynamics. As will become evident shortly, convergence difficulties are not an issue in this case since iteration is not required for explicit methods.

In this example you will assess the response of a stiffened square plate subjected to a blast loading in Abaqus/Explicit. The plate is firmly clamped on all four sides and has three equally spaced stiffeners welded to it. The plate is constructed of 25 mm thick steel and is 2 m square. The stiffeners are made from 12.5 mm thick plate and have a depth of 100 mm. [Figure 10&#8211;26](ch10s05.html#gxi-blast-load) shows the plate geometry and material properties in more detail. Since the plate thickness is significantly smaller than any other global dimensions, shell elements can be used to model the plate.

> **Figure:**

Figure 10&#8211;26 Problem description for blast load on a stiffened plate.

The purpose of this example is to determine the response of the plate and to see how it changes as the sophistication of the material model increases. Initially, we analyze the behavior with the standard elastic-plastic material model. Subsequently, we study the effects of including material damping and rate-dependent material properties.### 10.5.1&nbsp;Preprocessing&#8212;creating the model with Abaqus/CAE

Use Abaqus/CAE to create a three-dimensional model of the stiffened plate. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in &#8220;Blast loading on a stiffened plate,&#8221;  Section A.9. Instructions on how to fetch the script and run it within Abaqus/CAE are given in Appendix A, &#8220;Example Files.&#8221;

-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select Plug-insAbaqusGetting Started; highlight Blast loading on a stiffened plate; and click Run. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: blast loading on a stiffened plate,&#8221;  Section 10.5 of Getting Started with Abaqus: Keywords Edition.

**Defining the model geometry**

Create a three-dimensional, deformable part with an extruded shell base feature to represent the plate. Use an approximate part size of 5.0, and name the part Plate. A suggested approach for creating the part geometry shown in [Figure 10&#8211;27](ch10s05.html#gxi-blast-plate) is summarized in the following procedure:

> **Figure:**

Figure 10&#8211;27 Sketch of the stiffened plate (with grid spacing doubled).

**To create the stiffened plate geometry:**

-

To define the plate geometry, use the Create Lines: Connected tool to sketch an arbitrary horizontal line.

-

To define the stiffener geometry, add three vertical lines extending up from the plate. The horizontal position of these lines is arbitrary at this stage, but their endpoints must snap to the horizontal line.

-

Constrain the three vertical lines so they are of equal length, and dimension one of them so that it is 0.1 m long.

-

Split the plate at the points where it intersects the stiffeners.

-

Dimension the horizontal distance between the plate endpoints, and set the value to 2.0 m.

-

Apply equal length constraints to the four horizontal segments of the line.

The final part sketch is shown in [Figure 10&#8211;27](ch10s05.html#gxi-blast-plate).

-

Extrude the sketch to a depth of 2.0 m to create the plate.

**Defining the material properties**

Define the material and section properties for the plate and the stiffeners.

Create a material named Steel with a mass density of 7800 kg/m3, a Young's modulus of 210.0E9 Pa, and a Poisson's ratio of 0.3. At this stage we do not know whether there will be any plastic deformation, but we know the value of the yield stress and the details of the post-yield behavior for this steel. We will include this information in the material definition. The initial yield stress is 300 MPa, and the yield stress increases to 400 MPa at a plastic strain of 35%. To define the plastic material properties, enter the yield stress and plastic strain data shown in [Figure 10&#8211;26](ch10s05.html#gxi-blast-load). The plasticity stress-strain curve is shown in [Figure 10&#8211;28](ch10s05.html#gxi-yield).

> **Figure:**

Figure 10&#8211;28 Yield stress versus plastic strain.

During the analysis Abaqus calculates values of yield stress from the current values of plastic strain. As discussed earlier, the process of lookup and interpolation is most efficient when the stress-strain data are at equally spaced values of plastic strain. To avoid having the user input regular data, Abaqus/Explicit automatically regularizes the data. In this case the data are regularized by Abaqus/Explicit by expanding the data to 15 equally spaced points with increments of 0.025.

To illustrate the error message that is produced when Abaqus/Explicit cannot regularize the material data, you could set the regularization tolerance to 0.001 (in the Edit Material dialog box, select GeneralRegularization) and include one additional data pair, as shown in [Table 10&#8211;2](ch10s05.html#gxi-blast-plastic-mod). You can add a row by clicking mouse button 3 in the table and selecting Insert Row from the menu that appears.

Table 10&#8211;2 Modified plasticity data.

| | Yield Stress (Pa) | Plastic Strain

| | 300.0E6 | 0.000

| | 349.0E6 | 0.001

| | 350.0E6 | 0.025

| | 375.0E6 | 0.100

| | 394.0E6 | 0.200

| | 400.0E6 | 0.350

The combination of the low tolerance value and the small interval in the user-defined data would lead to difficulty in regularizing this material definition. The following error message would be written to the status (.sta) file and displayed in the Job Monitor dialog box in the Job module:```

***ERROR: Failed to regularize material data for material STEEL. Please check

your input data to see if they meet both criteria as explained in

"MATERIAL DATA DEFINITION" section of the

Abaqus Analysis User's Guide. In general, regularization is more difficult if the

smallest interval defined by the user is small compared to the

range of the independent variable.

```Before continuing, set the regularization tolerance back to the default value (0.03) and remove the additional pair of data points.

**Creating and assigning section properties**

Create two homogeneous shell section properties, each referring to the steel material definition but specifying different shell thicknesses. Name the first shell section property PlateSection, select Steel as the material, and specify 0.025 m as the value for the Shell thickness. Name the second shell section property StiffSection, select Steel as the material, and specify 0.0125 m as the value for the Shell thickness.

Assign the StiffSection definition to the stiffeners (use [Shift]+Click to select multiple regions in the viewport).

Before assigning the PlateSection definition to the plate, consider the following. If the plate and the stiffeners are joined directly at their midsurfaces (this is the default behavior), an area of material overlap will occur, as shown in [Figure 10&#8211;29](ch10s05.html#gxi-overlap-mat).

> **Figure:**

Figure 10&#8211;29 Overlapping material.

Although the thicknesses of the plate and stiffener are small in comparison to the overall dimensions of the structure (so that this overlapping material and the extra stiffness it creates would have little effect on the analysis results), a more precise model can be created by offsetting the plate reference surface from its midsurface. This technique allows the stiffeners to butt up against the plate without overlapping any material with the plate, as shown in [Figure 10&#8211;30](ch10s05.html#gxi-midsurf-joint).

> **Figure:**

Figure 10&#8211;30 Stiffener joint in which the plate's reference surface is offset from its midsurface.

To determine whether to offset the plate reference surface to its positive (SPOS) or negative (SNEG) side, query the shell normals (ToolsQuery) and note the color of the side of the plate facing the stiffeners (brown is the positive side; purple is the negative side). If necessary, flip the plate normals (AssignElement Normal) so that its segments have consistent normals. Then assign the PlateSection definition to the regions of the plate. In the Edit Section Assignment dialog box, set the shell offset to Top surface if the brown (positive) side of the plate faces the stiffeners and Bottom surface if the purple (negative) side faces the stiffeners.

To verify the offset, select ViewPart Display Options. In the Part Display Options dialog box that appears, toggle on Render shell thickness. If necessary, modify the offset to remove any overlap.

The model can be color-coded according to section assignment to verify that properties were assigned correctly (select Sections from the Color Code toolbar).

**Creating an assembly**

Create an independent instance of the plate. Use the default rectangular coordinate system, with the plate lying in the 1&#8211;3 plane.

At this point, it is convenient to create the geometry sets that will be used to specify boundary conditions and output requests. Create one set named Edge for the plate edges and one set named Center at the center of the intersection of the plate and the middle stiffener, as shown in [Figure 10&#8211;31](ch10s05.html#gxi-blast-sets). To create the set Center, you need to first partition the edge of the original part in half using the Partition Edge: Enter Parameter  tool.

> **Figure:**

Figure 10&#8211;31 Geometry sets.

**Defining steps and output requests**

Create a single dynamic, explicit step. Name the step Blast, and specify the following step description: Apply blast loading. Enter a value of 50E-3 s for the time period of the step.

In general, you should try to limit the number of frames written during the analysis to keep the size of the output database file reasonable. In this analysis saving information every 2 ms should provide sufficient detail to study the response of the structure. Edit the default output request F-Output-1, and set the number of intervals during the step at which preselected field data are saved to 25. This ensures that the selected data are written every 2&nbsp;ms since the total time for the step is 50 ms.

A more detailed set of output for selected regions of the model can be saved as history output. Create a history output request named Center-U2 for the step Blast. Select Center as the output domain, and select U2 as the translation output variable. Enter 500 as the number of intervals at which the output will be saved during the analysis.

**Prescribing boundary conditions and loads**

Next, define the boundary conditions used in this analysis. In the step Blast, create a Symmetry/Antisymmetry/Encastre mechanical boundary condition named Fix edges. Apply the boundary condition to the edges of the plate using the geometry set Edge, and specify ENCASTRE (U1 = U2 = U3 = UR1 = UR2 = UR3 = 0) to fully constrain the set.

The plate will be subjected to a load that varies with time: the pressure increases rapidly from zero at the start of the analysis to its maximum of 7.0 × 105&nbsp; Pa in 1 ms, at which point it remains constant for 9 ms before dropping back to zero in another 10 ms. It then remains at zero for the remainder of the analysis. See [Figure 10&#8211;32](ch10s05.html#gxi-pressure-load) for details.

> **Figure:**

Figure 10&#8211;32 Pressure load as a function of time.

Define a tabular amplitude curve named Blast. Enter the amplitude data given in [Table 10&#8211;3](ch10s05.html#gxi-blast-amp), and specify a smoothing parameter of 0.0.

Table 10&#8211;3 Blast load amplitude.

| | Time | Amplitude

| | 0.0 | 0.0

| | 1.0E3 | 7.0E5

| | 10.0E3 | 7.0E5

| | 20.0E3 | 0.0

| | 50.0E3 | 0.0

Next, define the pressure loading. Since the magnitude of the load will be defined by the amplitude definition, you need to apply only a unit pressure to the plate. Apply the pressure so that it pushes against the top of the plate (where the stiffeners are on the bottom of the plate). Such a pressure load will place the outer fibers of the stiffeners in tension.

**To define the pressure loading:**

-

In the Model Tree, double-click the Loads container. In the Create Load dialog box that appears, name the load Pressure load and select Blast as the step in which it will be applied. Select Mechanical as the load category and Pressure as the load type. Click Continue.

-

Select all the surfaces associated with the plate. When the appropriate surfaces are selected, click Done.

Abaqus/CAE uses two different colors to indicate the two sides of the shell surface. To complete the load definition, the colors must be consistent on each side of the plate.

-

If necessary, select Flip a surface in the prompt area to flip the colors for a region of the plate. Repeat this procedure until all of the faces on the top of the plate are the same color.

-

In the prompt area, select the color representing the side of the plate without the stiffeners.

-

In the Edit Load dialog box that appears, specify a uniform pressure of 1.0 Pa, and select the amplitude definition Blast. Click OK to complete the load definition.

The plate load and boundary conditions are shown in [Figure 10&#8211;33](ch10s05.html#gxi-blast-bc-load).

> **Figure:**

Figure 10&#8211;33 Pressure load and boundary conditions.

**Creating the mesh and defining a job**

Seed the part instance with a global element size of 0.1. In addition, select SeedEdges and specify that two elements be created along the height of each stiffener (in the Local Seeds dialog box, select By number as the method and set the number of elements to 2; toggle on the option to create a set containing the selected edges). Mesh the plate and stiffeners using quadrilateral shell elements (S4R) from the Explicit element library. The resulting mesh is shown in [Figure 10&#8211;34](ch10s05.html#gxi-stiff-plate-mesh-c). This relatively coarse mesh provides moderate accuracy while keeping the solution time to a minimum.

> **Figure:**

Figure 10&#8211;34 Meshed plate.

Create a job named BlastLoad. Specify the following job description: Blast load on a flat plate with stiffeners: S4R elements (20x20 mesh) Normal stiffeners (20x2).

Save your model in a model database file, and submit the job for analysis. Monitor the solution progress; correct any modeling errors that are detected, and investigate the cause of any warning messages.### 10.5.2&nbsp;Postprocessing

When the job completes, enter the Visualization module, and open the .odb file created by this job (BlastLoad.odb). By default, Abaqus plots the undeformed model shape with the shaded render style.

**Changing the view**

The default view is isometric, which does not provide a particularly clear view of the plate. To improve the viewpoint, rotate the view using the options in the View menu or the tools in the View Manipulation toolbar. Specify the view and select the viewpoint method for rotating the view. Enter the X-, Y-, and Z-coordinates of the viewpoint vector as 1,0.5,1 and the coordinates of the up vector as 0,1,0.

**Verifying shell section assignment**

You can also visualize the section assignment and the shell thickness while postprocessing the results. For example, regions with common section assignments can be color coded to verify that the properties were assigned correctly (select Sections from the Color Code toolbar to color the mesh according to section assignment). To render the shell thickness, select ViewODB Display Options from the main menu bar. In the ODB Display Options dialog box, toggle on Render shell thickness and click Apply. If the model looks correct, as shown in [Figure 10&#8211;35](ch10s05.html#gsx-blast-shell-thick), toggle off this option and click OK before proceeding with the rest of the postprocessing instructions. Otherwise, correct the section assignment and rerun the job.

> **Figure:**

Figure 10&#8211;35 Plate with shell thickness displayed.

**Animation of results**

As noted in earlier examples, animating your results will provide a general understanding of the dynamic response of the plate under the blast loading. First, plot the deformed model shape. Then, create a time-history animation of the deformed shape. Use the Animation Options dialog box to change the mode to Play once.

You will see from the animation that as the blast loading is applied, the plate begins to deflect. Over the duration of the load the plate begins to vibrate and continues to vibrate after the blast load has dropped to zero. The maximum displacement occurs at approximately 8 ms, and a displaced plot of that state is shown in [Figure 10&#8211;36](ch10s05.html#gxi-disp-shape-1ms).

> **Figure:**

Figure 10&#8211;36 Displaced shape at 8 ms.

The animation images can be saved to a file for playback at a later time.

**To save the animation:**

-

From the main menu bar, select AnimateSave As.

The Save Image Animation dialog box appears.

-

In the Settings field, enter the file name blast_base.

The format of the animation can be specified as AVI, QuickTime, VRML, or Compressed VRML.

-

Choose the QuickTime format, and click OK.

The animation is saved as blast_base.mov in your current directory. Once saved, your animation can be played external to Abaqus/CAE using industry-standard animation software.

**History output**

Since it is not easy to see the deformation of the plate from the deformed plot, it is desirable to view the deflection response of the central node in the form of a graph. The displacement of the node in the center of the plate is of particular interest since the largest deflection occurs at this node.

Display the displacement history of the central node, as shown in [Figure 10&#8211;37](ch10s05.html#gxi-central-disp) (with displacements in millimeters).

> **Figure:**

Figure 10&#8211;37 Central node displacement as a function of time.

**To generate a history plot of the central node displacement:**

-

In the Results Tree, double-click the history output data named Spatial displacement: U2 at the node in the center of the plate (set Center).

-

Save the current X&#8211;Y data: in the Results Tree, click mouse button 3 on the data name and select Save As from the menu that appears. Name the data DISP.

The units of the displacements in this plot are meters. Modify the data to create a plot of displacement (in millimeters) versus time by creating a new data object.

-

In the Results Tree, expand the XYData container.

The DISP data are listed underneath.

-

In the Results Tree, double-click XYData; then select Operate on XY data in the Create XY Data dialog box. Click Continue.

-

In the Operate on XY Data dialog box, multiply DISP by 1000 to create the plot with the displacement values in millimeters instead of meters. The expression at the top of the dialog box should appear as:```

"DISP" * 1000

```

-

Click Plot Expression to see the modified X&#8211;Y data. Save the data as U2_BASE.

-

Close the Operate on XY Data dialog box.

-

Click the Axis Options  tool in the toolbox. In the Axis Options dialog box, change the X-axis title to Time (s) and the Y-axis title to Displacement (mm). Click OK to close the dialog box. The resulting plot is shown in [Figure 10&#8211;37](ch10s05.html#gxi-central-disp).

The plot shows that the displacement reaches a maximum of 50.2 mm at 7.7 ms and then oscillates after the blast load is removed.

The other quantities saved as history output in the output database are the total energies of the model. The energy histories can help identify possible shortcomings in the model as well as highlight significant physical effects. Display the histories of five different energy output variables&#8212;ALLAE, ALLIE, ALLKE, ALLPD, and ALLSE.

**To generate history plots of the model energies:**

-

Save the history results for the ALLAE, ALLIE, ALLKE, ALLPD, and ALLSE output variables as X&#8211;Y data. A default name is given to each curve; rename each according to its output variable name: ALLAE, ALLKE, etc.

-

In the Results Tree, expand the XYData container.

The ALLAE, ALLIE, ALLKE, ALLPD, and ALLSE X&#8211;Y data objects are listed underneath.

-

Select ALLAE, ALLIE, ALLKE, ALLPD, and ALLSE using [Ctrl]+Click; click mouse button 3, and select Plot from the menu that appears to plot the energy curves.

-

To more clearly distinguish between the different curves in the plot, open the Curve Options dialog box and change their line styles.

-

For the curve ALLSE, select a dashed line style.

-

For the curve ALLPD, select a dotted line style.

-

For the curve ALLAE, select a chain dashed line style.

-

For the curve ALLIE, select the second thinnest line type.

-

To change the position of the legend, open the Chart Legend Options dialog box and switch to the Area tabbed page.

-

In the Position region of this page, toggle on Inset and click Dismiss. Drag the legend in the viewport so that it fits within the grid, as shown in [Figure 10&#8211;38](ch10s05.html#gxi-energy-terms).

> **Figure:**

Figure 10&#8211;38 Energy quantities as a function of time.

We can see that once the load has been removed and the plate vibrates freely, the kinetic energy increases as the strain energy decreases. When the plate is at its maximum deflection and, therefore, has its maximum strain energy, it is almost entirely at rest, causing the kinetic energy to be at a minimum.

The plastic strain energy rises to a plateau and then rises again. From the plot of kinetic energy we can see that the second rise in plastic strain energy occurs when the plate has rebounded from its maximum displacement and is moving back in the opposite direction. We are, therefore, seeing plastic deformation on the rebound after the blast pulse.

Even though there is no indication that hourglassing is a problem in this analysis, study the artificial strain energy to make sure. As discussed in Chapter 4, &#8220;Using Continuum Elements,&#8221; artificial strain energy or &#8220;hourglass stiffness&#8221; is the energy used to control hourglass deformation, and the output variable ALLAE is the accumulated artificial strain energy. This discussion on hourglass control applies equally to shell elements. Since energy is dissipated as plastic deformation as the plate deforms, the total internal energy is much greater than the elastic strain energy alone. Therefore, it is most meaningful in this analysis to compare the artificial strain energy to an energy quantity that includes the dissipated energy as well as the elastic strain energy. Such a variable is the total internal energy, ALLIE, which is a summation of all internal energy quantities. The artificial strain energy is approximately 2% of the total internal energy, indicating that hourglassing is not a problem.

One thing we can notice from the deformed shape is that the central stiffener is subject to almost pure in-plane bending. Using only two first-order, reduced-integration elements through the depth of the stiffener is not sufficient to model in-plane bending behavior. While the solution from this coarse mesh appears to be adequate since there is little hourglassing, for completeness we will study how the solution changes when we refine the mesh of the stiffener. Use caution when you refine the mesh, since mesh refinement will increase the solution time by increasing the number of elements and decreasing the element size.

Edit the mesh, and respecify the mesh density. Using the previously saved edge set, specify four elements through the height of each stiffener, and remesh the part instance. Create a new job named BlastLoadRefined. Submit this job for analysis, and investigate the results when the job has completed running.

This increase in the number of elements increases the solution time by approximately 20%. In addition, the stable time increment decreases by approximately a factor of two as a result of the reduction of the smallest element dimension in the stiffeners. Since the total increase in solution time is a combination of the two effects, the solution time of the refined mesh increases by approximately a factor of 1.2 × 2, or 2.4, over that of the original mesh.

[Figure 10&#8211;39](ch10s05.html#gxi-art-energy) shows the histories of artificial energy for both the original mesh and the mesh with the refined stiffeners. The artificial energy is slightly lower in the refined mesh. As a result, we would not expect the results to change significantly from the original to the refined mesh.

> **Figure:**

Figure 10&#8211;39 Artificial energy in the original and refined meshes.

[Figure 10&#8211;40](ch10s05.html#gxi-cent-disp-meshes) shows that the displacement of the plate's central node is almost identical in both cases, indicating that the original mesh is capturing the overall response adequately. One advantage of the refined mesh, however, is that it better captures the variation of stress and plastic strain through the stiffeners.

> **Figure:**

Figure 10&#8211;40 Central node displacement history for the original and refined meshes.

**Contour plots**

In this section you will use the contour plotting capability of the Visualization module to display the von Mises stress and equivalent plastic strain distributions in the plate. Use the model with the refined stiffener mesh to create the plots; from the main menu bar, select FileOpen and choose the file BlastLoadRefined.odb.

**To generate contour plots of the von Mises stress and equivalent plastic strain:**

-

From the list of variable types on the left side of the Field Output toolbar, select Primary.

-

From the list of output variables in the center of the toolbar, select S. The stress invariants and components are available in the next list to the right. Select the Mises stress invariant.

-

From the main menu bar, select ResultSection Points.

-

In the Section Points dialog box that appears, select Top and bottom as the active locations and click OK.

-

Select PlotContoursOn Deformed Shape, or use the  tool from the toolbox.

Abaqus plots the contours of the von Mises stress on both the top and bottom faces of each shell element. To see this more clearly, rotate the model in the viewport.

The view that you set earlier for the animation exercise should be changed so that the stress distribution is clearer.

-

Change the view back to the default isometric view using the  tool in the Views toolbar.

Tip:&nbsp;

If the Views toolbar is not visible, select ViewToolbarsViews from the main menu bar.

[Figure 10&#8211;41](ch10s05.html#gxi-cont-plot-mises) shows a contour plot of the von Mises stress at the end of the analysis.

> **Figure:**

Figure 10&#8211;41 Contour plot of von Mises stress at 50 ms.

-

Similarly, contour the equivalent plastic strain. Select Primary from the list of variable types on the left side of the Field Output toolbar and select PEEQ from the list of output variables next to it.

[Figure 10&#8211;42](ch10s05.html#gxi-equivaplast) shows a contour plot of the equivalent plastic strain at the end of the analysis.

> **Figure:**

Figure 10&#8211;42 Contour plot of equivalent plastic strain at 50 ms.

### 10.5.3&nbsp;Reviewing the analysis

The objective of this analysis is to study the deformation of the plate and the stress in various parts of the structure when it is subjected to a blast load. To judge the accuracy of the analysis, you will need to consider the assumptions and approximations made and identify some of the limitations of the model.

**Damping**

Undamped structures continue to vibrate with constant amplitude. Over the 50 ms of this simulation, the frequency of the oscillation can be seen to be approximately 100 Hz. A constant amplitude vibration is not the response that would be expected in practice since the vibrations in this type of structure would tend to die out over time and effectively disappear after 5&#8211;10 oscillations. The energy loss typically occurs by a variety of mechanisms including frictional effects at the supports and damping by the air.

Consequently, we need to consider the presence of damping in the analysis to model this energy loss. The energy dissipated by viscous effects, ALLVD, is nonzero in the analysis, indicating that there is already some damping present. By default, a *bulk viscosity* damping (discussed in Chapter 9, &#8220;Nonlinear Explicit Dynamics&#8221;) is always present and is introduced to improve the modeling of high-speed events.

In this shell model only linear damping is present. With the default value the oscillations would eventually die away, but it would take a long time because the bulk viscosity damping is very small. Material damping should be used to introduce a more realistic structural response. Thus, modify the material definition.

**To add damping to a material:**

-

In the Model Tree, double-click Steel underneath the Materials container.

-

In the Edit Material dialog box, select MechanicalDamping and specify 50 as the value for the mass proportional damping factor, Alpha. Beta is the parameter that controls stiffness proportional damping; at this stage, leave it set to zero.

-

Click OK.

The duration of the oscillation of the plate is approximately 30 ms, so we need to increase the analysis period to allow enough time for the vibration to be damped out. Edit the step definition, and increase the time period of step Blast to 150E-3 s.

The results of the damped analysis clearly show the effect of mass proportional damping. [Figure 10&#8211;43](ch10s05.html#gxi-damp-disp-hist) shows the displacement history of the central node for both the damped and undamped analyses. (We have extended the analysis time to 150 ms for the undamped model to compare the data more effectively.) The peak response is also reduced due to damping. By the end of the damped analysis the oscillation has decayed to a nearly static condition.

> **Figure:**

Figure 10&#8211;43 Damped and undamped displacement histories.

**Rate dependence**

Some materials, such as mild steel, show an increase in the yield stress with increasing strain rate. In this example the loading rate is high, so strain-rate dependence is likely to be important.

Add rate dependence to your material definition.

**To add rate dependence to your metal plasticity material model:**

-

In the Model Tree, double-click Steel underneath the Materials container.

-

In the Edit Material dialog box, select Plastic from the list of material behaviors.

-

Select SuboptionsRate Dependent.

-

In the Suboption Editor that appears, enter a value of 40 for the Multiplier and a value of 5 for the Exponent, and click OK.

With this definition of rate-dependent behavior, the ratio of the dynamic yield stress to the static yield stress () is given for an equivalent plastic strain rate (), according to the equation , where  and  are material constants (40 and 5 in this case).

Change the time period of step Blast back to the original value of 50 ms. Create a job named BlastLoadRateDep, and submit the job for analysis. When the analysis is complete, open the output database file BlastLoadRateDep.odb, and postprocess the results.

When rate dependence is included, the yield stress effectively increases as the strain rate increases. Therefore, because the elastic modulus is higher than the plastic modulus, we expect a stiffer response in the analysis with rate dependence. Both the displacement history of the central portion of the plate shown in [Figure 10&#8211;44](ch10s05.html#gxi-disp-central-node) and the history of plastic strain energy shown in [Figure 10&#8211;45](ch10s05.html#gxi-plas-strain-energy) confirm that the response is indeed stiffer when rate dependence is included. The results are, of course, sensitive to the material data. In this case the values of  and  are typical of a mild steel, but more precise data would be required for detailed design analyses.

> **Figure:**

Figure 10&#8211;44 Displacement of the central node with and without rate dependence (undamped).

> **Figure:**

Figure 10&#8211;45 Plastic strain energy with and without rate dependence (undamped).

### 10.6&nbsp;Hyperelasticity

We now turn our attention to another class of material nonlinearity, namely, the nonlinear elastic response exhibited by rubber materials.### 10.6.1&nbsp;Introduction

The stress-strain behavior of typical rubber materials, shown in [Figure 10&#8211;46](ch10s06.html#gss-rubber), is elastic but highly nonlinear.

> **Figure:**

Figure 10&#8211;46 Typical stress-strain curve for rubber.

This type of material behavior is called hyperelasticity. The deformation of hyperelastic materials, such as rubber, remains elastic up to large strain values (often well over 100%).

Abaqus makes the following assumptions when modeling a hyperelastic material:

-

The material behavior is elastic.

-

The material behavior is isotropic.

-

The simulation will include nonlinear geometric effects.

In addition, Abaqus/Standard assumes the hyperelastic material is incompressible by default. Abaqus/Explicit assumes the material is nearly incompressible (Poisson's ratio is 0.475 by default).

Elastomeric foams are another class of highly nonlinear, elastic materials. They differ from rubber materials in that they have very compressible behavior when subjected to compressive loads. They are modeled with a separate material model in Abaqus and are not discussed in detail in this guide.### 10.6.2&nbsp;Compressibility

Most solid rubber materials have very little compressibility compared to their shear flexibility. This behavior is not a problem with plane stress, shell, or membrane elements. However, it can be a problem when using other elements, such as plane strain, axisymmetric, and three-dimensional solid elements. For example, in applications where the material is not highly confined, it would be quite satisfactory to assume that the material is fully incompressible: the volume of the material cannot change except for thermal expansion. In cases where the material is highly confined (such as an O-ring used as a seal), the compressibility must be modeled correctly to obtain accurate results.

Abaqus/Standard has a special family of &#8220;hybrid&#8221; elements that must be used to model the fully incompressible behavior seen in hyperelastic materials. These &#8220;hybrid&#8221; elements are identified by the letter `H' in their name; for example, the hybrid form of the 8-node brick, C3D8, is called C3D8H.

Except for plane stress and uniaxial cases, it is not possible to assume that the material is fully incompressible in Abaqus/Explicit because the program has no mechanism for imposing such a constraint at each material calculation point. An incompressible material also has an infinite wave speed, resulting in a time increment of zero. Therefore, we must provide some compressibility. The difficulty is that, in many cases, the actual material behavior provides too little compressibility for the algorithms to work efficiently. Thus, except for plane stress and uniaxial cases, the user must provide enough compressibility for the code to work, knowing that this makes the bulk behavior of the model softer than that of the actual material. Some judgment is, therefore, required to decide whether or not the solution is sufficiently accurate, or whether the problem can be modeled at all with Abaqus/Explicit because of this numerical limitation. We can assess the relative compressibility of a material by the ratio of its initial bulk modulus, , to its initial shear modulus, . Poisson's ratio, , also provides a measure of compressibility since it is defined as

[Table 10&#8211;4](ch10s06.html#gxi-chp-material-table2) provides some representative values.

Table 10&#8211;4 Relationship between compressibility and Poisson's ratio.

| |  | Poisson's ratio

| | 10 | 0.452

| | 20 | 0.475

| | 50 | 0.490

| | 100 | 0.495

| | 1,000 | 0.4995

| | 10,000 | 0.49995

If no value is given for the material compressibility, by default Abaqus/Explicit assumes , corresponding to Poisson's ratio of 0.475. Since typical unfilled elastomers have  ratios in the range of 1,000 to 10,000 ( to ) and filled elastomers have  ratios in the range of 50 to 200 ( to ), this default provides much more compressibility than is available in most elastomers. However, if the elastomer is relatively unconfined, this softer modeling of the material's bulk behavior usually provides quite accurate results. Unfortunately, in cases where the material is highly confined&#8212;such as when it is in contact with stiff, metal parts and has a very small amount of free surface, especially when the loading is highly compressive&#8212;it may not be feasible to obtain accurate results with Abaqus/Explicit.

If you are defining the compressibility rather than accepting the default value in Abaqus/Explicit, an upper limit of 100 is suggested for the ratio of . Larger ratios introduce high frequency noise into the dynamic solution and require the use of excessively small time increments.### 10.6.3&nbsp;Strain energy potential

Abaqus uses a strain energy potential (*U*), rather than a Young's modulus and Poisson's ratio, to relate stresses to strains in hyperelastic materials. Several different strain energy potentials are available: a polynomial model, the Ogden model, the Arruda-Boyce model, the Marlow model, and the van der Waals model. Simpler forms of the polynomial model are also available, including the Mooney-Rivlin, neo-Hookean, reduced polynomial, and Yeoh models.

The polynomial form of the strain energy potential is one that is commonly used. Its form is

where *U* is the strain energy potential;  is the elastic volume ratio;  and  are measures of the distortion in the material; and *N*, , and  are material parameters, which may be functions of temperature. The  parameters describe the shear behavior of the material, and the  parameters introduce compressibility. If the material is fully incompressible (a condition not allowed in Abaqus/Explicit), all the values of  are set to zero and the second part of the equation shown above can be ignored. If the number of terms, *N*, is one, the initial shear modulus, , and bulk modulus, , are given by

and

If the material is also incompressible, the equation for the strain energy density is

This expression is commonly referred to as the Mooney-Rivlin material model. If  is also zero, the material is called neo-Hookean.

The other hyperelastic models are similar in concept and are described in &#8220;Hyperelasticity,&#8221;  Section 22.5 of the Abaqus Analysis User's Guide.

You must provide Abaqus with the relevant material parameters to use a hyperelastic material. For the polynomial form these are  and . It is possible that you will be supplied with these parameters when modeling hyperelastic materials; however, more likely you will be given test data for the materials that you must model. Fortunately, Abaqus can accept test data directly and calculate the material parameters for you (using a least squares fit).### 10.6.4&nbsp;Defining hyperelastic behavior using test data

A convenient way of defining a hyperelastic material is to supply Abaqus with experimental test data. Abaqus then calculates the constants using a least squares method. Abaqus can fit data for the following experimental tests:

-

Uniaxial tension and compression

-

Equibiaxial tension and compression

-

Planar tension and compression (pure shear)

-

Volumetric tension and compression

The deformation modes seen in these tests are shown in [Figure 10&#8211;47](ch10s06.html#gss-hyperelastic).

> **Figure:**

Figure 10&#8211;47 Deformation modes for the various experimental tests for defining hyperelastic material behavior.

Unlike plasticity data, the test data for hyperelastic materials must be given to Abaqus as nominal stress and nominal strain values.

Volumetric compression data only need to be given if the material's compressibility is important. Normally in Abaqus/Standard it is not important, and the default fully incompressible behavior is used. As noted earlier, Abaqus/Explicit assumes a small amount of compressibility if no volumetric test data are given.

**Obtaining the best material model from your data**

The quality of the results from a simulation using hyperelastic materials strongly depends on the material test data that you provide Abaqus. Typical tests are shown in [Figure 10&#8211;47](ch10s06.html#gss-hyperelastic). There are several things that you can do to help Abaqus calculate the best possible material parameters.

Wherever possible, try to obtain experimental test data from more than one deformation state&#8212;this allows Abaqus to form a more accurate and stable material model. However, some of the tests shown in [Figure 10&#8211;47](ch10s06.html#gss-hyperelastic) produce equivalent deformation modes for incompressible materials. The following are equivalent tests for incompressible materials:

-

Uniaxial tension &#8596; Equibiaxial compression

-

Uniaxial compression &#8596; Equibiaxial tension

-

Planar tension &#8596; Planar compression

You do not need to include data from a particular test if you already have data from another test that models a particular deformation mode.

In addition, the following may improve your hyperelastic material model:

-

Obtain test data for the deformation modes that are likely to occur in your simulation. For example, if your component is loaded in compression, make sure that your test data include compressive, rather than tensile, loading.

-

Both tension and compression data are allowed, with compressive stresses and strains entered as negative values. If possible, use compression or tension data depending on the application, since the fit of a single material model to both tensile and compressive data will normally be less accurate than for each individual test.

-

Try to include test data from the planar test. This test measures shear behavior, which can be very important.

-

Provide more data at the strain magnitudes that you expect the material will be subjected to during the simulation. For example, if the material will only have small tensile strains, say under 50%, do not provide much, if any, test data at high strain values (over 100%).

-

Use the material evaluation functionality in Abaqus/CAE to perform simulations of the experimental tests and to compare the results Abaqus calculates to the experimental data. If the computational results are poor for a particular deformation mode that is important to you, try to obtain more experimental data for that deformation mode. The technique is illustrated as part of the example discussed in &#8220;Example: axisymmetric mount,&#8221;  Section 10.7. Please consult the Abaqus/CAE User's Guide for further details.

**Stability of the material model**

It is common for the hyperelastic material model determined from the test data to be unstable at certain strain magnitudes. Abaqus performs a stability check to determine the strain magnitudes where unstable behavior will occur and prints a warning message in the data (.dat) file. The same information is printed in the Material Parameters and Stability Limit Information dialog box that appears when the material evaluation capability is used in Abaqus/CAE. You should check this information carefully since your simulation may not be realistic if any part of the model experiences strains beyond the stability limits. The stability checks are done for specific deformations, so it is possible for the material to be unstable below the strain levels indicated if the deformation is more complex. In Abaqus/Standard your simulation may not converge if a part of the model exceeds the stability limits.

See &#8220;Hyperelastic behavior of rubberlike materials,&#8221;  Section 22.5.1 of the Abaqus Analysis User's Guide, for suggestions on improving the accuracy and stability of the test data fit.

### 10.7&nbsp;Example: axisymmetric mount

You have been asked to find the axial stiffness of the rubber mount shown in [Figure 10&#8211;48](ch10s07.html#gss-axi-mount) and to identify any areas of high maximum principal stress that might limit the fatigue life of the mount. The mount is bonded at both ends to steel plates. It will experience axial loads up to 5.5 kN distributed uniformly across the plates. The cross-section geometry and dimensions are given in [Figure 10&#8211;48](ch10s07.html#gss-axi-mount).

> **Figure:**

Figure 10&#8211;48 Axisymmetric mount.

You can use axisymmetric elements for this simulation since both the geometry of the structure and the loading are axisymmetric. Therefore, you only need to model a plane through the component: each element represents a complete 360° ring. You will examine the static response of the mount; therefore, you will use Abaqus/Standard for your analysis.### 10.7.1&nbsp;Symmetry

You do not need to model the whole section of this axisymmetric component because the problem is symmetric about a horizontal line through the center of the mount. By modeling only half of the section, you can use half as many elements and, hence, approximately half the number of degrees of freedom. This significantly reduces the run time and storage requirements for the analysis or, alternatively, allows you to use a more refined mesh.

Many problems contain some degree of symmetry. For example, mirror symmetry, cyclic symmetry, axisymmetry, or repetitive symmetry (shown in [Figure 10&#8211;49](ch10s07.html#gss-symmetry)) are common. More than one type of symmetry may be present in the structure or component that you want to model.

> **Figure:**

Figure 10&#8211;49 Various forms of symmetry.

When modeling just a portion of a symmetric component, you have to add boundary conditions to make the model behave as if the whole component were being modeled. You may also have to adjust the applied loads to reflect the portion of the structure actually being modeled. Consider the portal frame in [Figure 10&#8211;50](ch10s07.html#gss-portal-frame).

> **Figure:**

Figure 10&#8211;50 Symmetric portal frame.

The frame is symmetric about the vertical line shown in the figure. To maintain symmetry in the model, any nodes on the symmetry line must be constrained from translating in the 1-direction and from rotating about the 2- or 3-axes.

In the frame problem the load is applied along the model's symmetry plane; therefore, only half of the total value should be applied to the portion you are modeling.

In axisymmetric analyses using axisymmetric elements, such as this rubber mount example, we need model only the cross-section of the component. The element formulation automatically includes the effects of axial symmetry.### 10.7.2&nbsp;Preprocessing&#8212;creating the model with Abaqus/CAE

Use Abaqus/CAE to create the model. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in &#8220;Axisymmetric mount,&#8221;  Section A.10. Instructions on how to fetch the script and run it within Abaqus/CAE are given in Appendix A, &#8220;Example Files.&#8221;

-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select Plug-insAbaqusGetting Started; highlight Axisymmetric mount; and click Run. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: axisymmetric mount,&#8221;  Section 10.7 of Getting Started with Abaqus: Keywords Edition.

**Part definition**

Create an axisymmetric, deformable, shell part. Name the part Mount, and specify an approximate part size of 0.3. Because of symmetry considerations, only the bottom half of the mount will be modeled. You can use the following suggested approach to create the part geometry. When you first enter the sketcher, the axis of revolution is displayed as a green dashed line with a fixed position constraint; your sketch cannot cross this axis.

**To sketch the mount geometry:**

-

Draw an arbitrary rectangle to the right of the axis of symmetry. Dimension it as follows:-

Set the horizontal distance between the axis of symmetry and the left edge of the rectangle to 0.01 m.

-

Set the vertical height of the rectangle to 0.030 m and its horizontal span to 0.050 m.

-

Sketch a circle using the Create Circle: Center and Perimeter tool . Select any point to the right of the rectangle as the center, and snap the perimeter point to any point along the right edge of the rectangle. Dimension the circle as follows:-

Set the horizontal distance between the axis of symmetry and the center of the circle to 0.1 m.

-

Set the vertical distance between the center of the circle and the top-right vertex of the rectangle to 0 m.

-

Set the vertical distance between the perimeter point (where the circle snaps to the rectangle) and the bottom-right vertex of the rectangle to 0.005 m.

The sketch appears as shown in [Figure 10&#8211;51](ch10s07.html#gss-mount-parta-c).

> **Figure:**

Figure 10&#8211;51 Construction geometry used to create the part (with grid spacing doubled).

-

Use the Auto-Trim tool  to remove the excess portions of the sketch as shown in [Figure 10&#8211;52](ch10s07.html#gss-mount-partb-c).

> **Figure:**

Figure 10&#8211;52 Final part geometry (with grid spacing doubled).

**Material properties: hyperelastic model for the rubber**

You have been given some experimental test data for the rubber material used in the mount. Three different sets of test data&#8212;a uniaxial test, a biaxial test, and a planar (shear) test&#8212;are available. The data (shown in [Figure 10&#8211;53](ch10s07.html#gss-mat-testdata) and tabulated in [Table 10&#8211;5](ch10s07.html#gss-mount-uniaxial), [Table 10&#8211;6](ch10s07.html#gss-mount-biaxial), and [Table 10&#8211;7](ch10s07.html#gss-mount-planar)) are given in terms of nominal stress and corresponding nominal strain.

Note:&nbsp;

Volumetric test data are not required when the material is incompressible (as is the case in this example).

> **Figure:**

Figure 10&#8211;53 Material test data for the rubber material.

Table 10&#8211;5 Uniaxial test data.

| | Stress (Pa) | Strain

| | 0.054E6 | 0.0380

| | 0.152E6 | 0.1338

| | 0.254E6 | 0.2210

| | 0.362E6 | 0.3450

| | 0.459E6 | 0.4600

| | 0.583E6 | 0.6242

| | 0.656E6 | 0.8510

| | 0.730E6 | 1.4268

Table 10&#8211;6 Biaxial test data.

| | Stress (Pa) | Strain

| | 0.089E6 | 0.0200

| | 0.255E6 | 0.1400

| | 0.503E6 | 0.4200

| | 0.958E6 | 1.4900

| | 1.703E6 | 2.7500

| | 2.413E6 | 3.4500

Table 10&#8211;7 Planar test data.

| | Stress (Pa) | Strain

| | 0.055E6 | 0.0690

| | 0.324E6 | 0.2828

| | 0.758E6 | 1.3862

| | 1.269E6 | 3.0345

| | 1.779E6 | 4.0621

When you define a hyperelastic material using experimental data, you also specify the strain energy potential that you want to apply to the data. Abaqus uses the experimental data to calculate the coefficients necessary for the specified strain energy potential. However, it is important to verify that an acceptable correlation exists between the behavior predicted by the material definition and the experimental data.

You can use the material evaluation option available in Abaqus/CAE to simulate one or more standard tests with the experimental data using the strain energy potential that you specify in the material definition.

**To define and evaluate hyperelastic material behavior:**

-

Create a hyperelastic material named Rubber. In this example a first-order, polynomial strain energy function is used to model the rubber material; thus, select Polynomial from the Strain energy potential list in the material editor. Enter the test data given above using the Test Data menu items in the material editor.

To visualize the experimental data, click mouse button 3 on the table for any of the test data and select Create X&#8211;Y Data from the menu that appears. You can then plot the data in the Visualization module.

Note:&nbsp;

In general, you may be unsure of which strain energy potential to specify. In this case, you could select Unknown from the Strain energy potential list in the material editor. You could then use the Evaluate option to guide your selection by performing standard tests with the experimental data using multiple strain energy potentials.

-

In the Model Tree, click mouse button 3 on Rubber underneath the Materials container. Select Evaluate from the menu that appears to perform the standard unit-element tests (uniaxial, biaxial, and planar). Specify a minimum strain of 0 and a maximum strain of 1.75 for each test. Evaluate only the first-order polynomial strain energy function. This form of the hyperelasticity model is known as the Mooney-Rivlin material model.

When the evaluation is complete, Abaqus/CAE enters the Visualization module. A dialog box appears containing material parameter and stability information. In addition, an X&#8211;Y plot that displays a nominal stress&#8211;nominal strain curve for the material as well as a plot of the experimental data appears for each test.

The computational and experimental results for the various types of tests are compared in [Figure 10&#8211;54](ch10s07.html#gss-biaxial), [Figure 10&#8211;55](ch10s07.html#gss-uniaxial), and [Figure 10&#8211;56](ch10s07.html#gss-planar) (for clarity, some of the computational data points are not shown). The Abaqus/Standard and experimental results for the biaxial tension test match very well. The computational and experimental results for the uniaxial tension and planar tests match well at strains less than 100%. The hyperelastic material model created from these material test data is probably not suitable for use in general simulations where the strains may be larger than 100%. However, the model will be adequate for this simulation if the principal strains remain within the strain magnitudes where the data and the hyperelastic model fit well.

> **Figure:**

Figure 10&#8211;54 Comparison of experimental data (solid line) and Abaqus/Standard results (dashed line): biaxial tension.

> **Figure:**

Figure 10&#8211;55 Comparison of experimental data (solid line) and Abaqus/Standard results (dashed line): uniaxial tension.

> **Figure:**

Figure 10&#8211;56 Comparison of experimental data (solid line) and Abaqus/Standard results (dashed line): planar shear.

If you find that the results are beyond these magnitudes or if you are asked to perform a different simulation, you will have to insist on getting better material data. Otherwise, you will not be able to have much confidence in your results.

**The hyperelastic material parameters**

In this simulation the material is assumed to be incompressible ( = 0). To achieve this, no volumetric test data were provided. To simulate compressible behavior, you must provide volumetric test data in addition to the other test data.

The hyperelastic material coefficients&#8212;, , and &#8212;that Abaqus calculates from the material test data appear in the Material Parameters and Stability Limit Information dialog box, shown in [Figure 10&#8211;57](ch10s07.html#gsi-mount-test1). The material model is stable at all strains with these material test data and this strain energy function.

> **Figure:**

Figure 10&#8211;57 Material parameters and stability limits for the first-order polynomial strain energy function.

However, if you specified that a second-order (N=2) polynomial strain energy function be used, you would see the warnings shown in [Figure 10&#8211;58](ch10s07.html#gsi-mount-test2). If you had only uniaxial test data for this problem, you would find that the Mooney-Rivlin material model Abaqus creates would have unstable material behavior above certain strain magnitudes.

> **Figure:**

Figure 10&#8211;58 Material parameters and stability limits for the second-order polynomial strain energy function.

**Completing the material and section definitions and assigning section properties**

The steel is modeled with linear elastic properties only ( = 200&nbsp;× 109 Pa,  = 0.3) because the loads should not be large enough to cause inelastic deformations. Create a material named Steel with these properties. In addition, create two homogeneous solid section definitions: one named RubberSection that refers to the rubber material and one named SteelSection that refers to the steel material.

Before assigning section properties, partition the part into the two regions shown in [Figure 10&#8211;59](ch10s07.html#gss-mount-partition-c) using the Partition Face: Sketch tool.

> **Figure:**

Figure 10&#8211;59 Partition used to divide the part into two regions.

In the Sketcher, draw a horizontal line extending from the point where the circular arc intersects the right edge to any point past the left edge of the sketch.

The upper region represents the rubber mount, while the lower region represents the steel plate. Assign the appropriate section definitions to each region.

**Creating an assembly and a step definition**

Create a dependent instance of the part. In this simulation you can accept the default r&#8211;z (1&#8211;2) axisymmetric coordinate system. Then, define a single static, general step named Compress&nbsp;mount. When hyperelastic materials are used in a model, Abaqus assumes that the model may undergo large deformations; but large deformations and other nonlinear geometric effects are not included by default in Abaqus/Standard. Therefore, you must include them in this simulation by toggling on Nlgeom; otherwise, Abaqus/Standard will terminate the analysis with an input error. Set the time period to 1.0 and the initial time increment to 0.01 (i.e., 1% of the total step time).

For the purpose of restricting output, create a geometry set named Out at the vertex located at the lower-left corner of the steel plate region.

Write the preselected variables and nominal strains as field output to the output database file every increment. In addition, write the displacements at a single point on the bottom of the steel plate to the output database file as history data so that the stiffness of the mount can be calculated. Use the geometry set Out for this purpose.

**Applying loads and boundary conditions**

Specify boundary conditions for the region on the symmetry plane (U2 = 0 is shown in [Figure 10&#8211;60](ch10s07.html#gss-mount-bcs-c); however, YSYMM would be equivalent in this case).

> **Figure:**

Figure 10&#8211;60 Boundary conditions on the rubber mount; pressure loading on the steel plate.

No boundary constraints are needed in the radial direction (global 1-direction) because the axisymmetric nature of the model does not allow the structure to move as a rigid body in the radial direction. Abaqus will allow nodes to move in the radial direction, even those initially on the axis of symmetry (i.e., those with a radial coordinate of 0.0), if no boundary conditions are applied to their radial displacements (degree of freedom 1). Since you want to let the mount deform radially in this analysis, do not apply any boundary conditions; again, Abaqus will prevent rigid body motions automatically.

The mount must carry a maximum axial load of 5.5 kN, spread uniformly over the steel plates. Therefore, apply a distributed load to the bottom of the steel plate, as shown in [Figure 10&#8211;60](ch10s07.html#gss-mount-bcs-c). The magnitude of the pressure is given by

**Creating the mesh and the job**

Use first-order, axisymmetric, hybrid solid elements (CAX4H) for the rubber mount. You must use hybrid elements because the material is fully incompressible. The elements are not expected to be subjected to bending, so shear locking in these fully integrated elements should not be a concern. Model the steel plates with a single layer of incompatible mode elements (CAX4I) because it is possible that the plates may bend as the rubber underneath them deforms.

Create a quadrilateral mesh. Seed the part by specifying the number of elements along the edges (by selecting SeedEdges or the  tool). Specify 30 elements along each horizontal edge, 14 elements along the vertical and curved edges of the rubber, and 1 element along the vertical edges of the steel. The mesh is shown in [Figure 10&#8211;61](ch10s07.html#gss-mount-mesh).

> **Figure:**

Figure 10&#8211;61 Mesh for the rubber mount.

Create a job named Mount. Give the job the following description: Axisymmetric mount analysis under axial loading.

Save your model in a model database file, and submit the job for analysis. Monitor the solution progress; correct any modeling errors that are detected, and investigate and correct as necessary the cause of any warning messages.### 10.7.3&nbsp;Postprocessing

Enter the Visualization module, and open the file Mount.odb.

**Calculating the stiffness of the mount**

Determine the stiffness of the mount by creating an X&#8211;Y plot of the displacement of the steel plate as a function of the applied load. You will first create a plot of the vertical displacement of the node on the steel plate for which you wrote data to the output database file. Data were written for the node&nbsp;in set Out in this model.

To create a history curve of vertical displacement and swap the *X*- and *Y*-axes:

-

In the Results Tree, expand the History Output container underneath the output database named Mount.odb.

-

Locate and select the vertical displacement U2 at the node in set Out.

-

Click mouse button 3, and  select Save As from the menu that appears to save the X&#8211;Y data.

The Save XY Data As dialog box appears.

-

In the Save XY Data As dialog box, name the curve SWAPPED and select swap(XY) as the save operation; click OK.

The plot of time-displacement appears in the viewport.

You now have a curve of time-displacement. What you need is a curve showing force-displacement. This is easy to create because in this simulation the force applied to the mount is directly proportional to the total time in the analysis. All you have to do to plot a force-displacement curve is multiply the curve SWAPPED by the magnitude of the load (5.5 kN).

**To multiply a curve by a constant value:**

-

In the Results Tree, double-click XYData.

The Create XY Data dialog box appears.

-

Select Operate on XY data, and click Continue.

The Operate on XY Data dialog box appears.

-

In the XY Data field, double-click SWAPPED.

The expression "SWAPPED" appears in the text field at the top of the dialog box. Your cursor should be at the end of the text field.

-

Multiply the data object in the text field by the magnitude of the applied load by entering *5500.

-

Save the multiplied data object by clicking Save As at the bottom of the dialog box.

The Save XY Data As dialog box appears.

-

In the Name text field, type FORCEDEF; and click OK to close the dialog box.

-

To view the force-displacement plot, click Plot Expression at the bottom of the Operate on XY Data dialog box.

You have now created a curve with the force-deflection characteristic of the mount (the axis labels do not reflect this since you did not change the actual variable plotted). To get the stiffness, you need to differentiate the curve FORCEDEF. You can do this by using the differentiate( ) operator in the Operate on XY Data dialog box.

**To obtain the stiffness:**

-

In the Operate on XY Data dialog box, clear the current expression.

-

From the Operators listed, click differentiate(X).

differentiate( ) appears in the text field at the top of the dialog box.

-

In the XY Data field, double-click FORCEDEF.

The expression differentiate( "FORCEDEF" ) appears in the text field.

-

Save the differentiated data object by clicking Save As at the bottom of the dialog box.

The Save XY Data As dialog box appears.

-

In the Name text field, type STIFF; and click OK to close the dialog box.

-

To plot the stiffness-displacement curve, click Plot Expression at the bottom of the Operate on XY Data dialog box.

-

Click Cancel to close the dialog box.

-

Open the Axis Options dialog box, and switch to the Title tabbed page.

-

Customize the axis titles so they appear as shown in [Figure 10&#8211;62](ch10s07.html#gss-stiff).

> **Figure:**

Figure 10&#8211;62 Stiffness characteristic of the mount.

-

Click Dismiss to close the Axis Options dialog box.

The stiffness of the mount increases by almost 100% as the mount deforms. This is a result of the nonlinear nature of the rubber and the change in shape of the mount as it deforms. Alternatively, you could have created the stiffness-displacement curve directly by combining all the operators above into one expression.

**To define the stiffness curve directly:**

-

In the Results Tree, double-click XYData.

The Create XY Data dialog box appears.

-

Select Operate on XY data, and click Continue.

The Operate on XY Data dialog box appears.

-

From the Operators listed, click differentiate(X).

differentiate( )&nbsp;appears in the text field at the top of the dialog box.

-

In the XY Data field, double-click SWAPPED.

The expression differentiate( "SWAPPED" )&nbsp;appears in the text field.

-

Place the cursor in the text field directly after the "SWAPPED"&nbsp;data object, and type *5500 to multiply the swapped data by the constant total force value.

differentiate(  "SWAPPED"*5500  )&nbsp;appears in the text field.

-

Save the differentiated data object by clicking Save As at the bottom of the dialog box.

The Save XY Data As dialog box appears.

-

In the Name text field, type STIFFNESS; and click OK to close the dialog box.

-

Click Cancel to close the Operate on XY Data dialog box.

-

Customize the X- and Y-axis labels as they appear in [Figure 10&#8211;62](ch10s07.html#gss-stiff) if you have not already done so.

-

In the Results Tree, click mouse button 3 on STIFFNESS underneath the XYData container and select Plot from the menu that appears to view the plot in [Figure 10&#8211;62](ch10s07.html#gss-stiff) that shows the variation of the mount's axial stiffness as the mount deforms.

**Model shape plots**

You will begin by plotting the undeformed model shape of the mount.

**To plot the undeformed model shape:**

From the main menu bar, select PlotUndeformed Shape; or use the  tool in the Visualization module toolbox to plot the undeformed model shape (see [Figure 10&#8211;63](ch10s07.html#gss-undeform-shape)).

> **Figure:**

Figure 10&#8211;63 Undeformed model shape of the rubber mount.

If the figure obscures the plot title, you can move the plot by clicking the  tool and holding down mouse button 1 to pan the deformed shape to the desired location. Alternatively, you can turn the plot title off (ViewportViewport Annotation Options).

In this figure the axisymmetric model is displayed as a planar, two-dimensional shape. You can producing a three-dimensional visual effect by sweeping the model through a specified angle. In addition, you can also mirror results about selected planes (such as symmetry planes) to render results on a full three-dimensional representation of the model. These are visualization aids only. Any numerical representation of the results, such as the contour legend, indicates only the portion of the model that was analyzed. Since in this problem the symmetry plane does not necessarily coincide with one of the global coordinate system planes, a local system will be defined to facilitate the mirroring operation.

**To define a local coordinate system for postprocessing:**

-

From the main menu bar, select ToolsCoordinate SystemCreate.

-

In the Create Coordinate System dialog box, enter rectangular as the name and click Continue.

-

Select the node at the top-left corner of the model as the origin, the node at the top-right corner as the point on the X-axis, and the node at the bottom-left corner as the point in the X&#8211;Y plane.

**To mirror and sweep the cross-section:**

-

From the main menu bar, select ViewODB Display Options.

-

In the ODB Display Options dialog box, click the Mirror/Pattern tab.

-

Select rectangular from the Mirror CSYS list.

-

Select XZ as the mirror plane.

-

Click Apply.

The mirrored image appears.

-

Click the Sweep/Extrude tab.

-

Toggle on Sweep elements and set the sweep range from 0 to 270 degrees. Set the number of segments to 45.

-

Click OK.

The swept image appears. To more clearly distinguish between the rubber and the steel, color code the model based on section assignment.

You will now plot the deformed model shape of the mount. This will allow you to evaluate the quality of the deformed mesh and to assess the need for mesh refinement.

**To plot the deformed model shape:**

From the main menu bar, select  PlotDeformed Shape, or use the  tool to plot the deformed model shape of the mount (see [Figure 10&#8211;64](ch10s07.html#gss-deformed-v)).

> **Figure:**

Figure 10&#8211;64 Deformed model shape of the rubber under an applied load of 5500 N (mirrored/swept image).

The plate has been pushed up, causing the rubber to bulge at the sides. Zoom in on the bottom left corner of the mesh using the  tool from the View Manipulation toolbar. Click mouse button 1, and hold it down to define the first corner of the new view; move the mouse to create a box enclosing the viewing area that you want ([Figure 10&#8211;65](ch10s07.html#gss-distortion)); and release the mouse button. Alternatively, you can zoom and pan the plot by selecting ViewSpecify from the main menu bar.

You should have a plot similar to the one shown in [Figure 10&#8211;65](ch10s07.html#gss-distortion) (in this and the images that follow, the sweep and mirroring operations applied earlier have been suppressed).

> **Figure:**

Figure 10&#8211;65 Distortion at the left-hand corner of the rubber mount model.

Some elements in this corner of the model are becoming badly distorted because the mesh design in this area was inadequate for the type of deformation that occurs there. Although the shape of the elements is fine at the start of the analysis, they become badly distorted as the rubber bulges outward, especially the element in the corner. If the loading were increased further, the element distortion may become so excessive that the analysis may abort. &#8220;Mesh design for large distortions,&#8221;  Section 10.8, discusses how to improve the mesh design for this problem.

The keystoning pattern exhibited by the distorted elements in the bottom right-hand corner of the model indicates that they are locking. A contour plot of the hydrostatic pressure stress in these elements (without averaging across elements sharing common nodes) shows rapid variation in the pressure stress between adjacent elements. This indicates that these elements are suffering from volumetric locking, which was discussed earlier in &#8220;Selecting elements for elastic-plastic problems,&#8221;  Section 10.3, in the context of plastic incompressibility. Volumetric locking arises in this problem from overconstraint. The steel is very stiff compared to the rubber. Thus, along the bond line the rubber elements cannot deform laterally. Since these elements must also satisfy incompressibility requirements, they are highly constrained and locking occurs. Analysis techniques that address volumetric locking are discussed in &#8220;Techniques for reducing volumetric locking,&#8221;  Section 10.9.

**Contouring the maximum principal stress**

Plot the maximum in-plane principal stress in the model. Follow the procedure given below to create a filled contour plot on the actual deformed shape of the mount with the plot title suppressed.

**To contour the maximum principal stress:**

-

By default, Abaqus/CAE displays S, Mises as the primary field output variable. In the Field Output toolbar, select Max. Principal as the invariant.

Abaqus/CAE automatically changes the current plot state to display a contour plot of the maximum in-plane principal stresses on the deformed model shape.

-

Open the Contour Plot Options dialog box.

-

Drag the uniform contour intervals slider to 8.

-

Click OK to view the contour plot and to close the dialog box.

Create a display group showing only the elements in the rubber mount.

-

In the Results Tree, expand the Materials container underneath the output database file named Mount.odb.

-

Click mouse button 3 on RUBBER, and select Replace from the menu that appears to replace the current display with the selected elements.

-

The viewport display changes and displays only the rubber mount elements, as shown in [Figure 10&#8211;66](ch10s07.html#gss-contours).

> **Figure:**

Figure 10&#8211;66 Contours of maximum principal stress in the rubber mount.

The maximum principal stress in the model, reported in the contour legend, is 136 kPa. Although the mesh in this model is fairly refined and, thus, the extrapolation error should be minimal, you may want to use the query tool  to determine the more accurate integration point values of the maximum principal stress.

When you look at the integration point values, you will discover that the peak value of maximum principal stress occurs in one of the distorted elements in the bottom right-hand part of the model. This value is likely to be unreliable because of the levels of element distortion and volumetric locking. If this value is ignored, there is an area near the plane of symmetry where the maximum principal stress is around 88.2 kPa.

The easiest way to check the range of the principal strains in the model is to display the maximum and minimum values in the contour legend.

**To check the principal nominal strain magnitude:**

-

From the main menu bar, select ViewportViewport Annotation Options.

The Viewport Annotation Options dialog box appears.

-

Click the Legend tab, and toggle on Show min/max values.

-

Click OK.

The maximum and minimum values appear at the bottom of the contour legend in the viewport.

-

In the Field Output toolbar, select Primary as the variable type if it is not already selected.

Abaqus/CAE automatically changes the current plot state to display a contour plot of the maximum in-plane principal stresses on the deformed model shape.

-

From the list of output variables, select NE.

-

From the list of invariants in the Field Output toolbar, select Max. Principal if it is not already selected.

The contour plot changes to display values for maximum principal nominal strain. Note the value of the maximum principal nominal strain from the contour legend.

-

From the list of invariants, select Min. Principal.

The contour plot changes to display values for minimum principal nominal strain. Note the value of the minimum principal nominal strain from the contour legend.

The maximum and minimum principal nominal strain values indicate that the maximum tensile nominal strain in the model is about 100% and the maximum compressive nominal strain is about 56%. Because the nominal strains in the model remained within the range where the Abaqus hyperelasticity model has a good fit to the material data, you can be fairly confident that the response predicted by the mount is reasonable from a material modeling viewpoint.

### 10.8&nbsp;Mesh design for large distortions

We know that the element distortions in the corners of the rubber mount are undesirable. The results in these areas are unreliable; and if the load were increased, the analysis might fail. These problems can be corrected by using a better mesh design. The mesh shown in [Figure 10&#8211;67](ch10s08.html#gss-simulation) is an example of an alternate mesh design that might be used to reduce element distortion in the bottom left corner of the rubber model.

> **Figure:**

Figure 10&#8211;67 Modified mesh to minimize element distortions in the bottom left corner of the rubber model during the simulation.

The issues surrounding the mesh distortion in the opposite corner are addressed in &#8220;Techniques for reducing volumetric locking,&#8221;  Section 10.9. The elements in the bottom left-hand corner region are now much more distorted in the initial, undeformed configuration. However, as the analysis progresses and the elements deform, their shape actually improves. The deformed shape plot, shown in [Figure 10&#8211;68](ch10s08.html#gss-displaced), illustrates that the amount of element distortion in this region is reduced; however, the level of mesh distortion in the bottom right-hand corner of the rubber model is still significant.

> **Figure:**

Figure 10&#8211;68 Deformed shape of the modified mesh.

The contours of maximum principal stress ([Figure 10&#8211;69](ch10s08.html#modified-mesh)) show that the very localized stress in that corner has been reduced only slightly.

> **Figure:**

Figure 10&#8211;69 Contours of maximum principal stress in the modified mesh.

Mesh design for large-distortion problems is more difficult than it is for small-displacement problems. A mesh must be produced where the shape of the elements is reasonable throughout the analysis, not just at the start. You must estimate how the model will deform using experience, hand calculations, or the results from a coarse finite element model.

### 10.9&nbsp;Techniques for reducing volumetric locking

A small amount of compressibility is introduced into the rubber material model in order to alleviate volumetric locking. Provided the amount of compressibility is small, the results obtained with a nearly incompressible material will be very similar to those obtained with an incompressible material.

Compressibility is introduced by setting the material constant  to a nonzero value. The value is chosen so that the initial Poisson's ratio, , is close to 0.5. The equations given in &#8220;Hyperelastic behavior of rubberlike materials,&#8221;  Section 22.5.1 of the Abaqus Analysis User's Guide, can be used to relate  and  in terms of  and  (the initial shear and bulk moduli, respectively) for the polynomial form of the strain energy potential. For example, the hyperelastic material coefficients obtained earlier from the test data (see &#8220;The hyperelastic material parameters&#8221; in &#8220;Preprocessing&#8212;creating the model with Abaqus/CAE,&#8221;  Section 10.7.2) were given as  176051 and  4332.63; thus, setting  5.E7 yields  0.46.

A model incorporating compressibility with additional mesh refinement (to reduce mesh distortion) is shown in [Figure 10&#8211;70](ch10s09.html#gss-vlock-mesh) (this mesh can be generated easily by changing the edge seeds in Abaqus/CAE or another preprocessor).

> **Figure:**

Figure 10&#8211;70 Modified mesh with refinement at both corners.

The deformed shape associated with this model is shown in [Figure 10&#8211;71](ch10s09.html#gss-vlock-defmesh).

> **Figure:**

Figure 10&#8211;71 Deformed shape of the modified mesh.

It is clear from this figure that the mesh distortion has been reduced significantly in the critical regions of the rubber model. Examining contour plots of the pressure (without averaging across elements) reveals a smooth variation in pressure stress between elements. Thus, volumetric locking has been eliminated.

### 10.10&nbsp;Related Abaqus examples

-

&#8220;Pressurized rubber disc,&#8221;  Section 1.1.7 of the Abaqus Benchmarks Guide

-

&#8220;Necking of a round tensile bar,&#8221;  Section 1.1.9 of the Abaqus Benchmarks Guide

-

&#8220;Fitting of rubber test data,&#8221;  Section 3.1.4 of the Abaqus Benchmarks Guide

-

&#8220;Uniformly loaded, elastic-plastic plate,&#8221;  Section 3.2.1 of the Abaqus Benchmarks Guide

### 10.11&nbsp;Suggested reading

The following provides the interested user with additional references on material modeling.

**General texts on materials**

-

Ashby, M. F., and D. R. H. Jones, *Engineering Materials*, Pergamon Press, 1980.

-

Callister, W. D., *Materials Science &amp; Engineering&#8212;An Introduction*, John Wiley, 1994.

-

Pascoe, K. J., *An Introduction to the Properties of Engineering Materials*, Van Nostrand, 1978.

**Plasticity**

-

SIMULIA, *Metal Inelasticity in Abaqus*.

-

Lubliner, J., *Plasticity Theory*, Macmillan Publishing Co., 1990.

-

Calladine, C. R., *Engineering Plasticity*, Pergamon Press, 1969.

**Rubber elasticity**

-

SIMULIA, *Modeling Rubber and Viscoelasticity with Abaqus*.

-

Gent, A., *Engineering with Rubber (How to Design Rubber Components)*, Hanser Publishers, 1992.

### 10.12&nbsp;Summary

-

Abaqus contains an extensive library to model the behavior of various engineering materials. It includes models for metal plasticity and rubber elasticity.

-

The stress-strain data for the metal plasticity model must be defined in terms of true stress and true plastic strain. Nominal stress-strain data can be converted easily into true stress-strain data.

-

The metal plasticity model in Abaqus assumes incompressible plastic behavior.

-

For efficiency Abaqus/Explicit *regularizes* user-defined material curves by fitting them with curves composed of equally spaced points.

-

The hyperelastic material model in Abaqus/Standard allows true incompressibility. The hyperelastic material model in Abaqus/Explicit does not: the default Poisson's ratio for hyperelastic materials in Abaqus/Explicit is 0.475. Some analyses may require increasing Poisson's ratio to model incompressibility more accurately.

-

Polynomial, Ogden, Arruda-Boyce, Marlow, van der Waals, Mooney-Rivlin, neo-Hookean, reduced polynomial, and Yeoh strain energy functions are available for rubber elasticity (hyperelasticity). All models allow the material coefficients to be determined directly from experimental test data. The test data must be specified as nominal stress and nominal strain values.

-

The material evaluation capability in Abaqus/CAE can be used to verify the correlation between the behavior predicted by the hyperelastic material models and experimental test data.

-

Stability warnings may indicate that a hyperelastic material model is unsuitable for the strain ranges you wish to analyze.

-

The presence of symmetry can be used to reduce the size of a simulation since only part of the component needs to be modeled. The effect of the rest of the component is represented by applying appropriate boundary conditions.

-

Mesh design for large-distortion problems is more difficult than for small-displacement problems. The elements in the mesh must not become too distorted at any stage of the analysis.

-

Volumetric locking can be alleviated by permitting a small amount of compressibility. Care must be taken to ensure that the amount of compressibility introduced into the problem does not grossly affect the overall results.

-

The X&#8211;Y plotting capabilities in Abaqus/CAE allow data in curves to be manipulated to create new curves. Two curves or a curve and a constant can be added, subtracted, multiplied, or divided. Curves can also be differentiated, integrated, and combined.