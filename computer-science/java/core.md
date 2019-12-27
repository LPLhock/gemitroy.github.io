# Core

## General 

access modifier 

super/interface type as parameter in method definition

protected 

class can only be public/default 

interface 

only return type difference is not polymorphism, throws compile error.

Class will not create default non-para constructer if any constructer is defined.

default method 

static method 

transient 

custom annotation 

volatile usage 

Long/Double read/write is not atomic operation on 32bit cpu 

Java Param Pass by value

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

### Reflection 

customized annotation 

Proxy/InvocationHandler 

Class.newInstance\(\) \(call no-arg constructor\) 

Each class has a single class object, constructed by JVM when loaded by class loader

### java.util.function

### Lambda

### Exception

Customize:

extends Exception/RuntimeException and call super\(message\)

