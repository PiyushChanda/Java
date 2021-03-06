# Java
# JDBC-Java DataBase Connectivity

DriverManager - Manages the driver class and provides a 'connection' object. This connection object can be used to connect to an RDBMS Database

Driver - Provided by database vendors, and must implement java.sql.driver interface. Acts as a mediator between the jdbc application and the RDBMS server.

Type1-JDBC-ODBC Bridge Driver
Type2-JDBC-Native Driver
Type3-JDBC-Middleware Server Driver
Type4-Pure Java Driver

Class.forName("oralcle.jdbc.driver.OracleDriver")-To load a driver. Once a driver is loaded, it automatically registers itself with the driver manager. after creating an object of itself.

DriverManager.getConnection()-To get a connection object, through which sql statements are loaded into the RDBMS, executed and results are taken back from the rdms.

To connect to a database, we need to prvide URL, protocol, port number, db name, userid and password.

URL : <client-protocol>:<server-protocol>://<server-name>:<port-number>/<dbname>
  
Similar to any client server technology, including the web technology

In JDBC:
Client Protocol is always JDBC
Server Side protocol is decided by the database vendor

oracle:thin
mysql
hsqldb:hsql
postgresql

jdbc:oracle:thin
..

Server is identified by its name, or its ip address.

:// - to separate the protocol and server name
:@ - for Oracle

Port Number: Unique number given by the os to each and every service running on the machine. It is like a mailbox, when there is an icoming network traffic, the os redirects the traffic to the appropiate software application identified by the port number. Generally they are configured with defaults.

Oracle - 1521
mysql - 3306
hsql - 9001
postgresql - 5432

Oracle: SID - service id is used as the last part instead of the database name.

for Orcale
jdbc:oracle:thin:@localhost:2521:XE
XE - SID, default, also we use : instead of /

# Statement/PreparedStatement/CallableStatement

Used to execute a query

Uses connection instane to sent the sql statements to a database

Transaction Demarcation - Marking the start and end of transaction

ACID - Atomic - All or None
ACID - Consistency - unitl the statemetns are commited or rolled back, data isshown to everyone in a consitent fashion.
ACID - Isolation - Every transaction is carried out indepedently of one another
ACID - The effect is persistent if the dbms informs the user about successful execution.

Connections object - set Autocommit to false, if it is set to true, all the sql statemenst are commite or rolled back independently.

# JDBC Program -

Connection conn = DriverManager.getConnection(url,username,password);
// Transaction Begins Here

Statement stmt = conn.createstatement() ;
stmt.execute(sql1);
conn.commit(); // The transaction ends here

Use try catch Block to a whole transaction.

try - sql statements and commit
catch - rollback
finally - release the resources

