Tutorial for the Spring Data REST Telosys bundle
===========================================

Note
-----
For this tutorial, we start from a derby database. This database manage a bookstore (Book, Author, Reviews etc ..). 
You can follow this tutorial with your own database.

1. Project Creation
----------------

* You can start by create a new __maven__ project or start on an existing one.
* The packaging of this project must be "war"

2. Initialize Telosys Tools
----------------------------------
- Open the properties window of your project
- In the left entries, select __"Telosys Tools"__ and fill all project informations in "General", "Packages" and "Folders" tab (right side)
- Click on the __"Apply"__ button (don't forget this step!)
- Click on __"Init Telosys Tools"__ in the "General" tab => __The "Telosys Tools" directory is now added in the project__
- In the "download" tab, download from this Github repository the __"spring-data-rest-templates-TT210"__
- Click on __"Download selected bundle(s)"__ and verify the checkbox __"Install downloaded bundle(s)"__ is checked.
- After this, close the project properties window.
- In the project, you should now have the __"spring-data-rest-templates-TT210"__ directory under __"TelosysTools/templates"__

3. Update maven dependencies
----------------------------------
- Under the __"spring-data-rest-templates-TT210"__ directory, open the __/misc/maven-pom.txt__
- Copy and paste the dependencies to your project pom (if they are not already exist)
- For this example, we use a dependency for the Derby driver. Adapt it to your database if needed.

4. Database repository generation
-------------------------------
- Open the database configuration file : "Telosys Tools / databases.dbcfg"
- The database editor is displayed
- Add a new connection to your database
- Test the connection to get "Connection is OK"
- Click on "Meta-data" tab and click on "Get tables" to see the tables of your database
- If all is OK, click on "Generate repository" button to generate a new ".dbrep" file in the "TelosysTools/repos" directory 

5. Manage entities links
-----------------------
- Open the ".dbrep" file in the "TelosysTools/repos" directory
- Go to the __"Links between entities" tab.
- Click on __"Generate links from foreign keys"__ button which is located __at bottom of the tab__
- You can see now the links between all entities

6. Generate the REST API
----------------------------
- Click on the __"Bulk generation"__ tab
- In the entities list, __select all entities__ you want to manage (be careful for links, __all linked entities must be selected__)
- Select the __"spring-data-rest-templates-TT210"__ templates bundle in the dropdown list => all templates are now visible in right list
- Select all templates and select __"copy static resources"__
- Click on the __"Generate"__ button
- You should have a successfull message
- The project source code __should compile successfully__

7. The Spring configuration
-----------------------------
- For this project, the spring configuration was performed in a java way.
- __RestWebApplicationInitilizer__ : Servlet context initilization
- __JpaRepositoryConfig__ : Database access configuration
- __ApplicationConfig__ : Declaration of MessageSource, validators, converters ...


8. The JPA Entities
----------------
- The JPA Entities were generated under the package you have enter in the Telosys Tools properties window.

9. The Spring data JPA repositories
------------------------------------------
- The JPA Repositories were generated under the "repository" package
- Search methods for the Many-to-One relationships were have also been generated

9. Converters
------------------------------
- Use for entity how have composite primary key

10. Validators
------------------------------
- Each entity had an associated validator wich is executed before the update


Configure the connection
-------------------------
- Open the __couchbase.properties__ file under the resources directory.
- You will find the following parameters :
- `couchbase.uris` : URL to the Couchbase server
- `couchbase.bucket` : Bucket name
- `couchbase.password` : Bucket password (empty if none)
- `couchbase.waitPersistOnDisk` : Use during document creation. It allows you to ensure that the document is persisted on disk on at least one server
- `couchbase.waitForIndexation` : Use during query. It allows to force update index before the view execution. You'll be ensure that all documents are indexed and processed by the view.
- `couchbase.database.version` : Version of your database. This version is checked by the `DatabaseConnectionProvider.initDatabase()` method.  
If versions are equal : no update view is performed  
If version on the file is newer than the document version created by this API : All views are created or updated.

Getting Started 
----------------
You can deploy the project under your server or launch ``` mvn tomcat7:run ```
To browse the resources, there is two ways :
- Access URL from your web browser
- Launch the spring rest-shell (see : [https://github.com/spring-projects/rest-shell](https://github.com/spring-projects/rest-shell)

Enjoy!
