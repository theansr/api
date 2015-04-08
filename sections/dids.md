DIDs
========

# Configure IVR 
`POST /dids/:did/configure_ivr` Create an IVR on a did 


### Request Data

* answer_url (string): This url will be invoked from ansr when there is an incoming call on the destination number. Currently the supported format of the answer_url response is XML. 
* answer_method (string): The method used to call the answer_url. Defaults to GET.

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0


# Examples

## Curl

Configure IVR 
```
curl https://api.theansr.com/v1/dids/{your_did}/configure_ivr -d "&answer_url=http://your_domain/redirection_url.xml&answer_method=GET" -u api-key:
```

Response
```
{ errorCode: 0 }
```

