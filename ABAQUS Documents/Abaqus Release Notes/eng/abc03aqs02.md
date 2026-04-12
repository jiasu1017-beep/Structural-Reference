# 3.2 Optimization across multiple models







**Product: **Abaqus/CAE  

**Benefits: **You can now create an optimization design response that covers multiple models. This allows you to create an optimization with nonlinear load cases.

**Description: ** You can incorporate multiple models into your optimization when linear perturbations about a base state are no longer sufficient as load cases. For example, you can simulate nonlinear load cases (which are not supported by Abaqus/CAE) by creating multiple copies of your nonlinear model and by creating a step in each model during which different loads and boundary conditions are applied. Each model must have the same Abaqus/CAE geometry, the same mesh, and the same section assignments, and the models must be open in your Abaqus/CAE session. 

**Abaqus/CAE Usage: **
```
Optimization module:
    ****Design Response**![](../graphics/images/arrow.gif)**Create****, **Name:** *design response name*,     **Type:** **Single-term**, **Steps**, **Specify**: **Model**,  **Step and Load Case**
```

**References: **

**Abaqus/CAE User's Guide**
- ["Creating and editing a design response," Section 18.7.1](../usi/usi-link.md#usi-opz-designresponseditor)
- ["Selecting the data source of a design response," Section 18.7.2](../usi/usi-link.md#usi-opz-designresponse-source)




