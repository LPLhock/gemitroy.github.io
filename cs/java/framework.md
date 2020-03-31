# Framework

## Spring 

### IOC

#### Bean Property:

Scope：

* singleton \(default\)
* prototype
* request
* session
* global-session

lazy-init: 

* false\(default\)
* true \(bean will init after been called first time\)

callback: 

* init-method
* destroy-method

### DI

#### XML based

constructor-based injection:

```text
<bean id = "textEditor" class = "com.TextEditor">
      <constructor-arg ref = "spellChecker"/>
</bean>

<bean id = "spellChecker" class = "com.SpellChecker"></bean>
```

 setter-based injection

```text
<bean id = "textEditor" class = "com.TextEditor">
      <property name = "spellChecker" ref = "spellChecker"/>
</bean>

<bean id = "spellChecker" class = "com.SpellChecker"></bean>
```

autowire injection

```text
<bean id = "textEditor" class = "com.TextEditor" autowire = "byName">
</bean>

<bean id = "spellChecker" class = "com.SpellChecker"></bean>
```

#### Annotation based

```text
-- enable annotation based, not enough
<context:annotation-config/>
-- this is needed
<context:component-scan>
```

* _@autowire_
* _@Component_
* _@Service_
* _@Repository_

 

### AOP \(method proxy only\)

* JDK Proxy \(interface based\) 
* CGLibs \(interface not needed\)
* compare with AspectJ 

### DataSource 

* DriverManagerDataSource

### Transaction

Security Data 

Spring Restful is not JAX-RS implementation

## Common

### Junit

### Log

log4j slf4j logback 

### ehcache 

### connection pool 

Apache DBCP 

C3PO 

## REST 

design principle use noun use parameter for filter/search/sort use version HATEOAS CXFRest Swagger 

