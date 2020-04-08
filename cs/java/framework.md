# Spring

## IOC

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

#### Bean lifecycle

* Instantiation -&gt; Ready
  * populate bean properties
  * postProcessBeforeInitilization
  * @PostConstruct
  * InitiatingBean interface
  * call customize init\(\)
  * postProcessAfterInitilization
* Ready -&gt; Shutdown
  * call customize destroy\(\)
  * DisposalBean interface
  * @Predestroy

## DI

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

#### Annotation based \(Will be overridden by XML\)

```text
-- enable annotation based, not enough
<context:annotation-config/>
-- this is needed
<context:component-scan>
```

_Bean level_

* _@Component_
* _@Service_
* _@Repository_

_Property level_

* _@Autowired \(byType. Inject on constructor, setter or field\)_
* _@Required_
* _@Resource\(byName.JSR\)_
* _@Qualifiter\(used together with other 3, specify the injected bean\)_

## AOP \(method proxy only\)

* JDK Proxy \(interface based\) 
* CGLibs \(class based\)
* Spring AOP vs AspectJ 
* * Spring AOP is dynamic proxy \(JDK or CGlibs\)
  * AspectJ is static proxy \(compiled before runtime\)
* Usage: Transaction, Logging, Security

## Data access

#### JdbcTemplate

* NamedParameterJdbcTemplate
*  SimpleJdbcTemplate
* RowMapper

#### JdbcDaoSupport

* already has JdbcTemplate property

#### DataSource 

* DriverManagerDataSource \(no pooling\)
* Apache DBCP \(pooling\)
* C3PO \(pooling\)

#### Transaction

```text
<bean id="transactionManager"class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
    <property name="dataSource" ref="dataSource" />
</bean>
```

* @Transactional
* Propagation = required
* Isolation level = default \( Use the **default isolation** level of the underlying database\)

## Spring Boot

## Security Data 

Spring Restful is not JAX-RS implementation 

