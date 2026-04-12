# 56.1 Amplitude object







The Amplitude object is the abstract base type for other Amplitude objects. The Amplitude object has no explicit constructor. The methods and members of the Amplitude object are common to all objects derived from the Amplitude.

**Access**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.1.1 Members

The Amplitude object has the following members:

**Prototype**

```
odb_String name() const;
odb_String timeSpan() const;
```

*name*

An odb_String specifying the repository key.

*timeSpan*

An odb_String specifying the time span of the amplitude. Possible values are "STEP" and "TOTAL". The default value is "STEP".




