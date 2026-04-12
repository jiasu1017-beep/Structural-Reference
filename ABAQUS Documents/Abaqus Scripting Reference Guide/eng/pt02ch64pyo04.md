# 64.4 Sequence object







An odb_Sequence object is a repository used to hold an ordered list of objects of a specific type. Data are added using the `append` method. The odb_Sequence object will automatically allocate memory to contain the appended object; the user may, however, control the efficiency of the memory allocation process through the constructor. 

### 64.4.1 odb_Sequence*Type*(...)

This method creates an empty odb_Sequence object of objects of type *Type*.

**Path**

```
odb_Sequence*Type*
```

**Prototype**

```
odb_Sequence*Type*();
```

**Required arguments**

None.

**Optional arguments**

*intialSize*

 An Int specifying the amount of memory to be allocated when the object is created. The default value is 0.

**Return value**

An empty odb_Sequence object.

**Exceptions**

None.

### 64.4.2 append(...)

This method adds items to an odb_Sequence object.

**Prototype**

```
void append(*Type* item);
```

**Required argument**

*item*

 An item of type *Type* to be appended to the odb_Sequence object, where *Type* must be one of the following:
- Float
- Int
- String
- SectionLayer
- LayerProperties
- FieldOutput

 For example, an odb_SequenceInt object accepts an argument of type Int.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 64.4.3 constGet/get(...)

This method accesses an item in an odb_Sequence object.

**Prototype**

```
*Type* get(int index);
const *Type*& constGet(int index) const;
```

**Required argument**

*index*

 An Int specifying the index of the item to be accessed from the odb_Sequence object.

**Optional arguments**

None.

**Return value**

An item of the *Type* stored in the odb_Sequence object.

**Exceptions**

None.

### 64.4.4 isMember(...)

This method checks whether an object is stored in the sequence.

**Prototype**

```
bool isMember(const *Type*& item) const;
```

**Required argument**

*item*

An object of type *Type*.

**Optional arguments**

None.

**Return value**

A Boolean specifying whether the object is stored in the sequence.

**Exceptions**

None.

### 64.4.5 operator[](...)

This method accesses an item in an odb_Sequence object.

**Prototype**

```
const *Type*& [int index] const;
```

**Required argument**

*index*

 An Int specifying the index of the item to be accessed from the odb_Sequence object.

**Optional arguments**

None.

**Return value**

An item of the *Type* stored in the odb_Sequence object.

**Exceptions**

None.

### 64.4.6 size(...)

This method returns the number of items in an odb_Sequence object.

**Prototype**

```
int size() const;
```

**Arguments**

None.

**Return value**

An Int indicating the number of items in the sequence.

**Exceptions**

None.



