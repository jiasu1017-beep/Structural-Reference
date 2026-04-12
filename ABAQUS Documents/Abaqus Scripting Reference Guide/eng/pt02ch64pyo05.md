# 64.5 String object







An odb_String object is used to specify a character string. The odb_String object provides a convenient means of storing and passing strings, along with a simple interface to append and modify the data stored in the string.

### 64.5.1 odb_String(...)

This constructor creates an odb_String object from a char*. Any method that accepts an odb_String argument will also accept a char*.

**Prototype**

```
odb_String(const char* string)
odb_String()
```

**Required argument**

A char* to initialize the odb_String.

**Optional arguments**

None.

**Return value**

An odb_String object.

**Exceptions**

None.

### 64.5.2 append(...)

This method adds characters to an odb_String object.

**Prototype**

```
void append(const odb_String& string);
```

**Required arguments**

*string*

An odb_String to be appended to the contents of odb_String.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 64.5.3 cStr(...)

This method returns a char* to the string held by an odb_String object.

**Prototype**

```
char* cStr();
```

**Arguments**

None.

**Return value**

A char* to the string held by the odb_String object.

**Exceptions**

None.

### 64.5.4 length(...)

This method returns the number of characters of an odb_String object. 

**Prototype**

```
int length();
```

**Arguments**

None.

**Return value**

An Int denoting the number of characters.

**Exceptions**

None.



