# 12.4 Defining contact in Abaqus/Standard

The first step in defining contact pairs (and optionally general contact) in Abaqus/Standard is to define the surfaces of the bodies that could potentially come into contact. The next step is to specify the surfaces that interact with each other; these are the contact interactions. The final step is to define the mechanical property models that govern the behavior of the surfaces when they are in contact.

The definition of surfaces is optional for general contact since an all-inclusive element-based surface is automatically created when general contact is used. You can use specific surface pairings to include regions not included in the default surface, to preclude interactions between different regions of a model, or to override global contact property assignments. For example, if you want to apply a certain friction coefficient to all but a few surfaces in your model, you can assign the primary friction coefficient globally and then override this property for a given pair of user-defined surfaces.

## 12.4.1 Contact interactions

In an Abaqus/Standard simulation possible contact is defined by assigning the surface names to a contact interaction (contact pair approach) or by invoking an automatically-defined all-inclusive element-based surface as the contact domain (general contact approach). For both contact approaches, each contact interaction must refer to a contact property, in much the same way that each element must refer to an element property. Constitutive behavior, such as the contact pressure-clearance relationship and friction, can be included in the contact property.

When you define a contact interaction, you must decide whether the magnitude of the relative sliding will be small or finite. The default is the more general finite-sliding formulation. The small-sliding formulation (available only for contact pairs) is appropriate if the relative motion of the two surfaces is less than a small proportion of the characteristic length of an element face. Using the small-sliding formulation when applicable results in a more efficient analysis.

## 12.4.2 Slave and master surfaces

