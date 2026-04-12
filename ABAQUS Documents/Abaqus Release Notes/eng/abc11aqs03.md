# 11.3 User control of domain decomposition







**Product: **Abaqus/Explicit  

**Benefits: **Improved parallel scalability can be achieved when localized regions are computationally intensive.

**Description: **You can influence the domain decomposition by specifying a region to be independently decomposed or by specifying that all elements of a particular element set should be constrained to the same parallel domain. This option is not recommended for widespread use. It can be beneficial to parallel scalability for some cases in which a localized region requires more extensive contact or other computations than other regions, but this option may degrade performance. For example, specifying the impact region in a bird strike model as an independent domain decomposition region may improve parallel scalability. Coupled Eulerian-Lagrangian simulations with localized adaptive mesh refinement (where elements are refined adding to the computational cost) may also benefit from defining a local domain decomposition region. With this approach, each processor will process multiple domains: for example, one domain associated with a localized region and one domain associated with the rest of the model. 

Multiple domain decomposition regions can be specified. The number of domains in total is the total number of domain decomposition regions times the user-specified number of domains per region. The number of domain decomposition regions is often one more than the number of user-defined domain decomposition regions because elements not explicitly defined to be in a domain decomposition region will form a separate domain decomposition region.
**References: **

**Abaqus Analysis User's Guide**
- ["Parallel execution in Abaqus/Explicit," Section 3.5.3](../usb/usb-link.md#usb-int-aparallelexecution)

**Abaqus Keywords Reference Guide**
- [*DOMAIN DECOMPOSITION](../key/key-link.md#usb-kws-mdomaindecomp)




