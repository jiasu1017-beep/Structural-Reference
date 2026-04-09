
9. Nonlinear Explicit Dynamics
../images/blu4rule.gif

In previous chapters you explored the basics of explicit dynamics procedures; in this chapter you will examine this topic in greater detail. The explicit dynamics procedure can be an effective tool for solving a wide variety of nonlinear solid and structural mechanics problems. It is often complementary to an implicit solver such as Abaqus/Standard. From a user standpoint, the distinguishing characteristics of the explicit and implicit methods are:

-

Explicit methods require a small time increment size that depends solely on the highest natural frequencies of the model and is independent of the type and duration of loading. Simulations generally take on the order of 10,000 to 1,000,000 increments, but the computational cost per increment is relatively small.
-

Implicit methods do not place an inherent limitation on the time increment size; increment size is generally determined from accuracy and convergence considerations. Implicit simulations typically take orders of magnitude fewer increments than explicit simulations. However, since a global set of equations must be solved in each increment, the cost per increment of an implicit method is far greater than that of an explicit method.
Knowing these characteristics of the two procedures can help you decide which methodology is appropriate for your problems.


---


9.1 Types of problems suited for Abaqus/Explicit
../images/blu4rule.gif

Before discussing how the explicit dynamics procedure works, it is helpful to understand what classes of problems are well-suited to Abaqus/Explicit. Throughout this guide we have incorporated pertinent examples of the following classes of problems commonly performed in Abaqus/Explicit:

**High-speed dynamic events**

