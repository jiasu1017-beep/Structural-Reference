# 60.58 Gel object







The Gel object defines a swelling gel.

**Access**

```
materialApi.materials()[*name*].gel()
```

### 60.58.1 Gel(...)

This method creates a Gel object.

**Path**

```
materialApi.materials()[*name*].Gel
```

**Prototype**

```
odb_Gel&
Gel(const odb_SequenceSequenceDouble& table);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

None.

**Table data**

- Radius of gel particles when completely dry, ![](../graphics/ker_eqn00259.gif).
- Fully swollen radius of gel particles, ![](../graphics/ker_eqn00260.gif).
- Number of gel particles per unit volume, ![](../graphics/ker_eqn00261.gif).
- Relaxation time constant for long-term swelling of gel particles, ![](../graphics/ker_eqn00262.gif).

**Return value**

A Gel object.

**Exceptions**

None.

### 60.58.2 Members

The Gel object has members with the same names and descriptions as the arguments to the [Gel](pt02ch60pyo58.md#ker-gel-gel-cpp) method.

### 60.58.3 Corresponding analysis keywords

| [*GEL](../key/key-link.md#usb-kws-mgel) |
| --- |




