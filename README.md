# SPRING BOOT

- [Spring Framework](#springFramework)

## Spring Framework

**doc_spring**
Spring Framework Documents

### Definitions

**Beans**

**Autowiring**

**Dependency Injection**

**Inversion Of Control**
Giving instance creation reponsibility to Spring framework

**IOC Container**

**Application Context**

### Annotations

**@Component**
Spring starts managing instances of class. String creates instances of class

**@Autowire**
Spring would start looking for dependencies

if you have more than two matches for autowiring
1. Put @Primary Notation to the first priority class
2. make attribute name same as chosen class name
Note: @Primary keyword has higher priortiy according to naming
3. @Qualifier("quick") wirte this annotation to the above of dependency and the class

**Plumbing Code**
Spring protects us form plumbing code

**Bean Scope**
1. singleton: One instance per Spring Context

2. prototype: new bean whenever requested
put @Scope("Prototype")
put @Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
put @Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE, proxyMode = ScopedProxyMode.TARGET_CLASS)

If Owner Class is Sigleton Scope and attribute class Prototoype scope. All generated classes become Sigleton Scope. To Achieve this

4. request: one bean per HTTP request

5. session: one bean per http session
Note: default is singleton

**Singleton**
In spring boot singleton is Application based. In tradational Java singleton is JVM based

**@Predestroy**
**postCOnstruct**

@ComponentScan("Path of the component")

#CDI - Context dependency Injection

**@Named** 
alternate @Component

**@Inject**
alternate of @Autowired

### Component Annotations
- @Component

Generic

- @Repository

Data Layer

- @Service

Business Layer

- @Controller

Facade, UI Layer, MVC Pattern

### Proporties File

You can put your constan values to this file and access them by using **@Value** annotation

system.basic.url = org.test.home

To Access From Component
@Value("${system.basic.url}")

@PropertySource("classpath:app.properties")

## UNIT TESTING

assertEquals

**Annotations**
@Test

@Before
This run befor every test (@Test annotation). It is important to emphasize that not only one execution. It works before each test.

@After

@BeforeClass
Runs before each class creation and must be static method

@AfterClass

### MOCKITO
@Mock

@InjectMocks

@RunWith(MockitoJUnitRunner.class)

```
mock(listMock.get(0)).thenReturn("Your param is zero");
```


```
Mockito.when(daoMock.getData()).thenReturn(new int[]{2,4});
```

### SPRING
@RunWith(SpringRunner.class)
@ContectConfiguration(classed =**.class)

**REST Controller**
@RestController
Add this annotation to the class

@GetMapping("/courses")
public List<Courses> getCourses()


