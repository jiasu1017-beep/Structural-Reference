# 63.19 RebarLayers object







The RebarLayers object defines the rebar properties of a section.

**Access**

```
sectionApi.sections()[*name*].rebarLayers()
```

### 63.19.1 RebarLayers(...)

This method creates a RebarLayers object.

**Path**

```
sectionApi.sections()[*name*].RebarLayers
```

**Prototype**

```
odb_RebarLayers&
RebarLayers(const odb_String& rebarSpacing,
            const odb_SequenceLayerProperties& layerTable);
```

**Required arguments**

*rebarSpacing*

An odb_String specifying the type of rebar geometry. Possible values are "CONSTANT", "ANGULAR", and "LIFT_EQUATION".

*layerTable*

A sequence of [LayerProperties](pt02ch63pyo15.md) objects specifying the layers of reinforcement.

**Optional arguments**

None.

**Return value**

A RebarLayers object.

**Exceptions**

None.

### 63.19.2 Members

The RebarLayers object has members with the same names and descriptions as the arguments to the [RebarLayers](pt02ch63pyo19.md#ker-rebarlayers-rebarlayers-cpp) method.

### 63.19.3 Corresponding analysis keywords

| [*REBAR LAYER](../key/key-link.md#usb-kws-mrebarlayer) |
| --- |




