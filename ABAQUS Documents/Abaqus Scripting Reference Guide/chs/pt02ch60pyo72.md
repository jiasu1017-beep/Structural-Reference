# 60.72 MullinsEffect object







The MullinsEffect specifies properties for mullins data.

**Access**

```
materialApi.materials()[*name*].mullinsEffect()
```

### 60.72.1 Members

The MullinsEffect object can have the following members:

**Prototype**

```
odb_String definition() const;
bool temperatureDependency() const;
int dependencies() const;
int properties() const;
odb_SequenceSequenceDouble table() const;
odb_SequenceUniaxialTestData uniaxialTests() const;
odb_UniaxialTestData uniaxialTests(int index) const;
odb_SequenceBiaxialTestData biaxialTests() const;
odb_BiaxialTestData biaxialTests(int index) const;
odb_SequencePlanarTestData planarTests() const;
odb_PlanarTestData planarTests(int index) const;
```

*definition*

An odb_String specifying the method of specifying the data. Possible values are "USER", "CONSTANTS", and "TEST_DATA". The default value is "CONSTANTS".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*properties*

An Int specifying the number of property values needed as data for the user-defined hyperelastic material. The default value is 0.

*table*

An odb_SequenceSequenceDouble specifying the items described below. The default value is an empty sequence.

*uniaxialTests*

A sequence of [UniaxialTestData](pt02ch60pyo101.md) objects.

*biaxialTests*

A sequence of [BiaxialTestData](pt02ch60pyo04.md) objects.

*planarTests*

A sequence of [PlanarTestData](pt02ch60pyo76.md) objects.




