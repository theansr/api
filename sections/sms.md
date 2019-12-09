SMS
===

## Create SMS

`POST /sms` send sms to given recipients

### Request Data

* sender (string): The name that will be shown as sender on the SMS. This value must contain **at least 4 characters** . If the value contains alphanumeric characters **the maximum length should be 11 characters** and if it contains only numeric characters **the maximum length should be 14 characters** . Default value Account's Caller ID
* recipients (string): The phone number of the recipients. Multiple recipients can be separated with comma (,). The phone number should be given in international format (e.g for UK number 44744xxxxxxx)
* body (string): The Body of the SMS. Should contain up to **160 characters**

### Response Data
The response is in JSON format

* call_id (string): The transaction id of a successful request 
* errorCode (integer): If the request is successful, errorCode is 0
* errors (JSON): JSON of error messages if the request is not successful
* price (float): The price of the SMS if the request is successful
 

## Create PIN Verification SMS
`POST /sms/verification_pin` send an sms with random verification pin number to given recipients

### Request Data
* sender (string): The name that will be shown as sender on the SMS. This value must contain **at least 4 characters** . If the value contains alphanumeric characters **the maximum length should be 11 characters** and if it contains only numeric characters **the maximum length should be 14 characters** . Default value Account's Caller ID.
* recipients (string): The phone number of the recipients. Multiple recipients can be separated with comma (,). The phone number should be given in international format (e.g for UK number 44744xxxxxxx).
* num_of_digits (integer): (Optional) The number of digits of the generated PIN (Default: 4).

### Response Data
The response is in JSON format

* call_id (string): The transaction id of a successful request.
* errorCode (integer): If the request is successful, errorCode is 0.
* errors (JSON): JSON of error messages if the request is not successful.
* price (float): The price of the SMS if the request is successful.
* verification_pin (string): The generated PIN.

## Show Verification PIN
`GET /sms/verification_pin/{call_id}` returns the verification pin that was generated on the given {call_id}

### Response Data
The response is in JSON format

* call_id (string): The given {call_id}.
* errorCode (integer): If the request is successful, errorCode is 0.
* errors (JSON): JSON of error messages if the request is not successful.
* verification_pin (string): The generated PIN.


## Verify PIN

`POST /sms/verify_pin/{call_id}` Verifies the pin against the given {call_id} and returns true or false

### Request Data
* pin (string): The PIN that should be verified against the given {call_id}.

### Response Data
The response is in JSON format

* call_id (string): The given {call_id}.
* errorCode (integer): If the request is successful, errorCode is 0.
* errors (JSON): JSON of error messages if the request is not successful.
* pin_verification (boolean): True is returned if there is a match in the posted {call_id} and {pin}.

# Examples

## Curl

Create SMS
```
curl https://api.theansr.com/v1/sms -d "&sender=TestSMS&recipients=44744xxxxxxx&body=Test123" -u api-key:
```

Response
```
{ call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", errorCode: 0, price: 0.0123}
```

Create Verification PIN SMS
```
curl https://api.theansr.com/v1/sms/verification_pin -d "&sender=TestSMS&recipients=44744xxxxxxx" -u api-key:
```

Response
```
{ call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", errorCode: 0, price: 0.0123, pin: 5678}
```


GET Verification PIN
```
curl https://api.theansr.com/v1/sms/verification_pin/NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T -u api-key:
```

Response
```
{ call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", errorCode: 0, verification_pin: 5678}
```

Verify PIN
```
curl https://api.theansr.com/v1/sms/verification_pin/NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T  -d "&pin=5678" -u api-key:
```

Response
```
{ call_id: "NEsCFhcN9mk3JKZuHqBoUm9Pma9s67T", errorCode: 0, pin_verification: true}
```
