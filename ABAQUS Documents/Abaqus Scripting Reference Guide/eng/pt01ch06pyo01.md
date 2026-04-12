# 6.1 Assembly object







An Assembly object is a container for instances of parts. The Assembly object has no constructor command. Abaqus creates the *rootAssembly* member when a [Model](pt01ch33pyo01.md) object is created.

**Access**

```
import assembly
mdb.models[*name*].rootAssembly
```

### 6.1.1 backup()

This method makes a backup copy of the features in the assembly. The `backup()` method is used in conjunction with the `restore()` method.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.2 clearGeometryCache()

This method deletes the geometry cache. Deleting the geometry cache reduces the amount of memory being used.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.3 deleteAllFeatures()

This method deletes all the features in the assembly.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.4 deleteFeatures(...)

This method deletes specified features from the assembly.

**Required argument**

*featureNames*

A sequence of Strings specifying the feature names that will be deleted from the assembly.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.5 excludeFromSimulation(...)

This method excludes the specified part instances from the analysis.

**Required arguments**

*instances*

A sequence of [PartInstance](pt01ch06pyo04.md) objects to be excluded from the analysis.

*exclude*

A Bool specifying whether to exclude the selected instances from the analysis or include them. 

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.6 featurelistInfo()

This method prints the name and status of all the features in the feature lists.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.7 getMassProperties(...)

This method returns the mass properties of the assembly, or instances or regions. Only beams, trusses, shells, solids, point, nonstructural mass, and rotary inertia elements are supported.

**Required arguments**

None.

**Optional arguments**

*regions*

A sequence of[PartInstance](pt01ch06pyo04.md) objects or a sequence of [Region](pt01ch45pyo03.md) objects specifying the part instances or regions whose mass properties are to be queried. The whole assembly is queried by default.

*relativeAccuracy*

A SymbolicConstant specifying the relative accuracy for geometry computation. Possible values are LOW, MEDIUM, and HIGH. The default value is LOW.

*useMesh*

A Boolean specifying whether the mesh should be used in the computation if the geometry is meshed. The default value is False.

*specifyDensity*

A Boolean specifying whether a user-specified density should be used in regions with density errors such as undefined material density. The default value is False.

*density*

A double value specifying the user-specified density value to be used in regions with density errors. The user-specified density should be greater than 0.

*specifyThickness*

A Boolean specifying whether a user-specified thickness should be used in regions with thickness errors such as undefined thickness. The default value is False.

*thickness*

A double value specifying the user-specified thickness value to be used in regions with thickness errors. The user-specified thickness should be greater than 0.

*miAboutCenterOfMass*

A Boolean specifying if the moments of inertia should be evaluated about the center of mass. The default value is True.

*miAboutPoint*

A tuple of three floats specifying the coordinates of the point about which to evaluate the moment of inertia. By default if the moments of inertia are not being evaluated about the center of mass, they will be evaluated about the origin.

**Return value**

