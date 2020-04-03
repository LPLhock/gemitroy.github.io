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

interface 

default method 

static method 

transient: prevent serialization 

custom annotation 

volatile usage 

parameterized argument 

```text
void func(int... values) { 
    for(i=0;i<n;i++) n = values[i]; 
    }
void func(int... values) ~= void func(int[] values)
```



### Stream 

### Reference type

SoftReference 

WeakReference 

PhantomReference 

### java.lang 

* ThreadLocal
* Runnable
* * forEach 
  * iterator 
  * * enable enhanced for-each 
* Iterable
* Cloneable no method, just a flag. 
* Enum 
* wait/notify 
* reflect

### Enum

```text
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
Level level = Level.MEDIUM;
```

### Reflection 

#### Customized annotation 

#### Proxy/InvocationHandler

### Class Loading

Class.newInstance\(\) \(call no-arg constructor\) return Object

Class.forName\(String name, boolean initialize, ClassLoader loader\) return Class

#### ClassLoader

BootStrapClassLoader \(Load class in JDK/JRE/LIB\)

Extension ClassLoader \(Load class in JDK/JRE/LIB/EXT\)

System ClassLoader \(Load class in classpath\)

*  ClassLoader.loadClass\(String name, boolean resolve\)
* 
### java.util.function

Functional Interface

### Lambda

### Method Reference

```text
System.out::println
```

### Exception

Customize:

extends Exception/RuntimeException and call super\(message\)

