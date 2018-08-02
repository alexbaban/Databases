# On ColdFusion with the Java driver

## MongoDB Driver Installation

* install MongoDB "Community Server" and tools  
  (https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)  
  (https://www.mongodb.com/download-center?jmp=nav#community)  
  
* read at (http://mongodb.github.io/mongo-java-driver/3.8/driver/getting-started/installation/)
* download Java driver at (https://oss.sonatype.org/content/repositories/releases/org/mongodb/mongo-java-driver/3.8.0/)  
   `mongo-java-driver-3.8.0.jar`
* copy to `\WEB-INF\lib`
* restart ColdFusion server


## Sample code

```coldfusion
<cfoutput>#now()#</cfoutput>
<hr />

<cfset Mongo = CreateObject("java","com.mongodb.MongoClient").init("localhost")>
<cfdump var="#Mongo#" expand="false" />
<hr />

<cfset db = Mongo.getDatabase('test')>
<cfdump var="#db#" expand="false" />
<hr />

<cfset coll = db.getCollection("education_income")>
<cfdump var="#coll#" expand="false" />
<hr />

<cfdump var="#coll.countDocuments()#" />
<hr />

<cfset args = {
    'Educational Attainment': {
        '$regex': '^T.*on',
        '$options': 'i'
    }
} />

<cfset parsedArgs = 
	CreateObject("java","com.mongodb.util.JSON")
		.parse(serializeJSON(args)) 
/>

<cfset count  = coll.countDocuments(parsedArgs) />
<cfdump var="#count#" />
<hr />

<cfset res  = coll.find(parsedArgs).iterator().next().toString() />
<cfdump var="#res#" />
<hr />

```