A Dictionary object with the following items:

 *area*: None or a Float specifying the sum of the area of the specified faces. The area is computed only for one side for shells.

 *areaCentroid*: None or a tuple of three Floats representing the coordinates of the area centroid.

 *volume*: None or a Float specifying the volume of the specified regions.

 *volumeCentroid*: None or a tuple of three Floats representing the coordinates of the volume centroid.

 *massFromMassPerUnitSurfaceArea*: None or a Float specifying the mass due to mass per unit surface area.

 *mass*: None or a Float specifying the mass of the specified regions. It is the total mass and includes mass from quantities such as mass per unit surface area.

 *centerOfMass*: None or a tuple of three Floats representing the coordinates of the center of mass.

 *momentOfInertia*: None or a tuple of six Floats representing the moments of inertia about the center of mass or about the point specified.

 *warnings*: A tuple of SymbolicConstants representing the problems encountered while computing the mass properties. Possible SymbolicConstants are:

 UNSUPPORTED_ENTITIES: Some unsupported entities exist in the specified regions. The mass properties are computed only for beams, trusses, shells, solids, point and non-structural mass elements, and rotary inertia elements. The mass properties are not computed for axisymmetric elements, springs, connectors, gaskets, or any other elements.

 MISSING_THICKNESS: For some regions, the section definitions are missing thickness values.

 ZERO_THICKNESS: For some regions, the section definitions have a zero thickness value.

 VARIABLE_THICKNESS: The nodal thickness or field thickness specified for some regions has been ignored.

 NON_APPLICABLE_THICKNESS: For some regions, the thickness value is not applicable to the corresponding sections specified on the regions.

 MISSING_DENSITY: For some regions, the section definitions are missing material density values.

 MISSING_MATERIAL_DEFINITION: For some regions, the material definition is missing.

 ZERO_DENSITY: For some regions, the section definitions have a zero material density value.

 UNSUPPORTED_DENSITY: For some regions, either a negative material density or a temperature dependent density has been specified, or the material value is missing for one or more plies in the composite section.

 SHELL_OFFSETS: For shells, this method does not account for any offsets specified.

 MISSING_SECTION_DEFINITION: For some regions, the section definition is missing.

 UNSUPPORTED_SECTION_DEFINITION: The section definition provided for some regions is not supported.

 REINFORCEMENTS: This method does not account for any reinforcements specified on the model.

 SMEARED_PROPERTIES: For regions with composite section assignments, the density is smeared across the thickness. The volume centroid and center of mass computations for a composite shell use a lumped mass approach where the volume and mass is assumed to be lumped in the plane of the shell. As a result of these approximations the volume centroid, center of mass and moments of inertia may be slightly inaccurate for regions with composite section assignments.

 UNSUPPORTED_NON_STRUCTURAL_MASS_ENTITIES: This method does not account for any non-structural mass on wires.

 INCORRECT_MOMENT_OF_INERTIA: For geometry regions with non-structural mass per volume, the non-structural mass is assumed to be a point mass at the centroid of the regions. Thus, the moments of inertia may be inaccurate as the distribution of the non-structural mass is not accounted for. Use the mesh for accurately computing the moments of inertia.

 MISSING_BEAM_ORIENTATIONS: For some regions with beam section assignments, the beam section orientations are missing.

 UNSUPPORTED_BEAM_PROFILES: This method supports the Box, Pipe, Circular, Rectangular, Hexagonal, Trapezoidal, I, L, T, Arbitrary, and Tapered beam profiles. Any other beam profile is not supported.

 TAPERED_BEAM_MI: Moment of inertia calculations for tapered beams are not accurate.

 SUBSTRUCTURE_INCORRECT_PROPERTIES: The user assigned density and thickness is not considered for substructures.

**Exceptions**

None.

### 6.1.8 getAngle(...)

This method returns the angle between the specified entities.

**Required arguments**

*plane1*

A [Face](pt01ch07pyo05.md), [MeshFace](pt01ch31pyo08.md), or a [Datum](pt01ch15pyo01.md) object specifying the first plane. The [Datum](pt01ch15pyo01.md) object must represent a datum plane. The *plane1* and *line1* arguments are mutually exclusive. One of them must be specified.

*plane2*

A [Face](pt01ch07pyo05.md), [MeshFace](pt01ch31pyo08.md), or a [Datum](pt01ch15pyo01.md) object specifying the second plane. The [Datum](pt01ch15pyo01.md) object must represent a datum plane. The *plane2* and *line2* arguments are mutually exclusive. One of them must be specified.

*line1*

An [Edge](pt01ch07pyo03.md), [MeshEdge](pt01ch31pyo04.md), or a [Datum](pt01ch15pyo01.md) object specifying the first curve. The [Datum](pt01ch15pyo01.md) object must represent a datum axis. The *plane1* and *line1* arguments are mutually exclusive. One of them must be specified.

*line2*

An [Edge](pt01ch07pyo03.md), [MeshEdge](pt01ch31pyo04.md), or a [Datum](pt01ch15pyo01.md) object specifying the second curve. The [Datum](pt01ch15pyo01.md) object must represent a datum axis. The *plane2* and *line2* arguments are mutually exclusive. One of them must be specified.

**Optional argument**

*commonVertex*

If the two selected [Edge](pt01ch07pyo03.md) objects have more than one vertex in common, this [Vertex](pt01ch07pyo15.md) object specifies the vertex at which to evaluate the angle.

