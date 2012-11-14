wordlift-home
=============

A default setup for WordLift.

### Create a job

Request:
```sh
curl -X POST \
 -H "Content-Type: application/json" \
 -H "Accept: application/json" \
 -d @var/samples/obamareelectionspeech.json \
 http://localhost:8080/wordlift/api/job
```

Response:
```json
	{
		"jobID":"f1fab3d0-cb33-4a38-8664-222b091423b8",
		"statusCode":200,
		"statusMessage":"A job has been created successfully."
	}
```

### Query the status of a job

Request:
```sh
curl -X GET \
 -H "Content-Type: application/json" \
 -H "Accept: application/json" \
 http://localhost:8080/wordlift/api/job/f1fab3d0-cb33-4a38-8664-222b091423b8
```

Response (for a *running* job):
```json
	{
		"state":"RUNNING",
		"code":200,
		"message":"Job created successfully.",
		"moreInfo":""
	}
```

Response (for a *complete* job):
```json
	{
		"state":"COMPLETE",
		"code":200,
		"message":"Job created successfully.",
		"moreInfo":""
	}
```

### Query the result of a job

Request:
```sh
curl -X GET \
 -H "Content-Type: application/json" \
 -H "Accept: application/json" \
 http://localhost:8080/wordlift/api/job/5d68691b-ec51-47b9-91ea-71d6654687c4/result
```

Response (of mimetype *application/rdf+xml*):
```xml
<rdf:RDF
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns:j.0="http://purl.org/dc/terms/"
    xmlns:j.1="http://fise.iks-project.eu/ontology/" > 
  <rdf:Description rdf:about="urn:enhancement-5e90ac34-7047-dfc9-87c4-d5f8a8221a75">
    <j.0:type rdf:resource="http://www.w3.org/2002/07/owl#Thing"/>
    <j.1:extracted-from rdf:resource="urn:content-item-sha1-fa9eafde45a7ad9f3d03a8e2364aea54ce942670"/>
    <j.1:confidence rdf:datatype="http://www.w3.org/2001/XMLSchema#double">1.0</j.1:confidence>
    <j.1:selected-text xml:lang="en">American</j.1:selected-text>
    <rdf:type rdf:resource="http://fise.iks-project.eu/ontology/Enhancement"/>
    <rdf:type rdf:resource="http://fise.iks-project.eu/ontology/TextAnnotation"/>
    <j.1:end rdf:datatype="http://www.w3.org/2001/XMLSchema#long">9867</j.1:end>
    <j.0:created rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">2012-11-14T11:48:35.306Z</j.0:created>
    <j.0:creator rdf:datatype="http://www.w3.org/2001/XMLSchema#string">io.insideout.wordlift.org.apache.stanbol.enhancer.engines.freeling.impl.FreelingPartOfSpeechTaggingEngine</j.0:creator>
    <j.1:start rdf:datatype="http://www.w3.org/2001/XMLSchema#long">9859</j.1:start>
  </rdf:Description>

  ...

  <rdf:Description rdf:about="urn:enhancement-3945a0d8-699e-0cdc-e463-4b14a7006458">
    <j.0:type rdf:resource="http://www.w3.org/2002/07/owl#Thing"/>
    <j.1:extracted-from rdf:resource="urn:content-item-sha1-fa9eafde45a7ad9f3d03a8e2364aea54ce942670"/>
    <j.1:confidence rdf:datatype="http://www.w3.org/2001/XMLSchema#double">1.0</j.1:confidence>
    <j.1:selected-text xml:lang="en">American</j.1:selected-text>
    <rdf:type rdf:resource="http://fise.iks-project.eu/ontology/Enhancement"/>
    <rdf:type rdf:resource="http://fise.iks-project.eu/ontology/TextAnnotation"/>
    <j.1:end rdf:datatype="http://www.w3.org/2001/XMLSchema#long">965</j.1:end>
    <j.0:created rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">2012-11-14T11:48:35.313Z</j.0:created>
    <j.0:creator rdf:datatype="http://www.w3.org/2001/XMLSchema#string">io.insideout.wordlift.org.apache.stanbol.enhancer.engines.freeling.impl.FreelingPartOfSpeechTaggingEngine</j.0:creator>
    <j.1:start rdf:datatype="http://www.w3.org/2001/XMLSchema#long">957</j.1:start>
  </rdf:Description>
</rdf:RDF>
```