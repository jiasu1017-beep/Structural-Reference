# 61.29 SectorDefinition object







The SectorDefinition object describes the number of symmetry sectors and axis of symmetry for a cyclic symmetry model.

**Access**

```
odb.sectorDefinition()
```

### 61.29.1 Members

The SectorDefinition object has the following members:

**Prototype**

```
int numSectors();
const odb_SequenceSequenceFloat symmetryAxis();
```

*numSectors*

An Int specifying the number of sectors in the cyclic symmetry model.

*symmetryAxis*

An odb_SequenceSequenceFloat specifying the coordinates of two points on the axis of symmetry.