**Return value**

A Float specifying the angle between the specified entities. If you provide a plane as an argument, Abaqus/CAE computes the angle using the normal to the plane.

**Exceptions**

None.

### 6.1.9 getCoordinates(...)

This method returns the coordinates of a specified point. 

**Required argument**

*entity*

A [Vertex](pt01ch07pyo15.md), [Datum](pt01ch15pyo01.md) point, [MeshNode](pt01ch31pyo09.md), or [ReferencePoint](pt01ch07pyo13.md) specifying the entity to query.

**Optional arguments**

None.

**Return value**

A tuple of three Floats representing the coordinates of the specified point. 

**Exceptions**

None.

### 6.1.10 getDistance(...)

Depending on the arguments provided, this method returns one of the following: 
- The distance between two points.
- The minimum distance between a point and an edge.
- The minimum distance between two edges.

**Required arguments**

*entity1*

A [Vertex](pt01ch07pyo15.md), [Datum](pt01ch15pyo01.md) point, [MeshNode](pt01ch31pyo09.md), or [Edge](pt01ch07pyo03.md) specifying the first entity from which to measure.

*entity2*

A [Vertex](pt01ch07pyo15.md), [Datum](pt01ch15pyo01.md) point, [MeshNode](pt01ch31pyo09.md), or [Edge](pt01ch07pyo03.md) specifying the second entity to which to measure.

**Optional argument**

*printResults*

A Boolean that determines whether a verbose output is to be printed. The default is True 

**Return value**

A Float specifying the calculated distance.

**Exceptions**

None.

### 6.1.11 getFacesAndVerticesOfAttachmentLines(...)

Given an array of edge objects, this method returns a tuple of dictionary objects. Each object consists of five members including the attachment line and associated face and vertex objects.

**Required argument**

*edges*

An [EdgeArray](pt01ch07pyo03.md) object which is a sequence of [Edge](pt01ch07pyo03.md) objects.

**Optional arguments**

None.

**Return value**

A tuple of dictionary objects. Each dictionary contains five items with the following keys:

 *edge*: An [Edge](pt01ch07pyo03.md) object specifying the attachment line.

 *startFace*: A [Face](pt01ch07pyo05.md) object specifying the face associated with one end of the attachment line.

 *endFace*: A [Face](pt01ch07pyo05.md) object specifying the face associated with the other end of the attachment line.

 *startVertex*: A [Vertex](pt01ch07pyo15.md) object specifying the vertex associated with one end of the attachment line. This end is also associated with the startFace.

 *endVertex*: A [Vertex](pt01ch07pyo15.md) object specifying the vertex associated with the other end of the attachment line. This end is also associated with the endFace.

**Exceptions**

None.

### 6.1.12 getSurfaceSections(...)

This method returns a list of the sections assigned to the regions encompassed by the specified surface.

**Required argument**

*surface*

A string specifying the Surface name.

**Optional arguments**

None.

**Return value**

A tuple of strings representing the section names. If no section names are found, the tuple will contain one empty string.

**Exceptions**

None.

### 6.1.13 importEafFile(...)

This method imports an assembly from an EAF file into the root assembly.

**Required argument**

*filename*

A String specifying the path to the EAF file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.14 importParasolidFile(...)

This method imports an assembly from the Parasolid file into the root assembly.

**Required argument**

*filename*

A String specifying the path to a Parasolid file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.15 importCatiaV4File(...)

This method imports an assembly from a CATIA V4 file into the root assembly.

**Required argument**

*filename*

A String specifying the path to the CATIA V4 file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.16 importCatiaV5File(...)

This method imports an assembly from a CATIA V5 Elysium Neutral file into the root assembly.

**Required argument**

*filename*

A String specifying the path to the CATIA V5 Elysium Neutral file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.17 importEnfFile(...)

This method imports an assembly from an Elysium Neutral file created by Pro/ENGINEER, I-DEAS, or CATIA V5 into the root assembly.

**Required argument**

*filename*

A String specifying the path to the Elysium Neutral file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.18 importIdeasFile(...)

This method imports an assembly from an I-DEAS Elysium Neutral file into the root assembly.

**Required argument**

