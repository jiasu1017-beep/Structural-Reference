# 7.6 FaceArray object







The FaceArray is a sequence of [Face](pt01ch07pyo05.md)                 objects. If the part is modified, then FaceArray must be updated for that part.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].faces
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].faces
mdb.models[*name*].parts[*name*].allSets[*name*].faces
mdb.models[*name*].parts[*name*].allSurfaces[*name*].faces
mdb.models[*name*].parts[*name*].faces
mdb.models[*name*].parts[*name*].sets[*name*].faces
mdb.models[*name*].parts[*name*].surfaces[*name*].faces
import assembly
mdb.models[*name*].rootAssembly.allinstances.faces
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].faces
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].faces
mdb.models[*name*].rootAssembly.allInternalSets[*name*].faces
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].faces
mdb.models[*name*].rootAssembly.allSets[*name*].faces
mdb.models[*name*].rootAssembly.allSurfaces[*name*].faces
mdb.models[*name*].rootAssembly.instances[*name*].faces
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].faces
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].faces
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].faces
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*].faces
mdb.models[*name*].rootAssembly.sets[*name*].faces
mdb.models[*name*].rootAssembly.surfaces[*name*].faces
```

### 7.6.1 findAt(...)

This method returns the object or objects in the FaceArray located at the given coordinates.

 `findAt`                       initially uses the ACIS tolerance of 1E-6. As a result, `findAt`                       returns any face that is at the arbitrary point specified or at a distance of less than 1E-6 from the arbitrary point. If nothing is found, `findAt`                       uses the tolerance for imprecise geometry (applicable only for imprecise geometric entities). The arbitrary point must not be shared by a second face. If two faces intersect or coincide at the arbitrary point, `findAt`                       chooses the first face that it encounters, and you should not rely on the return value being consistent.

 `findAt`                       will always try to find objects among all the faces in the part or assembly instance and will not restrict itself to a subset even if the FaceArray represents such subset.

**Required argument**

*coordinates*

A sequence of Floats specifying the *X*-, *Y*-, and *Z*-coordinates of the object to find.

 `findAt`                                returns either a Face object or a sequence of Face objects based on the type of input.
- If *coordinates* is a sequence of Floats, `findAt` returns the Face object at that point.
- If you omit the *coordinates* keyword argument, `findAt` accepts as arguments a sequence of pairs of sequences describing each face's coordinate and normal, and `findAt` returns a sequence of Face objects at the given locations. If you omit the *coordinates* keyword argument, you must also omit the *normal* argument. ``` faces = f.findAt(((-16.438578, -41.835673, -24.19804), ), ((25.210364, -35.689868, 1.860314), ), ((26.727683, -38.207055, 4.164759), )) ```

**Optional arguments**

*normal*

A sequence of Floats specifying the *X*-, *Y*-, and *Z*-components of a vector indicating the face normal.

*printWarning*

A Boolean specifying whether a message is to be printed to the CLI if no entity is found at the specified location. The default value is True.

**Return value**

A Face object.

**Exceptions**

None.

### 7.6.2 getSequenceFromMask(...)

This method returns the object or objects in the FaceArray identified using the specified *mask*. This command is generated when the [JournalOptions](pt01ch47pyo06.md)                       are set to COMPRESSEDINDEX. When a large number of objects are involved, this method is highly efficient.

**Required argument**

*mask*

A String specifying the object or objects.

**Optional arguments**

None.

**Return value**

A Face object or a sequence of Face objects.

**Exceptions**

None.

### 7.6.3 getMask()

This method returns a string specifying the object or objects.

**Arguments**

None.

**Return value**

                 A String specifying the object or objects.

**Exceptions**

None.

### 7.6.4 getByBoundingBox(...)

This method returns an array of face objects that lie within the specified bounding box.

**Required arguments**

None.

**Optional arguments**

*xMin*

A float specifying the minimum *X*-boundary of the bounding box.

*yMin*

A float specifying the minimum *Y*-boundary of the bounding box.

*zMin*

A float specifying the minimum *Z*-boundary of the bounding box.

*xMax*

A float specifying the maximum *X*-boundary of the bounding box.

*yMax*

A float specifying the maximum *Y*-boundary of the bounding box.

*zMax*

A float specifying the maximum *Z*-boundary of the bounding box.

**Return value**

A FaceArray                       object, which is a sequence of [Face](pt01ch07pyo05.md)                       objects.

**Exceptions**

None.

### 7.6.5 getByBoundingCylinder(...)

This method returns an array of face objects that lie within the specified bounding cylinder.

**Required arguments**

*center1*

A tuple of the *X*-, *Y*-, and *Z*-coordinates of the center of the first end of the cylinder.

*center2*

A tuple of the *X*-, *Y*-, and *Z*-coordinates of the center of the second end of the cylinder.

*radius*

A float specifying the radius of the cylinder.

**Optional arguments**

None.

**Return value**

A FaceArray                       object, which is a sequence of [Face](pt01ch07pyo05.md)                       objects.

**Exceptions**

None.

### 7.6.6 getByBoundingSphere(...)

This method returns an array of face objects that lie within the specified bounding sphere.

**Required arguments**

*center*

A tuple of the *X*-, *Y*-, and *Z*-coordinates of the center of the sphere.

*radius*

A float specifying the radius of the sphere.

**Optional arguments**

None.

**Return value**

A FaceArray                       object, which is a sequence of [Face](pt01ch07pyo05.md)                       objects.

**Exceptions**

None.

### 7.6.7 getBoundingBox()

This method returns a dictionary of two tuples representing minimum and maximum boundary                      values of the bounding box of the minimum size containing the face sequence.

**Arguments**

None.

**Return value**

A Dictionary object with the following items:

 *low*: a tuple of three floats representing the minimum *X*-, *Y*-, and *Z*-boundary values of the bounding box.

 *high*: a tuple of three floats representing the maximum *X*-, *Y*-, and *Z*-boundary values of the bounding box.

**Exceptions**

None.

### 7.6.8 getClosest(...)

This method returns an object or objects in the FaceArray closest to the given set of points, where the given points need not lie on the faces in the FaceArray. 

**Required argument**

*coordinates*

A sequence of a sequence of floats, where each sequence of floats describes the *X*-, *Y*-, and *Z*-coordinates of a point.

```
r=f.getClosest(coordinates=((20.0,20.0,10.0),(-1.0, -15.0, 15),))
```

```
r.keys()
```

```
[0, 1]
```

```
r[0]
```

```
(mdb.models['Model-1'].parts['Part-1'].faces[0],
                                 (15.7090625762939, 20.0, 10.0))
```

**Optional argument**

*searchTolerance*

A double specifying the distance within which the closest object must lie. The default value is half of the parent part/instance size.

**Return value**

This method returns a dictionary object. The key to the dictionary object is the position of the input point in the tuple specified in the *coordinates*                       starting at index 0. If a closest face could be found then the value is a sequence consisting of two objects. The first object in the sequence is a [Face](pt01ch07pyo05.md)                       that is close to the input point referred to by the key. The second object in the sequence is a sequence of floats that specifies the *X*-, *Y*-, and *Z*-location of the closest point on the [Face](pt01ch07pyo05.md)                     to the given point. See program listing above.

**Exceptions**

An exception occurs if the resulting sequence is empty.

```
Error: The mask results in an empty sequence
```

### 7.6.9 Members

The FaceArray object has no members.




