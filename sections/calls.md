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


## Create Verification PIN Call
`POST calls/verification_pin` creates a random verification PIN which is 'said' to the recipient 

### Request Data
* from (string): The caller id that will be shown on callee. Default Account's caller_id
* to (string): The destination number. The format of the destination number should be in full international format e.g for UK number 0044744xxxxxxx
* num_of_digits (integer): (Optional) The number of digits of the generated PIN (Default: 4)
* body(sting): (Optional) The text is said to the recipient before the verification PIN
* lang(String): (Optional) The language that is spoken to the recipient. (Default: en_US) Supported languages en_US, en_UK, el_GR 

### Response Data
The response is in JSON format

* call_id (string): The transaction id of a successful request 
* errorCode (integer): If the request is successful, errorCode is 0
* errors (JSON): JSON of error messages if the request is not successful
* price (float): The price of the SMS if the request is successful


## Show Verification PIN
`GET /sms/verification_pin/{call_id}` returns the verification pin that was generated on the given {call_id}

### Response Data
The response is in JSON format

* call_id (string): The given {call_id}  
* errorCode (integer): If the request is successful, errorCode is 0
* errors (JSON): JSON of error messages if the request is not successful
* verification_pin (integer): The generated PIN


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

Create Verification PIN Call
```
curl https://api.theansr.com/v1/calls/verification_pin -d "&from={your_caller_id}&to=0044744xxxxxxx&lang=el_GR" -u api-key:
```

Response
```
{ errorCode: 0, call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T" }
```

Create Verification PIN Call
```
curl https://api.theansr.com/v1/calls/verification_pin/NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T  -u api-key:
```

Response
```
{ call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", errorCode: 0, verification_pin: 5678}
```


# Answer URL Response

## XML
[XML Guide](https://github.com/theansr/api/blob/master/sections/xml_guide.md)