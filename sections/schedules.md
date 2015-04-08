Schedules
==========

# Create Schedule
`POST /ring_groups/:ring_group_id/schedules` Create a schedule on existing ring group  

### Request Data
* schedule: The schedule when the ring group will be active. The parameters of the schedule are starttime, endtime, weekdays, startdate, enddate. 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Create Schedule
`POST /ring_groups/:ring_group_id/schedules/:id` Update a schedule on existing ring group  

### Request Data
* schedule: The schedule when the ring group will be active. The parameters of the schedule are starttime, endtime, weekdays, startdate, enddate. 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Examples

## Curl

Create Schedule

```
 curl http://ansr-api.dev/v1/ring_groups/7/schedules -u 52f8172d38537cfe2505c3b6d9464300: -d "&schedule[starttime]=0923&schedule[endtime]=2000&schedule[startdate]=2015-04-14"
```

Response

{"errorCode":0,"transaction":{"id":"141e77476d9b00a3daf1b855248c9c3c5256eaa7","ring_group":{"id":7,"did":"445454xxxxxx","group":["445454xxxxxx","445454xxxxxx"],"duration":-1,"sorting":1,"status":false},"schedules":[{"id":4,"starttime":"0923","endtime":"2000","weekdays":null,"enddate":null,"startdate":"2015-04-14"}]}}


Update Schedule

```
 curl http://ansr-api.dev/v1/ring_groups/7/schedules/4 -u 52f8172d38537cfe2505c3b6d9464300: -d "&schedule[starttime]=1023&schedule[endtime]=2000&schedule[startdate]=2015-04-14"
```

Response

{"errorCode":0, "transaction" : {"id":"141e77476d9b00a3daf1b855248c9c3c5256eaa7","ring_group" : {"id":7,"did":"445454xxxxxx","group":["445454xxxxxx","445454xxxxxx"],"duration":-1,"sorting":1,"status":false}, "schedule" : {"id":4,"starttime":"1023","endtime":"2000","weekdays":null,"enddate":null,"startdate":"2015-04-14"}}}