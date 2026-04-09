
7. Linear Dynamics
../images/blu4rule.gif

A static analysis is sufficient if you are interested in the long-term response of a structure to applied loads. However, if the duration of the applied load is short (such as in an earthquake) or if the loading is dynamic in nature (such as that from rotating machinery), you must perform a dynamic analysis. This chapter discusses linear dynamic analysis in Abaqus/Standard; see [Chapter 9, "Nonlinear Explicit Dynamics](ch09.html)," for a discussion of nonlinear dynamic analysis in Abaqus/Explicit.


---


7.1 Introduction
../images/blu4rule.gif

A dynamic simulation is one in which inertia forces are included in the dynamic equation of equilibrium:

../graphics/gsa_eqn00059.gifwhere

*M*

is the mass of the structure,

../graphics/gsa_eqn00060.gif

is the acceleration of the structure,

*I*

are the internal forces in the structure, and

*P*

are the applied external forces.The expression in the equation shown above is nothing more than Newton's second law of motion (../graphics/gsa_eqn00061.gif).

The inclusion of the inertial forces (../graphics/gsa_eqn00062.gif) in the equation of equilibrium is the major difference between static and dynamic analyses. Another difference between the two types of simulations is in the definition of the internal forces, *I*. In a static analysis the internal forces arise only from the deformation of the structure; in a dynamic analysis the internal forces contain contributions created by both the motion (i.e., damping) and the deformation of the structure.7.1.1 Natural frequencies and mode shapes
../images/blu4rule.gif

The simplest dynamic problem is that of a mass oscillating on a spring, as shown in [Figure 7-1](ch07s01.html#gss-mass-spring).

**Figure 7-1** Mass-spring system.

../graphics/gss-mass-spring-nls.png

The internal force in the spring is given by ../graphics/gsa_eqn00063.gif so that its dynamic equation of motion is

../graphics/gsa_eqn00064.gifThis mass-spring system has a *natural frequency* (in radians/time) given by

../graphics/gsa_eqn00065.gif

If the mass is moved and then released, it will oscillate at this frequency. If the force is applied at this frequency, the amplitude of the displacement will increase dramatically--a phenomenon known as resonance.

Real structures have a large number of natural frequencies. It is important to design structures in such a way that the frequencies at which they may be loaded are not close to the natural frequencies. The natural frequencies can be determined by considering the dynamic response of the unloaded structure (../graphics/gsa_eqn00066.gif in the dynamic equilibrium equation). The equation of motion is then

../graphics/gsa_eqn00067.gifFor an undamped system ../graphics/gsa_eqn00068.gif, so

../graphics/gsa_eqn00069.gifSolutions to this equation have the form

../graphics/gsa_eqn00070.gifSubstituting this into the equation of motion yields the *eigenvalue* problem

../graphics/gsa_eqn00071.gifwhere ../graphics/gsa_eqn00072.gif.

This system has *n* eigenvalues, where *n* is the number of degrees of freedom in the finite element model. Let ../graphics/gsa_eqn00073.gif be the *j*th eigenvalue. Its square root, ../graphics/gsa_eqn00074.gif, is the *natural frequency* of the *j*th mode of the structure, and ../graphics/gsa_eqn00075.gif is the corresponding *j*th *eigenvector*. The eigenvector is also known as the *mode shape* because it is the deformed shape of the structure as it vibrates in the *j*th mode.

The frequency extraction procedure in Abaqus/Standard is used to determine the modes and frequencies of the structure. This procedure is easy to use in that you need only specify the number of modes required or the maximum frequency of interest.7.1.2 Modal superposition
../images/blu4rule.gif

The natural frequencies and mode shapes of a structure can be used to characterize its dynamic response to loads in the linear regime. The deformation of the structure can be calculated from a combination of the mode shapes of the structure using the *modal superposition* technique. Each mode shape is multiplied by a scale factor. The vector of displacements in the model, *u*, is defined as

../graphics/gsa_eqn00076.gifwhere ../graphics/gsa_eqn00077.gif is the modal displacement and ../graphics/gsa_eqn00078.gif is the generalized coordinate of mode *i*. This technique is valid only for simulations with small displacements, linear elastic materials, and no contact conditions--in other words, linear problems.

In structural dynamic problems the response of a structure usually is dominated by a relatively small number of modes, making modal superposition a particularly efficient method for calculating the response of such systems. Consider a model containing 10,000 degrees of freedom. Direct integration of the dynamic equations of motion would require the solution of 10,000 simultaneous equations at each point in time. If the structural response is characterized by 100 modes, only 100 equations need to be solved every time increment. Moreover, the modal equations are uncoupled, whereas the original equations of motion are coupled. There is an initial cost in calculating the modes and frequencies, but the savings obtained in the calculation of the response greatly outweigh the cost.

If nonlinearities are present in the simulation, the natural frequencies may change significantly during the analysis, and modal superposition cannot be employed. In this case direct integration of the dynamic equation of equilibrium is required, which is much more expensive than modal analysis.

A problem should have the following characteristics for it to be suitable for linear transient dynamic analysis:

-

The system should be linear: linear material behavior, no contact conditions, and no nonlinear geometric effects.
-

The response should be dominated by relatively few frequencies. As the frequency content of the response increases, such as is the case in shock and impact problems, the modal superposition technique becomes less effective.
-

The dominant loading frequencies should be in the range of the extracted frequencies to ensure that the loads can be described accurately.
-

The initial accelerations generated by any suddenly applied loads should be described accurately by the eigenmodes.
-

The system should not be heavily damped.


---


7.2 Damping
../images/blu4rule.gif

If an undamped structure is allowed to vibrate freely, the magnitude of the oscillation is constant. In reality, however, energy is dissipated by the structure's motion, and the magnitude of the oscillation decreases until the oscillation stops. This energy dissipation is known as damping. Damping is usually assumed to be viscous or proportional to velocity. The dynamic equilibrium equation can be rewritten to include damping as

../graphics/gsa_eqn00059.gif

../graphics/gsa_eqn00079.gifwhere

*C*

is the damping matrix for the structure and

../graphics/gsa_eqn00080.gif

is the velocity of the structure.

The dissipation of energy is caused by a number of effects, including friction at the joints of the structure and localized material hysteresis. Damping is a convenient way of including the important absorption of energy without modeling the effects in detail.

In Abaqus/Standard the eigenmodes are calculated for the undamped system, yet most engineering problems involve some kind of damping, however small. The relationship between the damped natural frequency and the undamped natural frequency for each mode is

../graphics/gsa_eqn00081.gifwhere

../graphics/gsa_eqn00082.gif

is the damped eigenvalue,

../graphics/gsa_eqn00083.gif

is the damping ratio, which is the fraction of critical damping,

*c*

is the damping of that mode shape, and

../graphics/gsa_eqn00084.gif

is the critical damping.

The eigenfrequencies of the damped system are very close to the corresponding quantities for the undamped system for small values of ../graphics/gsa_eqn00085.gif (../graphics/gsa_eqn00086.gif < 0.1). As ../graphics/gsa_eqn00085.gif increases, the undamped eigenfrequencies become less accurate; and as ../graphics/gsa_eqn00085.gif approaches 1, the use of undamped eigenfrequencies becomes invalid.

If a structure is critically damped (../graphics/gsa_eqn00087.gif), after any disturbance it will return to its initial static configuration as quickly as possible without overshooting ([Figure 7-2](ch07s02.html#gss-damping-v)).

**Figure 7-2** Damped motion patterns for various values of ../graphics/gsa_eqn00086.gif.

../graphics/gss-damping-v-nls.png7.2.1 Definition of damping in Abaqus/Standard
../images/blu4rule.gif

In Abaqus/Standard a number of different types of damping can be defined for a transient modal analysis: direct modal damping, Rayleigh damping, and composite modal damping.

Damping is defined for modal dynamic procedures. The damping is part of the step definition, and different amounts of damping can be defined for each mode.

**Direct modal damping**

The fraction of critical damping, ../graphics/gsa_eqn00085.gif, associated with each mode can be defined using direct modal damping. Typically, values in the range of 1% to 10% of critical damping are used. Direct modal damping allows you to define precisely the damping of each mode of the system.

**Rayleigh damping**

In Rayleigh damping the assumption is made that the damping matrix is a linear combination of the mass and stiffness matrices,

../graphics/gsa_eqn00088.gifwhere ../graphics/gsa_eqn00089.gif and ../graphics/gsa_eqn00090.gif are user-defined constants. Although the assumption that the damping is proportional to the mass and stiffness matrices has no rigorous physical basis, in practice the damping distribution rarely is known in sufficient detail to warrant any other more complicated model. In general, this model ceases to be reliable for heavily damped systems; that is, above approximately 10% of critical damping. As with the other forms of damping, you can define precisely the Rayleigh damping of each mode of the system.

For a given mode *i*, the damping ratio, ../graphics/gsa_eqn00091.gif, and the Rayleigh damping values, ../graphics/gsa_eqn00089.gif and ../graphics/gsa_eqn00090.gif, are related through

../graphics/gsa_eqn00092.gif

**Composite damping**

In composite damping a fraction of critical damping is defined for each material, and a composite damping value is found for the whole structure. This option is useful when many different materials are present in the structure. Composite damping is not discussed further in this guide.7.2.2 Choosing damping values
../images/blu4rule.gif

In most linear dynamic problems the proper specification of damping is important to obtain accurate results. However, damping is approximate in the sense that it models the energy absorbing characteristics of the structure without attempting to model the physical mechanisms that cause them. Therefore, it is difficult to determine the damping data required for a simulation. Occasionally, you may have data available from dynamic tests, but often you will have to work with data gleaned from references or experience. In such cases you should be very cautious in interpreting the results, and you should use parametric studies to assess the sensitivity of the simulation to damping values.


---


7.3 Element selection
../images/blu4rule.gif

Virtually all of the elements in Abaqus can be used in dynamic analyses. In general the rules for selecting the elements are the same as those for static simulations. However, for simulations of impact and blast loading, first-order elements should be used. They have a lumped mass formulation, which is better able to model the effect of stress waves than the consistent mass formulation used in the second-order elements.


---


7.4 Mesh design for dynamics
../images/blu4rule.gif

When you are designing meshes for dynamic simulations, you need to consider the mode shapes that will be excited in the response and use a mesh that is able to represent those mode shapes adequately. This means that a mesh that is adequate for a static simulation may be unsuitable for calculating the dynamic response to loading that excites high frequency modes.

Consider, for example, the plate shown in [Figure 7-3](ch07s04.html#gss-coarse-mesh). The mesh of first-order shell elements is adequate for a static analysis of the plate under a uniform load and is also suitable for the prediction of the first mode shape. However, the mesh is clearly too coarse to be able to model the sixth mode accurately.

**Figure 7-3** Vibration frequencies and corresponding mode shapes of the plate based on the coarse mesh.

../graphics/gss-coarse-mesh-nls.png

[Figure 7-4](ch07s04.html#gss-fine-mesh) shows the same plate modeled with a refined mesh of first-order elements. The displaced shape for the sixth mode now looks much better, and the frequency predicted for this mode is more accurate. If the dynamic loading on the plate is such that there is significant excitation of this mode, the refined mesh must be used; the results from the coarse mesh will not be accurate.

**Figure 7-4** Vibration frequencies and corresponding mode shapes of the plate based on the fine mesh.

../graphics/gss-fine-mesh-nls.png


---


7.5 Example: cargo crane under dynamic loading
../images/blu4rule.gif

This example uses the same cargo crane that you analyzed in ["Example: cargo crane,"  Section 6.4](ch06s04.html), but you have now been asked to investigate what happens when a load of 10 kN is dropped onto the lifting hook for 0.2 seconds. The connections at points *A*, *B*, *C*, and *D* (see [Figure 7-5](ch07s05.html#gss-cargo)) can only withstand a maximum pull-out force of 100 kN. You have to decide whether or not any of these connections will break.

**Figure 7-5** Cargo crane.

../graphics/gss-cargo.png

The short duration of the loading means that inertia effects are likely to be important, making dynamic analysis essential. You are not given any information regarding the damping of the structure. Since there are bolted connections between the trusses and the cross bracing, the energy absorption caused by frictional effects is likely to be significant. Based on experience, you therefore choose 5% of critical damping in each mode.

The magnitude of the applied load versus time is shown in [Figure 7-6](ch07s05.html#gss-load-time-v).

**Figure 7-6** Load-time characteristic.

../graphics/gss-load-time-v-nls.png

Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in ["Cargo crane - dynamic loading,"  Section A.5](ap01s05.html). Instructions on how to fetch the script and run it within Abaqus/CAE are given in [Appendix A, "Example Files](ap01.html)."
-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins**../images/arrow.gif**Abaqus**../images/arrow.gif**Getting Started**; highlight **Cargo crane dynamic loading**; and click **Run**. For more information about the Getting Started plug-ins, see "Running the Getting Started with Abaqus examples,"  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in "Example: cargo crane under dynamic loading,"  Section 7.5 of Getting Started with Abaqus: Keywords Edition.7.5.1 Modifications to the model
../images/blu4rule.gif

Open the model database file `Crane.cae`, and copy the `Static` model to a model named `Dynamic`. The dynamic analysis model is basically the same as the static analysis model, except for the modifications described below.

**Material**

In dynamic simulations the density of every material must be specified so that the mass matrix can be formed. The steel in the crane has a density of 7800 kg/m^3.

In this model the material properties were specified as part of the section definition. Thus, you will need to edit the `BracingSection` and `MainMemberSection` section definitions to specify the density. In the **Specify section material density** field of the **Edit Beam Section** dialog box, enter a value of `7800` for each section definition.

Note:
If material data are defined independently of the section properties, the density is included by editing the material definition and selecting **General**../images/arrow.gif**Density** in the **Edit Material** dialog box.

**Steps**

The step definitions that are used for the dynamic analysis are substantially different from those used in the static analysis. Therefore, the static step created previously will be replaced by two new steps.

The first step in the dynamic analysis calculates the natural frequencies and mode shapes of the structure. The second step then uses these data to calculate the transient modal dynamic response of the cargo crane. In this analysis we will assume that everything is linear. If you want to model any nonlinearities in this simulation, direct integration of the equations of motion using the implicit dynamic procedure must be performed instead. See ["Nonlinear dynamics,"  Section 7.9.2](ch07s09.html#gsa-dyn-nonlindyn), for further details.

Abaqus/Standard offers the Lanczos and the subspace iteration eigenvalue extraction methods. The Lanczos method is generally faster when a large number of eigenmodes is required for a system with many degrees of freedom. The subspace iteration method may be faster when only a few (less than 20) eigenmodes are needed.

We use the Lanczos eigensolver in this analysis and request 30 eigenvalues. Instead of specifying the number of modes required, it is also possible to specify the minimum and maximum frequencies of interest so that the step will complete once Abaqus/Standard has found all of the eigenvalues inside the specified range. A shift point may also be specified so that eigenvalues nearest the shift point will be extracted. By default, no minimum or maximum frequency or shift is used. If the structure is not constrained against rigid body modes, the shift value should be set to a small negative value to remove numerical problems associated with rigid body motion.

**To replace the static step with a frequency extraction step:**

-

In the Model Tree, expand the **Steps** container. Then, click mouse button 3 on the step named **Tip Load** and select **Replace** from the menu that appears. In the **Replace Step** dialog box, select **Frequency** from the list of available **Linear perturbation** procedures.

Model attributes that cannot be converted will be deleted. In this case the concentrated loads are deleted because they cannot be used in a frequency extraction step. However, the boundary conditions and output requests associated with the static step are inherited by the frequency extraction step.
-

In the **Basic** tabbed page of the **Edit Step** dialog box, enter the step description `First 30 modes`; accept the Lanczos eigensolver option; and request 30 eigenvalues.
-

Rename the step to `Extract Frequencies` by clicking mouse button 3 on the name `Tip Load` and selecting **Rename** from the menu that appears.

In structural dynamic analysis the response is usually associated with the lower modes. However, enough modes should be extracted to provide a good representation of the dynamic response of the structure. One way of checking that a sufficient number of eigenvalues has been extracted is to look at the total effective mass in each degree of freedom, which indicates how much of the mass is active in each direction of the extracted modes. The effective masses are tabulated in the data file under the eigenvalue output. Ideally, the sum of the modal effective masses for each mode in each direction should be at least 90% of the total mass. See ["Effect of the number of modes,"  Section 7.6](ch07s06.html), for more information.

The modal dynamics procedure will be used to perform the transient dynamic analysis. The transient response will be based on all the modes extracted in the first analysis step; 5% of critical damping should be used in all 30 modes.

**To create a transient modal dynamics step:**

-

In the Model Tree, double-click the **Steps** container to create a new step. Select **Modal dynamics** from the list of available **Linear perturbation** procedures, and name the step `Transient modal dynamics`. Insert the step after the frequency extraction step defined above.
-

In the **Basic** tabbed page of the **Edit Step** dialog box, enter the description `Crane Response to Dropped Load` and specify a time period of `0.5` and a time increment of `0.005`. In dynamic analysis time is a real, physical quantity.
-

In the **Damping** tabbed page of the **Edit Step** dialog box, specify direct modal damping and enter a critical damping fraction of `0.05` for modes `1` through `30`.

**Output**

Using the **Field Output Requests Manager**, modify the field output requests for the `Extract Frequencies` step so that the **Preselected defaults** are selected. By default, Abaqus/Standard writes the mode shapes to the output database (`.odb`) file so that they can be plotted using the Visualization module. The nodal displacements for each mode shape are normalized so that the maximum displacement is unity. Thus, these results, and the corresponding stresses and strains, are not physically meaningful: they should be used only for relative comparisons.

Dynamic analyses usually require many more increments than static analyses to complete. As a consequence, the volume of output from dynamic analyses can be very large, and you should control the output requests to keep the output files to a reasonable size. In this example you will request output of the deformed shape to the output database file at the end of every fifth increment. There will be 100 increments in the step (0.5/0.005); therefore, there will be 20 frames of field output.

In addition, you will write the displacements at the loaded end of the model (for example, set `Tip-a`) and the reaction forces at the fixed end (set `Attach`) as history data to the output database file every increment so that a higher resolution of these data will be available. In dynamic analyses we are also concerned about the energy distribution in the model and what form the energy takes. Kinetic energy is present in the model as a result of the motion of the mass; strain energy is present as a result of the displacement of the structure; energy is also dissipated through damping. By default, whole model energies are written as history data to the `.odb` file for the modal dynamic procedure. For this analysis you will restrict the energy output to the kinetic, internal, and viscous dissipation energies.

**To request output for the transient modal dynamics analysis step:**

-

Open the **Field Output Requests Manager**. Select the cell labeled `Created` that appears in the column labeled **Transient modal dynamics** (you may need to enlarge the column to see the complete step name).
-

Edit the field output request so that only the nodal displacements are written to the `.odb` file every `5` increments.
-

Open the **History Output Requests Manager**. Edit the default output request so that only ALLIE, ALLKE, and ALLVD are written after every increment. In addition, create two new output requests in the step labeled `Transient modal dynamics`. In the first write the displacements (translations only) for the set `Tip-a` after every increment; in the second, the reaction forces (not the moments) for the set `Attach` after every increment.

**Loads and boundary conditions**

The boundary conditions are the same as for the static analysis. Since these were retained during the step replacement operation, no new boundary conditions need to be defined.

Apply a concentrated force to the tip of the crane. The magnitude of this load is time dependent, as illustrated in [Figure 7-6](ch07s05.html#gss-load-time-v). The time dependence of the load can be defined using an amplitude curve. The actual magnitude of the load applied at any point in time is obtained by multiplying the magnitude of the load (10,000 N) by the value of the amplitude curve at that time.

**To specify a time-dependent load:**

-

Begin by defining an amplitude curve. In the Model Tree, double-click the **Amplitudes** container. Name the amplitude `Bounce`, and choose the type **Tabular**. Enter the data shown in [Table 7-1](ch07s05.html#gss-dyncrane-amp) in the **Edit Amplitude** dialog box. Accept the default selection of **Step time** as the time span, and specify `0.25` as the smoothing parameter value.

Tip:
Use mouse button 3 to access the table options.

**Table 7-1** Amplitude curve data.

-

Now define the load.  In the Model Tree, double-click the **Loads** container. Apply the load in the `Transient modal dynamics` step, name the load `Dyn load`, and choose **Concentrated force** as the load type. Apply the load to set `Tip-b`. The equation constraint defined previously between sets `Tip-a` and `Tip-b` means that the load will be carried equally by both halves of the crane.
-

In the **Edit Load** dialog box, enter a value for **CF2** of `-1.E4`, and choose `Bounce` for the amplitude.

In this example the structure has no initial velocities or accelerations, which is the default. However, if you wanted to define initial velocities, you could do so by selecting **Predefined Field**../images/arrow.gif**Create** from the main menu bar and assigning initial translational velocities to selected regions of the model in the initial step. You would also have to edit the definition of the modal dynamics step to use initial conditions.

**Running the analysis**

Create a job named `DynCrane` with the following description: `3-D model of light-service cargo crane dynamic analysis`.

Save your model in a model database file, and submit the job for analysis. Monitor the solution progress; correct any modeling errors that are detected and investigate the cause of any warning messages, taking action as necessary.7.5.2 Results
../images/blu4rule.gif

The **Job Monitor** gives a brief summary of the automatic time incrementation used in the analysis for each increment. The information is written as soon as the increment is completed, so that you can monitor the analysis as it is running. This facility is useful in large, complex problems. The information given in the **Job Monitor** is the same as that given in the status file (`DynCrane.sta`).

Examine the **Job Monitor** and the printed output data file (`DynCrane.dat`) to evaluate the analysis results.

**Job monitor**

In the **Job Monitor**, the first column shows the step number and the second column gives the increment number. The sixth column shows the number of iterations Abaqus/Standard needed to obtain a converged solution in each increment. Looking at the contents of the **Job Monitor**, we can see that the time increment associated with the single increment in Step 1 is very small. This step uses no time, because time is not relevant in a frequency extraction procedure.

The output for Step 2 shows that the time increment size is constant throughout the step and that each increment requires only one iteration. The bottom of the **Job Monitor** is shown in [Figure 7-7](ch07s05.html#gsi-dyncrane-monitor).

**Figure 7-7** Bottom portion of the **Job Monitor**: cargo crane dynamic analysis.

../graphics/gsi-dyncrane-monitor-nls.png

**Data file**

Click the **Data File** tab in the **Job Monitor** to display the data file in a tabbed page at the bottom of the dialog box. The primary results for Step 1 are the extracted eigenvalues, participation factors, and effective mass, as shown below.```
E I G E N V A L U E    O U T P U T

MODE NO    EIGENVALUE       FREQUENCY           GENERALIZED MASS  COMPOSITE MODAL DAMPING
(RAD/TIME) (CYCLES/TIME)

1       1773.4     42.112     6.7023       151.92           0.0000
2       7016.8     83.766     13.332       30.206           0.0000
3       7644.1     87.431     13.915       90.400           0.0000
4       22999.     151.65     24.136       250.64           0.0000
5       24714.     157.21     25.020       275.88           0.0000
6       34811.     186.58     29.695       493.15           0.0000
7       42748.     206.76     32.906       1106.4           0.0000
8       46473.     215.58     34.310       86.173           0.0000
9       47446.     217.82     34.667       2577.2           0.0000
10       56050.     236.75     37.680       3569.2           0.0000
....
25     2.26885E+05  476.32     75.809       207.46           0.0000
26     2.42798E+05  492.75     78.423       127.02           0.0000
27     2.84057E+05  532.97     84.825       1240.8           0.0000
28     2.92450E+05  540.79     86.069       330.74           0.0000
29     3.13943E+05  560.31     89.176       272.39           0.0000
30     3.64774E+05  603.97     96.124       64.971           0.0000

```The highest frequency extracted is 96 Hz. The period associated with this frequency is 0.0104 seconds, which is comparable to the fixed time increment of 0.005 seconds. There is no point in extracting modes whose period is substantially smaller than the time increment used. Conversely, the time increment must be capable of resolving the highest frequencies of interest.

The column for generalized mass lists the mass of a single degree of freedom system associated with that mode.

The table of participation factors indicates the predominant degrees of freedom in which the modes act. The results indicate, for example, that mode 1 acts predominantly in the 3-direction.```
P A R T I C I P A T I O N   F A C T O R S

MODE NO    X-COMPONENT    Y-COMPONENT    Z-COMPONENT    X-ROTATION     Y-ROTATION     Z-ROTATION

1     -6.11696E-04   -6.14521E-03     1.4284        0.71335        -6.0252       -3.37773E-02
2      0.18470       -0.25677        8.31954E-04    1.68388E-03   -6.05012E-03    -1.6826
3     -0.17440         1.5515        4.88123E-03   -8.04039E-03    3.24495E-02     9.2746
4     -8.68256E-05   -9.61259E-03    8.23615E-02    0.21604         1.2334       -2.97905E-02
5     -3.80675E-03    1.13829E-03   -3.04304E-02   -0.59220         1.7593       -2.20144E-02
6      3.71618E-02   -0.35674        6.05241E-03   -1.67946E-02    6.71292E-03   -0.96432
7     -2.48508E-03   -1.58332E-03    6.19821E-02    5.09235E-02   -0.29901       -6.65849E-04
8     -7.03851E-02    2.31655E-02    0.72459        0.49275        -3.8778        6.69085E-02
9      3.59820E-02   -2.34811E-02    2.23695E-02    1.47243E-02   -0.12808        6.65955E-04
10      3.48679E-02    4.02884E-02    1.96398E-02    1.09545E-02   -6.84066E-02    3.72037E-02
....
25     -8.25375E-02   -0.22218       -3.54545E-02    3.39238E-02   -2.18245E-02   -0.18688
26     -1.98905E-02   -0.35111        4.61269E-02   -2.12563E-02   -1.27532E-02   -0.18939
27      1.71772E-02    2.51340E-02    2.26524E-02   -1.02593E-02   -4.31559E-02    2.78870E-02
28      4.73352E-02    2.79265E-02   -0.11860        5.19825E-02    0.24175       -1.12541E-04
29      9.83488E-03   -3.64823E-03    4.65504E-03   -3.17284E-03   -1.56708E-02   -2.82848E-03
30      4.83733E-02    1.85495E-02    0.13426       -2.21861E-02   -0.35882       -1.87612E-02

```The table of effective mass indicates the amount of mass active in each degree of freedom for any one mode. The results indicate that the first mode with significant mass in the 2-direction is mode 3. The total modal effective mass in the 2-direction is 378.26 kg.```
E F F E C T I V E   M A S S

MODE NO    X-COMPONENT    Y-COMPONENT    Z-COMPONENT    X-ROTATION     Y-ROTATION     Z-ROTATION

1      5.68458E-05    5.73721E-03     309.98         77.309         5515.3        0.17333
2       1.0304         1.9915        2.09072E-05    8.56481E-05    1.10567E-03     85.521
3       2.7495         217.62        2.15392E-03    5.84420E-03    9.51888E-02     7776.2
4      1.88952E-06    2.31599E-02     1.7002         11.699         381.31        0.22244
5      3.99791E-03    3.57461E-04    0.25547         96.753         853.88        0.13370
6      0.68104         62.759        1.80648E-02    0.13910        2.22229E-02     458.58
7      6.83296E-03    2.77373E-03     4.2507         2.8692         98.926        4.90544E-04
8      0.42691        4.62440E-02     45.243         20.923         1295.8        0.38578
9       3.3366         1.4209         1.2896        0.55874         42.275        1.14296E-03
10       4.3393         5.7933         1.3767        0.42830         16.702         4.9402
....
25       1.4133         10.241        0.26078        0.23875        9.88154E-02     7.2457
26      5.02526E-02     15.658        0.27026        5.73911E-02    2.06589E-02     4.5558
27      0.36612        0.78387        0.63672        0.13060         2.3110        0.96499
28      0.74106        0.25794         4.6523        0.89371         19.329        4.18897E-06
29      2.63473E-02    3.62545E-03    5.90262E-03    2.74218E-03    6.68933E-02    2.17924E-03
30      0.15203        2.23557E-02     1.1711        3.19804E-02     8.3651        2.28687E-02

TOTAL         22.198         378.26         373.69         269.78         8348.4         8518.0

```The total mass of the model is given earlier in the data file and is 414.34 kg.

To ensure that enough modes have been used, the total effective mass in each direction should be a large proportion of the mass of the model (say 90%). However, some of the mass of the model is associated with nodes that are constrained. This constrained mass is approximately one-quarter of the mass of all the elements attached to the constrained nodes, which, in this case, is approximately 28 kg. Therefore, the mass of the model that is able to move is 385 kg.

Tip:
To determine the mass of the elements attached to the constrained nodes, switch to the Mesh module, click the query tool ../graphics/ico_info.png, and select **Mass properties** from the list of general queries. In the prompt area, select **Select mesh entities**, and select the six elements attached to the constrained nodes. The total mass is displayed in the message area (114 kg).The effective mass in the *x*-, *y*-, and *z*-directions is 6%, 98%, and 97%, respectively, of the mass that can move. The total effective mass in the 2- and 3-directions is well above the 90% recommended earlier; the total effective mass in the 1-direction is much lower. However, since the loading is applied in the 2-direction, the response in the 1-direction is not significant.

The data file does not contain any results for the modal dynamics step, because all of the data file output requests were suppressed.7.5.3 Postprocessing
../images/blu4rule.gif

Enter the Visualization module, and open the output database file `DynCrane.odb`.

**Plotting mode shapes**

You can visualize the deformation mode associated with a given natural frequency by plotting the mode shape associated with that frequency.

**To select a mode and plot the corresponding mode shape:**

-

In the context bar, click the frame selector tool ../graphics/ico_framesSmall.png.

The **Frame Selector** dialog box appears. Drag the bottom corner of the dialog box to enlarge it so that both step names are clearly visible.
-

Drag the frame slider to select frame `1`  in the **Extract Frequencies** step. This is the first eigenmode.
-

From the main menu bar, select **Plot**../images/arrow.gif**Deformed Shape**; or use the ../graphics/ico_plotDeformed.png tool in the toolbox.

Abaqus/CAE displays the deformed model shape associated with the first vibration mode, as shown in [Figure 7-8](ch07s05.html#gss-mode-1-v).

**Figure 7-8** Mode 1.

../graphics/gss-mode-1-c-nls.png
-

Select the third mode (frame `3`  in the **Extract Frequencies** step) from the **Frame Selector** dialog box. Afterward, close the dialog box.

Abaqus/CAE displays the third mode shape shown in [Figure 7-9](ch07s05.html#gss-mode-3-v).

**Figure 7-9** Mode 3.

../graphics/gss-mode-3-c-nls.png

Note:
A complete list of the available frames is given in the **Step/Frame** dialog box (**Result**../images/arrow.gif**Step/Frame**). This dialog box offers an alternative means to switching between frames.

**Animation of results**

You will animate the analysis results. First create a scale factor animation of the third eigenmode. Then create a time-history animation of the transient results.

**To create a scale factor animation of an eigenmode:**

-

From the main menu bar, select **Animate**../images/arrow.gif**Scale Factor**; or use the ../graphics/ico_animScaleFactor.png tool in the toolbox.

Abaqus/CAE displays the third mode shape and steps through different deformation scale factors ranging from 0 to 1.

Abaqus/CAE also displays the movie player controls on the right side of the context bar.
-

In the context bar, click ../graphics/ico_framePause.png to pause the animation.

**To create a time-history animation of the transient results:**

-

From the main menu bar, select **Result**../images/arrow.gif**Active Steps/Frames** to select which frames will be active in the history animation.

Abaqus/CAE displays the **Active Steps/Frames** dialog box.
-

Toggle the step names so that only the second step (**Transient modal dynamics**) is selected.
-

Click **OK** to accept the selection and to close the dialog box.
-

From the main menu bar, select **Animate**../images/arrow.gif**Time History**; or use the ../graphics/ico_animTimeHistory.png tool from the toolbox.

Abaqus/CAE steps through each available frame of the second step. The state block indicates the current step and increment throughout the animation. After the last increment of this step is reached, the animation process repeats itself.
-

You can customize the deformed shape plot while the animation is running.

-

Display the **Common Plot Options** dialog box.
-

Choose **Uniform** from the **Deformation Scale Factor** field.
-

Enter `15.0` as the deformation scale factor value.
-

Click **Apply** to apply your change.

Abaqus/CAE now steps through the frames in the second step with a deformation scale factor of `15.0`.
-

Choose **Auto-compute** from the **Deformation Scale Factor** field.
-

Click **OK** to apply your change and to close the **Common Plot Options** dialog box.

Abaqus/CAE now steps through the frames in the second step with a default deformation scale factor of `0.8`.

**Determining the peak pull-out force**

To find the peak pull-out force at the attachment points, create an *X-Y* plot of the reaction force in the 1-direction (variable RF1) at the attached nodes. This involves plotting multiple curves at the same time.

**To plot multiple curves:**

-

In the Results Tree, click mouse button 3 on **History Output** for the output database named `DynCrane.odb`. From the menu that appears, select **Filter**.
-

In the filter field, enter `*RF1*` to restrict the history output to just the reaction force components in the 1-direction.
-

From the list of available history output, select the four curves (using **[Ctrl]****+Click**) that have the following form:

`Reaction Force: RF1 PI: TRUSS-1 Node *xxx* in NSET ATTACH`
-

Click mouse button 3, and select **Plot** from the menu that appears.

Abaqus/CAE displays the selected curves.
-

Click ../graphics/afxI_cancel.png in the prompt area to cancel the current procedure.

**To position the grid:**

-

Double-click the plot to open the **Chart Options** dialog box.
-

In this dialog box, switch to the **Grid Area** tabbed page.
-

In the **Size** region of this page, select the **Square** option.
-

Use the slider to set the size to **75**.
-

In the **Position** region of this page, select the **Auto-align** option.
-

From the available alignment options, select the last one (position the grid in the lower right corner of the viewport).
-

Click **Dismiss**.

**To position the legend:**

-

Double-click the legend to open the **Chart Legend Options** dialog box.
-

In this dialog box, switch to the **Area** tabbed page.
-

In the **Position** region of this page, toggle on **Inset**.
-

To display the minimum and maximum values in the legend, switch to the **Contents** tabbed page of the dialog box. In the **Numbers** region of this page, toggle on **Show min/max**.
-

Click **Dismiss**.
-

Drag the legend in the viewport to reposition it.

The resulting plot (which has been customized) is shown in [Figure 7-10](ch07s05.html#gss-react-force-v). The curves for the two nodes at the top of each truss (points B and C) are almost a reflection of those for the nodes on the bottom of each truss (points A and D).

Note:
To modify the curve styles, click ../graphics/ico_xyCurveOptions.png in the Visualization toolbox to open the **Curve Options** dialog box.

**Figure 7-10** History of the reaction forces at the attached nodes.

../graphics/gss-react-force-c-nls.png

At the attachment points at the top of each truss structure, the peak tensile force is around 80 kN, which is below the 100 kN capacity of the connection. Keep in mind that a negative reaction force in the 1-direction means that the member is being pulled away from the wall. The lower attachments are in compression (positive reaction force) while the load is applied but oscillate between tension and compression after the load has been removed. The peak tensile force is about 40 kN, well below the allowable value. To find this value, probe the *X-Y* plot.

**To query the X-Y plot:**

-

From the main menu bar, select **Tools**../images/arrow.gif**Query**.

The **Query** dialog box appears.
-

Click **Probe values** in the **Visualization Module Queries** field.

The **Probe Values** dialog box appears.
-

Select the point indicated in [Figure 7-10](ch07s05.html#gss-react-force-v).

The *Y*-coordinate of this point is -40.30 kN, which corresponds to the value of the reaction force in the 1-direction.


---


7.6 Effect of the number of modes
../images/blu4rule.gif

For this simulation 30 modes were used to represent the dynamic behavior of the structure. The total modal effective mass for all of these modes was well over 90% of the mass of the structure that can move in the *y*- and *z*-directions, indicating that the dynamic representation is adequate.

[Figure 7-11](ch07s06.html#gss-numb-modes-v) shows the displacement in the direction of degree of freedom 2 of the node in set `Tip-a` versus time and illustrates the effect of using fewer modes on the quality of the results. If you look at the table of effective mass, you will see that the first significant mode in the 2-direction is mode 3, which accounts for the lack of response when only two modes are used. The displacement of this node in the direction of degree of freedom 2 for the analyses using five modes and 30 modes is similar after 0.2 seconds; however, the early response differs, suggesting that there are significant modes in the range of 5-30 relating to the early response. When five modes are used, the total modal effective mass in the 2-direction is only 57% of the moveable mass.

**Figure 7-11** Effect of different numbers of modes on the results.

../graphics/gss-numb-modes-c-nls.png


---


7.7 Effect of damping
../images/blu4rule.gif

In this simulation we used 5% of critical damping in all modes. This value was chosen from experience, based on the fact that the bolted connections between the trusses and the cross bracing might absorb significant energy as a result of local frictional effects. In cases such as this, where accurate data are not available, it is important to investigate the effect of the choices that you make.

[Figure 7-12](ch07s07.html#gss-results-v) compares the history of the reaction force at one of the top connections (point C) when 1%, 5%, and 10% of critical damping are used. As expected, the oscillations at lower damping levels do not diminish as quickly as those at higher damping levels, and the peak force is higher in the models with lower damping. With damping ratios even as low as 1%, the peak pull-out force is 85 kN, which is still less than the strength of the connection (100 kN). Therefore, the cargo crane should retain its integrity under this drop load.

**Figure 7-12** Effect of damping ratio on the pull-out force.

../graphics/gss-results-c-nls.png


---


7.8 Comparison with direct time integration
../images/blu4rule.gif

Since this is a transient dynamic analysis, it is natural to consider how the results compare with those obtained using direct integration of the equations of motion. Direct integration can be performed with either implicit (Abaqus/Standard) or explicit (Abaqus/Explicit) methods. Here we extend the analysis to use the explicit dynamics procedure.

A direct comparison with the results presented earlier is not possible since the B33 element type and direct modal damping are not available in Abaqus/Explicit. Thus, in the Abaqus/Explicit analysis the element type is changed to B31 and Rayleigh damping is used in place of direct modal damping.

Copy the `Dynamic` model to one named `explicit`. All subsequent changes should be made to the `explicit` model.

**To modify the model:**

-

Delete the modal dynamics step. When Abaqus/CAE warns you that deleting a step also deletes step-dependent objects, click **Yes**.
-

Replace the remaining frequency extraction step with an explicit dynamics step, and specify a time period of `0.5` s. In addition, edit the step to use linear geometry (toggle off **Nlgeom**).

This will result in a linear analysis.
-

Rename the step to `Transient dynamics`.
-

Create two additional history output requests. In the first, request displacement history for the set `Tip-a`; in the second, request reaction force history for the set `Attach`.
-

Add mass proportional damping to the bracing section properties. To do this, double-click **BracingSection** underneath the **Sections** container in the Model Tree; in the section editor that appears, click the **Damping** tab.

In the **Stiffness Proportional Material Damping** region, enter a value of `15` for **Alpha** and `0` for the remaining damping quantities.

These values produce a reasonable trade-off in the values of critical damping at low and high frequencies of the structure. For the three lowest natural frequencies, the effective value of ../graphics/gsa_eqn00085.gif is greater than 0.05, but as was shown in [Figure 7-11](ch07s06.html#gss-numb-modes-v), the first two modes do not contribute significantly to the response. For the remaining modes, the value of ../graphics/gsa_eqn00085.gif is less than 0.05. The variation of ../graphics/gsa_eqn00085.gif as a function of natural frequency is shown in [Figure 7-13](ch07s08.html#gsa-dyncrane-damping).

**Figure 7-13** Variation of damping ratio with frequency corresponding to the specified Rayleigh factors (../graphics/gsa_eqn00089.gif = 15, ../graphics/gsa_eqn00090.gif = 0).

../graphics/gsa-dyncrane-damping-nls.png
-

Repeat the above step for the main member section properties.
-

Redefine the tip load at set `Tip-b`. Specify **CF2** = `10000`, and use the amplitude definition `Bounce`.
-

Change the element library to **Explicit**, and assign element type B31 to all regions of the model.
-

Create a new job named `expDynCrane`, and submit it for analysis.

When the job completes, enter the Visualization module to examine the results. In particular, compare the tip displacement history obtained earlier from Abaqus/Standard with that obtained from Abaqus/Explicit. As shown in [Figure 7-14](ch07s08.html#gsa-dyncrane-compare), there are small differences in the response. These differences are due to the different element and damping types used for the modal dynamic analysis. In fact, if the Abaqus/Standard analysis is modified to use B31 elements and mass proportional damping, the results produced by the two analysis products are nearly indistinguishable (see [Figure 7-14](ch07s08.html#gsa-dyncrane-compare)), which confirms the accuracy of the modal dynamic procedure.

**Figure 7-14** Comparison of tip displacements obtained from Abaqus/Standard and Abaqus/Explicit.

../graphics/gsa-dyncrane-compare-nls.png


---


7.9 Other dynamic procedures
../images/blu4rule.gif

We now briefly review the other dynamic procedures available in Abaqus--namely linear modal dynamics and nonlinear dynamics.7.9.1 Linear modal dynamics
../images/blu4rule.gif

There are several other linear, dynamic procedures in Abaqus/Standard that employ the modal superposition technique. Unlike the modal dynamics procedure, which calculates the response in the time domain, these procedures provide results in the frequency domain, which can give additional insight into the behavior of the structure.

A complete description of these procedures is given in "Dynamic stress/displacement analysis,"  Section 6.3 of the Abaqus Analysis User's Guide.

**Steady-state dynamics**

This procedure calculates the amplitude and phase of the structure's response caused by harmonic excitation over a user-specified range of frequencies. Typical examples include the following:

-

The response of car engine mounts over a range of engine operating speeds.
-

Rotating machinery in buildings.
-

Components on aircraft engines.

**Response spectrum**

This procedure provides an estimate of the peak response (displacement, stress, etc.) when a structure is subjected to dynamic motion of its fixed points. The motion of the fixed points is known as "base motion"; an example is a seismic event causing ground motion. Typically the method is used when an estimate of the peak response is required for design purposes.

**Random response**

This procedure predicts the response of a system subjected to random continuous excitation. The excitation is expressed in a statistical sense using a power spectral density function. Examples of random response analysis include the following:

-

The response of an airplane to turbulence.
-

The response of a structure to noise, such as that emitted by a jet engine.
7.9.2 Nonlinear dynamics
../images/blu4rule.gif

As mentioned earlier, the modal dynamics procedure is suitable only for linear problems. When nonlinear dynamic response is of interest, the equations of motion must be integrated directly. The direct-integration of the equations of motion is performed in Abaqus/Standard using an implicit dynamics procedure. When this procedure is used, the mass, damping, and stiffness matrices are assembled and the equation of dynamic equilibrium is solved at each point in time. Since these operations are computationally intensive, direct-integration dynamics is more expensive than the modal methods.

Since the nonlinear dynamic procedure in Abaqus/Standard uses implicit time integration, it is suitable for nonlinear structural dynamics problems, for example, in which a sudden event initiates the dynamic response, such as an impact, or when the structural response involves large amounts of energy being dissipated by plasticity or viscous damping. In such studies the high frequency response, which is important initially, is damped out rapidly by the dissipative mechanisms in the model.

An alternative for nonlinear dynamic analyses is the explicit dynamics procedure available in Abaqus/Explicit. As discussed in [Chapter 2, "Abaqus Basics](ch02.html)," the explicit algorithm propagates the solution as a stress wave through the model, one element at a time. Thus, it is most suitable for applications in which stress wave effects are important and in which the event time being simulated is short (typically less than one second).

Another advantage associated with the explicit algorithm is that it can model discontinuous nonlinearities such as contact and failure more easily than Abaqus/Standard. Large, highly discontinuous problems are often more easily modeled with Abaqus/Explicit, even if the response is quasi-static. Explicit dynamic analyses are discussed further in [Chapter 9, "Nonlinear Explicit Dynamics](ch09.html)."


---


7.10 Related Abaqus examples
../images/blu4rule.gif

-

"Linear analysis of the Indian Point reactor feedwater line,"  Section 2.2.2 of the Abaqus Example Problems Guide
-

"Explosively loaded cylindrical panel,"  Section 1.3.3 of the Abaqus Benchmarks Guide
-

"Eigenvalue analysis of a cantilever plate,"  Section 1.4.6 of the Abaqus Benchmarks Guide


---


7.11 Suggested reading
../images/blu4rule.gif

-

Clough, R. W. and J. Penzien, *Dynamics of Structures*, McGraw-Hill, 1975.
-

NAFEMS Ltd., *A Finite Element Dynamics Primer*, 1993.
-

Spence, P. W. and C. J. Kenchington, *The Role of Damping in Finite Element Analysis*, Report R0021, NAFEMS Ltd., 1993.


---


7.12 Summary
../images/blu4rule.gif

-

Dynamic analyses include the effect of the structure's inertia.
-

The frequency extraction procedure in Abaqus/Standard extracts the natural frequencies and mode shapes of the structure.
-

The mode shapes can then be used to determine the dynamic response of linear systems by modal superposition. This technique is efficient, but it cannot be used for nonlinear problems.
-

Linear dynamic procedures are available in Abaqus/Standard to calculate the transient response to transient loading, the steady-state response to harmonic loading, the peak response to base motion, and the response to random loading.
-

You should extract enough modes to obtain an accurate representation of the dynamic behavior of the structure. The total modal effective mass in the direction in which motion will occur should be at least 90% of the mass that can move to produce accurate results.
-

You can define direct modal damping, Rayleigh damping, and composite modal damping in Abaqus/Standard. However, since the natural frequencies and mode shapes are based on the undamped structure, the structure being analyzed should be only lightly damped.
-

Modal techniques are not suitable for nonlinear dynamic simulations. Direct time integration methods or explicit analysis must be used in these situations.
-

Time variation of loads or prescribed boundary conditions can be defined with an amplitude curve.
-

Mode shapes and transient results can be animated in the Visualization module of Abaqus/CAE. This provides a useful way of understanding the response of dynamic and nonlinear static analyses.


---

