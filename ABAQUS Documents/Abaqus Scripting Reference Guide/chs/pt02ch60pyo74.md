# 60.74 Permeability object







The Permeability object defines permeability for pore fluid flow.

**Access**

```
materialApi.materials()[*name*].permeability()
```

### 60.74.1 Permeability(...)

This method creates a Permeability object.

**Path**

```
materialApi.materials()[*name*].Permeability
```

**Prototype**

```
odb_Permeability&
Permeability(double specificWeight,
             double inertialDragCoefficient,
             const odb_SequenceSequenceDouble& table,
             const odb_String& type,
             bool temperatureDependency,
             int dependencies);
```

**Required arguments**

*specificWeight*

A Double specifying the specific weight of the wetting liquid, ![](../graphics/ker_eqn00296.gif).

*inertialDragCoefficient*

A Double specifying                   The inertial drag coefficient of the wetting liquid, ![](../graphics/ker_eqn00296.gif).

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of permeability. Possible values are "ISOTROPIC", "ORTHOTROPIC", "ANISOTROPIC", "ISOTROPIC-CFD", and "CARMAN_KOZENY". The default value is "ISOTROPIC".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

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

### 60.74.2 Members

The Permeability object has members with the same names and descriptions as the arguments to the [Permeability](pt02ch60pyo74.md#ker-permeability-permeability-cpp) method.

In addition, the Permeability object can have the following members:

**Prototype**

```
odb_SaturationDependence saturationDependence() const;
odb_VelocityDependence velocityDependence() const;
```

*saturationDependence*

A [SaturationDependence](pt02ch60pyo88.md) object specifying the dependence of the permeability of a material on the saturation of the wetting liquid.

*velocityDependence*

A [VelocityDependence](pt02ch60pyo105.md) object specifying the dependence of the permeability of a material on the velocity of fluid flow.

### 60.74.3 Corresponding analysis keywords

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |




