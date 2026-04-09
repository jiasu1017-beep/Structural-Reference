# 3.4.2 Truss elements

### 3.4.2 Truss elements

**Products: **Abaqus/Standard  Abaqus/Explicit

Truss elements are one-dimensional bars or rods that are assumed to deform by axial stretching only. They are pin jointed at their nodes, and so only translational displacements and the initial position vector at each node are used in the discretization. When the strains are large, the formulation is simplified by assuming that the trusses are made of incompressible material.

There are two truss elements in Abaqus: a 2-node linear interpolation truss and a 3-node quadratic interpolation truss. The quadratic interpolation version is in the library mainly for compatibility with the quadratic interpolation elements of other types, such as shell element S8R5. The same interpolation functions are used for both the Cartesian displacement components and for the Cartesian components of the initial position vector, so these elements are the simplest form of isoparametric elements.

The elements are one-dimensional: a single material (isoparametric) coordinate, *g*, is defined along the element, with ![](../graphics/stm_eqn03446.gif) in the element. In a 2-node element node 1 is at ![](../graphics/stm_eqn03447.gif) and node 2 is at ![](../graphics/stm_eqn03448.gif). In the 3-node version node 1 is at ![](../graphics/stm_eqn03447.gif), node 2 is at ![](../graphics/stm_eqn03449.gif), and node 3 is at ![](../graphics/stm_eqn03450.gif).
### Interpolation

The interpolation for the 2-node element is

![](../graphics/stm_eqn03451.gif)and for the 3-node element,

![](../graphics/stm_eqn03452.gif)where ![](../graphics/stm_eqn01385.gif), ![](../graphics/stm_eqn01386.gif), and ![](../graphics/stm_eqn03453.gif) are the values of a variable at the nodes and ![](../graphics/stm_eqn03454.gif) is the interpolated value of this variable.
### Strain measure

These are one-dimensional elements, and the only strain considered is that along the axis of the element. The stretch ratio along the axis is

![](../graphics/stm_eqn03455.gif)where *l* measures length along the truss axis in the current configuration:

![](../graphics/stm_eqn03456.gif)and ![](../graphics/stm_eqn03457.gif) measures length along the axis in the original configuration.

For geometrically nonlinear analysis we use a logarithmic strain measure:

![](../graphics/stm_eqn03458.gif)
### First variation of strain

The first variation of strain is

![](../graphics/stm_eqn03459.gif)where

![](../graphics/stm_eqn03460.gif)is a unit tangent along the truss axis.
### Second variation of strain

The second variation of strain is

![](../graphics/stm_eqn03461.gif)
### Integration

**Stiffness**

The linear truss is a constant strain element and so is integrated exactly. The quadratic truss is integrated numerically using two Gauss points.

**Mass and consistent loads**

A linear truss has two Gauss points. A quadratic truss has three Gauss points.
### Virtual work contribution

The virtual work contribution from the stress in a truss element is

![](../graphics/stm_eqn03462.gif)where *a* is the current cross-sectional area of the truss, ![](../graphics/stm_eqn01110.gif) is the "true" (Cauchy) stress along the truss, ![](../graphics/stm_eqn00377.gif) is the logarithmic strain, and *l* is the length of the element.

Since we assume the truss is incompressible, ![](../graphics/stm_eqn03463.gif), where *A* is the original area and *L* the original length of the truss. So,

![](../graphics/stm_eqn03464.gif)

This is the form in which the internal virtual work contribution is used for truss elements.
### Mixed (hybrid) forms

"Hybrid" truss elements are also available in Abaqus/Standard. In those elements the axial force at the integration points is taken as an additional variable, with the compatibility condition introduced to define these variables. The formulation is identical to that used for the hybrid beam elements ("Hybrid beam elements,"  Section 3.5.4), without the bending terms.
### Reference

### Reference

"Truss elements,"  Section 29.2.1 of the Abaqus Analysis User's Guide