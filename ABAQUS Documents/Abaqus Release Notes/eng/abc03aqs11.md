# 3.11 Bidirectional import of parameters using the CATIA V6 Associative Interface







**Product: **Abaqus/CAE  

**Benefits: **After importing a model using the CATIA V6 Associative Interface, you can modify geometry parameters in the model. Both the Abaqus/CAE model and the original CATIA V6 model are updated based on the modified parameters, which allows you to keep your Abaqus/CAE and CATIA V6 models synchronized while you iterate on a design.

**Description: ** The parameter update capability for the CATIA V6 Associative Interface allows you to work exclusively in Abaqus/CAE after importing a model from CATIA V6 while keeping the original CATIA V6 model up to date with any geometric changes. Certain geometry parameters can be modified in Abaqus/CAE, then these modifications are propagated to the original CATIA V6 model (this functionality was previously available for only CATIA V5 and Pro/ENGINEER models).

To use bidirectional import, you must first specify the parameters and their values in the CATIA V6 model that will be imported into Abaqus/CAE. These parameters are used to define dimensions in the CATIA V6 model; for example, a parameter may be used to specify the radius of a hole feature. When you import the model into Abaqus/CAE using the CATIA V6 Associative Interface, the list of specified parameters is also imported. You use the **CAD Parameters** dialog box in Abaqus/CAE to modify the values of each parameter. When you click **Update**, the features associated with the modified dimensions are regenerated, and the model's geometry is updated in Abaqus/CAE and in the CATIA V6 model.  

For detailed instructions on using bidirectional import, download the CATIA V6 Associative Interface User's Guide from the Dassault Systmes Knowledge Base at [www.3ds.com/support/knowledge-base](http://www.3ds.com/support/knowledge-base).

**Abaqus/CAE Usage: **
```
Part module:
    ****Tools**![](../graphics/images/arrow.gif)**CAD Parameters****. 
Assembly module:
    ****Tools**![](../graphics/images/arrow.gif)**CAD Interfaces**![](../graphics/images/arrow.gif)**CAD Parameters****. 
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Updating geometry parameters in an imported model," Section 60.2](../usi/usi-link.md#usi-cad-bidirectional)




