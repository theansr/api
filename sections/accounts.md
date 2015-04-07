Accounts
========

# Get Balance
`GET /accounts/get_balance`

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0
* balance (float): The current balance of the account in EURO (&euro;)


# Configure IVR 
`POST /accounts/configure_ivr` Create an IVR on a destination number


### Request Data

* did (string): The destination number where the IVR is configured.
* answer_url (string): This url will be invoked from ansr when there is an incoming call on the destination number. Currently the supported format of the answer_url response is XML. 
* answer_method (string): The method used to call the answer_url. Defaults to GET.

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0

# Examples

## Curl

Get Balance
```
curl https://api.theansr.com/accounts/get_balance -u api-key:
```

Response
```
{ errorCode: 0, balance: 15.721 }
```

Configure IVR 
```
curl https://api.theansr.com/v1/account/configure_ivr -d "&did=0044744xxxxxxx&answer_url=http://your_domain/redirection_url.xml&answer_method=GET" -u api-key:
```

Response
```
{ errorCode: 0 }
```
