# 40.14 OdbDataNodeSet object







The OdbDataNodeSet object stores node set data.

**Access**

```
import visualization
session.odbData[*name*].nodeSets[*i*]
```

### 40.14.1 Members

The OdbDataNodeSet object has the following members:

*name*

A String specifying the set name. This attribute is read-only.

*nodes*

A String-to-tuple-of-Ints Dictionary specifying the nodes in the set. This attribute is read-only.




