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

Response:
```json
	{
		"jobID":"f1fab3d0-cb33-4a38-8664-222b091423b8",
		"status":
			{
				"state":"RUNNING",
				"code":200,
				"message":"Job created successfully.",
				"moreInfo":""
			},
		"jobRequest":
			{
				"consumerKey":"1234567890",
				"text":"President Barack Obama's speech in Chicago ... God bless these United States.",
				"callbackURL":"http://example.org",
				"mimeType":"application/rdf+xml"
			}
	}
```