The explicit dynamics method was originally developed to analyze high-speed dynamic events that can be extremely costly to analyze using implicit programs, such as Abaqus/Standard. As an example of such a simulation, the effect of a short-duration blast load on a steel plate is analyzed in [Chapter 10, "Materials](ch10.html)." Since the load is applied rapidly and is very severe, the response of the structure changes rapidly. Accurate tracking of stress waves through the plate is important for capturing the dynamic response. Since stress waves are associated with the highest frequencies of the system, obtaining an accurate solution requires many small time increments.

**Complex contact problems**

Contact conditions are formulated more easily using an explicit dynamics method than using an implicit method. The result is that Abaqus/Explicit can readily analyze problems involving complex contact interaction between many independent bodies. Abaqus/Explicit is particularly well-suited for analyzing the transient dynamic response of structures that are subject to impact loads and subsequently undergo complex contact interaction within the structure. An example of such a problem is the circuit board drop test presented in [Chapter 12, "Contact](ch12.html)." In this example a circuit board sitting in foam packaging is dropped on the floor from a height of 1 m. The problem involves impact between the packaging and the floor, as well as rapidly changing contact conditions between the circuit board and the packaging.

**Complex postbuckling problems**

Unstable postbuckling problems are solved readily in Abaqus/Explicit. In such problems the stiffness of the structure changes drastically as the loads are applied. Postbuckling response often includes the effects of contact interactions.

**Highly nonlinear quasi-static problems**

For a variety of reasons Abaqus/Explicit is often very efficient in solving certain classes of problems that are essentially static. Quasi-static process simulation problems involving complex contact such as forging, rolling, and sheet-forming generally fall within these classes. Sheet forming problems usually include very large membrane deformations, wrinkling, and complex frictional contact conditions. Bulk forming problems are characterized by large distortions, flash formation, and contact interaction with the dies. An example of a quasi-static forming simulation is presented in [Chapter 13, "Quasi-Static Analysis with Abaqus/Explicit](ch13.html)."

**Materials with degradation and failure**

Material degradation and failure often lead to severe convergence difficulties in implicit analysis programs, but Abaqus/Explicit models such materials well. An example of material degradation is the concrete cracking model, in which tensile cracking causes the material stiffness to become negative. An example of material failure is the ductile failure model for metals, in which material stiffness can degrade until it reduces to zero. At this time the failed elements are removed from the model entirely.Each of these types of analyses can include temperature and heat transfer effects.


---


9.2 Explicit dynamic finite element methods
../images/blu4rule.gif

This section contains an algorithmic description of the Abaqus/Explicit solver as well as a comparison between implicit and explicit time integration and a discussion of the advantages of the explicit dynamics method.9.2.1 Explicit time integration
../images/blu4rule.gif

Abaqus/Explicit uses a central difference rule to integrate the equations of motion explicitly through time, using the kinematic conditions at one increment to calculate the kinematic conditions at the next increment. At the beginning of the increment the program solves for dynamic equilibrium, which states that the nodal mass matrix, ../graphics/gsa_eqn00129.gif, times the nodal accelerations, ../graphics/gsa_eqn00130.gif, equals the net nodal forces (the difference between the external applied forces, ../graphics/gsa_eqn00131.gif, and internal element forces, ../graphics/gsa_eqn00132.gif):

../graphics/gsa_eqn00133.gif

The accelerations at the beginning of the current increment (time ../graphics/gsa_eqn00134.gif) are calculated as

../graphics/gsa_eqn00135.gif

Since the explicit procedure always uses a diagonal, or lumped, mass matrix, solving for the accelerations is trivial; there are no simultaneous equations to solve. The acceleration of any node is determined completely by its mass and the net force acting on it, making the nodal calculations very inexpensive.

The accelerations are integrated through time using the central difference rule, which calculates the change in velocity assuming that the acceleration is constant. This change in velocity is added to the velocity from the middle of the previous increment to determine the velocities at the middle of the current increment:

../graphics/gsa_eqn00136.gif

The velocities are integrated through time and added to the displacements at the beginning of the increment to determine the displacements at the end of the increment:

../graphics/gsa_eqn00137.gif

Thus, satisfying dynamic equilibrium at the beginning of the increment provides the accelerations. Knowing the accelerations, the velocities and displacements are advanced "explicitly" through time. The term "explicit" refers to the fact that the state at the end of the increment is based solely on the displacements, velocities, and accelerations at the beginning of the increment. This method integrates constant accelerations exactly. For the method to produce accurate results, the time increments must be quite small so that the accelerations are nearly constant during an increment. Since the time increments must be small, analyses typically require many thousands of increments. Fortunately, each increment is inexpensive because there are no simultaneous equations to solve. Most of the computational expense lies in the element calculations to determine the internal forces of the elements acting on the nodes. The element calculations include determining element strains and applying material constitutive relationships (the element stiffness) to determine element stresses and, consequently, internal forces.

Here is a summary of the explicit dynamics algorithm:

-

Nodal calculations.

-

Dynamic equilibrium.

../graphics/gsa_eqn00138.gif
-

Integrate explicitly through time.

../graphics/gsa_eqn00139.gif

../graphics/gsa_eqn00140.gif

-

Element calculations.

-

Compute element strain increments, ../graphics/gsa_eqn00141.gif, from the strain rate, ../graphics/gsa_eqn00142.gif.
-

Compute stresses, ../graphics/gsa_eqn00143.gif, from constitutive equations.

../graphics/gsa_eqn00144.gif
-

Assemble nodal internal forces, ../graphics/gsa_eqn00145.gif.

-

Set ../graphics/gsa_eqn00146.gif to ../graphics/gsa_eqn00134.gif and return to Step 1.
9.2.2 Comparison of implicit and explicit time integration procedures
../images/blu4rule.gif

For both the implicit and the explicit time integration procedures, equilibrium is defined in terms of the external applied forces, ../graphics/gsa_eqn00131.gif, the internal element forces, ../graphics/gsa_eqn00132.gif, and the nodal accelerations:

../graphics/gsa_eqn00147.gifwhere ../graphics/gsa_eqn00129.gif is the mass matrix. Both procedures solve for nodal accelerations and use the same element calculations to determine the internal element forces. The biggest difference between the two procedures lies in the manner in which the nodal accelerations are computed. In the implicit procedure a set of linear equations is solved by a direct solution method. The computational cost of solving this set of equations is high when compared to the relatively low cost of the nodal calculations with the explicit method.

Abaqus/Standard uses automatic incrementation based on the full Newton iterative solution method. Newton's method seeks to satisfy dynamic equilibrium at the end of the increment at time ../graphics/gsa_eqn00146.gif and to compute displacements at the same time. The time increment, ../graphics/gsa_eqn00148.gif, is relatively large compared to that used in the explicit method because the implicit scheme is unconditionally stable. For a nonlinear problem each increment typically requires several iterations to obtain a solution within the prescribed tolerances. Each Newton iteration solves for a correction, ../graphics/gsa_eqn00149.gif, to the incremental displacements, ../graphics/gsa_eqn00150.gif. Each iteration requires the solution of a set of simultaneous equations,

../graphics/gsa_eqn00151.gifwhich is an expensive procedure for large models. The effective stiffness matrix, ../graphics/gsa_eqn00152.gif, is a linear combination of the tangent stiffness matrix and the mass matrix for the iteration. The iterations continue until several quantities--force residual, displacement correction, etc.--are within the prescribed tolerances. For a smooth nonlinear response Newton's method has a quadratic rate of convergence, as illustrated below:

However, if the model contains highly discontinuous processes, such as contact and frictional sliding, quadratic convergence may be lost and a large number of iterations may be required. Cutbacks in the time increment size may become necessary to satisfy equilibrium. In extreme cases the resulting time increment size in the implicit analysis may be on the same order as a typical stable time increment for an explicit analysis, while still carrying the high solution cost of implicit iteration. In some cases convergence may not be possible using the implicit method.

Each iteration in an implicit analysis requires solving a large system of linear equations, a procedure that requires considerable computation, disk space, and memory. For large problems these equation solver requirements are dominant over the requirements of the element and material calculations, which are similar for an analysis in Abaqus/Explicit. As the problem size increases, the equation solver requirements grow rapidly so that, in practice, the maximum size of an implicit analysis that can be solved on a given machine often is dictated by the amount of disk space and memory available on the machine rather than by the required computation time.9.2.3 Advantages of the explicit time integration method
../images/blu4rule.gif

The explicit method is especially well-suited to solving high-speed dynamic events that require many small increments to obtain a high-resolution solution. If the duration of the event is short, the solution can be obtained efficiently.

Contact conditions and other extremely discontinuous events are readily formulated in the explicit method and can be enforced on a node-by-node basis without iteration. The nodal accelerations can be adjusted to balance the external and internal forces during contact.

The most striking feature of the explicit method is the absence of a global tangent stiffness matrix, which is required with implicit methods. Since the state of the model is advanced explicitly, iterations and tolerances are not required.


---


9.3 Automatic time incrementation and stability
../images/blu4rule.gif

The stability limit dictates the maximum time increment used by the Abaqus/Explicit solver. It is a critical factor in the performance of Abaqus/Explicit. The following sections describe the stability limit and discuss how Abaqus/Explicit determines this value. Issues surrounding the model design parameters that affect the stability limit are also addressed. These model parameters include the model mass, material, and mesh.9.3.1 Conditional stability of the explicit method
../images/blu4rule.gif

With the explicit method the state of the model is advanced through an increment of time, ../graphics/gsa_eqn00148.gif, based on the state of the model at the start of the increment at time ../graphics/gsa_eqn00134.gif. The amount of time that the state can be advanced and still remain an accurate representation of the problem is typically quite short. If the time increment is larger than this maximum amount of time, the increment is said to have exceeded the *stability limit*. A possible effect of exceeding the stability limit is a numerical instability, which may lead to an unbounded solution. It generally is not possible to determine the stability limit exactly, so conservative estimates are used instead. The stability limit has a great effect on reliability and accuracy, so it must be determined consistently and conservatively. For computational efficiency Abaqus/Explicit chooses the time increments to be as close as possible to the stability limit without exceeding it.9.3.2 Definition of the stability limit
../images/blu4rule.gif

The stability limit is defined in terms of the highest frequency in the system (../graphics/gsa_eqn00153.gif). Without damping the stability limit is defined by the expression

../graphics/gsa_eqn00154.gifand with damping it is defined by the expression

../graphics/gsa_eqn00155.gifwhere ../graphics/gsa_eqn00156.gif is the fraction of critical damping in the mode with the highest frequency. (Recall that critical damping defines the limit between oscillatory and non-oscillatory motion in the context of free-damped vibration. Abaqus/Explicit always introduces a small amount of damping in the form of bulk viscosity to control high-frequency oscillations.) Perhaps contrary to engineering intuition, damping always reduces the stability limit.

The actual highest frequency in the system is based on a complex set of interacting factors, and it is not computationally feasible to calculate its exact value. Alternately, we use a simple estimate that is efficient and conservative. Instead of looking at the global model, we estimate the highest frequency of each individual element in the model, which is always associated with the dilatational mode. It can be shown that the highest element frequency determined on an element-by-element basis is always higher than the highest frequency in the assembled finite element model.

Based on the element-by-element estimate, the stability limit can be redefined using the element length, ../graphics/gsa_eqn00157.gif, and the wave speed of the material, ../graphics/gsa_eqn00158.gif:

../graphics/gsa_eqn00159.gifFor most element types--a distorted quadrilateral element, for example--the above equation is only an estimate of the actual element-by-element stability limit because it is not clear how the element length should be determined. As an approximation the shortest element distance can be used, but the resulting estimate is not always conservative. The shorter the element length, the smaller the stability limit. The wave speed is a property of the material. For a linear elastic material with a Poisson's ratio of zero

../graphics/gsa_eqn00160.gifwhere ../graphics/gsa_eqn00161.gif is Young's modulus and ../graphics/gsa_eqn00162.gif is the mass density. The stiffer the material, the higher the wave speed, resulting in a smaller stability limit. The higher the density, the lower the wave speed, resulting in a larger stability limit.

Our simplified stability limit definition provides some intuitive understanding. The stability limit is the transit time of a dilatational wave across the distance defined by the characteristic element length. If we know the size of the smallest element dimension and the wave speed of the material, we can estimate the stability limit. For example, if the smallest element dimension is 5 mm and the dilatational wave speed is 5000 m/s, the stable time increment is on the order of 1  10^6 s.9.3.3 Fully automatic time incrementation versus fixed time incrementation in Abaqus/Explicit
../images/blu4rule.gif

Abaqus/Explicit uses equations such as those discussed in the previous section to adjust the time increment size throughout the analysis so that the stability limit, based on the current state of the model, is never exceeded. Time incrementation is automatic and requires no user intervention, not even a suggested initial time increment. The stability limit is a mathematical concept resulting from the numerical model. Since the finite element program has all of the relevant details, it can determine an efficient and conservative stability limit. However, Abaqus/Explicit does allow the user to override the automatic time incrementation, if desired.

The time increment used in an explicit analysis must be smaller than the stability limit of the central-difference operator. Failure to use a small enough time increment will result in an unstable solution. When the solution becomes unstable, the time history response of solution variables such as displacements will usually oscillate with increasing amplitudes. The total energy balance will also change significantly. If the model contains only one material type, the initial time increment is directly proportional to the size of the smallest element in the mesh. If the mesh contains uniform size elements but contains multiple material descriptions, the element with the highest wave speed will determine the initial time increment.

In nonlinear problems--those with large deformations and/or nonlinear material response--the highest frequency of the model will continually change, which consequently changes the stability limit. Abaqus/Explicit has two strategies for time incrementation control: fully automatic time incrementation (where the code accounts for changes in the stability limit) and fixed time incrementation.

Two types of estimates are used to determine the stability limit: element by element and global. An analysis always starts by using the element-by-element estimation method and may switch to the global estimation method under certain circumstances.

The element-by-element estimate is conservative; it will give a smaller stable time increment than the true stability limit that is based upon the maximum frequency of the entire model. In general, constraints such as boundary conditions and kinematic contact have the effect of compressing the eigenvalue spectrum, and the element-by-element estimates do not take this into account.

The adaptive, global estimation algorithm determines the maximum frequency of the entire model using the current dilatational wave speed. This algorithm continuously updates the estimate for the maximum frequency. The global estimator will usually allow time increments that exceed the element-by-element values.

A fixed time incrementation scheme is also available in Abaqus/Explicit. The fixed time increment size is determined either by the initial element-by-element stability estimate for the step or by a time increment specified directly by the user. Fixed time incrementation may be useful when a more accurate representation of the higher mode response of a problem is required. In this case, a time increment size smaller than the element-by-element estimates may be used. When fixed time incrementation is used, Abaqus/Explicit will not check that the computed response is stable during the step. The user should ensure that a valid response has been obtained by carefully checking the energy history and other response variables. 9.3.4 Mass scaling to control time incrementation
../images/blu4rule.gif

Since the mass density influences the stability limit, under some circumstances scaling the mass density can potentially increase the efficiency of an analysis. For example, because of the complex discretization of many models, there are often regions containing very small or poorly shaped elements that control the stability limit. These controlling elements are often few in number and may exist in localized areas. By increasing the mass of only these controlling elements, the stability limit can be increased significantly, while the effect on the overall dynamic behavior of the model may be negligible.

The automatic mass scaling features in Abaqus/Explicit can keep offending elements from hindering the stability limit. There are two fundamental approaches used in mass scaling: defining a scaling factor directly or defining a desired element-by-element stable time increment for the elements whose mass is to be scaled. These two approaches, described in detail in "Mass scaling,"  Section 11.6.1 of the Abaqus Analysis User's Guide, permit additional user control over the stability limit. However, use caution when employing mass scaling since significantly changing the mass of the model may change the physics of the problem.9.3.5 Effect of material on stability limit
../images/blu4rule.gif

The material model affects the stability limit through its effect on the dilatational wave speed. In a linear material the wave speed is constant; therefore, the only changes in the stability limit during the analysis result from changes in the smallest element dimension during the analysis. In a nonlinear material, such as a metal with plasticity, the wave speed changes as the material yields and the stiffness of the material changes. Abaqus/Explicit monitors the effective wave speeds in the model throughout the analysis, and the current material state in each element is used for stability estimates. After yielding, the stiffness decreases, reducing the wave speed and, consequently, increasing the stability limit.9.3.6 Effect of mesh on stability limit
../images/blu4rule.gif

Since the stability limit is roughly proportional to the shortest element dimension, it is advantageous to keep the element size as large as possible. Unfortunately, for accurate analyses a fine mesh is often necessary. To obtain the highest possible stability limit while using the required level of mesh refinement, the best approach is to have a mesh that is as uniform as possible. Since the stability limit is based on the smallest element dimension in the model, even a single small or poorly shaped element can reduce the stability limit drastically. For diagnostic purposes Abaqus/Explicit provides a list in the status (`.sta`) file of the 10 elements in the mesh with the lowest stability limit. If the model contains some elements whose stability limits are much lower than those of the rest of the mesh, remeshing the model more uniformly may be worthwhile.9.3.7 Numerical instability
../images/blu4rule.gif

Abaqus/Explicit remains stable for most elements under most circumstances. It is possible, however, to define spring and dashpot elements such that they become unstable during the course of an analysis. Therefore, it is useful to be able to recognize a numerical instability if it occurs in your analysis. If it does occur, the result typically will be unbounded, nonphysical, and often characterized by oscillatory solutions.


---


9.4 Example: stress wave propagation in a bar
../images/blu4rule.gif

This example demonstrates some of the fundamental ideas in explicit dynamics described earlier in [Chapter 2, "Abaqus Basics](ch02.html)." It also illustrates stability limits and the effect of mesh refinement and material properties on the solution time.

The bar has the dimensions shown in [Figure 9-1](ch09s04.html#gxi-probdescwaveprp).

**Figure 9-1** Schematic for wave propagation in a bar.

../graphics/gsx-probdescwaveprp-nls.pngTo make the problem a one-dimensional strain problem, all four lateral faces are on rollers; thus, the three-dimensional model simulates a one-dimensional problem. The material is steel with the properties shown in [Figure 9-1](ch09s04.html#gxi-probdescwaveprp). The free end of the bar is subjected to a blast load with a magnitude of 1.0  10^5 Pa and a duration of 3.88  10^5 s. The normalized load versus time is shown in [Figure 9-2](ch09s04.html#gxi-blast-amp-time-v).

**Figure 9-2** Blast amplitude versus time.

../graphics/gsx-blast-amp-time-v-nls.png9.4.1 Preprocessing--creating the model with Abaqus/CAE
../images/blu4rule.gif

In this section we discuss how to use Abaqus/CAE to create the model for this simulation. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in ["Stress wave propagation in a bar,"  Section A.7](ap01s07.html). Instructions on how to fetch the script and run it within Abaqus/CAE are given in [Appendix A, "Example Files](ap01.html)."
-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins**../images/arrow.gif**Abaqus**../images/arrow.gif**Getting Started**; highlight **Stress wave propagation in a bar**; and click **Run**. For more information about the Getting Started plug-ins, see "Running the Getting Started with Abaqus examples,"  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file that defines this problem can be created manually, as discussed in "Example: stress wave propagation in a bar,"  Section 9.4 of Getting Started with Abaqus: Keywords Edition.

**Defining the model geometry**

In this example you will create a three-dimensional, deformable body with a solid, extruded base feature. You will first sketch the two-dimensional profile of the bar and then extrude it.

**To create a part:**

-

Create a new part named `Bar`, and accept the default settings of a three-dimensional, deformable body and a solid, extruded base feature in the **Create Part** dialog box. Use an approximate size of `0.5` for the model.
-

Use the dimensions given in [Figure 9-3](ch09s04.html#gxi-bar-profile) to sketch the cross-section of the bar.

**Figure 9-3** Rectangular cross-section (with grid spacing doubled).

../graphics/gxi-bar-profile.pngThe following possible approach can be used:

-

Create a rectangle centered about the origin using the **Create Lines: Rectangle** tool.

Tip:
Create fixed horizontal and vertical construction lines through the origin of the sketch plane, and apply appropriate geometry constraints to the sketch.
-

Dimension the sketch so that the cross-section is 0.20 m high  0.20 m wide.
-

Click **Done** in the prompt area when you are finished sketching the profile.

The **Edit Base Extrusion** dialog box appears. To complete the part definition, you must specify the distance over which the profile will be extruded.
-

In the dialog box, enter an extrusion depth of `1.0` m.

-

Save your model in a model database file named `Bar.cae`.

**Defining the material and section properties**

Create a single linear elastic material named `Steel` with a mass density of `7800` kg/m^3, a Young's modulus of `207E9` Pa, and a Poisson's ratio of `0.3`.

Create a solid, homogeneous section definition named `BarSection` with **Steel** as the material.

Assign the section definition `BarSection` to the entire part.

**Creating an assembly**

Create an instance of the bar. The model is oriented by default so that the global 3-axis lies along the length of the bar.

**Creating geometry sets and surfaces**

Create the geometry sets `TOP`, `BOT`, `FRONT`, `BACK`, `FIX`, and `OUT` as shown in [Figure 9-4](ch09s04.html#gxi-node-sets). (The set `OUT` contains the edge shown in bold in [Figure 9-4](ch09s04.html#gxi-node-sets).) Create the surface named `LOAD` shown in [Figure 9-5](ch09s04.html#gxi-node-surfaces). These regions will be used later for the application of loads and boundary conditions, as well as for the definition of output requests.

**Figure 9-4** Sets.

../graphics/gxi-node-sets-nls.png

**Figure 9-5** Surface.

../graphics/gxi-surfaces-nls.png

**Defining steps**

Create a single dynamic, explicit step named `BlastLoad`. Enter `Apply pressure load pulse` as the step description, and set the **Time period** to `2.0E-4` s. In the **Edit Step** dialog box, click the **Other** tab. To keep the stress wave as sharp as possible, set the **Quadratic bulk viscosity parameter** (discussed in ["Bulk viscosity,"  Section 9.5.1](ch09s05.html#gsa-ovw-bulkvisc)) to zero.

**Specifying output requests**

Edit the default field output request so that preselected field data are written to the output database at four equally spaced intervals for the step `BlastLoad`.

Delete the existing default history output request, and create a new set of history output requests. In the **Create History Output** dialog box, accept the default name of `H-Output-1` and select the `BlastLoad` step. Click **Continue**. Click the arrow next to the **Domain** field, select **Set**, and select `OUT`. In the **Output Variables** section, click on the triangle to the left of **Stresses**. Click on the triangle to the left of **S, Stress components and invariants**, and toggle on the **S33** variable, which is the component of stress in the axial direction of the bar. Specify that output be saved at every increment.

**Prescribing boundary conditions**

Create a boundary condition named `Fix right end`, and constrain the right end of the bar (geometry set `FIX`) in all three directions (see [Figure 9-1](ch09s04.html#gxi-probdescwaveprp)). Create additional boundary conditions to constrain the top, bottom, front, and back faces in the directions normal to these faces (the 1-direction for sets `FRONT` and `BACK` and the 2-direction for sets `TOP` and `BOT`).

**Defining the load history**

The blast load is applied at its maximum value instantaneously and is held constant for 3.88  10^5 s. Then the load is suddenly removed and held constant at zero. Create an amplitude definition named `Blast` using the data shown in [Figure 9-6](ch09s04.html#gxi-blast-ampdef). For this problem the pressure load at any given time is the specified magnitude of the pressure load times the value interpolated from the amplitude curve.

**Figure 9-6** Tabular data for the blast load amplitude definition.

../graphics/gsx-blast-ampdef-nls.png

Create a pressure load named `Blast load`, and select `BlastLoad` as the step in which it will be applied. Apply the load to the surface `LOAD`. Select **Uniform** for the distribution, specify a value of `1.0E5` Pa for the load magnitude, and select **Blast** for the amplitude.

**Creating a mesh**

Using the material properties (neglecting Poisson's ratio), we can calculate the wave speed of the material using the equations introduced earlier.

../graphics/gsa_eqn00163.gifAt this speed the wave passes to the fixed end of the bar in 1.94  10^4 s. Since we are interested in stress propagation along the length of the bar through time, we need a sufficiently refined mesh to capture the stress wave accurately. We will assume that the blast load will take place over the span of 10 elements. To determine the length of these 10 elements, multiply the blast duration by the wave speed:

../graphics/gsa_eqn00164.gifThe length of 10 elements is 0.2 m. Since the total length of the bar is 1.0 m, we would have 50 elements along the length. To keep the mesh uniform, we will also have 10 elements in each of the transverse directions, making the mesh 50  10  10. This mesh is shown in [Figure 9-7](ch09s04.html#gxi-mesh).

**Figure 9-7** 50  10  10 mesh.

../graphics/gxi-mesh-2.png

Seed the part with a target global element size of `0.02`. Select C3D8R from the **Explicit** library as the element type, and mesh the part.

Note:
The proposed mesh density exceeds the model size limits of the Abaqus Student Edition. If you are using this product, specify one of the following:

-

A global element size of 0.04.
-

A 50  3  3 mesh.
-

A 25  5  5 mesh.

**Creating, running, and monitoring a job**

Create a job named `Bar`, and enter `Stress wave propagation in a bar (SI units)` for the job description. Submit the job, and monitor the results.  If any errors are encountered, correct the model and rerun the simulation. Be sure to investigate the cause of any warning messages and take appropriate action; recall that some warning messages can be ignored safely while others require corrective action.

**The status (.sta) file**

You can also look at the status file, `Bar.sta`, to monitor the job progress. You can browse or search this file by clicking the **Status File** tab in the **Job Monitor**. The status file contains information about moments of inertia, followed by information concerning the stability limit. The 10 elements with the lowest stable time limits are listed in rank order.```
Most critical elements:
Element number   Rank    Time increment   Increment ratio
(Instance name)
----------------------------------------------------------
1          1       2.237266E-06      1.000000E+00
BAR-1
10          2       2.237266E-06      1.000000E+00
BAR-1
21          3       2.237266E-06      1.000000E+00
BAR-1
30          4       2.237266E-06      1.000000E+00
BAR-1
31          5       2.237266E-06      1.000000E+00
BAR-1
40          6       2.237266E-06      1.000000E+00
BAR-1
51          7       2.237266E-06      1.000000E+00
BAR-1
60          8       2.237266E-06      1.000000E+00
BAR-1
61          9       2.237266E-06      1.000000E+00
BAR-1
70         10       2.237266E-06      1.000000E+00
BAR-1

```The status file continues with information about the progress of the solution.```
STEP 1  ORIGIN 0.0000

Total memory used for step 1 is approximately 6.8 megabytes.
Global time estimation algorithm will be used.
Scaling factor :  1.0000
Variable mass scaling factor at zero increment:  1.0000

STEP     TOTAL       CPU      STABLE    CRITICAL    KINETIC      TOTAL
INCREMENT     TIME      TIME      TIME   INCREMENT     ELEMENT     ENERGY     ENERGY
0  0.000E+00 0.000E+00  00:00:00 2.237E-06          70  0.000E+00  0.000E+00
INSTANCE WITH CRITICAL ELEMENT: BAR-1
ODB Field Frame Number      0 of      4 requested intervals at increment zero.
5  1.119E-05 1.119E-05  00:00:00 2.237E-06          70  4.504E-05 -1.963E-06
10  2.237E-05 2.237E-05  00:00:00 2.237E-06        2010  9.189E-05 -2.218E-06
15  3.471E-05 3.471E-05  00:00:00 2.931E-06        2090  1.434E-04 -2.361E-06
19  4.640E-05 4.640E-05  00:00:00 2.910E-06        1040  1.607E-04  1.850E-06
21  5.221E-05 5.221E-05  00:00:00 2.902E-06         600  1.588E-04  2.585E-06
ODB Field Frame Number      1 of      4 requested intervals at  5.176230E-05
25  6.380E-05 6.380E-05  00:00:00 2.890E-06         590  1.569E-04  6.082E-07
29  7.535E-05 7.535E-05  00:00:00 2.880E-06        4640  1.553E-04 -7.049E-07
33  8.685E-05 8.685E-05  00:00:00 2.873E-06        4670  1.537E-04 -1.386E-06

```

Similar information is available in the **Job Diagnostics** dialog box of the Visualization module. This dialog box also allows you to plot histories of the data, as shown in [Figure 9-8](ch09s04.html#gxi-stableinc-nls). To create a history plot, select a step from the **Job History**, select a column in the **Incrementation** tab, and click **Plot selected column**.

**Figure 9-8** Stable time increment history.

../graphics/gxi-stableinc-nls.png9.4.2 Postprocessing
../images/blu4rule.gif

In the Model Tree, click mouse button 3 on the job named **Bar** and select **Results** from the menu that appears to enter the Visualization module and automatically open the output database (`.odb`) file created by this job. Alternatively, from the **Module** list located in the context bar, select **Visualization** to enter the Visualization module; open the `.odb` file by selecting **File**../images/arrow.gif**Open** from the main menu bar and double-clicking on the appropriate file.

**Plotting the stress along a path**

We are interested in looking at how the stress distribution along the length of the bar changes with time. To do so, we will look at the stress distribution at three different times throughout the course of the analysis.

Create a curve of the variation of the stress in the 3-direction (S33) along the axis of the bar for each of the first three frames of the output database file. To create these plots, you first need to define a straight path along the axis of the bar.

**To create a point list path along the center of the bar:**

-

In the Results Tree, double-click **Paths**.

The **Create Path** dialog box appears.
-

Name the path `Center`. Select **Point list** as the path type, and click **Continue**.

The **Edit Point List Path** dialog box appears.
-

In the **Point Coordinates** table, enter the coordinates of the centers of both ends of the bar. The input specifies a path from the first point to the second point, as defined in the global coordinate system of the model.

Note:
If you generated the geometry and mesh using the procedure described earlier, the table entries are `0, 0, 1` and `0, 0, 0`. If you used an alternate procedure to generate the bar geometry, you can use the ../graphics/ico_info.png tool in the **Query** toolbar to determine the coordinates of the centers at each end of the bar.
-

When you have finished, click **OK** to close the **Edit Point List Path** dialog box.

**To save X-Y plots of stress along the path at three different times:**

-

In the Results Tree, double-click **XYData**.

The **Create XY Data** dialog box appears.
-

Choose **Path** as the *X-Y* data source, and click **Continue**.

The **XY Data from Path** dialog box appears with the path that you created visible in the list of available paths. If the undeformed model shape is currently displayed, the path you select is highlighted in the plot.
-

Toggle on **Include intersections** under **Point Locations**.
-

Accept **True distance** as the selection in the **X Values** region of the dialog box.
-

Click **Field Output** in the **Y Values** region of the dialog box to open the **Field Output** dialog box.
-

Select the S33 stress component, and click **OK**.

The field output variable in the **XY Data from Path** dialog box changes to indicate that stress data in the 3-direction (S33) will be created.

Note:
Abaqus/CAE may warn you that the field output variable will not affect the current image. Leave the plot state **As is**, and click **OK** to continue.
-

Click **Step/Frame** in the **Y Values** region of the **XY Data from Path** dialog box.
-

In the **Step/Frame** dialog box that appears, choose frame 1, which is the second of the five recorded frames. (The first frame listed, frame 0, is the base state of the model at the beginning of the step.) Click **OK**.

The **Y Values** region of the **XY Data from Path** dialog box changes to indicate that data from Step 1, frame 1 will be created.
-

To save the *X-Y* data, click **Save As**.

The **Save XY Data As** dialog box appears.
-

Name the *X-Y* data `S33_T1`, and click **OK**.

`S33_T1` appears in the **XYData** container of the Results Tree.
-

Repeat Steps 7 through 9 to create *X-Y* data for frames 2 and 3. Name the data sets `S33_T2` and `S33_T3`, respectively.
-

To close the **XY Data from Path** dialog box, click **Cancel**.

**To plot the stress curves:**

-

In the **XYData** container, drag the cursor to select all three *X-Y* data sets.
-

Click mouse button 3, and select **Plot** from the menu that appears.

Abaqus/CAE plots the stress in the 3-direction along the center of the bar for frames 1, 2, and 3, corresponding to approximate simulation times of 5  10^5 s, 1  10^4 s, and 1.5  10^4 s, respectively.
-

Click ../graphics/afxI_cancel.png in the prompt area to cancel the current procedure.

**To customize the X-Y plot:**

-

Double-click the *Y*-axis.

The **Axis Options** dialog box appears. The **Y Axis** is selected.
-

In the **Tick Mode** region of the **Scale** tabbed page, select **By increment** and specify that the *Y*-axis major tick marks occur at `20E3` Pa increments.

You can also customize the axis titles.
-

Switch to the **Title**  tabbed page.
-

Enter `Stress - S33 (Pa)` as the *Y*-axis title.
-

To edit the *X*-axis, select the axis label in the **X Axis** field of the dialog box. In the **Title**  tabbed page of the dialog box, enter `Distance along bar (m)` as the *X*-axis title.
-

Click **Dismiss** to close the **Axis Options** dialog box.

**To customize the appearance of the curves in the X-Y plot:**

-

In the Visualization toolbox, click ../graphics/ico_xyCurveOptions.png to open the **Curve Options** dialog box.
-

In the **Curves** field, select `S33_T2`.
-

Choose the dotted line style for the `S33_T2` curve.

The `S33_T2` curve becomes dotted.
-

Repeat Steps 2 and 3 to make the `S33_T3` curve dashed.
-

Dismiss the **Curve Options** dialog box.

The customized plot appears in [Figure 9-9](ch09s04.html#gxi-stressbar-v). (For clarity, the default grid and legend positions have been changed.)

**Figure 9-9** Stress (S33) along the bar at three different time instances.

../graphics/gxi-stressbar-v-nls.png

We can see that the length of the bar affected by the stress wave is approximately 0.2 m in each of the three curves. This distance should correspond to the distance that the blast wave travels during its time of application, which can be checked by a simple calculation. If the length of the wave front is 0.2 m and the wave speed is 5.15  10^3 m/s, the time it takes for the wave to travel 0.2 m is 3.88  10^5 s. As expected, this is the duration of the blast load that we applied. The stress wave is not exactly square as it passes along the bar. In particular, there is "ringing" or oscillation of the stress behind the sudden changes in stress. Linear bulk viscosity, discussed later in this chapter, damps the ringing so that it does not affect the results adversely.

**Creating a history plot**

Another way to study the results is to view the time history of stress at three different points within the bar; for example, at distances of 0.25 m, 0.50 m, and 0.75 m from the loaded end of the bar. To do this, we must first determine the labels of the elements located at these positions. An easy way to accomplish this is to query the elements in a display group consisting of the elements along the edge of the bar (set `OUT`).

**To query the element labels:**

-

In the Results Tree, expand the **Element Sets** container underneath the output database file named `Bar.odb`. Click mouse button 3 on the set named **OUT**, and select **Replace** from the menu that appears.
-

From the main menu bar, select **Tools**../images/arrow.gif**Query**; or use the ../graphics/ico_info.png tool in the **Query** toolbar.
-

In the **Query** dialog box that appears, click **Element**.
-

Click on the elements shaded in [Figure 9-10](ch09s04.html#gxi-elemout) (every 13th element along the bar). The element ID (label) appears in the prompt area (and also in the message area). Make note of the element labels for the three shaded elements.

**Figure 9-10** `History plot` display group.

../graphics/gxi-elemout.png

**To plot the stress history:**

-

In the Results Tree, click mouse button 3 on **History Output** and deselect **Group Children** from the menu that appears.
-

Select the data for the three elements you have identified (again, every 13th element). Use **[Ctrl]****+Click** to select multiple *X-Y* data sets.
-

Click mouse button 3, and select **Plot** from the menu that appears.

Abaqus/CAE displays an *X-Y* plot of the longitudinal stress in each element versus time.
-

Click ../graphics/afxI_cancel.png in the prompt area to cancel the current procedure.

As before, you can customize the appearance of the plot.

**To customize the X-Y plot:**

-

Double-click the *X*-axis.

The **Axis Options** dialog box appears.
-

Switch to the **Title** tabbed page.
-

Specify `Total time (s)` as the *X*-axis title.
-

Click **Dismiss** to close the dialog box.

**To customize the appearance of the curves in the X-Y plot:**

-

In the Visualization toolbox, click ../graphics/ico_xyCurveOptions.png to open the **Curve Options** dialog box.
-

In the **Curves** field, select the temporary *X-Y* data label that corresponds to the element closest to the free end of the bar. (Of the elements in this set, this one is affected first by the stress wave.)
-

Enter `S33-0.25` as the curve legend text.
-

In the **Curves** field, select the temporary *X-Y* data label that corresponds to the element in the middle of the bar. (This is the element affected next by the stress wave.)
-

Specify `S33-0.5` as the curve legend text, and change the curve style to dotted.
-

In the **Curves** field, select the temporary *X-Y* data label that corresponds to the element closest to the fixed end of the bar. (This is the element affected last by the stress wave.)
-

Specify `S33-0.75` as the curve legend text, and change the curve style to dashed.
-

Click **Dismiss** to close the dialog box.

The customized plot appears in [Figure 9-11](ch09s04.html#gxi-stressbartimehis-v). (For clarity, the default grid and legend positions have been changed.)

**Figure 9-11** Time history of stress (S33) at three points along the length of the bar (0.25 m, 0.5 m, and 0.75 m).

../graphics/gxi-stressbartimehis-v-nls.png

In the history plot we can see that stress at a given point increases as the stress wave travels through the point. Once the stress wave has passed completely through the point, the stress at the point oscillates about zero.9.4.3 How the mesh affects the stable time increment and CPU time
../images/blu4rule.gif

In ["Automatic time incrementation and stability,"  Section 9.3](ch09s03.html), we discussed how mesh refinement affects the stability limit and the CPU time. Here we will illustrate this effect with the wave propagation problem. We began with a reasonably refined mesh of square elements with 50 elements along the length and 10 elements in each of the two transverse directions. For illustrative purposes, we will now use a coarse mesh of 25  5  5 elements and observe how refining the mesh in the various directions changes the CPU time. The four meshes are shown in [Figure 9-12](ch09s04.html#gxi-meshrefine).

**Figure 9-12** Meshes from least to most refined.

../graphics/gsx-meshrefine.png

[Table 9-1](ch09s04.html#gxi-table1) shows how the CPU time (normalized with respect to the coarse mesh model result) changes with mesh refinement for this problem. The first half of the table provides the expected results, based on the simplified stability equations presented in this guide; the second half of the table provides the results obtained by running the analyses in Abaqus/Explicit on a desktop workstation.

**Table 9-1** Mesh refinement and solution time.

For the theoretical results we choose the coarsest mesh, 25  5  5, as the base state, and we define the stable time increment, the number of elements, and the CPU time as variables A, B, and C, respectively. As the mesh is refined, two things happen: the smallest element dimension decreases, and the number of elements in the mesh increases. Each of these effects increases the CPU time. In the first level of refinement, the 50  5  5 mesh, the smallest element dimension is cut in half and the number of elements is doubled, increasing the CPU time by a factor of four over the previous mesh. However, further doubling the mesh to 50  10  5 does not change the smallest element dimension; it only doubles the number of elements. Therefore, the CPU time increases by only a factor of two over the 50  5  5 mesh. Further refining the mesh so that the elements are uniform and square in the 50  10  10 mesh again doubles the number of elements and the CPU time.

This simplified calculation predicts quite well the trends of how mesh refinement affects the stable time increment and CPU time. However, there are reasons why we did not compare the predicted and actual stable time increment values. First, recall that we made the approximation that the stable time increment is

../graphics/gsa_eqn00166.gifWe then assumed that the characteristic element length, ../graphics/gsa_eqn00157.gif, is the smallest element dimension, whereas Abaqus/Explicit actually determines the characteristic element length based on the overall size and shape of the element. Another complication is that Abaqus/Explicit employs a global stability estimator, which allows a larger stable time increment to be used. These factors make it difficult to predict the stable time increment accurately before running the analysis. However, since the trends follow nicely from the simplified theory, it is straightforward to predict how the stable time increment will change with mesh refinement.9.4.4 How the material affects the stable time increment and CPU time
../images/blu4rule.gif

The same wave propagation analysis performed on different materials would take different amounts of CPU time, depending on the wave speed of the material. For example, if we were to change the material from steel to aluminum, the wave speed would change from 5.15  10^3 m/s to

../graphics/gsa_eqn00167.gifThe change from aluminum to steel has minimal effect on the stable time increment, because the stiffness and the density differ by nearly the same amount. In the case of lead the difference is more substantial, as the wave speed decreases to

../graphics/gsa_eqn00168.gifwhich is approximately one-fifth the wave speed of steel. The stable time increment for the lead bar would be five times the stable time increment of our steel bar.


---


9.5 Damping of dynamic oscillations
../images/blu4rule.gif

There are two reasons for adding damping to a model: to limit numerical oscillations or to add physical damping to the system. Abaqus/Explicit provides several methods of introducing damping into the analysis.9.5.1 Bulk viscosity
../images/blu4rule.gif

Bulk viscosity introduces damping associated with volumetric straining. Its purpose is to improve the modeling of high-speed dynamic events. Abaqus/Explicit contains linear and quadratic forms of bulk viscosity. You can modify the default bulk viscosity parameters in the step definition, although it is rarely necessary to do so. The bulk viscosity pressure is not included in the material point stresses because it is intended as a numerical effect only. As such, it is not considered part of the material's constitutive response.

**Linear bulk viscosity**

By default, linear bulk viscosity is always included to damp "ringing" in the highest element frequency. It generates a bulk viscosity pressure that is linear in the volumetric strain rate, according to the following equation:

../graphics/gsa_eqn00169.gifwhere ../graphics/gsa_eqn00170.gif is a damping coefficient, whose default value is 0.06, ../graphics/gsa_eqn00162.gif is the current material density, ../graphics/gsa_eqn00158.gif is the current dilatational wave speed, ../graphics/gsa_eqn00157.gif is the element characteristic length, and ../graphics/gsa_eqn00171.gif is the volumetric strain rate.

**Quadratic bulk viscosity**

Quadratic bulk viscosity is included only in continuum elements (except for the plane stress element, CPS4R) and is applied only if the volumetric strain rate is compressive. The bulk viscosity pressure is quadratic in the strain rate, according to the following equation:

../graphics/gsa_eqn00172.gifwhere ../graphics/gsa_eqn00173.gif is the damping coefficient, whose default value is 1.2.

The quadratic bulk viscosity smears a shock front across several elements and is introduced to prevent elements from collapsing under extremely high velocity gradients. Consider a simple one-element problem in which the nodes on one side of the element are fixed and the nodes on the other side have an initial velocity in the direction of the fixed nodes, as shown in [Figure 9-13](ch09s05.html#gxi-fixednodes).

**Figure 9-13** Element with fixed nodes and prescribed velocities.

../graphics/gsx-fixednodes.pngThe stable time increment size is precisely the transit time of a dilatational wave across the element. Therefore, if the initial nodal velocity is equal to the dilatational wave speed of the material, the element collapses to zero volume in one time increment. The quadratic bulk viscosity pressure introduces a resisting pressure that prevents the element from collapsing.

**Fraction of critical damping due to bulk viscosity**

The bulk viscosity pressures are based on only the dilatational modes of each element. The fraction of critical damping in the highest element mode is given by the following equation:

../graphics/gsa_eqn00174.gifwhere ../graphics/gsa_eqn00156.gif is the fraction of critical damping. The linear term alone represents 6% of critical damping, whereas the quadratic term is usually much smaller.9.5.2 Viscous pressure
../images/blu4rule.gif

Viscous pressure loads are commonly used in structural problems and quasi-static problems to damp out the low-frequency dynamic effects, thus allowing static equilibrium to be reached in a minimal number of increments. These loads are applied as distributed loads defined by the following formula:

../graphics/gsa_eqn00175.gifwhere ../graphics/gsa_eqn00176.gif is the pressure applied to the body; ../graphics/gsa_eqn00177.gif is the viscosity, given on the data line as the magnitude of the load; ../graphics/gsa_eqn00178.gif is the velocity vector of the point on the surface where the viscous pressure is being applied; and ../graphics/gsa_eqn00179.gif is the unit outward normal vector to the surface at the same point. For typical structural problems it is not desirable to absorb all of the energy. Typically, ../graphics/gsa_eqn00177.gif is set equal to a small percentage--perhaps 1 or 2 percent--of the quantity ../graphics/gsa_eqn00180.gif as an effective way of minimizing ongoing dynamic effects.9.5.3 Material damping
../images/blu4rule.gif

The material model itself may provide damping in the form of plastic dissipation or viscoelasticity. For many applications such damping may be adequate. Another option is to use Rayleigh damping. There are two damping factors associated with Rayleigh damping: ../graphics/gsa_eqn00181.gif for mass proportional damping and ../graphics/gsa_eqn00182.gif for stiffness proportional damping.

**Mass proportional damping**

The ../graphics/gsa_eqn00181.gif factor defines a damping contribution proportional to the mass matrix for an element. The damping forces that are introduced are caused by the absolute velocities of nodes in the model. The resulting effect can be likened to the model moving through a viscous fluid so that any motion of any point in the model triggers damping forces. Reasonable mass proportional damping does not reduce the stability limit significantly.

**Stiffness proportional damping**

The ../graphics/gsa_eqn00182.gif factor defines damping proportional to the elastic material stiffness. A "damping stress," ../graphics/gsa_eqn00183.gif, proportional to the total strain rate is introduced, using the following formula:

../graphics/gsa_eqn00184.gifwhere ../graphics/gsa_eqn00185.gif is the strain rate. For hyperelastic and hyperfoam materials ../graphics/gsa_eqn00186.gif is defined as the initial elastic stiffness. For all other materials ../graphics/gsa_eqn00186.gif is the material's current elastic stiffness. This damping stress is added to the stress caused by the constitutive response at the integration point when the dynamic equilibrium equations are formed, but it is not included in the stress output. Damping can be introduced for any nonlinear analysis and provides standard Rayleigh damping for linear analyses. For a linear analysis stiffness proportional damping is exactly the same as defining a damping matrix equal to ../graphics/gsa_eqn00182.gif times the stiffness matrix. Stiffness proportional damping must be used with caution because it may significantly reduce the stability limit. To avoid a dramatic drop in the stable time increment, the stiffness proportional damping factor, ../graphics/gsa_eqn00182.gif, should be less than or of the same order of magnitude as the initial stable time increment without damping.9.5.4 Discrete dashpots
../images/blu4rule.gif

Yet another option is to define individual dashpot elements. Each dashpot element provides a damping force proportional to the relative velocity of its two nodes. The advantage of this approach is that it enables you to apply damping only at points where you decide it is necessary. Dashpots always should be used in parallel with other elements, such as springs or trusses, so that they do not cause a significant reduction in the stability limit.


---


9.6 Energy balance
../images/blu4rule.gif

Energy output is often an important part of an Abaqus/Explicit analysis. Comparisons between various energy components can be used to help evaluate whether an analysis is yielding an appropriate response.9.6.1 Statement of energy balance
../images/blu4rule.gif

An energy balance for the entire model can be written as

../graphics/gsa_eqn00187.gifwhere ../graphics/gsa_eqn00188.gif is the internal energy, ../graphics/gsa_eqn00189.gif is the viscous energy dissipated, ../graphics/gsa_eqn00190.gif is the frictional energy dissipated, ../graphics/gsa_eqn00191.gif is the kinetic energy, ../graphics/gsa_eqn00192.gif is the internal heat energy, ../graphics/gsa_eqn00193.gif is the work done by the externally applied loads, and ../graphics/gsa_eqn00194.gif, ../graphics/gsa_eqn00195.gif, and ../graphics/gsa_eqn00196.gif are the work done by contact penalties, by constraint penalties, and by propelling added mass, respectively. ../graphics/gsa_eqn00197.gif is the external heat energy through external fluxes. The sum of these energy components is ../graphics/gsa_eqn00198.gif, which should be constant. In the numerical model ../graphics/gsa_eqn00198.gif is only approximately constant, generally with an error of less than 1%.

**Internal energy**

The internal energy is the sum of the recoverable elastic strain energy, ../graphics/gsa_eqn00199.gif; the energy dissipated through inelastic processes such as plasticity, ../graphics/gsa_eqn00200.gif; the energy dissipated through viscoelasticity or creep, ../graphics/gsa_eqn00201.gif; the artificial strain energy, ../graphics/gsa_eqn00202.gif; the energy dissipated through damage, ../graphics/gsa_eqn00203.gif; the energy dissipated through distortion control, ../graphics/gsa_eqn00204.gif; and the fluid cavity energy, ../graphics/gsa_eqn00205.gif:

../graphics/gsa_eqn00206.gifThe artificial strain energy includes energy stored in hourglass resistances and transverse shear in shell and beam elements. Large values of artificial strain energy indicate that mesh refinement or other changes to the mesh are necessary.

**Viscous energy**

The viscous energy is the energy dissipated by damping mechanisms, including bulk viscosity damping and material damping. A fundamental variable in the global energy balance, viscous energy is not part of the energy dissipated through viscoelasticity or inelastic processes.

**External work of applied forces**

The external work is integrated forward continuously, defined entirely by nodal forces (moments) and displacements (rotations). Prescribed boundary conditions also contribute to the external work.

9.6.2 Output of the energy balance
../images/blu4rule.gif

Each of the energy quantities can be requested as output and can be plotted as time histories summed over the entire model, particular element sets, individual elements, or as energy density within each element. The variable names associated with the energy quantities summed over the entire model or element sets are as listed in [Table 9-2](ch09s06.html#gxi-table2).

**Table 9-2** Whole model energy output variables.

In addition, Abaqus/Explicit can produce element-level energy output and energy density output, as listed in [Table 9-3](ch09s06.html#gxi-xpl-table3).

**Table 9-3** Whole element energy output variables.


---


9.7 Summary
../images/blu4rule.gif

-

Abaqus/Explicit uses a central difference rule to integrate the kinematics explicitly through time.
-

The explicit method requires many small time increments. Since there are no simultaneous equations to solve, each increment is inexpensive.
-

The explicit method has great cost savings over the implicit method as the model size increases.
-

The *stability limit* is the maximum time increment that can be used to advance the kinematic state and still remain accurate.
-

Abaqus/Explicit automatically controls the time increment size throughout the analysis to maintain stability.
-

As the material stiffness increases, the stability limit decreases; as the material density increases, the stability limit increases.
-

For a mesh with a single material, the stability limit is roughly proportional to the smallest element dimension.
-

Generally, mass proportional damping is used in Abaqus/Explicit to damp low-frequency oscillations, and stiffness proportional damping is used to damp high-frequency oscillations.


---

