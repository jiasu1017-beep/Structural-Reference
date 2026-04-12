# 64.3 RepositoryIterator object







Iterators are provided to navigate the repositories. Examples of using an iterator can be found in the example problem section.

### 64.3.1 odb_TypeRepositoryIT(...)

This method constructs an iterator for a repository.

**Path**

```
odb_*Type*RepositoryIT
```

**Prototype**

```
odb_*Type*RepositoryIT(const odb_*Type*Repository& repository);
```

**Required argument**

*repository*

The repository over which to iterate.

**Optional arguments**

None.

**Return value**

An Iterator object.

**Exceptions**

None.

### 64.3.2 first(...)

This method sets the iterator to the first item in the repository.

**Prototype**

```
first();
```

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 64.3.3 next(...)

This method sets the iterator to the next item in the repository.

**Prototype**

```
next();
```

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 64.3.4 isDone(...)

This method checks whether the iterator is at the end of the repository.

**Prototype**

```
bool isDone();
```

**Arguments**

None.

**Return value**

A Boolean specifying whether the end of the repository has been reached.

**Exceptions**

None.

### 64.3.5 currentKey(...)

This method returns the name of the item to which the iterator is currently pointing.

**Prototype**

```
odb_String currentKey();
```

**Arguments**

None.

**Return value**

An odb_String specifying the name of the item that will be returned by the `currentValue` method.

**Exceptions**

None.

### 64.3.6 currentValue(...)

This method returns the item in the repository to which the iterator is currently pointing.

**Prototype**

```
const *type*& currentValue();
```

**Arguments**

None.

**Return value**

An item of the class *type* to which the iterator is currently pointing.

**Exceptions**

None.



