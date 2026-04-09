# 2.5.7 Steady-state linear dynamic analysis

### 2.5.7 Steady-state linear dynamic analysis

**Product: **Abaqus/Standard

Steady-state linear dynamic analysis predicts the linear response of a structure subjected to continuous harmonic excitation. In many cases steady-state linear dynamic analysis in Abaqus/Standard uses the set of eigenmodes extracted in a previous eigenfrequency step to calculate the steady-state solution as a function of the frequency of the applied excitation. Abaqus/Standard also has a "direct" steady-state linear dynamic analysis procedure, in which the equations of steady harmonic motion of the system are solved directly without using the eigenmodes, and a "subspace" steady-state linear dynamic analysis procedure, in which the equations are projected onto a subspace of selected eigenmodes of the undamped system. These options are intended for systems in which the behavior is dependent on frequency, for when the model includes damping, or for systems in which the governing equations are not symmetric.

This section describes the linear steady-state response procedure based on the eigenmodes.

The projection of the equations of motion of the system onto the ![](../graphics/stm_eqn00904.gif)th mode gives

![](../graphics/stm_eqn01343.gif)where ![](../graphics/stm_eqn00968.gif) is the amplitude of mode ![](../graphics/stm_eqn00904.gif) (the ![](../graphics/stm_eqn00904.gif)th "generalized coordinate"), ![](../graphics/stm_eqn01344.gif) is the damping associated with this mode (see below), ![](../graphics/stm_eqn01296.gif) is the undamped frequency of the mode, ![](../graphics/stm_eqn01345.gif) is the generalized mass associated with the mode, and ![](../graphics/stm_eqn01346.gif) is the forcing associated with this mode. The forcing is defined by the frequency, ![](../graphics/stm_eqn01258.gif), and the real and imaginary parts of the nodal equivalent forces, ![](../graphics/stm_eqn01347.gif) and ![](../graphics/stm_eqn01348.gif), projected onto the eigenmode ![](../graphics/stm_eqn01174.gif):

![](../graphics/stm_eqn01349.gif)In this equation summation is implied by the repeat of the superscript ![](../graphics/stm_eqn01350.gif) indicating a degree of freedom in the model; but throughout this section we are working with only a single modal equation, so no summation is implied by the repeat of the mode subscript ![](../graphics/stm_eqn01351.gif). The load vector is written in terms of its real and imaginary parts, ![](../graphics/stm_eqn01347.gif) and ![](../graphics/stm_eqn01348.gif), since this is the manner in which the loading is defined in Abaqus/Standard. It is equivalently possible to write the loading in terms of its magnitude, ![](../graphics/stm_eqn01352.gif), and phase, ![](../graphics/stm_eqn01353.gif), as ![](../graphics/stm_eqn01354.gif), where ![](../graphics/stm_eqn01355.gif) and ![](../graphics/stm_eqn01356.gif).

Several representations of modal damping are provided. Modal damping defines ![](../graphics/stm_eqn01357.gif), where ![](../graphics/stm_eqn01209.gif) is the fraction of critical damping in the mode. Structural damping gives a damping force proportional to the modal amplitude:

![](../graphics/stm_eqn01358.gif)where ![](../graphics/stm_eqn01359.gif) is the structural damping coefficient for the mode. Rayleigh damping is defined by ![](../graphics/stm_eqn01360.gif); ![](../graphics/stm_eqn01361.gif) and ![](../graphics/stm_eqn01362.gif) are the Rayleigh coefficients damping low and high frequency modes, respectively. Rayleigh damping can be reproduced exactly by modal damping as

![](../graphics/stm_eqn01363.gif)Introducing all of these damping definitions into [Equation 2.5.7&#8211;1](02s05a30.md) gives

![](../graphics/stm_eqn01364.gif)The solution to this equation is

![](../graphics/stm_eqn01365.gif)where ![](../graphics/stm_eqn01366.gif) is the amplitude of the projected load vector and ![](../graphics/stm_eqn01367.gif) is the amplitude of the complex "transfer function" for mode ![](../graphics/stm_eqn00904.gif). ![](../graphics/stm_eqn01368.gif) defines the response in mode ![](../graphics/stm_eqn00904.gif) from the force projection onto that mode and is defined by its real and imaginary parts as

![](../graphics/stm_eqn01369.gif)where ![](../graphics/stm_eqn01370.gif) denotes

![](../graphics/stm_eqn01371.gif)The amplitude of the response is

![](../graphics/stm_eqn01372.gif)and the phase angle of the response is

![](../graphics/stm_eqn01373.gif)

If a harmonic base motion is applied, the real and imaginary parts of the modal loads are given as

![](../graphics/stm_eqn01374.gif)

![](../graphics/stm_eqn01375.gif)where ![](../graphics/stm_eqn01186.gif) is the structure's mass matrix and ![](../graphics/stm_eqn01376.gif) is a vector that has unit magnitude in the direction of the base acceleration at any grounded node and is otherwise zero; ![](../graphics/stm_eqn01377.gif) and ![](../graphics/stm_eqn01378.gif) are the real and imaginary parts of the base acceleration. If the base motion is given as a velocity or displacement, the corresponding accelerations are ![](../graphics/stm_eqn01379.gif) and ![](../graphics/stm_eqn01380.gif), where ![](../graphics/stm_eqn01381.gif) and ![](../graphics/stm_eqn01382.gif) are the real and imaginary parts of the velocity, or ![](../graphics/stm_eqn01383.gif) and ![](../graphics/stm_eqn01384.gif), where ![](../graphics/stm_eqn01385.gif) and ![](../graphics/stm_eqn01386.gif) are the real and imaginary parts of the displacement.

The peak amplitude of any physical variable, ![](../graphics/stm_eqn00657.gif), is available from the modal amplitudes as

![](../graphics/stm_eqn01387.gif)

Steady-state response is given as a frequency sweep through a user-specified range of frequencies. Since the structural response peaks around the natural frequencies, a bias function is used to cluster the response points around the frequencies. The biasing is described in "Mode-based steady-state dynamic analysis,"  Section 6.3.8 of the Abaqus Analysis User's Guide.
### Reference

### Reference

"Mode-based steady-state dynamic analysis,"  Section 6.3.8 of the Abaqus Analysis User's Guide