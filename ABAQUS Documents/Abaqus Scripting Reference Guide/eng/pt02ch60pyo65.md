# 60.65 JouleHeatFraction object







The JouleHeatFraction object defines the fraction of electric energy released as heat.

**Access**

```
materialApi.materials()[*name*].jouleHeatFraction()
```

### 60.65.1 JouleHeatFraction(...)

This method creates a JouleHeatFraction object.

**Path**

```
materialApi.materials()[*name*].JouleHeatFraction
```

**Prototype**

```
odb_JouleHeatFraction&
JouleHeatFraction(double fraction);
```

**Required arguments**

None.

**Optional argument**

*fraction*

A Double specifying the fraction of electrical energy released as heat, including any unit conversion factor. Possible values are 0.0 ![](../graphics/ker_eqn00013.gif) *fraction* ![](../graphics/ker_eqn00013.gif) 1.0. The default value is 1.0.

**Return value**

A JouleHeatFraction object.

**Exceptions**

RangeError.

### 60.65.2 Members

The JouleHeatFraction object has members with the same names and descriptions as the arguments to the [JouleHeatFraction](pt02ch60pyo65.md#ker-jouleheatfraction-jouleheatfraction-cpp) method.

### 60.65.3 Corresponding analysis keywords

| [*JOULE HEAT FRACTION](../key/key-link.md#usb-kws-mjouleheatfrac) |
| --- |




