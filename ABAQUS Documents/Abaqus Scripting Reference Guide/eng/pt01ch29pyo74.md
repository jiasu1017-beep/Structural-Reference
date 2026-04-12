# 29.74 Permeability object







The Permeability object defines permeability for pore fluid flow.

**Access**

```
import material
mdb.models[*name*].materials[*name*].permeability
import odbMaterial
session.odbs[*name*].materials[*name*].permeability
```

### 29.74.1 Permeability(...)

This method creates a Permeability object.

**Path**

```
mdb.models[*name*].materials[*name*].Permeability
session.odbs[*name*].materials[*name*].Permeability
```

**Required arguments**

*specificWeight*

A Float specifying the specific weight of the wetting liquid, ![](../graphics/ker_eqn00296.gif).

*inertialDragCoefficient*

A Float specifying                   The inertial drag coefficient of the wetting liquid, ![](../graphics/ker_eqn00296.gif).

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of permeability. Possible values are ISOTROPIC, ORTHOTROPIC, ANISOTROPIC, ISOTROPIC-CFD, and CARMAN_KOZENY. The default value is ISOTROPIC.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- ![](../graphics/ker_eqn00143.gif).
- Void ratio, ![](../graphics/ker_eqn00289.gif).
- Temperature, if the data depend on temperature.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00144.gif).
- ![](../graphics/ker_eqn00145.gif).
- ![](../graphics/ker_eqn00146.gif).
- Void ratio, ![](../graphics/ker_eqn00289.gif).
- Temperature, if the data depend on temperature.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00144.gif).
- ![](../graphics/ker_eqn00147.gif).
- ![](../graphics/ker_eqn00145.gif).
- ![](../graphics/ker_eqn00148.gif).
- ![](../graphics/ker_eqn00149.gif).
- ![](../graphics/ker_eqn00146.gif).
- Void ratio, ![](../graphics/ker_eqn00289.gif).
- Temperature, if the data depend on temperature.

If *type*=ISOTROPIC_CFD, the table data specify the following:- ![](../graphics/ker_eqn00143.gif).
- Porosity, ![](../graphics/ker_eqn00289.gif).

If *type*=CARMAN_KOZENY, the table data specify the following:- Kozeny constant![](../graphics/ker_eqn00289.gif).
- Pore particle radius, ![](../graphics/ker_eqn00289.gif).

**Return value**

A Permeability object.

**Exceptions**

RangeError.

### 29.74.2 setValues(...)

This method modifies the Permeability object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Permeability](pt01ch29pyo74.md#ker-permeability-permeability-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.74.3 Members

The Permeability object has members with the same names and descriptions as the arguments to the [Permeability](pt01ch29pyo74.md#ker-permeability-permeability-pyc) method.

In addition, the Permeability object can have the following members:

*saturationDependence*

A [SaturationDependence](pt01ch29pyo88.md) object specifying the dependence of the permeability of a material on the saturation of the wetting liquid.

*velocityDependence*

A [VelocityDependence](pt01ch29pyo105.md) object specifying the dependence of the permeability of a material on the velocity of fluid flow.

### 29.74.4 Corresponding analysis keywords

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |




