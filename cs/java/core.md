# Core

### Statement

class can only be public/default 

only return type difference is not polymorphism, throws compile error.

Class will not create default non-para constructer if any constructer is defined.

Long/Double read/write is not atomic operation on 32bit cpu 

Java param is passed by value \(a copy of the value\)

### General 

access modifier 

super/interface type as parameter in method definition

protected  

static method 

transient: prevent serialization 

#### interface vs abstract class

| **Interface** | **Abstract** |
| :--- | :--- |
| abstract method | abstract method |
| default method \(auto added into subclass\) | concrete method |

#### Parameterized argument

```text
void func(int... values) { 
    for(i=0;i<n;i++) n = values[i]; 
    }
void func(int... values) ~= void func(int[] values) 
```

### Reference type

SoftReference 

WeakReference 

PhantomReference 

### Iterable

Implement Iterable to to enable the enhanced for-each loop

#### Cloneable 

Implement Cloneable to allow clone\(\). no method, just a flag.  

### Enum

```text
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
Level level = Level.MEDIUM;
```

### Exception

Customize:

extends Exception/RuntimeException and call super\(message\)

#### Try-Catch

always catch subclass exception first

