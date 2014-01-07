spring-data-rest-templates-TT210
================================

Telosys Tools bundle (2.1.0 or newer) for Spring Data Rest generation (Support of HATEOAS)

Expose your JPA entities with a RESTful API (HATEOAS Support)

This bundle allows you to generate for each of your database tables :
- The associated JPA entities
- The Spring configuration for Spring DATA REST, DATA JPA and MVC
- The associated JPA repositories (include search methods for Many-to-one relationships)
- Spring Validators
- Spring Converters for the composite primary keys

Installation
-------------
If you have not yet installed the Telosys plugin, I invite you to follow this link : [https://sites.google.com/site/telosystools/](https://sites.google.com/site/telosystools/)  
and choose the bundle "spring-data-rest-templates-TT210"


Generated files
------------------  

* __[table].java__ : JPA POJO from your database table
* __[table]Repository.java__ : Spring JPA Repository
* __[table]Validator.java__ : Spring JPA Validators
* __ApplicationConfig.java, JpaRepositoryConfig.java, RestWebApplicationInitializer.java__ : Spring configuration

Tutorial
-------------
[How to use it !](doc/HOWTO.md)

