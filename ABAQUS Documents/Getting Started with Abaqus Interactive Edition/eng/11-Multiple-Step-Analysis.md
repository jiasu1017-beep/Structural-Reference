11&nbsp;Multiple Step Analysis

## 11.&nbsp;Multiple Step Analysis

The general goal of an Abaqus simulation is to predict the response of a structure to applied loads. Recall that in a general sense the term *load* in Abaqus refers to anything that induces a change in the response of a structure from its initial state; for example, nonzero boundary conditions or applied displacements, point forces, pressures, fields, etc. In some cases loads are relatively simple, such as a single set of point loads on a structure. In other problems the loads applied to a structure can be very complex. For example, different loads may be applied to different portions of the model in a particular sequence over some period of time, or the magnitude of the loads may vary as a function of time. The term *load history* is used to refer to such complex loading of a model.

In Abaqus the user divides the complete load history of the simulation into a number of *steps*. Each step is a period of &#8220;time,&#8221; specified by the user, for which Abaqus calculates the response of the model to a particular set of loads and boundary conditions. The user must specify the type of response, known as the analysis procedure, during each step and may change analysis procedures from step to step. For example, static dead loads, perhaps gravitational loads, could be applied to a structure in one step; and the dynamic response of the loaded structure to earthquake accelerations could be calculated in the next step. Both implicit and explicit analyses can contain multiple steps; however, implicit and explicit steps cannot be combined in the same analysis job. To combine a series of implicit and explicit steps, the results transfer (or import) capability can be used. This feature is discussed in &#8220;Transferring results between Abaqus/Explicit and Abaqus/Standard,&#8221;  Section 9.2.2 of the Abaqus Analysis User's Guide, and is not discussed further here.

Abaqus divides all of its analysis procedures into two main groups: linear perturbation and general. General analysis steps can be included in an Abaqus/Standard or an Abaqus/Explicit analysis; linear perturbation steps are available only in Abaqus/Standard. Loading conditions and &#8220;time&#8221; are defined differently for the two cases. Furthermore, the results from each type of procedure should be interpreted differently.

The response of the model during a general analysis procedure, known as a *general step*, may be either nonlinear or linear. In a step that uses a perturbation procedure, which is called a *perturbation step*, the response can only be linear. Abaqus/Standard treats such steps as a linear perturbation about the preloaded, predeformed state (known as the base state) created by any previous general steps; therefore, its capability for doing linear simulations is rather more general than that of a purely linear analysis program.

### 11.1&nbsp;General analysis procedures

The starting point for each general step is the deformed state at the end of the last general step. Therefore, the state of the model evolves in a sequence of general steps as it responds to the loads defined in each step. Any initial conditions define the starting point for the first general step in the simulation.

All general analysis procedures share the same concepts for applying loads and defining &#8220;time.&#8221;### 11.1.1&nbsp;Time in general analysis steps

