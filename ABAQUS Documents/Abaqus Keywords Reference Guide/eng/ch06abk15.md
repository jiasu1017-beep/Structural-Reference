# *FLEXIBLE BODY







### *FLEXIBLE BODYGenerate a flexible body from a substructure.

This option is used to generate a flexible body from an Abaqus/Standard substructure. Abaqus/Standard generates several flexible body types that can be used by external flexible body dynamics solvers. The generated flexible body entities are stored in the substructure `.sim` file and can be postprocessed to generate the input data for external flexible body dynamics solvers.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)
- [*SUBSTRUCTURE GENERATE](ch18abk42.md)

### **Optional parameter: **

TYPE

Set TYPE=ADAMS to generate flexible body entities for the Adams flexible body dynamics solver from MSC.Software Corporation.

Set TYPE=EXCITE to generate the CON6 flexible body entities for the EXCITE flexible body dynamics solver from AVL.

Set TYPE=GENERIC (default) to generate a generic flexible body. A generic flexible body can be converted into Adams, SIMPACK, or EXCITE flexible bodies by the postprocessing programs.

Set TYPE=SID to generate the Standard Input Data representation of the flexible body.

Set TYPE=SIMPACK to generate flexible body entities for the SIMPACK flexible body dynamics solver from SIMPACK AG.

**There are no data lines associated with this option.**



