# 50.10 RandomResponseFrequency object







A RandomResponseFrequency is an object used to define frequency over a range of modes.

**Access**

```
import step
mdb.models[*name*].steps[*name*].freq[*i*]
```

### 50.10.1 Members

The RandomResponseFrequency object has the following members:

*lower*

A Float specifying the lower limit of the frequency range in cycles per time.

*upper*

A Float specifying the upper limit of the frequency range in cycles per time.

*nCalcs*

An Int specifying the number of points between eigenfrequencies at which the response should be calculated.

*bias*

A Float specifying the bias parameter.




