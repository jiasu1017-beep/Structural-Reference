# 9.3 Automatic time incrementation and stability

The stability limit dictates the maximum time increment used by the Abaqus/Explicit solver. It is a critical factor in the performance of Abaqus/Explicit. The following sections describe the stability limit and discuss how Abaqus/Explicit determines this value. Issues surrounding the model design parameters that affect the stability limit are also addressed. These model parameters include the model mass, material, and mesh.

## 9.3.1 Conditional stability of the explicit method

With the explicit method the state of the model is advanced through an increment of time, ![](../graphics/gsk_eqn00179.gif), based on the state of the model at the start of the increment at time ![](../graphics/gsk_eqn00165.gif). The amount of time that the state can be advanced and still remain an accurate representation of the problem is typically quite short. If the time increment is larger than this maximum amount of time, the increment is said to have exceeded the *stability limit*. A possible effect of exceeding the stability limit is a numerical instability, which may lead to an unbounded solution. It generally is not possible to determine the stability limit exactly, so conservative estimates are used instead. The stability limit has a great effect on reliability and accuracy, so it must be determined consistently and conservatively. For computational efficiency Abaqus/Explicit chooses the time increments to be as close as possible to the stability limit without exceeding it.

## 9.3.2 Definition of the stability limit

The stability limit is defined in terms of the highest frequency in the system (![](../graphics/gsk_eqn00184.gif)). Without damping the stability limit is defined by the expression

![](../graphics/gsk_eqn00185.gif)

and with damping it is defined by the expression

![](../graphics/gsk_eqn00186.gif)

where ![](../graphics/gsk_eqn00187.gif) is the fraction of critical damping in the mode with the highest frequency. (Recall that critical damping defines the limit between oscillatory and non-oscillatory motion in the context of free-damped vibration. Abaqus/Explicit always introduces a small amount of damping in the form of bulk viscosity to control high-frequency oscillations.) Perhaps contrary to engineering intuition, damping always reduces the stability limit.

The actual highest frequency in the system is based on a complex set of interacting factors, and it is not computationally feasible to calculate its exact value. Alternately, we use a simple estimate that is efficient and conservative. Instead of looking at the global model, we estimate the highest frequency of each individual element in the model, which is always associated with the dilatational mode. It can be shown that the highest element frequency determined on an element-by-element basis is always higher than the highest frequency in the assembled finite element model.

Based on the element-by-element estimate, the stability limit can be redefined using the element length, ![](../graphics/gsk_eqn00188.gif), and the wave speed of the material, ![](../graphics/gsk_eqn00189.gif):

![](../graphics/gsk_eqn00190.gif)

For most element types—a distorted quadrilateral element, for example—the above equation is only an estimate of the actual element-by-element stability limit because it is not clear how the element length should be determined. As an approximation the shortest element distance can be used, but the resulting estimate is not always conservative. The shorter the element length, the smaller the stability limit. The wave speed is a property of the material. For a linear elastic material with a Poisson's ratio of zero

![](../graphics/gsk_eqn00191.gif)

where ![](../graphics/gsk_eqn00192.gif) is Young's modulus and ![](../graphics/gsk_eqn00029.gif) is the mass density. The stiffer the material, the higher the wave speed, resulting in a smaller stability limit. The higher the density, the lower the wave speed, resulting in a larger stability limit.

Our simplified stability limit definition provides some intuitive understanding. The stability limit is the transit time of a dilatational wave across the distance defined by the characteristic element length. If we know the size of the smallest element dimension and the wave speed of the material, we can estimate the stability limit. For example, if the smallest element dimension is 5 mm and the dilatational wave speed is 5000 m/s, the stable time increment is on the order of 1 × 10⁻⁶ s.

## 9.3.3 Fully automatic time incrementation versus fixed time incrementation in Abaqus/Explicit

Abaqus/Explicit uses equations such as those discussed in the previous section to adjust the time increment size throughout the analysis so that the stability limit, based on the current state of the model, is never exceeded. Time incrementation is automatic and requires no user intervention, not even a suggested initial time increment. The stability limit is a mathematical concept resulting from the numerical model. Since the finite element program has all of the relevant details, it can determine an efficient and conservative stability limit. However, Abaqus/Explicit does allow the user to override the automatic time incrementation, if desired.