By default, contact pairs in Abaqus/Standard use a pure master-slave contact algorithm: nodes on one surface (the slave) cannot penetrate the segments that make up the other surface (the master), as shown in [Figure 12–7](#gss-master-surf). The algorithm places no restrictions on the master surface; it can penetrate the slave surface between slave nodes, as shown in [Figure 12–7](#gss-master-surf).

**Figure 12–7** The master surface can penetrate the slave surface.

![](../graphics/gss-master-surf-nls.png)

Due to the strict master-slave formulation, you must be careful to select the slave and master surfaces correctly in order to achieve the best possible contact simulation. Some simple rules to follow are:

- the slave surface should be the more finely meshed surface; and
- if the mesh densities are similar, the slave surface should be the surface with the softer underlying material.

The general contact algorithm in Abaqus/Standard enforces contact in an average sense between interacting surfaces; Abaqus/Standard automatically assigns master and slave roles.

## 12.4.3 Contact discretization

Abaqus/Standard offers two contact discretization methods: a traditional node-to-surface method and a surface-to-surface method. The node-to-surface discretization method defines contact conditions between each slave node and the master surface. The surface-to-surface discretization method considers the shape of both the master and slave surfaces when defining the contact constraints. The contact pair algorithm can use either discretization method; general contact uses only the surface-to-surface approach.

## 12.4.4 Small and finite sliding

When using the small-sliding formulation, Abaqus/Standard establishes the relationship between the slave nodes and the master surface at the beginning of the simulation. Abaqus/Standard determines which segment on the master surface will interact with each node on the slave surface. It maintains these relationships throughout the analysis, never changing which master surface segments interact with which slave nodes. If geometric nonlinearity is included in the model, the small-sliding algorithm accounts for any rotation and deformation of the master surface and updates the load path through which the contact forces are transmitted. If geometric nonlinearity is not included in the model, any rotation or deformation of the master surface is ignored and the load path remains fixed.

The finite-sliding contact formulation requires that Abaqus/Standard continually track which part of the master surface is in contact with each slave node. This is a very complex calculation, especially if both the contacting bodies are deformable. The structures in such simulations can be either two- or three-dimensional. Abaqus/Standard can also model the finite-sliding self-contact of a deformable body. Such a situation occurs when a structure folds over onto itself.

The finite-sliding formulation for contact between a deformable body and a rigid surface is not as complex as the finite-sliding formulation for two deformable bodies. Finite-sliding simulations where the master surface is rigid can be performed for both two- and three-dimensional models.

The contact pair algorithm can consider either small or finite sliding effects; general contact only considers finite sliding effects.

## 12.4.5 Element selection

Selection of elements for contact depends heavily on the contact enforcement used. For example, for traditional contact formulations (i.e., the node-to-surface discretization) it is generally better to use first-order elements for those parts of a model that will form a slave surface. Second-order elements can sometimes cause problems in this case because of the way these elements calculate consistent nodal loads for a constant pressure. The consistent nodal loads for a constant pressure, *P*, on a second-order, two-dimensional element with area *A* are shown in [Figure 12–8](#gss-nodloadconstpress).

**Figure 12–8** Equivalent nodal loads for a constant pressure on a two-dimensional, second-order element.

![](../graphics/gss-nodloadconstpress-nls.png)

The node-to-surface contact formulation bases important decisions on the forces acting on the slave nodes. It is difficult for the algorithm to tell if the force distribution shown in [Figure 12–8](#gss-nodloadconstpress) represents a constant contact pressure or an actual variation across the element. The equivalent nodal forces for a three-dimensional, second-order brick element are even more confusing because they do not even have the same sign for a constant pressure, making it very difficult for the algorithm to work correctly, especially for nonuniform contact. Therefore, to avoid such problems, Abaqus/Standard automatically adds a midface node to any face of a second-order, three-dimensional brick or wedge element that defines a slave surface when it is used with the node-to-surface formulation. The equivalent nodal forces for a second-order element face with a midface node have the same sign for a constant pressure, although they still differ considerably in magnitude.

The equivalent nodal forces for applied pressures on first-order elements always have a consistent sign and magnitude; therefore, there is no ambiguity about the contact state that a given distribution of nodal forces represents.

If you are using the node-to-surface formulation and your geometry is complicated and requires the use of an automatic mesh generator, the modified second-order tetrahedral elements (`C3D10M`) in Abaqus/Standard should be used. These elements are designed to be used in complex contact simulations; regular second-order tetrahedral elements (`C3D10`) have zero contact force at their corner nodes, leading to poor predictions of the contact pressures. The modified second-order tetrahedral elements can calculate the contact pressures accurately.

Regular second-order elements can generally be used without difficulty with the surface-to-surface formulation.

## 12.4.6 Contact algorithm

Understanding the algorithm Abaqus/Standard uses to solve contact problems will help you understand the diagnostic output in the message file and carry out contact simulations successfully.

The contact algorithm in Abaqus/Standard, which is shown in [Figure 12–9](#gss-contact-alg-nls), is built around the Newton-Raphson technique discussed in [Chapter 8, "Nonlinearity"](ch08.html).

**Figure 12–9** Contact algorithm in Abaqus/Standard.

![](../graphics/gss-contact-alg-nls.png)

Abaqus/Standard examines the state of all contact interactions at the start of each increment to establish whether slave nodes are open or closed. If a node is closed, Abaqus/Standard determines whether it is sliding or sticking. Abaqus/Standard applies a constraint for each closed node and removes constraints from any node where the contact state changes from closed to open. Abaqus/Standard then carries out an iteration and updates the configuration of the model using the calculated corrections.

In the updated configuration Abaqus/Standard checks for changes in the contact conditions at the slave nodes. Any node where the clearance after the iteration becomes negative or zero has changed status from open to closed. Any node where the contact pressure becomes negative has changed status from closed to open. If any contact changes are detected in the current iteration, Abaqus/Standard labels it a *severe discontinuity iteration*.

Abaqus/Standard continues to iterate until the severe discontinuities are sufficiently small (or no severe discontinuities occur) and the equilibrium (flux) tolerances are satisfied. Alternatively, you can choose a different approach in which Abaqus/Standard will continue to iterate until no severe discontinuities occur before checking for equilibrium.

The summary for each completed increment in the message and status files shows how many iterations were severe discontinuity iterations and how many were equilibrium iterations (an equilibrium iteration is one in which no severe discontinuities occur). The total number of iterations for an increment is the sum of these two. For some increments, you may find that all iterations are labeled severe discontinuity iterations (this occurs when small contact changes are detected in each iteration and equilibrium is ultimately satisfied).

Abaqus/Standard applies sophisticated criteria involving changes in penetration, changes in the residual force, and the number of severe discontinuities from one iteration to the next to determine whether iteration should be continued or terminated. Hence, it is in principle not necessary to limit the number of severe discontinuity iterations. This makes it possible to run contact problems that require large numbers of contact changes without having to change the control parameters. The default limit for the maximum number of severe discontinuity iterations is 50, which in practice should always be more than the actual number of iterations in an increment.