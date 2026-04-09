# 8.3 Including nonlinearity in an Abaqus analysis

We now discuss how to account for nonlinearity in an Abaqus analysis. The main focus is on geometric nonlinearity.

## 8.3.1 Geometric nonlinearity

Incorporating the effects of geometric nonlinearity in an analysis requires only minor changes to an Abaqus/Standard model. You need to make sure the step definition considers geometrically nonlinear effects by setting the `NLGEOM` parameter equal to `YES` on the `*STEP` option. This is the default setting in Abaqus/Explicit. You also need to set time incrementation parameters as discussed in ["Automatic incrementation control in Abaqus/Standard," Section 8.2.3](ch08s02.html#gsk-gen-nln-automatic).

The following input describes a static analysis in which the load is applied over 5 units of time and the initial time increment is 1 unit of time; the minimum and maximum time increments are set to 0.0001 and 1.5, respectively:

![](../graphics/gss-c7-delta-t-input.png)

Abaqus will apply 20% (1.0/5.0) of the total load in the first increment, and it will terminate the analysis if it has problems converging and requires an increment smaller than 0.0001. If the time increment grows because the solution is converging easily, the maximum time increment Abaqus can use is 1.5.

**Local directions**

In a geometrically nonlinear analysis the local material directions may rotate with the deformation in each element. For shell, beam, and truss elements the local material directions always rotate with the deformation. For solid elements the local material directions rotate with the deformation only if the elements refer to an `*ORIENTATION` option; otherwise, the default local material directions remain constant throughout the analysis.

Local directions defined at nodes by using the `*TRANSFORM` option remain fixed throughout the analysis; they do not rotate with the deformation. See ["Transformed coordinate systems," Section 2.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.htm#usb-int-ptransform) for further details.

**Effect on subsequent steps**

Once you include geometric nonlinearity in a step, it is considered in all subsequent steps. If nonlinear geometric effects are not requested in a subsequent step, Abaqus will issue a warning stating that they are being included in the step anyway.

**Other geometrically nonlinear effects**

The large deformations in a model are not the only important effects that are considered when geometric nonlinearity is activated. Abaqus/Standard also includes terms in the element stiffness calculations that are caused by the applied loads, the so-called load stiffness. These terms improve convergence behavior. In addition, the membrane loads in shells and the axial loads in cables and beams contribute much of the stiffness of these structures in response to transverse loads. By including geometric nonlinearity, the membrane stiffness in response to transverse loads is considered as well.

## 8.3.2 Material nonlinearity

The addition of material nonlinearity to an Abaqus model is discussed in [Chapter 10, "Materials"](ch10.html).

## 8.3.3 Boundary nonlinearity

The introduction of boundary nonlinearity is discussed in [Chapter 12, "Contact"](ch12.html).
