# 2.5.5 Modal dynamic analysis

### 2.5.5 Modal dynamic analysis

**Product: **Abaqus/Standard

The modal dynamic procedure provides time history analysis of linear systems. The excitation is given as a function of time: it is assumed that the amplitude curve is specified so that the magnitude of the excitation varies linearly within each increment. When the model is projected onto the eigenmodes used for its dynamic representation, we obtain the following set of equations at time *t*:

![](../graphics/stm_eqn01218.gif)where the ![](../graphics/stm_eqn00904.gif) and ![](../graphics/stm_eqn01219.gif) indices span the eigenspace; ![](../graphics/stm_eqn01220.gif)is the projected viscous damping matix; ![](../graphics/stm_eqn01221.gif) is the "generalized coordinate" of the mode ![](../graphics/stm_eqn01219.gif) (the amplitude of the response in this mode); ![](../graphics/stm_eqn01222.gif) is the natural frequency of the undamped mode ![](../graphics/stm_eqn01219.gif) (obtained as the square root of the eigenvalue in the eigenfrequency step that precedes the modal dynamic time history analysis); ![](../graphics/stm_eqn01223.gif) is the magnitude of the loading projected onto this mode (the "generalized load" for the mode); and ![](../graphics/stm_eqn01224.gif) is the change in *f* over the time increment, which is ![](../graphics/stm_eqn00883.gif).