*filename*

A String specifying the path to the I-DEAS Elysium Neutral file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.19 importProEFile(...)

This method imports an assembly from a Pro/ENGINEER Elysium Neutral file into the root assembly.

**Required argument**

*filename*

A String specifying the path to the Pro/ENGINEER Elysium Neutral file from which to import the assembly.

**Optional argument**

You use the following optional argument only to import specific instances and their associated parts.

*ids*

A sequence of Ints. Each Int in the sequence is a unique identifier of the occurrence in the assembly tree or component identifier associated with the part in the EAF file. If *ids* is an empty sequence, all occurrences or parts will be imported. The default value is an empty sequence.

**Return value**

None

**Exceptions**

None.

### 6.1.20 makeDependent(...)

This method converts the specified part instances from independent to dependent part instances.

**Required argument**

*instances*

A sequence of [PartInstance](pt01ch06pyo04.md) objects to convert to dependent part instances. 

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.21 makeIndependent(...)

This method converts the specified part instances from dependent to independent part instances.

**Required argument**

*instances*

A sequence of [PartInstance](pt01ch06pyo04.md) objects to convert to independent part instances. 

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.22 printAssignedSections()

This method prints a summary of assigned connector sections.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.23 printConnectorOrientations()

This method prints a summary of connector orientations.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.24 projectReferencesOntoSketch(...)

This method projects the specified edges, vertices, and datum points from the assembly onto the specified [ConstrainedSketch](pt01ch48pyo01.md) object. The edges, vertices, and datum points appear on the sketch as reference geometry.

**Required argument**

*sketch*

The [ConstrainedSketch](pt01ch48pyo01.md) object on which the edges, vertices, and datum points are projected.

**Optional arguments**

*filter*

A SymbolicConstant specifying how to limit the amount of projection. Possible values are ALL_EDGES and COPLANAR_EDGES. If *filter*=COPLANAR_EDGES, edges that are coplanar to the sketching plane are the only candidates for projection. The default value is ALL_EDGES.

*upToFeature*

A Feature object specifying a marker in the feature-based history of the part. Abaqus/CAE projects onto the sketch only the part entities that were created before the feature specified by this marker. By default, all part entities are candidates for projection.

*edges*

A sequence of candidate edges to be projected onto the sketch. By default, all edges are candidates for projection.

*vertices*

A sequence of candidate vertices to be projected onto the sketch. By default, all vertices are candidates for projection.

**Return value**

None

**Exceptions**

None.

### 6.1.25 queryCachedStates()

This method displays the position of geometric states relative to the sequence of features in the assembly cache. The output is displayed in the message area.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.26 regenerate()

This method regenerates the assembly and brings it up to date with the latest values of the assembly parameters. When you modify features of an assembly, it may be convenient to postpone regeneration until you make all your changes, since regeneration can be time consuming. In contrast, when you modify features of a part that is included in the assembly, you should use this command to regenerate the assembly. When you regenerate the assembly, it will reflect the changes that you made to the part.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.27 regenerationWarnings()

This method prints any regeneration warnings associated with the features.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.28 restore()

This method restores the parameters of all features in the assembly to the value they had before a failed regeneration. Use the `restore` method after a failed regeneration, followed by a `regenerate` command.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.29 resumeAllFeatures()

This method resumes all the suppressed features in the part or assembly.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.30 resumeFeatures(...)

This method resumes the specified suppressed features in the assembly.

**Required argument**

*featureNames*

A sequence of Strings specifying the names of features to resume.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.31 resumeLastSetFeatures()

This method resumes the last set of features to be suppressed in the assembly.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.32 rotate(...)

This method rotates given instances by the specified amount.

**Required arguments**

*instanceList*

A sequence of Strings specifying the names of instances to rotate.

*axisPoint*

A sequence of three Floats specifying the coordinates of a point on the axis.

*axisDirection*

A sequence of three Floats specifying the direction of the axis.

*angle*

A Float specifying the rotation angle in degrees. Use the right-hand rule to determine the direction.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.33 translate(...)

This method translates given instances by the specified amount.

**Required arguments**

*instanceList*

A sequence of Strings specifying the names of instances to translate.

*vector*

