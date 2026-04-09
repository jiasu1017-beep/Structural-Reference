# 2.5.6 Response spectrum analysis

### 2.5.6 Response spectrum analysis

**Product: **Abaqus/Standard

Response spectrum analysis is intended to provide an inexpensive approach to estimating the peak response of a model (usually a model of a structure) subjected to "base motion": the simultaneous motion of all nodes fixed with boundary conditions. The approach assumes that the system's response is linear, so it can be analyzed in the frequency domain using its lowest eigenmodes---![](../graphics/stm_eqn01295.gif)---and eigenfrequencies ![](../graphics/stm_eqn01296.gif)---extracted in a previous eigenfrequency step. The method is typically used to estimate the response of a building or of a piping system in a building to an earthquake. The method is not appropriate if the excitation is so severe that nonlinear effects in the system are important. In such a case the time history of the base excitation must be known and used with a dynamic analysis step to obtain the system's response.

Even for a linear system the response spectrum method provides only estimates of the peak response. If more precise values are required, a modal dynamic analysis step can be used to integrate the system through time and, thus, develop its response to the given base excitation.

In response spectrum analysis the estimates of peak values are obtained by combining the peak responses of the participating modes corresponding to user-specified spectra definitions. Several approximations are introduced by response spectrum analysis. The conversion from a time history of excitation into an equivalent frequency domain spectrum is based on the behavior of a single degree of freedom system. Different spectra are often applied in different excitation directions. Once the spectra are known, the peak modal responses can be calculated. The manner in which these peak modal responses are combined to estimate the peak physical response, together with the manner in which multidirectional excitations are combined, introduces approximations. Since no one method gives good approximations for all cases, several methods are offered. These methods are discussed in the [Regulatory Guide 1.92 (1976)](07s01a01-References.md) of the U.S. Nuclear Regulatory Commission, in the papers by [Anagnastopoulos (1981)](07s01a01-References.md), [Der Kiureghian (1981)](07s01a01-References.md), and [Smeby (1984)](07s01a01-References.md) and in the book by [A. K. Gupta (1990)](07s01a01-References.md). The choice of the summation rules depends on the particular case and is a matter of the user's judgment.

Since response spectrum analysis is commonly used as a basic design tool, spectra are defined in many design codes for such applications as seismic analysis of buildings. In such cases the user works from the given spectra. In other cases the time history of a known base excitation must first be converted into a response spectrum by considering the response of a single degree of freedom system excited by the known base motion. For this purpose the single degree of freedom system is characterized by its undamped natural frequency, ![](../graphics/stm_eqn01091.gif), and the fraction of critical damping present in the system, ![](../graphics/stm_eqn01040.gif). The equation of motion of the system is integrated through time to find peak values of relative displacement, relative velocity, and absolute acceleration. The integration described in "Modal dynamic analysis,"  Section 2.5.5, can be used for this purpose, since it is exact when the base motion record varies linearly with time. Thus, the maximum values of displacement, velocity, and acceleration are found for the linear, one degree of freedom system. This process is repeated for all frequency and damping values in the range of interest to construct displacement, velocity, and acceleration spectra, ![](../graphics/stm_eqn01297.gif), ![](../graphics/stm_eqn01298.gif) and ![](../graphics/stm_eqn01299.gif). A FORTRAN program to build spectra in this way from an acceleration record is given in "Analysis of a cantilever subject to earthquake motion,"  Section 1.4.13 of the Abaqus Benchmarks Guide (file [cantilever_spectradata.f](cantilever_spectradata.md).)

If there is no damping, the relationship between ![](../graphics/stm_eqn01300.gif), ![](../graphics/stm_eqn01301.gif), and ![](../graphics/stm_eqn01302.gif) is given by

![](../graphics/stm_eqn01303.gif)In Abaqus/Standard it is assumed that the damping is always small, so these relationships are used whenever a conversion is needed.

A response spectrum is defined by giving a table of values of *S* at increasing values of frequency, ![](../graphics/stm_eqn01091.gif), for increasing values of damping, ![](../graphics/stm_eqn01040.gif). Linear interpolation on a logarithmic scale is used to compute the response for any required frequency and damping factor. Any number of spectra can be defined.