If the projected damping matrix is diagonal, [Equation 2.5.5&#8211;1](02s05a28.md) becomes the following uncoupled set of equations:

![](../graphics/stm_eqn01225.gif)where ![](../graphics/stm_eqn01226.gif) is the critical damping ratio given by the relation

![](../graphics/stm_eqn01227.gif) where ![](../graphics/stm_eqn01228.gif) is the modal viscous damping coefficient and ![](../graphics/stm_eqn01229.gif) is the modal mass in mode ![](../graphics/stm_eqn01219.gif).
### Solution to the uncoupled system

The solution to the uncoupled equations is obtained readily as a particular integral for the loading and a solution to the homogeneous equation (with no right-hand side). These solutions can be combined and written in the general form

![](../graphics/stm_eqn01230.gif)where ![](../graphics/stm_eqn01231.gif) and ![](../graphics/stm_eqn01232.gif), ![](../graphics/stm_eqn01233.gif) are constants, since we have assumed that the loading only varies linearly over the time increment (that is, ![](../graphics/stm_eqn01234.gif) is constant).

There are three cases of this solution for nonrigid body motion (![](../graphics/stm_eqn01235.gif)), depending on whether the damping in the modal equilibrium equation is greater than, equal to, or less than critical damping (that is, depending on whether ![](../graphics/stm_eqn01236.gif) is positive, zero, or negative).
### Solution to the coupled system

[Equation 2.5.5&#8211;3](02s05a28.md) can be generalized to address full coupling in the projected damping matrix.  Let the matrix ![](../graphics/stm_eqn00162.gif) be split into its diagonal and off-diagonal parts so that

![](../graphics/stm_eqn01237.gif) Then, with the additional assumption that the off-diagonal damping force varies linearly over a time increment, the equation for the uncoupled system can be rewritten as

![](../graphics/stm_eqn01238.gif) where ![](../graphics/stm_eqn01239.gif) is given by

![](../graphics/stm_eqn01240.gif)![](../graphics/stm_eqn01239.gif) is fully populated but is a function only of ![](../graphics/stm_eqn00883.gif), so it needs to be factored only a single time for a given analysis.
### Integral coefficients

There are three cases of this solution for nonrigid body motion (![](../graphics/stm_eqn01235.gif)), depending on whether the damping in the modal equilibrium equation is greater than, equal to, or less than critical damping (that is, depending on whether ![](../graphics/stm_eqn01236.gif) is positive, zero, or negative).Damping less than critical

This case is the most common. With

![](../graphics/stm_eqn01241.gif)we have

![](../graphics/stm_eqn01242.gif)

![](../graphics/stm_eqn01243.gif) Damping equal to critical

In this case

![](../graphics/stm_eqn01244.gif)

![](../graphics/stm_eqn01245.gif)Damping higher than critical

In this case, with

![](../graphics/stm_eqn01246.gif)we have

![](../graphics/stm_eqn01247.gif)

![](../graphics/stm_eqn01248.gif)

![](../graphics/stm_eqn01249.gif)Rigid body mode with damping

If there are rigid body modes in the finite element model, there will be one or several eigenvalues that are zero. The equation of motion ([Equation 2.5.5&#8211;1](02s05a28.md)) is reduced to

![](../graphics/stm_eqn01250.gif)

Only Rayleigh damping can be specified for a rigid body mode, since the critical damping is zero. Furthermore, since it is a rigid body mode, only the mass damping factor, ![](../graphics/stm_eqn00904.gif), appears (stiffness damping requires that there be straining of the body). For this case

![](../graphics/stm_eqn01251.gif)

![](../graphics/stm_eqn01252.gif)Rigid body mode without damping

For the particular case of a rigid body mode without damping, the equation of motion ([Equation 2.5.5&#8211;1](02s05a28.md)) is reduced to

![](../graphics/stm_eqn01253.gif)For this case

![](../graphics/stm_eqn01254.gif)
### Structural damping in modal dynamic analysis

Structural damping is a commonly used damping model that represents damping as complex stiffness.  This representation causes no difficulty for frequency domain analysis such as steady-state dynamics for which the solution is already complex.  However, in the time domain, the solution must remain real-valued.  To allow users to apply their structural damping model in the time domain, a method has been developed to convert structural damping to an equivalent viscous damping.  This technique was designed so that, in the frequency domain, the viscous damping applied is identical to structural damping if the projected damping matrix is diagonal.

We start with the equation of a single degree-of-freedom oscillator,

![](../graphics/stm_eqn01255.gif)where *m* is the mass, *c* is the viscous damping factor, *k* is the stiffness, *x* is the response, *f* is the force, and  ![](../graphics/stm_eqn01256.gif) is the structural damping factor.  If we normalize by the mass and assume harmonic input, we obtain the relation

![](../graphics/stm_eqn01257.gif)where ![](../graphics/stm_eqn01091.gif)   is the natural frequency, ![](../graphics/stm_eqn01258.gif) is the excitation frequency,  ![](../graphics/stm_eqn01040.gif) is the coefficient of the harmonic response, and  ![](../graphics/stm_eqn01259.gif) is the coefficient of the harmonic input.  The relation between the viscous damping factor *c* and the critical damping factor  ![](../graphics/stm_eqn01040.gif) is such that   ![](../graphics/stm_eqn01260.gif).

Based on the two previous equations, if we want the viscous damping factor to have the same effect as the structural damping factor, we must have

![](../graphics/stm_eqn01261.gif)  If we further assume that  ![](../graphics/stm_eqn01262.gif), the relation simplifies to

![](../graphics/stm_eqn01263.gif) Now we consider the finite element system of equations,

![](../graphics/stm_eqn01264.gif)  where  ![](../graphics/stm_eqn01265.gif) is the finite element viscous damping matrix and  ![](../graphics/stm_eqn01266.gif) is the finite element structural damping matrix.  If we project these equations onto the eigenmodes, the damping matrices become

![](../graphics/stm_eqn01267.gif)  which could be fully populated.  If we take the case that  ![](../graphics/stm_eqn01265.gif) and  ![](../graphics/stm_eqn01266.gif) are diagonal, their diagonal elements can be written

![](../graphics/stm_eqn01268.gif)where  ![](../graphics/stm_eqn00904.gif) is a particular mode.  Maintaining the relation developed for the single degree-of-freedom system ![](../graphics/stm_eqn01269.gif)  for this diagonal case would require

![](../graphics/stm_eqn01270.gif) For nondiagonal matrices the expression for equivalent viscous damping becomes

![](../graphics/stm_eqn01271.gif) where D is a diagonal matrix whose entries are given by

![](../graphics/stm_eqn01272.gif)
### Response of nodal and element variables

The time integration is done in terms of the generalized coordinates, and the response of the physical variables is then immediately available by summation:

![](../graphics/stm_eqn01273.gif)

![](../graphics/stm_eqn01274.gif)

![](../graphics/stm_eqn01275.gif)

![](../graphics/stm_eqn01276.gif)where ![](../graphics/stm_eqn01277.gif) are the modes, ![](../graphics/stm_eqn01278.gif) are the modal strain amplitudes, ![](../graphics/stm_eqn01279.gif) are the modal stress amplitudes, and ![](../graphics/stm_eqn01280.gif) are the modal reaction force amplitudes corresponding to each eigenvector ![](../graphics/stm_eqn00904.gif).
### Initial conditions

At the beginning of the step initial displacements and initial velocities must be converted to equivalent values of the generalized coordinates, which can be done exactly only if the number of eigenvectors equals the number of degrees of freedom. Since this is usually not the case, the initial values of the generalized coordinate displacement and velocity are calculated as

![](../graphics/stm_eqn01281.gif)where ![](../graphics/stm_eqn01282.gif) is the generalized mass for the eigenvector ![](../graphics/stm_eqn00904.gif), ![](../graphics/stm_eqn01283.gif) is the eigenvector, ![](../graphics/stm_eqn01284.gif) is the mass matrix, and ![](../graphics/stm_eqn01285.gif) are the initial displacements.

Similarly, for the initial velocities

![](../graphics/stm_eqn01286.gif)

For the case where the initial conditions are given by a previous modal dynamic analysis, the generalized displacement, velocity, and acceleration are simply taken from the previous analysis.
### Base motion definition

Many linear dynamic problems involve finding the response of a structure to a "base motion": a time history of displacement, velocity, or acceleration given for the points where the displacements of the structure are prescribed. In all cases these base motions are converted into an acceleration history. If the displacement or velocity history has nonzero values at time ![](../graphics/stm_eqn01287.gif) 0, corrections to the acceleration histories are made at times ![](../graphics/stm_eqn01287.gif) 0 and ![](../graphics/stm_eqn01288.gif). If velocities are given, the acceleration at ![](../graphics/stm_eqn01287.gif) 0 is

![](../graphics/stm_eqn01289.gif)If displacements are given, the accelerations at ![](../graphics/stm_eqn01287.gif) 0 and ![](../graphics/stm_eqn01288.gif) are

![](../graphics/stm_eqn01290.gif)In the above expressions and in the expressions to follow, a superscript * indicates user-defined amplitude data.

If velocities are given for tabular or equally spaced amplitude curve definitions, the acceleration is defined by the central difference rule

![](../graphics/stm_eqn01291.gif)If displacements are given, the acceleration is defined by the central difference rule

![](../graphics/stm_eqn01292.gif)

The response is calculated relative to the base. If total values of nodal variables are required, the motion at the base is added to the relative values:

![](../graphics/stm_eqn01293.gif)where

![](../graphics/stm_eqn01294.gif)
### Reference

### Reference

"Transient modal dynamic analysis,"  Section 6.3.7 of the Abaqus Analysis User's Guide