A sequence of three Floats specifying a translation vector.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.34 saveGeometryCache()

This method caches the current geometry, which improves regeneration performance.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.35 setValues(...)

This method modifies the behavior associated with the specified assembly.

**Required argument**

*regenerateConstraintsTogether*

A Boolean specifying whether the positioning constraints in the assembly should be regenerated together before regenerating other assembly features. The default value is ON.

If the assembly has position constraint features and you modify the value of *regenerateConstraintsTogether*, Abaqus/CAE will regenerate the assembly features.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If one or more features in the assembly fails to regenerate:

```
FeatureError: Regeneration failed
```

### 6.1.36 suppressFeatures(...)

This method suppresses specified features.

**Required argument**

*featureNames*

A sequence of Strings specifying the names of features to suppress in the assembly.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.37 unlinkInstances(...)

This method converts the specified [PartInstance](pt01ch06pyo04.md) objects from linked child instances to regular instances.  The parts associated with the selected instances will be converted to regular parts as well.

**Required argument**

*instances*

A sequence of [PartInstance](pt01ch06pyo04.md) objects to be converted to regular part instances. 

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.38 writeAcisFile(...)

This method exports the assembly to a named file in ACIS format.

**Required argument**

*fileName*

A String specifying the name of the file to which to write.

**Optional argument**

*version*

A Float specifying the ACIS version. For example, the Float “12.0” corresponds to ACIS Version 12.0. The default value is the current version of ACIS.

**Return value**

None

**Exceptions**

None.

### 6.1.39 writeCADParameters(...)

This method writes the parameters that were imported from the CAD system to a parameter file.

**Required argument**

*paramFile*

A String specifying the parameter file name.

**Optional arguments**

*modifiedParams*

A tuple of tuples each containing the part name, the parameter name and the modified parameter value. Default is an empty tuple.

*updatePaths*

A Bool specifying whether to update the path of the CAD model file specified in the *parameterFile* to the current directory, if the CAD model is present in the current directory.

**Return value**

None

**Exceptions**

None.

### 6.1.40 lock()

This method locks the assembly. Locking the assembly prevents any further changes to the assembly that can trigger regeneration of the assembly.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.41 unlock()

This method unlocks the assembly. Unlocking the assembly allows it to be regenerated after any modifications to the assembly.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 6.1.42 setMeshNumberingControl(...)

This method changes the start node and/or element labels on the specified independent part instances before or after Abaqus/CAE generates the meshes. For the meshed instances, Abaqus/CAE changes the node and/or element labels while preserving the original order and incrementation.

**Required argument**

*instances*

A sequence of [PartInstance](pt01ch06pyo04.md) objects to change the start node and/or element labels. 

**Optional arguments**

*startNodeLabel*

A positive Integer specifying the new start node label.

*startElemLabel*

A positive Integer specifying the new start element label.

**Return value**

None

**Exceptions**

None.

### 6.1.43 copyMeshPattern(...)

 This method copies a mesh pattern from a source region consisting of a set of shell elements or element faces onto a target face, mapping nodes and elements in a one-one correspondence between source and target. 

**Required arguments**

None.

**Optional arguments**

*elements*

A sequence of [MeshElement](pt01ch31pyo05.md) objects or a Set object containing elements and specifying the source region.

*faces*

A sequence of [Face](pt01ch07pyo05.md) objects that have associated with shell elements or element faces and specifying the source region.

*elemFaces*

A sequence of [MeshFace](pt01ch31pyo08.md) objects specifying the source region.

*targetFace*

A  [MeshFace](pt01ch31pyo08.md) object specifying the target region. The target face can be of a different part instance.

*nodes*

A sequence of MeshNode objects or a Set object containing nodes on the boundary of source region which are to be positioned to the boundary of target face.

*coordinates*

A sequence of three-dimensional coordinate tuples specifying the coordinates for each of the given nodes. When specified, the number of coordinate tuples must match the number of given nodes, and be ordered to correspond to the given nodes in *ascending order* according to index. These coordinates are positions of the nodes of a mesh that will be the target face corresponding to nodes provided.

**Return value**

None

**Exceptions**

None.