The time increment used in an explicit analysis must be smaller than the stability limit of the central-difference operator. Failure to use a small enough time increment will result in an unstable solution. When the solution becomes unstable, the time history response of solution variables such as displacements will usually oscillate with increasing amplitudes. The total energy balance will also change significantly. If the model contains only one material type, the initial time increment is directly proportional to the size of the smallest element in the mesh. If the mesh contains uniform size elements but contains multiple material descriptions, the element with the highest wave speed will determine the initial time increment.

In nonlinear problems—those with large deformations and/or nonlinear material response—the highest frequency of the model will continually change, which consequently changes the stability limit. Abaqus/Explicit has two strategies for time incrementation control: fully automatic time incrementation (where the code accounts for changes in the stability limit) and fixed time incrementation.

Two types of estimates are used to determine the stability limit: element by element and global. An analysis always starts by using the element-by-element estimation method and may switch to the global estimation method under certain circumstances.

The element-by-element estimate is conservative; it will give a smaller stable time increment than the true stability limit that is based upon the maximum frequency of the entire model. In general, constraints such as boundary conditions and kinematic contact have the effect of compressing the eigenvalue spectrum, and the element-by-element estimates do not take this into account.

The adaptive, global estimation algorithm determines the maximum frequency of the entire model using the current dilatational wave speed. This algorithm continuously updates the estimate for the maximum frequency. The global estimator will usually allow time increments that exceed the element-by-element values.

A fixed time incrementation scheme is also available in Abaqus/Explicit. The fixed time increment size is determined either by the initial element-by-element stability estimate for the step or by a time increment specified directly by the user. Fixed time incrementation may be useful when a more accurate representation of the higher mode response of a problem is required. In this case, a time increment size smaller than the element-by-element estimates may be used. When fixed time incrementation is used, Abaqus/Explicit will not check that the computed response is stable during the step. The user should ensure that a valid response has been obtained by carefully checking the energy history and other response variables.

## 9.3.4 Mass scaling to control time incrementation

Since the mass density influences the stability limit, under some circumstances scaling the mass density can potentially increase the efficiency of an analysis. For example, because of the complex discretization of many models, there are often regions containing very small or poorly shaped elements that control the stability limit. These controlling elements are often few in number and may exist in localized areas. By increasing the mass of only these controlling elements, the stability limit can be increased significantly, while the effect on the overall dynamic behavior of the model may be negligible.

The automatic mass scaling features in Abaqus/Explicit can keep offending elements from hindering the stability limit. There are two fundamental approaches used in mass scaling: defining a scaling factor directly or defining a desired element-by-element stable time increment for the elements whose mass is to be scaled. These two approaches, described in detail in "Mass scaling," Section 11.6.1 of the Abaqus Analysis User's Guide, permit additional user control over the stability limit. However, use caution when employing mass scaling since significantly changing the mass of the model may change the physics of the problem.

## 9.3.5 Effect of material on stability limit

The material model affects the stability limit through its effect on the dilatational wave speed. In a linear material the wave speed is constant; therefore, the only changes in the stability limit during the analysis result from changes in the smallest element dimension during the analysis. In a nonlinear material, such as a metal with plasticity, the wave speed changes as the material yields and the stiffness of the material changes. Abaqus/Explicit monitors the effective wave speeds in the model throughout the analysis, and the current material state in each element is used for stability estimates. After yielding, the stiffness decreases, reducing the wave speed and, consequently, increasing the stability limit.

## 9.3.6 Effect of mesh on stability limit

Since the stability limit is roughly proportional to the shortest element dimension, it is advantageous to keep the element size as large as possible. Unfortunately, for accurate analyses a fine mesh is often necessary. To obtain the highest possible stability limit while using the required level of mesh refinement, the best approach is to have a mesh that is as uniform as possible. Since the stability limit is based on the smallest element dimension in the model, even a single small or poorly shaped element can reduce the stability limit drastically. For diagnostic purposes Abaqus/Explicit provides a list in the status (`.sta`) file of the 10 elements in the mesh with the lowest stability limit. If the model contains some elements whose stability limits are much lower than those of the rest of the mesh, remeshing the model more uniformly may be worthwhile.

## 9.3.7 Numerical instability

Abaqus/Explicit remains stable for most elements under most circumstances. It is possible, however, to define spring and dashpot elements such that they become unstable during the course of an analysis. Therefore, it is useful to be able to recognize a numerical instability if it occurs in your analysis. If it does occur, the result typically will be unbounded, nonphysical, and often characterized by oscillatory solutions.
