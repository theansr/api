Faxes
=====

# Create Fax
`POST /faxes` Make an outbound call

### Request Data

* to (string): The destination number. The format of the destination number should be in full international format e.g for UK number 0044744xxxxxxx
* message (file): The file that is going to be sent as fax. Currently only pdf files are supported. 


### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Answer URL Response

# Examples

## Curl

Create Fax
```
curl https://api.theansr.com/v1/faxes -d "&to=0044744xxxxxxx" -u api-key:

```

Response
```
{"errorCode":0, "transaction" : {"id":"141e77476d9b00a3daf1b855248c9c3c5256eaa7", "fax" : { "call_id" => "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T" } } }
```