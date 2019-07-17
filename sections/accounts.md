Accounts
========

# Get Balance
`GET /accounts/get_balance`

### Response Data
The response is given in JSON format
* errorCode (integer): If the request is successful, errorCode is 0
* balance (float): The current balance of the account in EURO (&euro;)



# Examples

## Curl

Get Balance
```
curl https://api.theansr.com/v1/accounts/get_balance -u api-key:
```

Response
```
{ errorCode: 0, balance: 15.721 }
```