### 6.1.44 smoothNodes(...)

 This method smoothes the given nodes of a native mesh, moving them locally to a more optimal location that improves quality of the mesh

**Required arguments**

None.

**Optional arguments**

*nodes*

A sequence of MeshNode objects or a Set object containing nodes. Nodes that are not part of native mesh only will be smoothed

*coordinates*

A sequence of MeshNode objects or a Set object containing nodes.

**Return value**

None

**Exceptions**

None.

### 6.1.45 Members

The Assembly object can have the following members:

*isOutOfDate*

An Int specifying that feature parameters have been modified but that the assembly has not been regenerated. Possible values are 0 and 1. 

*timeStamp*

A Float specifying which gives an indication when the assembly was last modified.

*isLocked*

An Int specifying whether the assembly is locked or not. Possible values are 0 and 1.

*regenerateConstraintsTogether*

A Boolean specifying whether the positioning constraints in the assembly should be regenerated together before regenerating other assembly features. The default value is ON.

If the assembly has position constraint features and you modify the value of *regenerateConstraintsTogether*, Abaqus/CAE will regenerate the assembly features.

*vertices*

A [VertexArray](pt01ch07pyo15.md) object specifying all the vertices existing at the assembly level. This member does not provide access to the vertices at the instance level.

*edges*

An [EdgeArray](pt01ch07pyo03.md) object specifying all the edges existing at the assembly level. This member does not provide access to the edges at the instance level.

*elements*

A [MeshElementArray](pt01ch31pyo05.md) object specifying all the elements existing at the assembly level. This member does not provide access to the elements at the instance level.

*nodes*

A [MeshNodeArray](pt01ch31pyo09.md) object specifying all the nodes existing at the assembly level. This member does not provide access to the nodes at the instance level.

*instances*

A repository of [PartInstance](pt01ch06pyo04.md) objects.

*datums*

A repository of [Datum](pt01ch15pyo01.md) objects specifying all [Datum](pt01ch15pyo01.md) objects in the assembly.

*features*

A repository of [Feature](pt01ch20pyo01.md) objects specifying all [Feature](pt01ch20pyo01.md) objects in the assembly.

*featuresById*

A repository of [Feature](pt01ch20pyo01.md) objects specifying all [Feature](pt01ch20pyo01.md) objects in the assembly.

The [Feature](pt01ch20pyo01.md) objects in the `featuresById` repository are the same as the [Feature](pt01ch20pyo01.md) objects in the `features` repository. However, the key to the objects in the `featuresById` repository is an integer specifying the *ID*, whereas the key to the objects in the `features` repository is a string specifying the *name*.

*surfaces*

A repository of [Surface](pt01ch45pyo05.md) objects specifying for more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*allSurfaces*

A repository of [Surface](pt01ch45pyo05.md) objects specifying for more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*allInternalSurfaces*

A repository of [Surface](pt01ch45pyo05.md) objects specifying picked regions.

*sets*

A repository of [Set](pt01ch45pyo04.md) objects.

*allSets*

A repository of [Set](pt01ch45pyo04.md) objects specifying for more information, see [Chapter 45, "Region commands](pt01ch45.md).”

*allInternalSets*

A repository of [Set](pt01ch45pyo04.md) objects specifying picked regions.

*skins*

A repository of [Skin](pt01ch45pyo06.md) objects specifying the skins created on the assembly.

*stringers*

A repository of [Stringer](pt01ch45pyo07.md) objects specifying the stringers created on the assembly.

*referencePoints*

A repository of [ReferencePoint](pt01ch07pyo13.md) objects.

*modelInstances*

A repository of [ModelInstance](pt01ch06pyo05.md) objects.

*allinstances*

A [PartInstance](pt01ch06pyo04.md) object specifying the PartInstances and A [ModelInstance](pt01ch06pyo05.md) object specifying the ModelInstances.

*engineeringFeatures*

An [EngineeringFeature](pt01ch19pyo01.md) object.

*modelName*

A String specifying the name of the model to which the assembly belongs.

*connectorOrientations*

A [ConnectorOrientationArray](pt01ch06pyo02.md) object.

*sectionAssignments*

A [SectionAssignmentArray](pt01ch44pyo01.md) object.




