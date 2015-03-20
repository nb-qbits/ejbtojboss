**Install a JDBC Driver to JBoss as a module**
Define new module for jdbc driver inside /modules directory. Following steps:

 1. Create a directory “oracle/jdbc/main” inside the “jboss-as-7.0.1.Final/modules” directory.  
 2. paste your “ojdbc6.jar” oracle Jdbc Driver inside “jboss-as-7.0.1.Final/modules/oracle/jdbc/main” directory.  
 3. Create a file “module.xml” inside “jboss-as-7.0.1.Final/modules/oracle/jdbc/main” as following:
 

    <?xml version="1.0" encoding="UTF-8"?> <module xmlns="urn:jboss:module:1.0" name="oracle.jdbc"> <resources> <resource-root path="ojdbc6.jar"/> </resources> <dependencies> <module name="javax.api"/> <module name="javax.transaction.api"/> </dependencies> </module>

4. Now open  “jboss-as-7.0.1.Final/standalone/configuration/standalone.xml” file or “jboss-as-7.0.1.Final/domain/configuration/domain.xml” file and then add the driver declaration tag refering to your module as following, by default you will see the driver declaration tag already contains the declaration for <driver name=”h2″ module=”com.h2database.h2″>:

<drivers> <driver name="OracleJDBCDriver" module="oracle.jdbc" /> <driver name="h2" module="com.h2database.h2"> <xa-datasource-class> org.h2.jdbcx.JdbcDataSource </xa-datasource-class> </driver> </drivers>
    
Here we declared the <driver name=”OracleJDBCDriver” module=”oracle.jdbc”/>

5. Create DataSource in your JBoss and then in the Driver section you can refer to this Module name “oracle.jdbc”
