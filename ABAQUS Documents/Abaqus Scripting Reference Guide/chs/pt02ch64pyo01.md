# 64.1 BaseException object







The odb_BaseException object catches all exceptions thrown in the output database

**Access**

```
catch(odb_BaseException& exc)
```

### 64.1.1 UserReport()

This method returns a description of the error condition that generated the exception.

**Prototype**

```
odb_String UserReport() const;
```

**Arguments**

None.

**Return value**

None

**Exceptions**

None.



