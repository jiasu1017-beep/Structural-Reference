# *SURFACE







### *SURFACEDefine a surface or region in a model.

This option is used to define surfaces for contact simulations, tie constraints, fasteners, and coupling, as well as regions for distributed surface loads, acoustic radiation, acoustic impedance, and output of integrated quantities on a surface. In Abaqus/Standard it is also used to define surfaces for cavity radiation analysis and assembly loads. In Abaqus/Explicit this option can also be used to define boundary regions on adaptive mesh domains.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Element-based surfaces are supported by the Surface toolset. Node-based surfaces are not supported; if node-based surfaces are imported into Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak?, they are treated as sets.

##### **References:**

- ["Surfaces: overview," Section 2.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-asurfoverview)
- ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["Node-based surface definition," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)
- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)
- ["Eulerian surface definition," Section 2.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-aeulsurf)
- ["Operating on surfaces," Section 2.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-acombinedsurf)
- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["Contact interaction analysis: overview," Section 36.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactoverview)
- ["RSURFU," Section 1.1.16 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ursurfu)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the surface.

### **Required parameter for cavity radiation simulations: **

PROPERTY

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the name of the [*SURFACE PROPERTY](ch18abk52.md) definition associated with this surface. See ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation).

### **Optional parameters: **

COMBINE

Set COMBINE=UNION to create a surface based on the union of two or more surfaces of the same type.

Set COMBINE=INTERSECTION to create a surface based on the intersection of two surfaces of the same type.

Set COMBINE=DIFFERENCE to create a surface based on the difference of two surfaces of the same type (the second surface is subtracted from the first).

 Only the NAME parameter and, in cavity radiation simulations, the PROPERTY parameter can be used in conjunction with this parameter.

CROP

Include this parameter to create a new surface that will contain only those faces from an existing surface that have nodes in a specified rectangular box.

Only the NAME parameter and, in cavity radiation simulations, the PROPERTY parameter can be used in conjunction with this parameter.

DEFINITION

This parameter is relevant only for surfaces defined using TYPE=CUTTING SURFACE.

Set DEFINITION=COORDINATES (default) to define the cutting plane by giving the coordinates of a point on the cutting plane and the normal to the cutting plane.

Set DEFINITION=NODES to define the cutting plane by giving global node numbers for point *a* on the cutting plane and point *b* that lies off the cutting plane with the cutting plane normal determined by the vector from *a* to *b*.

FILLET RADIUS

This parameter can be used with TYPE=SEGMENTS, TYPE=CYLINDER, or TYPE= REVOLUTION to define a radius of curvature to smooth discontinuities between adjoining straight-line segments, adjoining circular-arc segments, and adjoining straight-line and circular-arc segments.

INTERNAL

Abaqus/CAE uses the INTERNAL parameter to identify surfaces that are created internally. The INTERNAL parameter is used only in models defined in terms of an assembly of part instances. The default is to omit the INTERNAL parameter.

REGION TYPE

