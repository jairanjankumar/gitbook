# DBConnection

**PostgreSQL Connection Test**

Scala code for DB Connection

DBConnectionTest.scala

```
import java.sql.{Connection, DriverManager}

object DBConnectionTest extends App{

  println("-- PostgreSQL Connection Test --")
  val url = "jdbc:postgresql://localhost:5307/DBschema?user=userName&password=userNamePwd"

  var connection:Connection = null
  Class.forName("org.postgresql.Driver")
  connection = DriverManager.getConnection(url)

  if (connection != null) println("!!! DB Connection Successful !!!")
  else println("Failed to connect")

  val statement = connection.createStatement()
  val resultSet = statement.executeQuery("SELECT job_id, workflow_name FROM reactorx_job limit 1")
  resultSet.next()
  val job_id = resultSet.getString("job_id")
  val workflow_name = resultSet.getString("workflow_name")
  println(s"Fetched one row from DB -- job_id : $job_id & workflow_name $workflow_name")

  connection.close()
}
```

Java Code for DB Connection

PostgresTest.Java

```
import java.sql.*;

public class PostgresTest {
   public static void main(String[] argv) {

       System.out.println("-- PostgreSQL Connection Test --");
       try {
           Class.forName("org.postgresql.Driver");
           Connection connection = null;
           connection = DriverManager.getConnection("jdbc:postgresql://localhost:5307/DBschema?user=userName&password=userNamePwd");

           if (connection != null) {
               System.out.println("!!! DB Connection Successful !!!");
           } else {
               System.out.println("Failed to connect");
           }

           Statement statement = connection.createStatement();
           ResultSet resultSet = statement.executeQuery("SELECT job_id, workflow_name FROM reactorx_job limit 1");
           resultSet.next();

           String job_id = resultSet.getString("job_id");
           String workflow_name = resultSet.getString("workflow_name");

           System.out.println("Fetched one row from DB -- job_id : " + job_id +" & workflow_name : " + workflow_name);

       } catch (Exception e) {
           e.printStackTrace();
           return;
       }
   }
}
```

Run Result

```
$ javac PostgresTest.java
$ java -cp /home/TestDBConnection/postgresql-9.3-1104.jdbc41.jar:/home/TestDBConnection/ PostgresTest
-- PostgreSQL Connection Test --
!!! DB Connection Successful !!!
Fetched one row from DB -- job_id : 175749763031891970 & workflow_name : TEST WORKFLOW
```

Please Note

Mac/Unix -> separator is ':'

```
java -cp /home/TestDBConnection/postgresql-9.3-1104.jdbc41.jar:/home/TestDBConnection/ PostgresTest
```

Windows -> separator is ';'

```
java -cp /home/TestDBConnection/postgresql-9.3-1104.jdbc41.jar;/home/TestDBConnection/ PostgresTest
```
