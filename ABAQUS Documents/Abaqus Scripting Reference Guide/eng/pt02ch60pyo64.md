# 60.64 InelasticHeatFraction object







The InelasticHeatFraction object defines the fraction of the rate of inelastic dissipation that appears as a heat source.

**Access**

```
materialApi.materials()[*name*].inelasticHeatFraction()
```

### 60.64.1 InelasticHeatFraction(...)

This method creates an InelasticHeatFraction object.

**Path**

```
materialApi.materials()[*name*].InelasticHeatFraction
```

**Prototype**

```
odb_InelasticHeatFraction&
InelasticHeatFraction(double fraction);
```

**Required arguments**

None.

**Optional argument**

*fraction*

A Double specifying the fraction of inelastic dissipation rate that appears as a heat flux per unit volume. The fraction may include a unit conversion factor if required. Possible values are 0.0 ![](../graphics/ker_eqn00013.gif) *fraction* ![](../graphics/ker_eqn00013.gif) 1.0. The default value is 0.9.

**Return value**

An InelasticHeatFraction object.

**Exceptions**

RangeError.

### 60.64.2 Members

The InelasticHeatFraction object has members with the same names and descriptions as the arguments to the [InelasticHeatFraction](pt02ch60pyo64.md#ker-inelasticheatfraction-inelasticheatfraction-cpp) method.

### 60.64.3 Corresponding analysis keywords

| [*INELASTIC HEAT FRACTION](../key/key-link.md#usb-kws-minelastheatfrac) |
| --- |