The response spectrum procedure allows up to three spectra, which we denote by *k*, ![](../graphics/stm_eqn01304.gif), to be applied to the model in orthogonal physical directions defined by their direction cosines, ![](../graphics/stm_eqn01305.gif). These spectra can come from different excitations (with a certain level of correlation between them), or they can be components of a single base excitation acting in an arbitrary direction.

When modal methods are used to define a model's response, the value of any physical variable is defined from the amplitudes of the modal responses (the "generalized coordinates"), ![](../graphics/stm_eqn00968.gif). The first stage in the response spectrum procedure is to estimate the peak values of these modal responses. For mode ![](../graphics/stm_eqn00904.gif) and spectrum *k* this is

![](../graphics/stm_eqn01306.gif)where ![](../graphics/stm_eqn00748.gif) is a user-defined scaling parameter, ![](../graphics/stm_eqn01307.gif) is the *k*th displacement spectrum, ![](../graphics/stm_eqn01308.gif) is the *j*th direction cosine for the *k*th spectrum, and ![](../graphics/stm_eqn01309.gif) is the participation factor for mode ![](../graphics/stm_eqn00904.gif) in direction *j* (see "Variables associated with the natural modes of a model,"  Section 2.5.2, for the definition of ![](../graphics/stm_eqn01309.gif)). Similar expressions for ![](../graphics/stm_eqn01310.gif) and ![](../graphics/stm_eqn01311.gif) are obtained by using velocity or acceleration spectra in the above formula.

We now have estimates of the peak responses of the "generalized coordinates"---the amplitudes of the responses of the natural modes of the system for excitation in each direction. If the input spectra in the different directions are components of a single base excitation acting in an arbitrary direction, for each mode we can combine these peak responses into a single value by specifying algebraic summation of the values for the different spatial directions:

![](../graphics/stm_eqn01312.gif)In this case the modal combinations discussed below still apply, but the subscript *k* is no longer relevant and should be ignored.

Let us denote by ![](../graphics/stm_eqn01313.gif) the peak response of some physical variable ![](../graphics/stm_eqn01314.gif) (a component of displacement, stress, section force, reaction force, etc.) caused by motion in the natural mode ![](../graphics/stm_eqn00904.gif) excited by the response spectrum in excitation direction *k* at frequency ![](../graphics/stm_eqn01091.gif) and with damping ![](../graphics/stm_eqn01040.gif). Denote the component of the eigenvector ![](../graphics/stm_eqn00904.gif) associated with ![](../graphics/stm_eqn01315.gif) by ![](../graphics/stm_eqn01316.gif). Then

![](../graphics/stm_eqn01317.gif)

![](../graphics/stm_eqn01318.gif)and

![](../graphics/stm_eqn01319.gif)

We need to combine these estimates of the peak physical responses in the individual modes into estimates of the total peak response of the particular physical variable to the given spectrum, ![](../graphics/stm_eqn01320.gif). Since the peak responses in the different modes will not in general occur at the same time, this combination is only an estimate, so several formul are offered, as follows:

Summation of the absolute values of the modal peak responses estimates

![](../graphics/stm_eqn01321.gif)This provides the most conservative estimate of the peak response, since it assumes that all modes provide peak response in phase at the same time.

Square root of the summation of the squares (SRSS) estimates

![](../graphics/stm_eqn01322.gif)This summation usually provides a reasonable estimate if the natural frequencies of the modes are well separated.

The Naval Research Laboratory method distinguishes the mode, ![](../graphics/stm_eqn01219.gif), in which the physical variable has its maximum response, and adds the square root of the sum of squares of the peak responses in all other modes to the absolute value of the peak response of that mode. This gives the estimate

![](../graphics/stm_eqn01323.gif)Again, the modes must be reasonably well-spaced in the frequency domain to obtain an accurate estimate with this method.

A variety of methods are available that aim to improve the estimation for structures with closely spaced frequencies. Abaqus/Standard provides two of them: the Ten Percent Method recommended by [Regulatory Guide 1.92 (1976)](07s01a01-References.md) of the U.S. Nuclear Regulatory Commission and the Complete Quadratic Combination Method, which was first introduced by [Der Kiureghian (1981)](07s01a01-References.md) and developed by [Smeby and Der Kiureghian (1984)](07s01a01-References.md). Both methods reduce to the SRSS method if the modes are well separated with no coupling among them.

