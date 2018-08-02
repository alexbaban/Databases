# On ColdFusion with the Java driver

## MongoDB Driver Installation

* read at (http://mongodb.github.io/mongo-java-driver/3.8/driver/getting-started/installation/)
* download at (https://oss.sonatype.org/content/repositories/releases/org/mongodb/mongo-java-driver/3.8.0/)
  `mongo-java-driver-3.8.0.jar`
* copy to `\WEB-INF\lib`
* restart ColdFusion server


## Sample code

```coldfusion
<cfoutput>#now()#</cfoutput>
<hr />

<cfset Mongo  = CreateObject("java","com.mongodb.MongoClient").init("localhost")>
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

<cfset res  = coll.countDocuments(parsedArgs) />
<cfdump var="#res#" />
<hr />

<cfset res  = coll.find(parsedArgs).iterator().next().toString() />
<cfdump var="#res#" />
<hr />

```
