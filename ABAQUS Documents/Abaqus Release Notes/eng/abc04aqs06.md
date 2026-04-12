# 4.6 Flexible body generation







**Product: **Abaqus/Standard  

**Benefits: **You can now generate a flexible body from a substructure. In flexible body dynamic simulations, this capability can eliminate the need to store the full substructure recovery matrix, which is often very large, improving performance and reducing the size of the substructure `.sim` file.

**Description: **Abaqus/Standard can generate a flexible body from a substructure. The generated flexible body can be used in flexible body dynamic simulations using external solvers. Abaqus/Standard supports generation of several flexible body types that can be used by external flexible body dynamics solvers. The generated flexible body entities are stored in the substructure `.sim` file and can be converted to conventional flexible body representations by postprocessing programs. 
**References: **

**Abaqus Analysis User's Guide**
- ["Defining substructures," Section 10.1.2](../usb/usb-link.md#usb-anl-asuperelementdef)

**Abaqus Keywords Reference Guide**
- [*FLEXIBLE BODY](../key/key-link.md#usb-kws-hflexiblebody)
- [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate)




