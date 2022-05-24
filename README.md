# doc_spring
Spring Framework Documents

# Definitions

**Beans**

**Autowiring**

**Dependency Injection**

**Inversion Of Control**
Giving instance creation reponsibility to Spring framework

**IOC Container**

**Application Context**

# Annotations

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

