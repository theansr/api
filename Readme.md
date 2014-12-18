RESTful ansr API
================

All URLs start with https://api.theansr.com/v1/. SSL only. The path is prefixed with the API version. If we change the API in backward-incompatible ways, we'll bump the version marker and maintain stable support for the old URLs.

# API Authentication
The API uses basic HTTP Authentication over SSL, so every request should include a standard Authorization header with the following:
* Username : Your  api-key
* Password : empty string

Remember that anyone who has your authentication token can see and change everything you have access to.

# API Ready for use

* [Accounts](https://github.com/theansr/api/blob/master/sections/accounts.md)
* [SMS](https://github.com/theansr/api/blob/master/sections/sms.md)
* [Calls](https://github.com/theansr/api/blob/master/sections/calls.md)