Two additional methods, the Grouping Method and the Double Sum Combination Method, are also available to satisfy [Regulatory Guide 1.92](07s01a01-References.md).
### Ten Percent Method

The Ten Percent Method described in [Regulatory Guide 1.92](07s01a01-References.md) modifies the SRSS Method by adding a contribution from all pairs of modes ![](../graphics/stm_eqn00904.gif) and ![](../graphics/stm_eqn01219.gif) whose frequencies are within 10% of each other, giving the estimate

![](../graphics/stm_eqn01324.gif)The frequencies of modes ![](../graphics/stm_eqn00904.gif) and ![](../graphics/stm_eqn01219.gif) are considered to be within 10% whenever

![](../graphics/stm_eqn01325.gif)
### Complete Quadratic Combination Method

The Complete Quadratic Combination Method (CQC) combines the modal response with the formula

![](../graphics/stm_eqn01326.gif)where ![](../graphics/stm_eqn01327.gif) are cross-correlation coefficients between modes ![](../graphics/stm_eqn00904.gif) and ![](../graphics/stm_eqn01219.gif), which depend on the ratio of frequencies and modal damping between the two modes:

![](../graphics/stm_eqn01328.gif)where

![](../graphics/stm_eqn01329.gif)If double eigenvalues occur with the same damping coefficient, their correlation coefficient will be ![](../graphics/stm_eqn01330.gif). If modes are well-spaced, their cross-correlation coefficient will be small (![](../graphics/stm_eqn01331.gif)) and the method will give the same results as the SRSS method. This method is usually recommended for asymmetrical building systems, since, in such cases, other methods can underestimate the response in the direction of motion and overestimate the response in the transverse direction (see "Response spectra of a three-dimensional frame building,"  Section 2.2.3 of the Abaqus Example Problems Guide).

For the case of different base excitations acting along orthogonal directions, we still need to sum over the directions indicated by the subscript *k*. [Regulatory Guide 1.92](07s01a01-References.md) specifies that this directional summation be based on the square root of the sum of the squares summation rule:

![](../graphics/stm_eqn01332.gif)This rule is appropriate when the base motions in different directions are statistically independent (uncorrelated)---when they are acting along "principal directions." The existence of a set of directions along which the ground motions can be considered uncorrelated is discussed by [Penzien and Watabe (1975)](07s01a01-References.md). Such considerations are especially important when the CQC modal combination method is used. In the Abaqus implementation of the CQC method it is assumed that the horizontal components act along the principal directions and are of equal intensity. For details on the CQC method applied to more general cases, see [Smeby and Der Kiureghian (1984)](07s01a01-References.md).
### Grouping Method

The Grouping Method, also known as the NRC Grouping Method, improves the response estimation for structures with closely spaced eigenvalues. The modal responses are grouped such that the lowest and highest frequency modes in a group are within 10% and no mode is in more than one group. The modal responses are summed absolutely within groups before performing a SRSS combination of the groups. Within the group responses are summed as

![](../graphics/stm_eqn01333.gif) for ![](../graphics/stm_eqn01334.gif) frequencies within any ![](../graphics/stm_eqn01335.gif) group and then performing:

![](../graphics/stm_eqn01336.gif) The above expression includes all the groups, and the group can consist of just one frequency response if the frequency does not have another member that is within the 10% limit. The Ten Percent Method, by comparison, will always produce results higher in value than the grouping method.
### Double Sum Combination Method

The Double Sum Combination Method, also known as Rosenblueth's Double Sum Combination, is the first attempt to evaluate modal correlation based on random vibration theory. The method utilizes the time duration ![](../graphics/stm_eqn01337.gif) of strong earthquake motion. The mode correlation coefficients ![](../graphics/stm_eqn01338.gif) that also depend on frequencies and damping coefficient ![](../graphics/stm_eqn01040.gif) lead to the following mode combination:

![](../graphics/stm_eqn01339.gif)where

![](../graphics/stm_eqn01340.gif)where

![](../graphics/stm_eqn01341.gif)

![](../graphics/stm_eqn01342.gif)
### Reference

### Reference

"Response spectrum analysis,"  Section 6.3.10 of the Abaqus Analysis User's Guide