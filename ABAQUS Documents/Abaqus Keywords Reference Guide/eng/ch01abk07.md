# *ADAPTIVE MESH REFINEMENT







### *ADAPTIVE MESH REFINEMENTActivate adaptive mesh refinement in an Eulerian domain.

This option is used to activate adaptive mesh refinement in an Eulerian domain and to specify the refinement criteria in that domain. 

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["Defining adaptive mesh refinement in the Eulerian domain," Section 14.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeulerianadaptivemeshrefinement)
- [*EULERIAN SECTION](ch05abk33.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set where adaptive mesh refinement is applied.

### **Optional parameter: **

LEVEL

Set this parameter equal to the maximum number of levels of refinement. The default value is 1.

COARSENING

Set COARSENING=YES (default) to specify that refinement can be removed once the refinement criteria are no longer met. 

Set COARSENING=NO to specify that refinement cannot be removed even when the refinement criteria are no longer met. 

RATIO

Set this parameter equal to the ratio of the maximum increase in the number of elements during mesh refinement compared to the original number of elements in the specified element set. The default value is 8.0.

### **Data lines to define the criteria used in the mesh refinement: **

**First line:**




