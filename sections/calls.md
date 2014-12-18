Calls
=====

# Create Call
`POST /calls` Make an outbound call

### Request Data

* from (string): The caller id that will be shown on callee. Default Account's caller_id
* to (string): The destination number. The format of the destination number should be in full international format e.g for UK number 0044744xxxxxxx
* answer_url (string): This url will be invoked from ansr when the call is answered. Currently the supported format of the answer_url response is XML. 
* answer_method (string): The method used to call the answer_url. Defaults to GET.


### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0
* call_id (string): The call_id of the outbound call that has been initiated.

# Answer URL Response

## XML
[XML Guide](https://github.com/theansr/api/blob/master/sections/xml_guide.md)

# Examples

## Curl

Create Call
```
curl https://api.theansr.com/v1/calls -d "&from={your_caller_id}&to=0044744xxxxxxx&answer_url=http://your_domain/redirection_url.xml&answer_method=GET" -u api-key:
```

Response
```
{ errorCode: 0, call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T" }
```

