# N







### native mesh

The meshed representation of a part instance. You create a native mesh by discretizing geometry using the Abaqus/CAE Mesh module. You use the Mesh module to mesh native parts that you positioned in the assembly. A native mesh and its attributes are feature based, and a native mesh maintains its association with the original parts and with the assembly.
For more information:- ["What is feature-based modeling?," Section 11.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-concepts)

### native part

A part created using the Abaqus/CAE Part module. Abaqus/CAE stores each native part in the form of an ordered list of features. The parameters that define each feature—extruded depth, hole diameter, sweep path, etc.—define the geometry of the part.
For more information:- ["What is feature-based modeling?," Section 11.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-concepts)

### NLGEOM

An abbreviation for [geometric nonlinearity](gl01gls08.md#gls-geometricnonlinear).

### node set

A named collection of nodes.
For more information:- ["Node definition," Section 2.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inode)

- [Chapter 73, "The Set and Surface toolsets," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### non-manifold edge

An exterior element edge at which more than two exterior element faces meet. You can use the Query toolset in the Abaqus/CAE Mesh module to highlight free and non-manifold mesh edges in a solid or shell mesh. Non-manifold edges may indicate problems, especially in a solid mesh.
For more information:- ["Obtaining mesh information," Section 17.19.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn-querymesh)

### normal axis

A spatially varying orientation at the centroid of each native or orphan mesh element. The normal axis for a [discrete orientation](gl01gls05.md#gls-discreteorient) represents the normal axis of the material orientation. Abaqus/CAE uses the normal axis and the [primary axis](gl01gls17.md#gls-primaryaxis) to construct a right-handed Cartesian coordinate system. You choose the coordinate system axis that you want the normal axis to represent in the resultant orientation and select topology or datums or enter vector values to define the desired axis.
For more information:- ["Using discrete orientations for material orientations and composite layup orientations," Section 12.16 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp-discrete-orient)




