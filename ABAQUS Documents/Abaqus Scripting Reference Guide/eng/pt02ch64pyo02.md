# 64.2 Repository object







Repositories are provided to store objects retrieved by name. Both the repositories and the content of the repositories are created by the API; the user can only retrieve objects from repositories. Iterators are provided to navigate the repositories.

### 64.2.1 operator[](...)

This method accesses an item in an odb_Repository object. This method should be used with caution because it does not perform any checking of the index range.

**Prototype**

```
*type* [odb_string name] const;
```

**Required argument**

*name*

A char* or an odb_String specifying the object to be retrieved.

**Optional arguments**

None.

**Return value**

The object of type *type* saved in the repository under the given name.

**Exceptions**

None.

### 64.2.2 get/constGet(...)

This method accesses an item in an odb_Repository object.

**Prototype**

```
*type* get(const char* name);
const *type*& constGet(const char* name) const;
```

**Required argument**

*name*

A char* or an odb_String specifying the object to be retrieved.

**Optional arguments**

None.

**Return value**

The object of type *type* saved in the repository under the given name.

**Exceptions**

None.

### 64.2.3 isMember(...)

This method checks whether an object with a given name is stored in the repository.

**Prototype**

```
bool isMember(const odb_String& name) const;
bool isMember(const char* name) const;
```

**Required argument**

*name*

A char* or an odb_String specifying the name under which the object is stored.

**Optional arguments**

None.

**Return value**

A Boolean specifying whether the object is stored in the repository.

**Exceptions**

None.

### 64.2.4 size(...)

This method returns the number of items in an `odb_Repository` object.

**Prototype**

```
int size() const;
```

**Arguments**

None.

**Return value**

An Int indicating the number of items in the repository.

**Exceptions**

None.