Abaqus has two measures of time in a simulation. The *total time* increases throughout all general steps and is the accumulation of the total step time from each general step. Each step also has its own time scale (known as the *step time*), which begins at zero for each step. Time varying loads and boundary conditions can be specified in terms of either time scale. The time scales for an analysis whose history is divided into three steps, each 100 seconds long, are shown in [Figure 11&#8211;1](ch11s01.html#gss-total-time).

> **Figure:**

Figure 11&#8211;1 Step and total time for a simulation.

### 11.1.2&nbsp;Specifying loads in general steps

In general steps the loads must be specified as total values, not incremental values. For example, if a concentrated load has a value of 1000&nbsp;N in the first step and it is increased to 3000&nbsp;N in the second general step, the magnitude given for the load in the two steps should be 1000&nbsp;N and 3000&nbsp;N, not 1000&nbsp;N and 2000&nbsp;N.

By default, all previously defined loads are propagated to the current step. In the current step you can define additional loads as well as modify any previously defined load (for example, change its magnitude or deactivate it). Any previously defined load that is not specifically modified in the current step continues to follow its associated amplitude definition, provided that the amplitude curve is defined in terms of total time; otherwise, the load is maintained at the magnitude it had at the end of the last general step.

### 11.2&nbsp;Linear perturbation analysis

Linear perturbation analysis steps are available only in Abaqus/Standard.

The starting point for a linear perturbation step is called the base state of the model. If the first step in a simulation is a linear perturbation step, the base state is the state of the model specified using initial conditions. Otherwise, the base state is the state of the simulation at the end of the last general step prior to the linear perturbation step. Although the response of the structure during the perturbation step is by definition linear, the model may have a nonlinear response in previous general steps. For models with a nonlinear response in the prior general steps, Abaqus/Standard uses the current elastic modulus as the linear stiffness for perturbation procedures. This modulus is the initial elastic modulus for elastic-plastic materials and the tangent modulus for hyperelastic materials (see [Figure 11&#8211;2](ch11s02.html#gss-tangentmod)); the moduli used for other material models are described in &#8220;General and linear perturbation procedures,&#8221;  Section 6.1.3 of the Abaqus Analysis User's Guide.

> **Figure:**

Figure 11&#8211;2 For hyperelastic materials the tangent modulus is used as the stiffness in linear perturbation steps that occur after general, nonlinear steps.

The loads in the perturbation step should be sufficiently small that the model's response would not deviate much from that predicted with the tangent modulus. If the simulation includes contact, the contact state between two surfaces does not change during a perturbation step: points that were closed in the base state remain closed, and points that were open remain open.### 11.2.1&nbsp;Time in linear perturbation steps

If another general step follows a perturbation step, Abaqus/Standard uses the state of the model at the end of the last general step as its starting point, not the state of the model at the end of the perturbation step. Thus, the response from a linear perturbation step has no permanent effect on the simulation. Therefore, Abaqus/Standard does not include the step time of linear perturbation steps in the total time for the analysis. In fact, what Abaqus/Standard actually does is to define the step time of a perturbation step to be very small (1036) so that it has no effect when it is added to the total accumulated time. The exception to this rule is the modal dynamics procedure.### 11.2.2&nbsp;Specifying loads in linear perturbation steps

Loads and prescribed boundary conditions given in linear perturbation steps are always local to that step. The load magnitudes (including the magnitudes of prescribed boundary conditions) given in a linear perturbation step are always the perturbation (increment) of the load, not the total magnitude. Likewise, the value of any solution variable is output as the perturbation value only&#8212;the value of the variable in the base state is not included.

As an example of a simple load history that includes a mixture of general and perturbation steps, consider the bow and arrow shown in [Figure 11&#8211;3](ch11s02.html#iusing-bow-arrow).

> **Figure:**

Figure 11&#8211;3 Simple bow and arrow.

Step&nbsp;1 might be to string the bow&#8212;to pretension the bowstring. Step&nbsp;2 would then follow this by pulling back the string with an arrow, thus storing more strain energy in the system. Step&nbsp;3 might then be a linear perturbation analysis step: an eigenvalue frequency analysis to investigate the natural frequencies of the loaded system. Such a step might also have been included between Steps&nbsp;1 and&nbsp;2, to find the natural frequencies of the bow and string just after the string is pretensioned but before it is pulled back to shoot. Step&nbsp;4 is then a nonlinear dynamic analysis, in which the bowstring is released, so that the strain energy that was stored in the system by pulling back the bowstring in Step&nbsp;2 imparts kinetic energy to the arrow and causes it to leave the bow. This step thus continues to develop the nonlinear response of the system, but now with dynamic effects included.

In this case it is obvious that each nonlinear general analysis step must use the state at the end of the previous nonlinear general analysis step as its initial condition. For example, the dynamic part of the history has no loading&#8212;the dynamic response is caused by the release of some of the strain energy stored in the static steps. This effect introduces a natural order dependency in the model: nonlinear general analysis steps follow one another, in the order in which the events they define occur, with linear perturbation analysis steps inserted at the appropriate times in this sequence to investigate the linear behavior of the system at those times.

A more complex load history is illustrated in [Figure 11&#8211;4](ch11s02.html#gss-sink), which shows a schematic representation of the steps in the manufacture and use of a stainless steel sink.

> **Figure:**

Figure 11&#8211;4 Steps in the manufacture and use of a sink.

The sink is formed from sheet steel using a punch, a die, and a blank holder. This forming simulation will consist of a number of general steps. Typically, the first step may involve the application of blank holder pressure, and the punching operation will be simulated in the second step. The third step will involve the removal of the tooling, allowing the sink to spring back into its final shape. Each of these steps is a general step since together they model a sequential load history, where the starting condition for each step is the ending condition from the previous step. These steps obviously include many nonlinear effects (plasticity, contact, large deformations). At the end of the third step, the sink will contain residual stresses and inelastic strains caused by the forming process. Its thickness will also vary as a direct result of the manufacturing process.

The sink is then installed: boundary conditions would be applied around the edge of the sink where it is attached to the worktop. The response of the sink to a number of different loading conditions may be of interest and has to be simulated. For example, a simulation may need to be performed to ensure that the sink does not break if someone stands on it. Step 4 would, therefore, be a linear perturbation step analyzing the static response of the sink to a local pressure load. Remember that the results from Step 4 will be perturbations from the state of the sink after the forming process; do not be surprised, for example, if the displacement of the center of the sink in this step is say only 2&nbsp;mm, but you know that the sink deformed much more than that since the start of the forming simulation. This hypothetical 2&nbsp;mm deflection is just the additional deformation from the sink's final configuration after the forming process (i.e., the end of Step&nbsp;3) caused by the weight of the person. The total deflection, measured from the undeformed sheet's configuration, is the sum of this 2&nbsp;mm and the deflection at the end of Step&nbsp;3.

The sink may also be fitted with a waste disposal unit, so its steady-state dynamic response to a harmonic load at certain frequencies must be simulated. Step 5 would, therefore, be a second linear perturbation step using the direct steady-state dynamics procedure with a load applied at the point of attachment of the disposal unit. The base state for this step is the state at the end of the previous general step&#8212;that is, at the end of the forming process (Step&nbsp;3). The response in the previous perturbation step (Step&nbsp;4) is ignored. The two perturbation steps are, therefore, separate, independent simulations of the sink's response to loads applied to the base state of the model.

If another general step is included in the analysis, the condition of the structure at the start of the step is that at the end of the previous general step (Step&nbsp;3). Step&nbsp;6 could, therefore, be a general step with loads modeling the sink being filled with water. The response in this step may be linear or nonlinear. Following this general step, Step&nbsp;7 could be a simulation repeating the analysis performed in Step&nbsp;4. However, in this case the base state (the state of the structure at the end of the previous general step) is the state of the model at the end of Step&nbsp;6. Therefore, the response will be that of a full sink, rather than an empty one. Performing another steady-state dynamics simulation would produce inaccurate results because the mass of the water, which would change the response considerably, would not be considered in the analysis.

The following procedures in Abaqus/Standard are always linear perturbation steps:

-

linear eigenvalue buckling,

-

frequency extraction,

-

transient modal dynamics,

-

random response,

-

response spectrum, and

-

steady-state dynamics.

The static procedure can be either a general or linear perturbation procedure.

### 11.3&nbsp;Example: vibration of a piping system

In this example you will study the vibrational frequencies of a 5&nbsp;m long section of a piping system. The pipe is made of steel and has an outer diameter of 18&nbsp;cm and a 2&nbsp;cm wall thickness (see [Figure 11&#8211;5](ch11s03.html#gss-pipingsystem)).

> **Figure:**

Figure 11&#8211;5 Portion of piping system being analyzed.

It is clamped firmly at one end and can move only axially at the other end. This 5&nbsp;m portion of the piping system may be subjected to harmonic loading at frequencies up to 50&nbsp;Hz. The lowest vibrational mode of the unloaded structure is 40.1&nbsp;Hz, but this value does not consider how the loading applied to the piping structure may affect its response. To ensure that the section does not resonate, you have been asked to determine the magnitude of the in-service load that is required so that its lowest vibrational mode is higher than 50&nbsp;Hz. You are told that the section of pipe will be subjected to axial tension when in service. Start by considering a load magnitude of 4&nbsp;MN.

The lowest vibrational mode of the pipe will be a sine wave deformation in any direction transverse to the pipe axis because of the symmetry of the structure's cross-section. You will use three-dimensional beam elements to model the pipe section.

The analysis requires a natural frequency extraction. Thus, you will use Abaqus/Standard as your analysis product.### 11.3.1&nbsp;Preprocessing&#8212;creating the model with Abaqus/CAE

Create the model for this example using Abaqus/CAE. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in &#8220;Vibration of a piping system,&#8221;  Section A.11. Instructions on how to fetch the script and run it within Abaqus/CAE are given in Appendix A, &#8220;Example Files.&#8221;

-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select Plug-insAbaqusGetting Started; highlight Vibration of a piping system; and click Run. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: vibration of a piping system,&#8221;  Section 11.3 of Getting Started with Abaqus: Keywords Edition.

**Part geometry**

Create a three-dimensional, deformable, planar wire part. (Remember to use an approximate part size that is slightly larger than the largest dimension in your model.) Name the part Pipe, and use the Create Lines: Connected tool to sketch a horizontal line of length 5.0 m. Dimension the sketch as needed to ensure that the length is specified precisely.

**Material and section properties**

The pipe is made of steel with a Young's modulus of 200 × 109 Pa and a Poisson's ratio of 0.3. Create a linear elastic material named Steel with these properties. You must also define the density of the steel material (7800&nbsp;kg/m3) because eigenmodes and eigenfrequencies will be extracted in this simulation and a mass matrix is needed for this type of procedure.

Next, create a Pipe profile. Name the profile PipeProfile, choose Thin-walled as the formulation, and specify an outer radius of 0.09 m and a wall thickness of 0.02 m for the pipe.

Create a Beam section named PipeSection. In the Edit Beam Section dialog box, specify that section integration will be performed during the analysis and assign material Steel and profile PipeProfile to the section definition.

Finally, assign section PipeSection to the pipe. In addition, define the beam section orientation with the approximate -direction as the vector (0.0, 0.0, &#8211;1.0) (the default). In this model the actual -vector will coincide with this approximate vector.

**Assembly and sets**

Create a dependent instance of the part named Pipe. For convenience, create geometry sets that contain the vertices at the left and right ends of the pipe and name them Left and Right, respectively. These regions will be used later to assign loads and boundary conditions to the model.

**Steps**

In this simulation you need to investigate the eigenmodes and eigenfrequencies of the steel pipe section when a 4&nbsp;MN tensile load is applied. Therefore, the analysis will be split into two steps:

| | Step 1.&nbsp;General step: | Apply a 4&nbsp;MN tensile force.

| | Step 2.&nbsp;Linear perturbation step: |  Calculate modes and frequencies.

Create a general static step named Pull I with the following step description: Apply axial tensile load of 4.0 MN. The actual magnitude of time in this step will have no effect on the results; unless the model includes damping or rate-dependent material properties, &#8220;time&#8221; has no physical meaning in a static analysis procedure. Therefore, use a time period of 1.0. Include the effects of geometric nonlinearity, and specify an initial increment size that is 1/10 the total step time. This causes Abaqus/Standard to apply 10% of the load in the first increment. Accept the default number of allowable increments.

You need to calculate the eigenmodes and eigenfrequencies of the pipe in its loaded state. Thus, create a second analysis step using the linear perturbation frequency extraction procedure. Name the step Frequency I, and give it the following description: Extract modes and frequencies. Although only the first (lowest) eigenmode is of interest, extract the first eight eigenmodes for the model.

**Output requests**

The default output database output requests created by Abaqus/CAE for each step will suffice; you do not need to create any additional output database output requests.

To request output to the restart file, select OutputRestart Requests from the main menu bar of the Step module. For the step labeled Pull I, write data to the restart file every 10 increments; for the step labeled Frequency I, write data to the restart file every increment.

**Loads and boundary conditions**

In the first step create a load named Force that applies a 4 × 106&nbsp;N tensile force to the right end of the pipe section such that it deforms in the positive axial (global 1) direction. Forces are applied, by default, in the global coordinate system.

The pipe section is clamped at its left end. It is also clamped at the other end; however, the axial force must be applied at this end, so only degrees of freedom 2 through 6 (U2, U3, UR1, UR2, and UR3) are constrained. Apply the appropriate boundary conditions to sets Left and Right in the first step.

In the second step you require the natural frequencies of the extended pipe section. This does not involve the application of any perturbation loads, and the fixed boundary conditions are carried over from the previous general step. Therefore, you do not need to specify any additional loads or boundary conditions in this step.

**Mesh and job definition**

Seed and mesh the pipe section with 30 uniformly spaced second-order, pipe elements (PIPE32).

Before continuing, rename the model to Original. This model will later form the basis of the model used in the example discussed in &#8220;Example: restarting the pipe vibration analysis,&#8221;  Section 11.5.

Create a job named Pipe with the following description: Analysis of a 5 meter long pipe under tensile load.

Save your model in a model database file, and submit the job for analysis. Monitor the solution progress; correct any modeling errors and investigate the source of any warning messages, taking corrective action as necessary.### 11.3.2&nbsp;Monitoring the job

Check the Job Monitor as the job is running. When the analysis completes, its contents will look similar to [Figure 11&#8211;6](ch11s03.html#gsi-pipe-monitor).

> **Figure:**

Figure 11&#8211;6 Job Monitor: original pipe vibration analysis.

Both steps are shown, and the time associated with the linear perturbation step (Step 2) is very small: the frequency extraction procedure, or any linear perturbation procedure, does not contribute to the general loading history of the model.### 11.3.3&nbsp;Postprocessing

Enter the Visualization module, and open the output database file, Pipe.odb, created by this job.

**Deformed shapes from the linear perturbation steps**

The Visualization module automatically uses the last available frame on the output database file. The results from the second step of this simulation are the natural mode shapes of the pipe and the corresponding natural frequencies. Plot the first mode shape.

**To plot the first mode shape:**

-

From the main menu bar, select ResultStep/Frame.

The Step/Frame dialog box appears.

-

Select step Frequency I and frame Mode 1.

-

Click OK.

-

From the main menu bar, select PlotDeformed Shape.

-

Click the  tool in the toolbox to allow multiple plot states in the viewport; then click the  tool or select PlotUndeformed Shape to add the undeformed shape plot to the existing deformed plot in the viewport.

-

Include node symbols on both plots (the superimpose options control the appearance of the undeformed shape when multiple plot states are displayed). Change the color of the node symbols to green and the symbol shape to a solid circle.

-

Click the auto-fit tool  so that the entire plot is rescaled to fit in the viewport.

The default view is isometric. Try rotating the model to find a better view of the first eigenmode, similar to that shown in [Figure 11&#8211;7](ch11s03.html#gss-pipesection).

> **Figure:**

Figure 11&#8211;7 First and second eigenmode shapes of the pipe section under the tensile load (the modes lie in planes orthogonal to each other).

Since this is a linear perturbation step, the undeformed shape is the shape of the structure in the base state. This makes it easy to see the motion relative to the base state. Use the  Frame Selector to plot the other mode shapes. You will discover that this model has many repeated eigenmodes. This is a result of the symmetric nature of the pipe's cross-section, which yields two eigenmodes for each natural frequency, corresponding to the 1&#8211;2 and 1&#8211;3 planes. The second eigenmode shape is shown in [Figure 11&#8211;7](ch11s03.html#gss-pipesection). Some of the higher vibrational mode shapes are shown in [Figure 11&#8211;8](ch11s03.html#gss-eigenmodes).

> **Figure:**

Figure 11&#8211;8 Shapes of eigenmodes 3 through 6; corresponding mode shapes lie in planes orthogonal to each other.

The natural frequency associated with each eigenmode is reported in the plot title. The lowest natural frequency of the pipe section when the 4&nbsp;MN tensile load is applied is 47.1&nbsp;Hz. The tensile loading has increased the stiffness of the pipe and, thus, increased the vibrational frequencies of the pipe section. This lowest natural frequency is within the frequency range of the harmonic loads; therefore, resonance of the pipe may be a problem when it is used with this loading.

You, therefore, need to continue the simulation and apply additional tensile load to the pipe section until you find the magnitude that raises the natural frequency of the pipe section to an acceptable level. Rather than repeating the analysis and increasing the applied axial load, you can use the restart capability in Abaqus to continue the load history of a prior simulation in a new analysis.

### 11.4&nbsp;Restart analysis

Multistep simulations need not be defined in a single job. Indeed, it is usually desirable to run a complex simulation in stages. This allows you to examine the results and confirm that the analysis is performing as expected before continuing with the next stage. The Abaqus restart analysis capability allows a simulation to be restarted and the model's response to additional load history to be calculated.

The restart analysis capability is discussed in detail in &#8220;Restarting an analysis,&#8221;  Section 9.1.1 of the Abaqus Analysis User's Guide.### 11.4.1&nbsp;The restart and state files

The Abaqus/Standard restart (.res) file and the Abaqus/Explicit state (.abq) file contain the information necessary to continue a previous analysis. In Abaqus/Explicit the package (.pac) file and the selected results (.sel) file are also used for restarting an analysis and must be saved upon completion of the first job. In addition, both products require the output database (.odb) file. Restart files can become very large for large models; when restart data are requested, they are written for every increment or interval by default. Thus, it is important to control the frequency at which restart data are written. Sometimes it is useful to allow data to be overwritten on the restart file during a step. This means that at the end of the analysis there is only one set of restart data for each step, corresponding to the state of the model at the end of each step. However, if the analysis is interrupted for some reason, such as a computer malfunction, the analysis can be continued from the point where restart data were last written.### 11.4.2&nbsp;Restarting an analysis

When restarting a simulation using the results of a previous analysis, you specify the particular point in the simulation's load history from which to restart the analysis. The model used in the restart analysis, however, must be the same as the model used in the original analysis up to the restart location. Specifically,

-

the restart analysis model must not modify or add any geometry, mesh, materials, sections, beam section profiles, material orientations, beam section orientations, interaction properties, or constraints that are already defined in the original analysis model; and

-

similarly, it must not modify any step, load, boundary condition, predefined field, or interaction at or before the restart location.

You may, however, define new sets and amplitude curves in the restart analysis model.

**Continuing an interrupted run**

The restart analysis continues directly from the specified step and increment of the previous analysis. If the given step and increment do not correspond to the end of the previous analysis (for example, if the analysis was interrupted by a computer malfunction), Abaqus will try to finish the original step before trying to simulate any new steps.

In Abaqus/Explicit in cases where restart is being performed simply to continue a long step (which might have been terminated because the time limit for the job was exceeded, for example), you can restart the run by using the Recover job type as shown in [Figure 11&#8211;9](ch11s04.html#gsi-multi-recover).

> **Figure:**

Figure 11&#8211;9 Recover job type.

**Continuing with additional steps**

If the previous analysis completed successfully and, having viewed the results, you want to add additional steps to the load history, the specified step and increment should be the last step and last increment of the previous analysis.

**Changing an analysis**

Sometimes, having viewed the results of the previous analysis, you may want to restart the analysis from an intermediate point and change the remaining load history in some manner&#8212;for example, to add more output requests, to change the loading, or to adjust the analysis controls. This can be necessary, for example, when a step has exceeded its maximum number of increments. If an analysis is restarted because the maximum number of increments has been exceeded, Abaqus/Standard thinks that the analysis is partway through a step, tries to complete the step, and promptly exceeds the maximum number of increments again.

In such situations you should indicate that the current step should be terminated at the specified step and increment. The simulation may then continue with the new steps. For example, if a step allowed only a maximum of 20 increments, which was less than the number necessary to complete the step, a new step should be defined in which the entire step definition, including applied loads and boundary conditions, is identical to that specified in the original run with the following exceptions:

-

The number of increments should be increased.

-

The total time of the new step should be the total time of the original step less the time completed in the first run. For example, if the time of the step as originally specified was 100 seconds and the analysis ran out of increments at a step time of 20 seconds, the duration of the step in the restart analysis should be 80 seconds.

-

Any amplitude definitions specified in terms of step time need to be respecified to reflect the new time scale of the step. Amplitude definitions specified in terms of total time do not need to be changed, provided the modifications given above are used.

The magnitudes of any loads or prescribed boundary conditions remain unchanged since they are always total values in general analysis steps.

### 11.5&nbsp;Example: restarting the pipe vibration analysis

To demonstrate how to restart an analysis, take the pipe section example in &#8220;Example: vibration of a piping system,&#8221;  Section 11.3, and restart the simulation, adding two additional steps of load history. The first simulation predicted that the piping section would be vulnerable to resonance when extended axially; you must now determine how much additional axial load will increase the pipe's lowest vibrational frequency to an acceptable level.

Step&nbsp;3 will be a general step that increases the axial load on the pipe to 8&nbsp;MN, and Step&nbsp;4 will calculate the eigenmodes and eigenfrequencies again.### 11.5.1&nbsp;Creating a restart analysis model

Open the model database file Pipe.cae (if it is not already open). Copy the model named Original to a model named Restart. The modifications to this model are discussed next. If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: restarting the pipe vibration analysis,&#8221;  Section 11.5 of Getting Started with Abaqus: Keywords Edition.

**Model attributes**

To perform a restart analysis, the model's attributes must be changed to indicate that the model should reuse data from a previous analysis. In the Model Tree, double-click the Restart model underneath the Models container. In the Edit Model Attributes dialog box that appears, specify that restart data will be read from the job Pipe and that the restart location will be the end of step Frequency I.

**Step definitions**

You will now create two new analysis steps. The first new step is a general static step; name the step Pull II, and insert it immediately after the step Frequency I. Give the step the following description: Apply axial tensile load of 8.0 MN; and set the time period for the step to 1.0 and the initial time increment to 0.1.

The second new step is a frequency extraction step; name the step Frequency II, and insert it immediately after the step Pull II. Give the step the following description: Extract modes and frequencies; and use the Lanczos eigensolver to extract the first 8 natural modes and frequencies of the pipe.

**Output requests**

For the step Pull II, write data to the restart file every 10 increments.

Accept all other default output data requests.

**Load definition**

Modify the load definition so that the tensile load that is applied to the pipe is doubled in the second general static step (Pull II). To do this, expand the Force item underneath the Loads container in the Model Tree. In the list that appears, expand the States item. Double-click the step named Pull II, and change the value of the applied force to 8.0E+06 in this step.

**Job definition**

Create a job named PipeRestart with the following description: Restart analysis of a 5 meter long pipe under tensile load. Set the job type to Restart if it is not already. (If the job type is not set to Restart, Abaqus/CAE ignores the model's restart attributes.)

Save your model in a model database file, and submit the job for analysis. Monitor the solution progress; correct any modeling errors and investigate the source of any warning messages, taking corrective action as necessary.### 11.5.2&nbsp;Monitoring the job

Again, check the Job Monitor as the job is running. When the analysis completes, its contents will look similar to [Figure 11&#8211;10](ch11s05.html#gsi-pipe-restart-monitor).

> **Figure:**

Figure 11&#8211;10 Job Monitor: restart pipe vibration analysis.

This analysis starts at Step&nbsp;3 since Steps&nbsp;1 and 2 were completed in the previous analysis. There are now two output database (.odb) files associated with this simulation. Data for Steps&nbsp;1 and 2 are in the file Pipe.odb; data for Steps&nbsp;3 and 4 are in the file PipeRestart.odb. When plotting results, you need to remember which results are stored in each file, and you need to ensure that Abaqus/CAE is using the correct output database file.### 11.5.3&nbsp;Postprocessing the restart analysis results

Switch to the Visualization module, and open the output database file from the restart analysis, PipeRestart.odb.

**Plotting the eigenmodes of the pipe**

Plot the same six eigenmode shapes of the pipe section for this simulation as were plotted in the previous analysis. The eigenmode shapes can be plotted using the procedures described for the original analysis. These eigenmodes and their natural frequencies are shown in [Figure 11&#8211;11](ch11s05.html#gss-internalpress); again, the corresponding mode shapes lie in planes orthogonal to each other.

> **Figure:**

Figure 11&#8211;11 Shapes and frequencies of eigenmodes 1 through 6 with 8 MN tensile load.

Under 8&nbsp;MN of axial load, the lowest mode is now at 53.1&nbsp;Hz, which is greater than the required minimum of 50&nbsp;Hz. If you want to find the exact load at which the lowest mode is just above 50&nbsp;Hz, you can repeat this restart analysis and change the value of the applied load.

Plotting X&#8211;Y graphs from field data for selected steps

Use the field data stored in the output database files, Pipe.odb and PipeRestart.odb, to plot the history of the axial stress in the pipe for the whole simulation.

**To generate a history plot of the axial stress in the pipe for the restart analysis:**

-

In the Results Tree, double-click XYData.

The Create XY Data dialog box appears.

-

Select ODB field output from this dialog box, and click Continue to proceed.

The XY Data from ODB Field Output dialog box appears.

-

In the Variables tabbed page of this dialog box, accept the default selection of Integration Point for the variable position and select S11 from the list of available stress components.

-

At the bottom of the dialog box, toggle Select for the section point and click Settings to choose a section point.

-

In the Field Report Section Point Settings dialog box that appears, select the category beam and choose any of the available section points for the pipe cross-section. Click OK to exit this dialog box.

-

In the Elements/Nodes tabbed page of the XY Data from ODB Field Output dialog box, select Element labels as the selection Method. There are 30 elements in the model, and they are numbered consecutively from 1 to 30. Enter any element number (for example, 25) in the Element labels text field that appears on the right side of the dialog box.

-

Click Active Steps/Frames, and select Pull II  as the only step from which to extract data.

-

At the bottom of the XY Data from ODB Field Output dialog box, click Plot to see the history of axial stress in the element.

The plot traces the axial stress history at each integration point of the element in the restart analysis. Since the restart is a continuation of an earlier job, it is often useful to view the results from the entire (original and restarted) analysis.

**To generate a history plot of the axial stress in the pipe for the entire analysis:**

-

Save the current plot by clicking Save at the bottom of the XY Data from ODB Field Output dialog box. Two curves are saved (one for each integration point), and default names are given to the curves.

-

Rename either curve RESTART, and delete the other curve.

-

From the main menu bar, select FileOpen; or use the  tool in the File toolbar to open the file Pipe.odb.

-

Following the procedure outlined above, save the plot of the axial stress history for the same element and integration/section point used above. Name this plot ORIGINAL.

-

In the Results Tree, expand the XYData container.

The ORIGINAL and RESTART curves are listed underneath.

-

Select both plots with [Ctrl]+Click. Click mouse button 3, and select Plot from the menu that appears to create a plot of axial stress history in the pipe for the entire simulation.

-

To change the style of the line, open the Curve Options dialog box.

-

For the RESTART curve, select a dotted line style.

-

Click Dismiss to close the dialog box.

-

To change the axis titles, open the Axis Options dialog box.

In this dialog box, switch to the Title tabbed page.

-

Change the X-axis title to TOTAL TIME, and change the Y-axis title to STRESS S11.

-

Click Dismiss to close the dialog box.

The plot created by these commands is shown in [Figure 11&#8211;12](ch11s05.html#gss-history-v). The axial stress history of the same element during Step&nbsp;3 can be plotted by itself by selecting only the RESTART curve (see [Figure 11&#8211;13](ch11s05.html#gss-hist-step3-v)).

> **Figure:**

Figure 11&#8211;12 History of axial stress in the pipe.

> **Figure:**

Figure 11&#8211;13 History of axial stress in the pipe during Step 3.

### 11.6&nbsp;Related Abaqus examples

-

&#8220;Deep drawing of a cylindrical cup,&#8221;  Section 1.3.4 of the Abaqus Example Problems Guide

-

&#8220;Linear analysis of the Indian Point reactor feedwater line,&#8221;  Section 2.2.2 of the Abaqus Example Problems Guide

-

&#8220;Vibration of a cable under tension,&#8221;  Section 1.4.3 of the Abaqus Benchmarks Guide

-

&#8220;Random response to jet noise excitation,&#8221;  Section 1.4.10 of the Abaqus Benchmarks Guide

### 11.7&nbsp;Summary

-

An Abaqus simulation can include any number of steps.

-

Implicit and explicit steps are not allowed in the same analysis job.

-

An analysis step is a period of &#8220;time&#8221; during which the response of the model to a specified set of loads and boundary conditions is calculated. The character of this response is determined by the particular analysis procedure used during the step.

-

The response of a structure in a general analysis step may be either linear or nonlinear.

-

The starting condition for each general step is the ending condition of the previous general step. Thus, the model's response evolves during a sequence of general steps in a simulation.

-

Linear perturbation steps (available only in Abaqus/Standard) calculate the linear response of the structure to a perturbation load. The response is reported relative to the base state defined by the condition of the model at the end of the last general step.

-

Analyses can be restarted as long as a restart file is saved. Restart files can be used to continue an interrupted analysis or to add additional load history to the simulation.