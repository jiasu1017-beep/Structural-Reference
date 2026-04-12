# Browsing the Abaqus Keywords Reference Guide







This HTML guide describes all of the input options that are available in Abaqus. 

A brief description of the intended use of the keyword is listed at the top of each keyword section.

The **Products** field lists each of the products that support the keyword. Keywords that are at least partially supported in Abaqus/CAE include Abaqus/CAE in the list of products. The user interface in Abaqus/CAE does not necessarily support all optional parameters for each supported keyword. 

The **Type** field indicates whether the keyword appears in the model or history data portion of the input file. For more information, see ["Defining a model in Abaqus," Section 1.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-imodel). 

The **Level** field indicates the level(s) at which the keyword can appear within the input file if the model is defined in terms of an assembly of part instances. For more information, see ["Defining an assembly," Section 2.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ipartassy).

The **Abaqus/CAE** field indicates where within Abaqus/CAE you can locate the user interface related to the keyword. You can also refer to [Appendix A, "Keyword support," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-kwb), which lists all Abaqus keywords and their support within the user interface or from the input file reader. 

To find examples of the usage of a particular keyword in an input file, you can use the **findkeyword** utility (defined in ["Querying the keyword/problem database," Section 3.2.15 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dkeywordproc)) to search the sample input files included with the Abaqus release. The **abaqus fetch** utility is used to extract these input files for use. For example, to fetch input file [boltpipeflange_3d_cyclsym.inp](../eif/boltpipeflange_3d_cyclsym.inp), type

```
abaqus fetch job=boltpipeflange_3d_cyclsym.inp
```
The **abaqus fetch** utility is explained in detail in ["Fetching sample input files," Section 3.2.16 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfetchproc).