This parameter is relevant only for surfaces defined on the boundary of an adaptive mesh domain. A surface defined in the interior of an adaptive mesh domain will move independently of the material unless the surface is constrained by mesh constraints. See ["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains).

Set REGION TYPE=LAGRANGIAN to create a Lagrangian boundary region. The edge of a Lagrangian boundary region will follow the material while allowing adaptive meshing along the edge and within the interior of the region.

Set REGION TYPE=SLIDING (default) to create a sliding boundary region. The edge of a sliding boundary region will slide over the material. Adaptive meshing will occur on the edge and within the interior of the region. Mesh constraints are typically applied on the edge of a sliding boundary region to fix it spatially.

Set REGION TYPE=EULERIAN to create an Eulerian boundary region in an adaptive mesh domain. This option is used to create a boundary region across which material can flow. Mesh constraints must be used normal to an Eulerian boundary region to allow material to flow through the region. If no mesh constraints are applied, an Eulerian boundary region will behave in the same way as a sliding boundary region.

TRIM

Set TRIM=YES to invoke trimming of open free surfaces. Set TRIM=NO to suppress surface trimming. The default value is TRIM=YES unless the surface is used as a master surface in a finite-sliding contact formulation in Abaqus/Standard or the surface is used with the contact pair algorithm in Abaqus/Explicit. TRIM=YES has no effect on surfaces used with the contact pair algorithm in Abaqus/Explicit.

TYPE

Set TYPE=ELEMENT (default) to define a free surface automatically for the elements specified or to define a surface on the elements by using element face identifiers.

Set TYPE=NODE to define a surface by specifying a list of nodes or node set labels.

Set TYPE=SEGMENTS to create a two-dimensional analytical surface in the ![](../graphics/key_eqn01033.gif) plane for planar models or in the ![](../graphics/key_eqn01034.gif) plane for axisymmetric models by defining connected line segments.

Set TYPE=CYLINDER to define a three-dimensional analytical surface by sweeping connected line segments defined in a local (*x*, *y*) plane along a specified generator vector.

Set TYPE=REVOLUTION to define a three-dimensional analytical surface by providing connected line segments, which are given in an ![](../graphics/key_eqn01034.gif) plane and are rotated about an axis.

Set TYPE=CUTTING SURFACE to generate an interior element-based surface using a cutting plane passing through an element set. The generated surface is an approximation to the cutting plane.

Set TYPE=EULERIAN MATERIAL to define a surface on the exterior boundary of an Eulerian material instance. This option applies only to Abaqus/Explicit.

Set TYPE=USER to define an analytical surface via user subroutine [`RSURFU`](../sub/sub-link.md#sub-xsl-rsurfu) in Abaqus/Standard.

Set TYPE=XFEM to generate a crack surface for enriched cracked elements. The generated surface is supported only for the application of distributed pressure loads. This option applies only to Abaqus/Standard.

### **Additional optional parameters used for contact pair analyses in Abaqus/Explicit: **

MAX RATIO

Set this parameter equal to the upper bound of the ratio of a facet's contact thickness to its minimum edge (or diagonal) length. This ratio is computed after the SCALE THICK parameter is applied to the contact thickness. The contact thickness for individual facets will be adjusted, if necessary, to conform to this maximum ratio.

If this parameter is omitted, no upper bound will be enforced. If this parameter is included without a value specified, the default value is 0.6.

NO OFFSET

Include this parameter to indicate that this surface will ignore the midplane offset of any shell, membrane, or rigid elements that form the surface.

NO THICK

Include this parameter to indicate that this surface will ignore the thickness of any shell, membrane, or rigid elements that form the surface. A surface defined with this parameter cannot be used to define a double-sided surface or for self-contact.

SCALE THICK

This parameter applies only when the surface is used with the [*CONTACT PAIR](ch03abk68.md) option.

Set this parameter equal to the amount by which to scale the thicknesses of the underlying elements to compute the contact thicknesses. The default is 1.0 (i.e., no scaling).

### **Data lines for COMBINE=UNION: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **Data line for COMBINE=INTERSECTION or COMBINE=DIFFERENCE: **

**First (and only) line:**

For COMBINE=DIFFERENCE the second surface is subtracted from the first.

### **Data lines to define a surface when the CROP parameter is included: **

**First line:**

**Second line:**

**Third line (optional):**

### **Data lines to define a surface using elements or element sets when the TYPE=ELEMENT parameter is used: **

**First line:**

Repeat this data line as often as necessary to define the surface.

### **Data lines to define a surface using nodes or node sets when the TYPE=NODE parameter is used: **

**First line:**

Repeat this data line as often as necessary to define the surface.

### **Data lines to define a surface using a plane cutting through the given element sets when TYPE=CUTTING SURFACE, DEFINITION=COORDINATES: **

**First line:**

**Second line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **Data lines to define a surface using a plane cutting through the given element sets when TYPE=CUTTING SURFACE, DEFINITION=NODES: **

**First line:**

**Second line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **Data line to define surfaces created with TYPE=EULERIAN MATERIAL: **

**First line:**

### **Data lines to define a crack surface created with TYPE=XFEM: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **No data lines are needed for TYPE=USER. **

### **Data lines to define surfaces created with TYPE=SEGMENTS: **

**First line:**

Second and subsequent data lines define the various line, circular, and parabolic segments (see below for their format) that form the profile of the analytical surface.

### **Data lines to define surfaces created with TYPE=CYLINDER: **

**First line (leave blank if this surface is being defined within a part or a part instance):**

**Second line (leave blank if this surface is being defined within a part or a part instance):**

**Third line:**

Fourth and subsequent data lines define the various line, circular, and parabolic segments (see below for their format) that form the profile of the analytical surface.

### **Data lines to define surfaces created with TYPE=REVOLUTION: **

**First line (leave blank if this surface is being defined within a part or a part instance):**

**Second line:**

Third and subsequent data lines define the various line, circular, and parabolic segments (see below for their format) that form the profile of the analytical surface.

### **Data lines that define the line segments that form the analytical surface for TYPE=SEGMENTS, TYPE=CYLINDER, and TYPE=REVOLUTION: **

**Data line to define a straight line segment:**

**Data line to define a circular arc segment (the arc must be less than 179.74):**

**Data line to define a parabolic arc segment:**

For surfaces created with TYPE=SEGMENTS, the *x*- and *y*-coordinates are the global *X*- and *Y*-coordinates or *r*- and *z*-coordinates. For surfaces created with TYPE=CYLINDER, the *x*- and *y*-coordinates are the local *x*- and *y*-coordinates. For surfaces created with TYPE=REVOLUTION, the *x*- and *y*-coordinates are the local *r*- and *z*-coordinates.

**Figure 18.47–1** [*SURFACE](ch18abk47.md), TYPE=CYLINDER.

![](../graphics/krigidsurface-cylinder-nls.png)

**Figure 18.47–2** [*SURFACE](ch18abk47.md), TYPE=REVOLUTION.

![](../graphics/krigidsurface-rev-nls.png)




