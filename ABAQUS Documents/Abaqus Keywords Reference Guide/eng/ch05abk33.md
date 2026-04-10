# *EULERIAN SECTION







### *EULERIAN SECTIONSpecify element properties for Eulerian elements.

This option is used to define properties of Eulerian continuum elements, including the list of materials that may occupy the elements.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["Eulerian elements," Section 32.14.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eeulerianelem)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the Eulerian elements.

### **Optional parameters: **

ADVECTION

Set ADVECTION=SECOND ORDER (default) to use a second-order algorithm to remap solution variables after remeshing has been performed. 

 Set ADVECTION=FIRST ORDER to use a first-order algorithm to remap solution variables after remeshing has been performed.

CONTROLS

Set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used to specify a nondefault hourglass control formulation option or scale factor. The [*SECTION CONTROLS](ch18abk01.md) option can be used to select the hourglass control and order of accuracy of the formulation.

FLUX LIMIT RATIO

Set this parameter equal to the ratio between the maximum distance a node is allowed to move during one increment and the characteristic length of the Eulerian element containing the node. The value of this parameter must be positive. The default value is 1.0, and the suggested range for the value is between 0.1 and 1.0.

### **Data lines to define Eulerian elements: **

**First line:**

Repeat this data line as often as necessary to define the list of all materials that may appear in the Eulerian section.




