# Java Reflection

## Customized annotation

```text
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.FIELD)
public @interface NewAnno{
    public String key() default "";
}

Then use Reflection to add process
```

## Dynamic Proxy

* Proxy
* InvocationHandler

#### Why:

To manipulate the behavior of a class method in running time

#### When:

* Spring AOP
* Transaction management
* Logging

## Class Loading

Sequence: Load -&gt; Link -&gt; Initialization

```text
Class cl = Class.forName(SomeClass, boolean initialize, ClassLoader loader)
SomeClass obj = (SomeClass)Class.newInstance() //(call no-arg constructor) 
```

### ClassLoader

BootStrap ClassLoader \(Load class in JDK/JRE/LIB\)

Extension ClassLoader \(Load class in JDK/JRE/LIB/EXT\)

System ClassLoader \(Load class in classpath\)

*  ClassLoader.loadClass\(String name, boolean resolve\)

