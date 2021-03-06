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
```
@GetMapping("/courses")
public List<Courses> getCourses(){return Arrays.asList(new Course(1,"",""))}
```

### AOP (Aspect Oriented Programming)
@Before

@After


@Around

You can measure execution time of process

## JDBC & JPA

H2 is inmemory database

### JDBC

***RowMapper***

```
new BeanPropertyRowMapper<Person>(Person.class)
```
Dao and Database attribute names completely same
  
### JPA (Java Persistance API)

Define entity and map them to columns of table 

Hibernate implements JPA. Hibernate is a class

JPA stands fr ORM

JPA -> interface
Hibernate -> class


We need to have default constructor.
```
@Entity
@Table(name="person")
public class Person
{ 
  @Id
  @GeneratedValue
  private int id;
  
  private String name;
  
  private String location;
  
  private Date birthDate;
}

```

```

@Repository
@Transactional
public class PersonJpaRepository
{
@PersistenceContext
EntityManager entityManager;

public Person findById(int id)
{
   return entityManager.find(Person.class,id);
}

}

```


***JPQL***

```
@Entity
@NamedQuery(name="find_all_persons",query = "select p from Person p"
public class Person{
...
}

```

**Predefined Repository**

```
public interface PersonSpringDataRepository extends JpaRepository<Peron,Integer>
{
}

```

## ACTUATOR

## SPRING MVC


## DOCKER

docker up

docket-compose


## KUBERNETES (K8S)

kubectl

```

docker run -p 8080:8080 in28min/hello-world-rest-api:0.0.1.RELEASE
 
kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl scale deployment hello-world-rest-api --replicas=3
kubectl delete pod hello-world-rest-api-58ff5dd898-62l9d
kubectl autoscale deployment hello-world-rest-api --max=10 --cpu-percent=70
kubectl edit deployment hello-world-rest-api #minReadySeconds: 15
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
 
gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-a --project solid-course-258105
kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get componentstatuses
kubectl get pods --all-namespaces
 
kubectl get events
kubectl get pods
kubectl get replicaset
kubectl get deployment
kubectl get service
 
kubectl get pods -o wide
 
kubectl explain pods
kubectl get pods -o wide
 
kubectl describe pod hello-world-rest-api-58ff5dd898-9trh2
 
kubectl get replicasets
kubectl get replicaset
 
kubectl scale deployment hello-world-rest-api --replicas=3
kubectl get pods
kubectl get replicaset
kubectl get events
kubectl get events --sort.by=.metadata.creationTimestamp
 
kubectl get rs
kubectl get rs -o wide
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl get rs -o wide
kubectl get pods
kubectl describe pod hello-world-rest-api-85995ddd5c-msjsm
kubectl get events --sort-by=.metadata.creationTimestamp
 
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-n6c7l
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-8bhdt
 
gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-c --project solid-course-258105
docker login
docker push in28min/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
docker push in28min/mmv2-currency-conversion-service:0.0.11-SNAPSHOT
 
kubectl create deployment currency-exchange --image=in28min/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
kubectl expose deployment currency-exchange --type=LoadBalancer --port=8000
kubectl get svc
kubectl get services
kubectl get pods
kubectl get po
kubectl get replicaset
kubectl get rs
kubectl get all
 
kubectl create deployment currency-conversion --image=in28min/mmv2-currency-conversion-service:0.0.11-SNAPSHOT
kubectl expose deployment currency-conversion --type=LoadBalancer --port=8100
 
kubectl get svc --watch
 
kubectl get deployments
 
kubectl get deployment currency-exchange -o yaml >> deployment.yaml 
kubectl get service currency-exchange -o yaml >> service.yaml 
 
kubectl diff -f deployment.yaml
kubectl apply -f deployment.yaml
 
kubectl delete all -l app=currency-exchange
kubectl delete all -l app=currency-conversion
 
kubectl rollout history deployment currency-conversion
kubectl rollout history deployment currency-exchange
kubectl rollout undo deployment currency-exchange --to-revision=1
 
kubectl logs currency-exchange-9fc6f979b-2gmn8
kubectl logs -f currency-exchange-9fc6f979b-2gmn8 
 
kubectl autoscale deployment currency-exchange --min=1 --max=3 --cpu-percent=5 
kubectl get hpa
 
kubectl top pod
kubectl top nodes
kubectl get hpa
kubectl delete hpa currency-exchange
 
kubectl create configmap currency-conversion --from-literal=CURRENCY_EXCHANGE_URI=http://currency-exchange
kubectl get configmap
 
kubectl get configmap currency-conversion -o yaml >> configmap.yaml
 
watch -n 0.1 curl http://34.66.241.150:8100/currency-conversion-feign/from/USD/to/INR/quantity/10
 
docker push in28min/mmv2-currency-conversion-service:0.0.12-SNAPSHOT
docker push in28min/mmv2-currency-exchange-service:0.0.12-SNAPSHOT

```



