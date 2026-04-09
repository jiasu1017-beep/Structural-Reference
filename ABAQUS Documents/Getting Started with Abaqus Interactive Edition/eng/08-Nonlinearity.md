
8. Nonlinearity
../images/blu4rule.gif

This chapter discusses nonlinear structural analysis in Abaqus. The differences between linear and nonlinear analyses are summarized below.

**Linear analysis**

All the analyses discussed so far have been linear: there is a linear relationship between the applied loads and the response of the system. For example, if a linear spring extends statically by 1 m under a load of 10 N, it will extend by 2 m when a load of 20 N is applied. This means that in a linear Abaqus/Standard analysis the flexibility of the structure need only be calculated once (by assembling the stiffness matrix and inverting it). The linear response of the structure to other load cases can be found by multiplying the new vector of loads by the inverted stiffness matrix. Furthermore, the structure's response to various load cases can be scaled by constants and/or superimposed on one another to determine its response to a completely new load case, provided that the new load case is the sum (or multiple) of previous ones. This principle of superposition of load cases assumes that the same boundary conditions are used for all the load cases.

Abaqus/Standard uses the principle of superposition of load cases in linear dynamics simulations, which are discussed in [Chapter 7, "Linear Dynamics](ch07.html)."

**Nonlinear analysis**

A nonlinear structural problem is one in which the structure's stiffness changes as it deforms. All physical structures exhibit nonlinear behavior. Linear analysis is a convenient approximation that is often adequate for design purposes. It is obviously inadequate for many structural simulations including manufacturing processes, such as forging or stamping; crash analyses; and analyses of rubber components, such as tires or engine mounts. A simple example is a spring with a nonlinear stiffening response (see [Figure 8-1](ch08.html#gss-spring)).

**Figure 8-1** Linear and nonlinear spring characteristics.

../graphics/gss-spring-nls.png

Since the stiffness is now dependent on the displacement, the initial flexibility can no longer be multiplied by the applied load to calculate the spring's displacement for any load. In a nonlinear implicit analysis the stiffness matrix of the structure has to be assembled and inverted many times during the course of the analysis, making it much more expensive to solve than a linear implicit analysis. In an explicit analysis the increased cost of a nonlinear analysis is due to reductions in the stable time increment. The stable time increment is discussed further in [Chapter 9, "Nonlinear Explicit Dynamics](ch09.html)."

Since the response of a nonlinear system is not a linear function of the magnitude of the applied load, it is not possible to create solutions for different load cases by superposition. Each load case must be defined and solved as a separate analysis.


---


8.1 Sources of nonlinearity
../images/blu4rule.gif

There are three sources of nonlinearity in structural mechanics simulations:

-

Material nonlinearity.
-

Boundary nonlinearity.
-

Geometric nonlinearity.
8.1.1 Material nonlinearity
../images/blu4rule.gif

This type of nonlinearity is probably the one that you are most familiar with and is covered in more depth in [Chapter 10, "Materials](ch10.html)." Most metals have a fairly linear stress/strain relationship at low strain values; but at higher strains the material yields, at which point the response becomes nonlinear and irreversible (see [Figure 8-2](ch08s01.html#gss-elastplast)).

**Figure 8-2** Stress-strain curve for an elastic-plastic material under uniaxial tension.

../graphics/gss-elastplast-nls.png

Rubber materials can be approximated by a nonlinear, reversible (elastic) response (see [Figure 8-3](ch08s01.html#gss-rubbertype)).

**Figure 8-3** Stress-strain curve for a rubber-type material.

../graphics/gss-rubbertype-nls.png

Material nonlinearity may be related to factors other than strain. Strain-rate-dependent material data and material failure are both forms of material nonlinearity. Material properties can also be a function of temperature and other predefined fields.8.1.2 Boundary nonlinearity
../images/blu4rule.gif

Boundary nonlinearity occurs if the boundary conditions change during the analysis. Consider the cantilever beam, shown in [Figure 8-4](ch08s01.html#gss-cantilever), that deflects under an applied load until it hits a "stop."

**Figure 8-4** Cantilever beam hitting a stop.

../graphics/gss-cantilever.png

The vertical deflection of the tip is linearly related to the load (if the deflection is small) until it contacts the stop. There is then a sudden change in the boundary condition at the tip of the beam, preventing any further vertical deflection, and so the response of the beam is no longer linear. Boundary nonlinearities are extremely discontinuous: when contact occurs during a simulation, there is a large and instantaneous change in the response of the structure.

Another example of boundary nonlinearity is blowing a sheet of material into a mold. The sheet expands relatively easily under the applied pressure until it begins to contact the mold. From then on the pressure must be increased to continue forming the sheet because of the change in boundary conditions.

Boundary nonlinearity is covered in [Chapter 12, "Contact](ch12.html)."8.1.3 Geometric nonlinearity
../images/blu4rule.gif

The third source of nonlinearity is related to changes in the geometry of the structure during the analysis. Geometric nonlinearity occurs whenever the magnitude of the displacements affects the response of the structure. This may be caused by:

-

Large deflections or rotations.
-

"Snap through."
-

Initial stresses or load stiffening.

For example, consider a cantilever beam loaded vertically at the tip (see [Figure 8-5](ch08s01.html#gss-deflection)).

**Figure 8-5** Large deflection of a cantilever beam.

../graphics/gss-deflection.pngIf the tip deflection is small, the analysis can be considered as being approximately linear. However, if the tip deflections are large, the shape of the structure and, hence, its stiffness changes. In addition, if the load does not remain perpendicular to the beam, the action of the load on the structure changes significantly. As the cantilever beam deflects, the load can be resolved into a component perpendicular to the beam and a component acting along the length of the beam. Both of these effects contribute to the nonlinear response of the cantilever beam (i.e., the changing of the beam's stiffness as the load it carries increases).

One would expect large deflections and rotations to have a significant effect on the way that structures carry loads. However, displacements do not necessarily have to be large relative to the dimensions of the structure for geometric nonlinearity to be important. Consider the "snap through" under applied pressure of a large panel with a shallow curve, as shown in [Figure 8-6](ch08s01.html#gss-snap-through).

**Figure 8-6** Snap-through of a large shallow panel.

../graphics/gss-snap-through-nls.png

In this example there is a dramatic change in the stiffness of the panel as it deforms. As the panel "snaps through," the stiffness becomes negative. Thus, although the magnitude of the displacements, relative to the panel's dimensions, is quite small, there is significant geometric nonlinearity in the simulation, which must be taken into consideration.

An important difference between the analysis products should be noted here: by default, Abaqus/Standard assumes small deformations, while Abaqus/Explicit assumes large deformations.


---


8.2 The solution of nonlinear problems
../images/blu4rule.gif

The nonlinear load-displacement curve for a structure is shown in [Figure 8-7](ch08s02.html#gss-nonlinear).

**Figure 8-7** Nonlinear load-displacement curve.

../graphics/gss-nonlinear-nls.pngThe objective of the analysis is to determine this response. Consider the external forces, *P*, and the internal (nodal) forces, *I*, acting on a body (see [Figure 8-8](ch08s02.html#gss-loads)(a) and [Figure 8-8](ch08s02.html#gss-loads)(b), respectively).

**Figure 8-8** Internal and external loads on a body.

../graphics/gss-loads-nls.pngThe internal loads acting on a node are caused by the stresses in the elements that contain that node.

For the body to be in static equilibrium, the net force acting at every node must be zero. Therefore, the basic statement of static equilibrium is that the internal forces, *I*, and the external forces, *P*, must balance each other:

../graphics/gsa_eqn00093.gif

Abaqus/Standard uses the Newton-Raphson method to obtain solutions for nonlinear problems. In a nonlinear analysis the solution usually cannot be calculated by solving a single system of equations, as would be done in a linear problem. Instead, the solution is found by applying the specified loads gradually and incrementally working toward the final solution. Therefore, Abaqus/Standard breaks the simulation into a number of *load increments* and finds the approximate equilibrium configuration at the end of each load increment. It often takes Abaqus/Standard several iterations to determine an acceptable solution to a given load increment. The sum of all of the incremental responses is the approximate solution for the nonlinear analysis. Thus, Abaqus/Standard combines incremental and iterative procedures for solving nonlinear problems.

Abaqus/Explicit determines a solution to the dynamic equilibrium equation ../graphics/gsa_eqn00094.gif without iterating by explicitly advancing the kinematic state from the end of the previous increment. Solving a problem explicitly does not require the formation of tangent stiffness matrices. The explicit central-difference operator satisfies the dynamic equilibrium equations at the beginning of the increment, *t*; the accelerations calculated at time *t* are used to advance the velocity solution to time ../graphics/gsa_eqn00095.gif and the displacement solution to time ../graphics/gsa_eqn00096.gif. For linear and nonlinear problems alike, explicit methods require a small time increment size that depends solely on the highest natural frequency of the model and is independent of the type and duration of loading. Simulations typically require a large number of increments; however, due to the fact that a global set of equations is not solved in each increment, the cost per increment of an explicit method is much smaller than that of an implicit method. The small increments characteristic of an explicit dynamic method make Abaqus/Explicit well suited for nonlinear analysis.8.2.1 Steps, increments, and iterations
../images/blu4rule.gif

This section introduces some new vocabulary for describing the various parts of an analysis. It is important that you clearly understand the difference between an analysis *step*, a load *increment*, and an *iteration*.

-

The load history for a simulation consists of one or more steps. You define the steps, which generally consist of an analysis procedure option, loading options, and output request options. Different loads, boundary conditions, analysis procedure options, and output requests can be used in each step. For example:
-

Step 1: Hold a plate between rigid jaws.
-

Step 2: Add loads to deform the plate.
-

Step 3: Find the natural frequencies of the deformed plate.

-

An increment is part of a step. In nonlinear analyses the total load applied in a step is broken into smaller increments so that the nonlinear solution path can be followed.

In Abaqus/Standard you suggest the size of the first increment, and Abaqus/Standard automatically chooses the size of the subsequent increments. In Abaqus/Explicit the default time incrementation is fully automatic and does not require user intervention. Because the explicit method is conditionally stable, there is a stability limit for the time increment. The stable time increment is discussed in [Chapter 9, "Nonlinear Explicit Dynamics](ch09.html)."

At the end of each increment the structure is in (approximate) equilibrium and results are available for writing to the output database, restart, data, or results files. The increments at which you select results to be written to the output database file are called *frames*.

The issues associated with time incrementation in Abaqus/Standard and Abaqus/Explicit analyses are quite different, since time increments are generally much smaller in Abaqus/Explicit.
-

An iteration is an attempt at finding an equilibrium solution in an increment when solving with an implicit method. If the model is not in equilibrium at the end of the iteration, Abaqus/Standard tries another iteration. With every iteration the solution Abaqus/Standard obtains should be closer to equilibrium; sometimes Abaqus/Standard may need many iterations to obtain an equilibrium solution. When an equilibrium solution has been obtained, the increment is complete. Results can be requested only at the end of an increment.

Abaqus/Explicit does not need to iterate to obtain the solution in an increment.
8.2.2 Equilibrium iterations and convergence in Abaqus/Standard
../images/blu4rule.gif

The nonlinear response of a structure to a small load increment, ../graphics/gsa_eqn00097.gif, is shown in [Figure 8-9](ch08s02.html#gss-first-iteration). Abaqus/Standard uses the structure's initial stiffness, ../graphics/gsa_eqn00098.gif, which is based on its configuration at ../graphics/gsa_eqn00099.gif, and ../graphics/gsa_eqn00097.gif to calculate a *displacement correction*, ../graphics/gsa_eqn00100.gif, for the structure. Using ../graphics/gsa_eqn00100.gif, the structure's configuration is updated to ../graphics/gsa_eqn00101.gif.

**Figure 8-9** First iteration in an increment.

../graphics/gss-first-iteration-nls.png

**Convergence**

Abaqus/Standard forms a new stiffness, ../graphics/gsa_eqn00102.gif, for the structure, based on its updated configuration, ../graphics/gsa_eqn00101.gif. Abaqus/Standard also calculates ../graphics/gsa_eqn00103.gif, in this updated configuration. The difference between the total applied load, *P*, and ../graphics/gsa_eqn00103.gif can now be calculated as:

../graphics/gsa_eqn00104.gifwhere ../graphics/gsa_eqn00105.gif is the *force residual* for the iteration.

If ../graphics/gsa_eqn00105.gif is zero at every degree of freedom in the model, point *a* in [Figure 8-9](ch08s02.html#gss-first-iteration) would lie on the load-deflection curve, and the structure would be in equilibrium. In a nonlinear problem it is almost impossible to have ../graphics/gsa_eqn00105.gif equal zero, so Abaqus/Standard compares it to a tolerance value. If ../graphics/gsa_eqn00105.gif is less than this force residual tolerance, Abaqus/Standard accepts the structure's updated configuration as the equilibrium solution. By default, this tolerance value is set to 0.5% of an average force in the structure, averaged over time. Abaqus/Standard automatically calculates this spatially and time-averaged force throughout the simulation.

If ../graphics/gsa_eqn00105.gif is less than the current tolerance value, *P* and ../graphics/gsa_eqn00103.gif are in equilibrium, and ../graphics/gsa_eqn00101.gif is a valid equilibrium configuration for the structure under the applied load. However, before Abaqus/Standard accepts the solution, it also checks that the displacement correction, ../graphics/gsa_eqn00100.gif, is small relative to the total incremental displacement, ../graphics/gsa_eqn00106.gif. If ../graphics/gsa_eqn00100.gif is greater than 1% of the incremental displacement, Abaqus/Standard performs another iteration. Both convergence checks must be satisfied before a solution is said to have *converged* for that load increment. The exception to this rule is the case of a *linear* increment, which is defined as any increment in which the largest force residual is less than 10^8 times the time-averaged force. Any case that passes such a stringent comparison of the largest force residual with the time-averaged force is considered linear and does not require further iteration. The solution is accepted without any check on the size of the displacement correction.

If the solution from an iteration is not converged, Abaqus/Standard performs another iteration to try to bring the internal and external forces into balance. This second iteration uses the stiffness, ../graphics/gsa_eqn00102.gif, calculated at the end of the previous iteration together with ../graphics/gsa_eqn00105.gif to determine another displacement correction, ../graphics/gsa_eqn00107.gif, that brings the system closer to equilibrium (point *b* in [Figure 8-10](ch08s02.html#gss-second-iteration)).

**Figure 8-10** Second iteration.

../graphics/gss-second-iteration-nls.png

Abaqus/Standard calculates a new force residual, ../graphics/gsa_eqn00108.gif, using the internal forces from the structure's new configuration, ../graphics/gsa_eqn00109.gif. Again, the largest force residual at any degree of freedom, ../graphics/gsa_eqn00108.gif, is compared against the force residual tolerance, and the displacement correction for the second iteration, ../graphics/gsa_eqn00107.gif, is compared to the increment of displacement, ../graphics/gsa_eqn00110.gif. If necessary, Abaqus/Standard performs further iterations.

For each iteration in a nonlinear analysis Abaqus/Standard forms the model's stiffness matrix and solves a system of equations. This means that each iteration is equivalent, in computational cost, to conducting a complete linear analysis. It should now be clear that the computational expense of a nonlinear analysis in Abaqus/Standard can be many times greater than for a linear one.

It is possible with Abaqus/Standard to save results at each converged increment. Thus, the amount of output data available from a nonlinear simulation is many times that available from a linear analysis of the same geometry. Consider both of these factors and the types of nonlinear simulations that you want to perform when planning your computer resources.8.2.3 Automatic incrementation control in Abaqus/Standard
../images/blu4rule.gif

Abaqus/Standard automatically adjusts the size of the load increments so that it solves nonlinear problems easily and efficiently. You only need to suggest the size of the first increment in each step of your simulation. Thereafter, Abaqus/Standard automatically adjusts the size of the increments. If you do not provide a suggested initial increment size, Abaqus/Standard will try to apply all of the loads defined in the step in the first increment. In highly nonlinear problems Abaqus/Standard will have to reduce the increment size repeatedly, resulting in wasted CPU time. Generally it is to your advantage to provide a reasonable initial increment size (see ["Modifications to the model,"  Section 8.4.1](ch08s04.html#gsa-nln-modhistory), for an example); only in very mildly nonlinear problems can all of the loads in a step be applied in a single increment.

The number of iterations needed to find a converged solution for a load increment will vary depending on the degree of nonlinearity in the system. By default, if the solution appears to diverge, Abaqus/Standard abandons the increment and starts again with the increment size set to 25% of its previous value. An attempt is then made at finding a converged solution with this smaller load increment. If the increment still fails to converge, Abaqus/Standard reduces the increment size again. By default, Abaqus/Standard allows a maximum of five cutbacks of increment size in an increment before stopping the analysis.

In Abaqus/Standard you can also specify the maximum number of increments allowed during the step. Abaqus/Standard terminates the analysis with an error message if it needs more increments than this limit to complete the step. The default number of increments for a step is 100; if significant nonlinearity is present in the simulation, the analysis may require many more increments. You specify an upper limit on the number of increments that Abaqus/Standard can use, rather than the number of increments it must use.

In a nonlinear analysis a step takes place over a finite period of "time," although this "time" has no physical meaning unless inertial effects or rate-dependent behavior are present. In Abaqus/Standard you specify the initial time increment, ../graphics/gsa_eqn00111.gif, and the total step time, ../graphics/gsa_eqn00112.gif. The ratio of the initial time increment to the step time specifies the proportion of load applied in the first increment. The initial load increment is given by

../graphics/gsa_eqn00113.gifThe choice of initial time increment can be critical in certain nonlinear simulations in Abaqus/Standard, but for most analyses an initial increment size that is 5% to 10% of the total step time is usually sufficient. In static simulations the total step time is usually set to 1.0 for convenience, unless, for example, rate-dependent material effects or dashpots are included in the model. With a total step time of 1.0 the proportion of load applied is always equal to the current step time; i.e., 50% of the total load is applied when the step time is 0.5.

Although you must specify the initial increment size in Abaqus/Standard, Abaqus/Standard automatically controls the size of the subsequent increments. This automatic control of the increment size is suitable for the majority of nonlinear simulations performed with Abaqus/Standard, although further controls on the increment size are available. Abaqus/Standard will terminate an analysis if excessive cutbacks caused by convergence problems reduce the increment size below the minimum value. The default minimum allowable time increment, ../graphics/gsa_eqn00114.gif, is 10^5 times the total step time. By default, Abaqus/Standard has no upper limit on the increment size, ../graphics/gsa_eqn00115.gif, other than the total step time. Depending on your Abaqus/Standard simulation, you may want to specify different minimum and/or maximum allowable increment sizes. For example, if you know that your simulation may have trouble obtaining a solution if too large a load increment is applied, perhaps because the model may undergo plastic deformation, you may want to decrease ../graphics/gsa_eqn00115.gif.

If the increment converges in fewer than five iterations, this indicates that the solution is being found fairly easily. Therefore, Abaqus/Standard automatically increases the increment size by 50% if two consecutive increments require fewer than five iterations to obtain a converged solution.

Details of the automatic load incrementation scheme are given in the **Job Diagnostics** dialog box, as shown in more detail in ["Job diagnostics,"  Section 8.4.2](ch08s04.html#gsa-nln-results).


---


8.3 Including nonlinearity in an Abaqus analysis
../images/blu4rule.gif

We now discuss how to account for nonlinearity in an Abaqus analysis. The main focus is on geometric nonlinearity.8.3.1 Geometric nonlinearity
../images/blu4rule.gif

Incorporating the effects of geometric nonlinearity in an analysis requires only minor changes to an Abaqus/Standard model. You need to make sure the step definition considers geometrically nonlinear effects. This is the default setting in Abaqus/Explicit. You also need to set time incrementation parameters as discussed in ["Automatic incrementation control in Abaqus/Standard,"  Section 8.2.3](ch08s02.html#gsa-nln-automatic).

**Local directions**

In a geometrically nonlinear analysis the local material directions may rotate with the deformation in each element. For shell, beam, and truss elements the local material directions always rotate with the deformation. For solid elements the local material directions rotate with the deformation only if the elements refer to nondefault local material directions; otherwise, the default local material directions remain constant throughout the analysis.

Local directions defined at nodes remain fixed throughout the analysis; they do not rotate with the deformation. See "Transformed coordinate systems,"  Section 2.1.5 of the Abaqus Analysis User's Guide, for further details.

**Effect on subsequent steps**

Once you include geometric nonlinearity in a step, it is considered in all subsequent steps. If nonlinear geometric effects are not requested in a subsequent step, Abaqus will issue a warning stating that they are being included in the step anyway.

**Other geometrically nonlinear effects**

The large deformations in a model are not the only important effects that are considered when geometric nonlinearity is activated. Abaqus/Standard also includes terms in the element stiffness calculations that are caused by the applied loads, the so-called load stiffness. These terms improve convergence behavior. In addition, the membrane loads in shells and the axial loads in cables and beams contribute much of the stiffness of these structures in response to transverse loads. By including geometric nonlinearity, the membrane stiffness in response to transverse loads is considered as well.8.3.2 Material nonlinearity
../images/blu4rule.gif

The addition of material nonlinearity to an Abaqus model is discussed in [Chapter 10, "Materials](ch10.html)."8.3.3 Boundary nonlinearity
../images/blu4rule.gif

The introduction of boundary nonlinearity is discussed in [Chapter 12, "Contact](ch12.html)."


---


8.4 Example: nonlinear skew plate
../images/blu4rule.gif

This example is a continuation of the linear skew plate simulation described in [Chapter 5, "Using Shell Elements](ch05.html)," and shown in [Figure 8-11](ch08s04.html#gss-skewplate).

**Figure 8-11** Skew plate.

../graphics/gss-skewplate-nls.pngYou will now reanalyze the plate in Abaqus/Standard to include the effects of geometric nonlinearity. The results from this analysis will allow you to determine the importance of geometrically nonlinear effects and, therefore, the validity of the linear analysis.

If you wish, you can follow the guidelines at the end of this example to extend the simulation to perform a dynamic analysis using Abaqus/Explicit.

Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:

-

A Python script for this example is provided in ["Nonlinear skew plate,"  Section A.6](ap01s06.html). Instructions on how to fetch the script and run it within Abaqus/CAE are given in [Appendix A, "Example Files](ap01.html)."
-

A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins**../images/arrow.gif**Abaqus**../images/arrow.gif**Getting Started**; highlight **Nonlinear skew plate**; and click **Run**. For more information about the Getting Started plug-ins, see "Running the Getting Started with Abaqus examples,"  Section 82.1 of the Abaqus/CAE User's Guide.

If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in "Example: nonlinear skew plate,"  Section 8.4 of Getting Started with Abaqus: Keywords Edition.8.4.1 Modifications to the model
../images/blu4rule.gif

Open the model database file `SkewPlate.cae`. Copy the model named `Linear` to a model named `Nonlinear`.

For the `Nonlinear` skew plate model, you will include nonlinear geometric effects as well as change the output requests.

**Defining the step**

In the Model Tree, double-click the **Apply Pressure** step underneath the **Steps** container to edit the step definition. In the **Basic** tabbed page of the **Edit Step** dialog box, toggle on **Nlgeom** to include geometric nonlinearity effects, and ensure the time period for the step is set to `1.0`. In the **Incrementation** tabbed page, set the initial increment size to `0.1`. The default maximum number of increments is `100`; Abaqus may use fewer increments than this upper limit, but it will stop the analysis if it needs more.

You may wish to change the description of the step to reflect that it is now a nonlinear analysis step.

**Output control**

In a linear analysis Abaqus solves the equilibrium equations once and calculates the results for this one solution. A nonlinear analysis can produce much more output because results can be requested at the end of each converged increment. If you do not select the output requests carefully, the output files become very large, potentially filling the disk space on your computer.

As noted earlier, output is available in four different files:

-

the output database (`.odb`) file, which contains data in a neutral binary format necessary to postprocess the results with Abaqus/CAE;
-

the data (`.dat`) file, which contains printed tables of selected results (available only in Abaqus/Standard);
-

the restart (`.res`) file, which is used to continue the analysis; and
-

the results (`.fil`) file, which is used with third-party postprocessors.

Only the output database (`.odb`) file is discussed here. If selected carefully, data can be saved frequently during the simulation without using excessive disk space.

Open the **Field Output Requests Manager**. On the right side of the dialog box, click **Edit** to open the field output editor. Remove the field output requests defined for the linear analysis model, and specify the default field output requests by selecting **Preselected defaults** under **Output Variables**. This preselected set of output variables is the most commonly used set of field variables for a general static procedure.

To reduce the size of the output database file, write field output every second increment. If you were simply interested in the final results, you could either select **Last increment** or set the frequency at which output is saved equal to a large number. Results are always stored at the end of each step, regardless of the value specified; therefore, using a large value causes only the final results to be saved.

The history output request for the displacements of the nodes at the midspan can be kept from the previous analysis. You will explore these results using the *X-Y* plotting capability in the Visualization module.

**Running and monitoring the job**

Create a job for the `Nonlinear` model named `NlSkewPlate`, and give it the description `Nonlinear Elastic Skew Plate`. Remember to save your model in a new model database file.

Submit the job for analysis, and monitor the solution progress. If any errors are encountered, correct them; if any warning messages are issued, investigate their source and take corrective action as necessary.

[Figure 8-12](ch08s04.html#gsi-nlskew-job-monitor) shows the contents of the **Job Monitor** for this nonlinear skew plate simulation.

**Figure 8-12** **Job Monitor**: nonlinear skew plate analysis.

../graphics/gsi-nlskew-job-monitor-nls.pngThe first column shows the step number--in this case there is only one step. The second column gives the increment number. The sixth column shows the number of iterations Abaqus/Standard needed to obtain a converged solution in each increment; for example, Abaqus/Standard needed four iterations in increment 1. The eighth column shows the total step time completed, and the ninth column shows the increment size (../graphics/gsa_eqn00116.gif).

This example shows how Abaqus/Standard automatically controls the increment size and, therefore, the proportion of load applied in each increment. In this analysis Abaqus/Standard applied 10% of the total load in the first increment: you specified ../graphics/gsa_eqn00111.gif to be 0.1 and the step time to be 1.0. Abaqus/Standard needed four iterations to converge to a solution in the first increment. Abaqus/Standard only needed two iterations in the second increment, so it automatically increased the size of the next increment by 50% to ../graphics/gsa_eqn00117.gif = 0.15. Abaqus/Standard also increased ../graphics/gsa_eqn00116.gif in both the fourth and fifth increments. It adjusted the final increment size to be just enough to complete the analysis; in this case the final increment size was 0.0875.8.4.2 Job diagnostics
../images/blu4rule.gif

In addition to allowing you to monitor the progress of your analysis job, Abaqus/CAE provides a visual diagnostics tool to help you understand the convergence behavior of your job and debug the model if necessary. Abaqus/Standard stores information in the output database for each step, increment, attempt, and iteration of an analysis. This diagnostic information is saved automatically for every job that you run. If an analysis takes longer than expected or terminates prematurely, you can view the job diagnostic information in Abaqus/CAE to help determine the cause and to identify ways to correct the model.

Enter the Visualization module, and open the output database file `NlSkewPlate.odb` to examine the convergence history. From the main menu bar, select **Tools**../images/arrow.gif**Job Diagnostics** to open the **Job Diagnostics** dialog box. Click the "../graphics/gsa_eqn00025.gif" symbols in the **Job History** list to expand the list to include the steps, increments, attempts, and iterations in the analysis job. For example, under **Increment 1**, select **Attempt 1**, as shown in [Figure 8-13](ch08s04.html#gsi-nlskew-inc1-summary).

**Figure 8-13** Summary information for the first attempt of the first increment.

../graphics/gsi-nlskew-inc1-summary-nls.pngThe **Attempt** information on the right side of the dialog box contains basic information such as the increment size; the **Iterations** information contains the number of iterations attempted. Select **Iteration 1** of this attempt to see detailed information regarding the first iteration. The information on the **Summary** tabbed page tells you that convergence was not achieved in this iteration, so click the **Residuals** tab to understand why.

As shown in [Figure 8-14](ch08s04.html#gsi-nlskew-iter1-dsp), the **Residuals** tabbed page displays the values of the average force, ../graphics/gsa_eqn00118.gif, and time average force, ../graphics/gsa_eqn00119.gif, in the model.

**Figure 8-14** Force residual information for the first iteration.

../graphics/gsi-nlskew-iter1-dsp-nls.pngIt also displays the values of the largest residual force, ../graphics/gsa_eqn00120.gif, the largest increment of displacement, ../graphics/gsa_eqn00121.gif, and the largest correction to displacement, ../graphics/gsa_eqn00122.gif, as well as the nodes and degrees of freedom (DOF) at which these occur. The location in the model where any of these occur can be highlighted in the viewport by toggling on **Highlight selection in viewport** at the bottom of the dialog box. The selection of the diagnostic criterion is persistent. Thus, you can click your way through the list of iterations on the left side of the dialog box to quickly see how the location associated with a given criterion changes throughout the iteration history. This may prove very useful if you are trying to debug a large, complex model. A similar display is available for rotational degrees of freedom (select **Rotation** under the list of **Variables**).

In this example the initial time increment is 0.1, as specified in the step definition. The average force for the increment is 12.2 N; and the time average force, ../graphics/gsa_eqn00119.gif, has the same value since this is the first increment. The largest residual force in the model, ../graphics/gsa_eqn00120.gif, is 749.6 N, which is clearly greater than 0.005  ../graphics/gsa_eqn00123.gif. ../graphics/gsa_eqn00120.gif occurred at node 167 in degree of freedom 1 (your values and node numbers may vary). Abaqus/Standard must also check for equilibrium of the moments in the model since this model includes shell elements. The moment/rotation field also failed to satisfy the equilibrium check.

Although failure to satisfy the equilibrium check is enough to cause Abaqus/Standard to try another iteration, you should also examine the displacement correction. In the first iteration of the first increment of the first step the largest increment of displacement, ../graphics/gsa_eqn00124.gif, and the largest correction to displacement, ../graphics/gsa_eqn00125.gif, are both 5.578  10^3 m; and the largest increment of rotation and correction to rotation are both 1.598  10^2 radians. Since the incremental values and the corrections are always equal in the first iteration of the first increment of the first step, the check that the largest corrections to nodal variables are less than 1% of the largest incremental values will always fail. However, if Abaqus/Standard judges the solution to be linear (a judgement based on the magnitude of the residuals, ../graphics/gsa_eqn00120.gif < 10^8../graphics/gsa_eqn00119.gif), it will ignore this criterion.

Since Abaqus/Standard did not find an equilibrium solution in the first iteration, it tries a second iteration. The residual information for the second iteration is shown in [Figure 8-15](ch08s04.html#gsi-nlskew-iter2-dsp).

**Figure 8-15** Force residual information for the second iteration.

../graphics/gsi-nlskew-iter2-dsp-nls.png

In the second iteration ../graphics/gsa_eqn00120.gif has fallen to 0.173 N at node 167 in degree of freedom 1. However, equilibrium is not satisfied in this iteration because 0.005  ../graphics/gsa_eqn00123.gif, where ../graphics/gsa_eqn00123.gif = 1.00 N, is still less than ../graphics/gsa_eqn00120.gif. The displacement correction criterion also failed again because ../graphics/gsa_eqn00126.gif = 7.055  10^5, which occurred at node 5 in degree of freedom 1, is more than 1% of ../graphics/gsa_eqn00127.gif = 5.584  10^3, the maximum displacement increment.

Both the moment residual check and the largest correction to rotation check were satisfied in this second iteration; however, Abaqus/Standard must perform two more iterations because the solutions did not pass the force residual check (or the largest correction to displacement criterion). The residual information for the additional iterations necessary to obtain a solution in the first increment are shown in [Figure 8-16](ch08s04.html#gsi-nlskew-iter3-dsp) and [Figure 8-17](ch08s04.html#gsi-nlskew-iter4-dsp).

**Figure 8-16** Force residual information for the third iteration.

../graphics/gsi-nlskew-iter3-dsp-nls.png

**Figure 8-17** Force residual information for the fourth iteration.

../graphics/gsi-nlskew-iter4-dsp-nls.png

After the fourth iteration ../graphics/gsa_eqn00123.gif = 0.997 N and ../graphics/gsa_eqn00128.gif = 1.794  10^7 N at node 76 in degree of freedom 1. These values satisfy ../graphics/gsa_eqn00128.gif< 0.005  ../graphics/gsa_eqn00123.gif, so the force residual check is satisfied. Comparing ../graphics/gsa_eqn00125.gif to the largest increment of displacement shows that the displacement correction is below the required tolerance. The solution for the forces and displacements has, therefore, converged. The checks for both the moment residual and the rotation correction continue to be satisfied, as they have been since the second iteration. With a solution that satisfies equilibrium for all variables (displacement and rotation in this case), the first load increment is complete. The attempt summary ([Figure 8-13](ch08s04.html#gsi-nlskew-inc1-summary)) shows the number of iterations that were required for this increment and the size of the increment.

Abaqus/Standard continues this process of applying an increment of load then iterating to find a solution until it completes the whole analysis (or reaches the maximum increment that you specified). In this analysis it required five more increments. The step summary is shown in [Figure 8-18](ch08s04.html#gsi-nlskew-job-summary).

**Figure 8-18** Analysis step summary.

../graphics/gsi-nlskew-job-summary-nls.png

In addition to the residual information discussed above, analysis warning messages related to numerical singularities, zero pivots, and negative eigenvalues, if they exist, are displayed in the **Job Diagnostics** dialog box (in the **Warnings** tabbed page). Always investigate the cause of these warnings.8.4.3 Postprocessing
../images/blu4rule.gif

You will now postprocess the results.

**Showing the available frames**

To begin this exercise, determine the available output frames (the increment intervals at which results were written to the output database).

**To show the available frames:**

-

From the main menu bar, select **Result**../images/arrow.gif**Step/Frame**.

The **Step/Frame** dialog box appears.

During the analysis Abaqus/Standard wrote field output results to the output database file every second increment, as was requested. Abaqus/Viewer displays the list of the available frames, as shown in [Figure 8-19](ch08s04.html#gss-c7-frame-selector-v).

**Figure 8-19** Available frames.

../graphics/gsk-c7-frame-selector-c-nls.png

The list tabulates the steps and increments for which field variables are stored. This analysis consisted of a single step with six increments. The results for increment 0 (the initial state of the step) are saved by default, and you saved data for increments 2, 4, and 6. By default, Abaqus/CAE always uses the data for the last available increment saved in the output database file.
-

Click **OK** to dismiss the **Step/Frame** dialog box.

**Displaying the deformed and undeformed model shapes**

Use the **Allow Multiple Plot States** ../graphics/ico_plotMultipleStates.png tool to display the deformed model shape with the undeformed model shape superimposed. Set the render style for both images to wireframe, and toggle off the translucency of the superimposed plot from the **Superimpose Plot Options** dialog box. Rotate the view to obtain a plot similar to that shown in [Figure 8-20](ch08s04.html#gss-deform-plate-v). By default, the deformed shape is plotted for the last increment. (For clarity, the edges of the undeformed shape are plotted using a dashed style.)

**Figure 8-20** Deformed and undeformed model shapes of the skew plate.

../graphics/gss-deform-plate-c.png

**Using results from other frames**

You can evaluate the results from other increments saved to the output database file by selecting the appropriate frame.

**To select a new frame:**

-

From the main menu bar, select **Result**../images/arrow.gif**Step/Frame**.

The **Step/Frame** dialog box appears.
-

Select `Increment 4` from the **Frame** menu.
-

Click **OK** to apply your changes and to close the **Step/Frame** dialog box.

Any plots now requested will use results from increment 4. Repeat this procedure, substituting the increment number of interest, to move through the output database file.

Note:
Alternatively, you may use the **Frame Selector** dialog box to select a results frame.

**X-Y plotting**

You saved the displacements of the midspan nodes (node set `Midspan`) in the history portion of the output database file `NlSkewPlate.odb` for each increment of the simulation. You can use these results to create *X-Y* plots. In particular, you will plot the vertical displacement history of the nodes located at the edges of the plate midspan.

**To create X-Y plots of the midspan displacements:**

-

First, display only the nodes in the node set named `Midspan`: in the Results Tree, expand the **Node Sets** container underneath the output database file named `NlSkewPlate.odb`. Click mouse button 3 on the set named **MIDSPAN**, and select **Replace** from the menu that appears.
-

Use the **Common Plot Options** dialog box to show the node labels (i.e., numbers) to determine which nodes are located at the edges of the plate midspan.
-

In the Results Tree, expand the **History Output** container for the output database named `NlSkewPlate.odb`.
-

Locate the output labeled as follows: `Spatial displacement: U3 at Node *xxx* in NSET MIDSPAN`. Each of these curves represents the vertical motion of one of the midspan nodes.
-

Select (using **[Ctrl]****+Click**) the vertical motion of the two midspan edge nodes. Use the node labels to determine which curves you need to select.
-

Click mouse button 3, and select **Plot** from the menu that appears.

Abaqus reads the data for both curves from the output database file and plots a graph similar to the one shown in [Figure 8-21](ch08s04.html#gss-midspan-v). (For clarity, the second curve has been changed to a dashed line, and the default grid and legend positions have been changed.)

**Figure 8-21** Midspan displacement history at the edges of the skew plate.

../graphics/gss-midspan-c-nls.png

The nonlinear nature of this simulation is clearly seen in these curves: as the analysis progresses, the plate stiffens. In this simulation the increase in the plate stiffness with the deformation is due to membrane effects. Therefore, the resulting peak displacement is less than that predicted by the linear analysis, which did not include this effect.

You can create *X-Y* curves from either history or field data stored in the output database (`.odb`) file. *X-Y* curves can also be read from an external file or they can be typed into the Visualization module interactively. Once curves have been created, their data can be further manipulated and plotted to the screen in graphical form.

The *X-Y* plotting capability of the Visualization module is discussed further in [Chapter 10, "Materials](ch10.html)."

**Tabular data**

Create a tabular data report of the midspan displacements. Use the node set `Midspan` to create the appropriate display group and the frame selector to choose the final frame. The contents of the report are shown below.```
Field Output Report

Source 1
---------

ODB: NlSkewPlate.odb
Step: Apply pressure
Frame: Increment      6: Step Time =    1.000

Loc 1 : Nodal values from source 1

Output sorted by column "Node Label".

Field Output reported at nodes for part: PLATE-1

Node            U.U1            U.U2            U.U3
Label          @Loc 1          @Loc 1          @Loc 1
-----------------------------------------------------------------
1    -2.68697E-03    -747.394E-06    -49.4696E-03
2    -2.27869E-03    -806.331E-06    -45.4817E-03
7    -2.57405E-03    -759.298E-06    -48.5985E-03
8    -2.49085E-03    -775.165E-06    -47.7038E-03
9     -2.4038E-03    -793.355E-06     -46.533E-03
66    -2.62603E-03    -750.246E-06    -49.0086E-03
70    -2.53886E-03    -762.497E-06    -48.1876E-03
73    -2.45757E-03    -778.207E-06     -47.144E-03
76    -2.36229E-03    -794.069E-06    -45.9613E-03

Minimum           -2.68697E-03    -806.331E-06    -49.4696E-03

At Node               1               2               1
Maximum           -2.27869E-03    -747.394E-06    -45.4817E-03

At Node               2               1               2

```

Compare these with the displacements from the linear analysis in [Chapter 5, "Using Shell Elements](ch05.html)." The maximum displacement at the midspan in this simulation is about 9% less than that predicted from the linear analysis. Including the nonlinear geometric effects in the simulation reduces the vertical deflection (U3) of the midspan of the plate.

Another difference between the two analyses is that in the nonlinear simulation there are nonzero deflections in the 1- and 2-directions. What effects make the in-plane displacements, U1 and U2, nonzero in the nonlinear analysis? Why is the vertical deflection of the plate less in the nonlinear analysis?

The plate deforms into a curved shape: a geometry change that is taken into account in the nonlinear simulation. As a consequence, membrane effects cause some of the load to be carried by membrane action rather than by bending alone. This makes the plate stiffer. In addition, the pressure loading, which is always normal to the plate's surface, starts to have a component in the 1- and 2-directions as the plate deforms. The nonlinear analysis includes the effects of this stiffening and the changing direction of the pressure. Neither of these effects is included in the linear simulation.

The differences between the linear and nonlinear simulations are sufficiently large to indicate that a linear simulation is not adequate for this plate under this particular loading condition.8.4.4 Running the analysis in Abaqus/Explicit
../images/blu4rule.gif

As an optional exercise, you can modify the model and run a dynamic analysis of the skew plate in Abaqus/Explicit. To do so, you must add a density of 7800 kg/m^3 to the material definition, replace the existing step with an explicit dynamic step, and change the element library to **Explicit**. After making the appropriate model changes, you can create and run a new job to examine the transient dynamic effects in the plate under a suddenly applied load.


---


8.5 Related Abaqus examples
../images/blu4rule.gif

-

"Elastic-plastic collapse of a thin-walled elbow under in-plane bending and internal pressure,"  Section 1.1.2 of the Abaqus Example Problems Guide
-

"Laminated composite shells: buckling of a cylindrical panel with a circular hole,"  Section 1.2.2 of the Abaqus Example Problems Guide
-

"Unstable static problem: reinforced plate under compressive loads,"  Section 1.2.5 of the Abaqus Example Problems Guide
-

"Large rotation of a one degree of freedom system,"  Section 1.3.5 of the Abaqus Benchmarks Guide
-

"Vibration of a cable under tension,"  Section 1.4.3 of the Abaqus Benchmarks Guide


---


8.6 Suggested reading
../images/blu4rule.gif

The following references provide additional information on nonlinear finite element methods. They allow the interested user to explore the topic in more depth.

**General texts on nonlinear finite element analysis**

-

Belytschko, T., W. K. Liu, and B. Moran, *Nonlinear Finite Elements for Continua and Structures*, Wiley & Sons, 2000.
-

Bonet, J., and R. D. Wood, *Nonlinear Continuum Mechanics for Finite Element Analysis*, Cambridge, 1997.
-

Cook, R. D., D. S. Malkus, and M. E. Plesha, *Concepts and Applications of Finite Element Analysis*, Wiley & Sons, 1989.
-

Crisfield, M. A., *Non-linear Finite Element Analysis of Solids and Structures, Volume I: Essentials*, Wiley & Sons, 1991.
-

Crisfield, M. A., *Non-linear Finite Element Analysis of Solids and Structures, Volume II: Advanced Topics*, Wiley & Sons, 1997.
-

E. Hinton (editor), *NAFEMS Introduction to Nonlinear Finite Element Analysis*, NAFEMS Ltd., 1992.
-

Oden, J. T., *Finite Elements of Nonlinear Continua*, McGraw-Hill, 1972.


---


8.7 Summary
../images/blu4rule.gif

-

There are three sources of nonlinearity in structural problems: material, geometric, and boundary (contact). Any combination of these may be present in an Abaqus analysis.
-

Geometric nonlinearity occurs whenever the magnitude of the displacements affects the response of the structure. It includes the effects of large displacements and rotations, snap through, and load stiffening.
-

In Abaqus/Standard nonlinear problems are solved iteratively using the Newton-Raphson method. A nonlinear problem will require many times the computer resources required by a linear problem.
-

Abaqus/Explicit does not need to iterate to obtain a solution; however, the computational cost may be affected by reductions in the stable time increment due to large changes in geometry.
-

A nonlinear analysis step is split into a number of increments.

-

Abaqus/Standard iterates to find the approximate static equilibrium obtained at the end of each new load increment. Abaqus/Standard controls the load incrementation by using convergence controls throughout the simulation.
-

Abaqus/Explicit determines a solution by advancing the kinematic state from one increment to the next, using a smaller time increment than what is commonly used in implicit analyses. The size of the increment is limited by the stable time increment. By default, time incrementation is completely automated in Abaqus/Explicit.

-

The **Job Monitor** dialog box allows the progress of an analysis to be monitored while it is running. The **Job Diagnostics** dialog box contains the details of the load incrementation and iterations.
-

Results can be saved at the end of each increment so that the evolution of the structure's response can be seen in the Visualization module. Results can also be plotted in the form of *X-Y* graphs.


---

