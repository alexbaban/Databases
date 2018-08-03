# ColdFusion and the H2 Database

## Setup with ColdFusion

* stop the ColdFusion server
* download and install H2
* copy `h2-1.4.197.jar` from the install directory to ColdFusion install directory, `WEB-INF\lib` subfolder
* start the ColdFusion server then login into "Administrator", then go to "Data Sources"
* add new data source, "Driver" type "other"
* type (do not copy + paste) `org.h2.Driver` into "Driver Class" field

## Values for the "JDBC URL" field

* an absolute path can be used, for example to create a database named `temp` located in `c:\databases` folder
  `jdbc:h2:c:\databases\temp`

* a relative path can be used, for example to create a database named `temp` located in current user's home directory `databases` subfolder
  `jdbc:h2:~/databases/temp` or  
  `jdbc:h2:./databases/temp`
  
## Test table

`test.cfm`

```coldfusion
<cfoutput>#now()#</cfoutput>
<hr />

<cfquery name="createTable" datasource="test" result="createTableResult">
    CREATE TABLE Persons (
        PersonID int,
        LastName varchar(255),
        FirstName varchar(255),
        Address varchar(255),
        City varchar(255)
    )

</cfquery>

<cfdump var="#createTableResult#" label="Create Table Result" />
<hr />


<cfquery name="readTable" datasource="test">
    SELECT * from Persons
</cfquery>

<cfdump var="#readTable#" label="Read Table Output" />
<hr />

```
