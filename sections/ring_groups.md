RingGroups
===========

# Create RingGroup
`POST /dids/:did/ring_groups` Create an Ring group on a did 

### Request Data
* destinations: The destination numbers of the ring group. The format of the destination number should be in full international format e.g for UK number 0044744xxxxxxx
* schedule(mandatory): The schedule when the ring group will be active. The parameters of the schedule are starttime, endtime, weekdays, startdate, enddate. 
* sorting(mandatory): This value is used to prioratize the active groups. 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Index RingGroup
`POST /dids/:did/ring_groups/index` Returns all the ring groups of a did 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Enable RingGroup
`POST /dids/:did/ring_groups/:id/enable` Enable specific ring group of a did 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Disable RingGroup
`POST /dids/:did/ring_groups/:id/disable` Disable specific ring group of a did 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Add Destination to RingGroup
`POST /dids/:did/ring_groups/:id/add_destination` Add destination to specific ring group of a did 

### Request Data
* destination: The destination number of the ring group that will be added. The format of the destination number should be in full international format e.g for UK number 0044744xxxxxxx

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Remove Destination from RingGroup
`POST /dids/:did/ring_groups/:id/remove_destination` Remove destination to ring group of a did 

### Request Data
* destination: The destination number of the ring group that will be removed. The format of the destination number should be in full international format e.g for UK number 0044744xxxxxxx

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0


# Show RingGroup Details
`POST /dids/:did/ring_groups/:id/show` Remove destination to ring group of a did 

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0
* transaction : JSON Hash which contains, the api transaction uuid, ring_group details and schedule details of the ring_group

# Examples

## Curl

Create RingGroup

```
 curl http://ansr-api.dev/v1/dids/{your_did}/ring_groups -u 52f8172d38537cfe2505c3b6d9464300: -d "&destinations[]=4418xxxxxx&destinations[]=4421xxxxxx&schedule[starttime]=0923&schedule[endtime]=2000&schedule[startdate]=2015-04-14"
```

Response 

{ errorCode: 0, :transaction => { :id => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", :ring_group => {:id => 3} }}

View RingGroups

```
 curl https://api.theansr.com/v1/dids/{your_did}/ring_groups/index -u 52f8172d38537cfe2505c3b6d9464300: 
```

Response 

{ errorCode: 0, :transaction => { :id => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", :ring_groups => [{:id => 3 ...}, {:id => 4 ....} }}


Disable RingGroup

```
 curl https://api.theansr.com/v1/dids/{your_did}/ring_groups/3/enable -u 52f8172d38537cfe2505c3b6d9464300: 
```

Response 

{ errorCode: 0, :transaction => { :id => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", :ring_group => {:id => 3} }}

Enable RingGroup

```
 curl https://api.theansr.com/v1/dids/{your_did}/ring_groups/3/enable -u 52f8172d38537cfe2505c3b6d9464300: 
```

Response 

{ errorCode: 0, :transaction => { :id => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", :ring_group => {:id => 3} }}


Add destination to RingGroup

```
 curl https://api.theansr.com/v1/dids/{your_did}/ring_groups/3/add_destination -u 52f8172d38537cfe2505c3b6d9464300: -d "&destination=4421xxxxxxxx"
```

Response 

{ errorCode: 0, :transaction => { :id => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", :ring_group => {:id => 3} } }

Remove destination from RingGroup

```
 curl https://api.theansr.com/v1/dids/{your_did}/ring_groups/3/remove_destination -u 52f8172d38537cfe2505c3b6d9464300: -d "&destination=4421xxxxxxxx"
```

Response 

{ errorCode: 0, :transaction => { :id => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", :ring_group => {:id => 3} } }

Show RingGroup Details

```
 curl https://api.theansr.com/v1/dids/{your_did}/ring_groups/3/show -u 52f8172d38537cfe2505c3b6d9464300: -d "&destination=4421xxxxxxxx"
```

Response

{"errorCode":0,"transaction":{"id":"141e77476d9b00a3daf1b855248c9c3c5256eaa7","ring_group":{"id":7,"did":"445454xxxxxx","group":["445454xxxxxx","445454xxxxxx"],"duration":-1,"sorting":1,"status":false},"schedules":[{"id":4,"starttime":"0923","endtime":"2000","weekdays":null,"enddate":null,"startdate":"2015-04-14"}]}}

