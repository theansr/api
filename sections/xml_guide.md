XML Guide
=========

Your application must use ansr XML to control a call. The XML elements can be combined in different ways to perform complex actions. Some of the possible control actions are:
* Playing music
* Reading out specified text
* Requesting numeric inputs

## Supported Tags

* [GetDigits](https://github.com/theansr/api/blob/master/sections/xml_guide.md#getdigits)
* [Play](https://github.com/theansr/api/blob/master/sections/xml_guide.md#play)
* [Say](https://github.com/theansr/api/blob/master/sections/xml_guide.md#say)
* [Redirect](https://github.com/theansr/api/blob/master/sections/xml_guide.md#redirect)


### GetDigits
The `GetDigits` element is used to collect the digits entered by a caller/callee. Once the caller/callee has finished entering the digits, the API submits the data to the provided `action` URL using a HTTP `GET` or `POST` request.

You could play a message nested inside the `GetDigits` element while the digits are being received in the background. This is useful for creating a phone tree (IVR).

Nesting Rules

You can nest `<Say>` and `<Play>` elements within the `<GetDigits>` element.

Attributes

* action (mandatory): The URL to which the digits are sent. 
* method (mandatory): Submit to action URL using GET or POST.
* numDigits (mandatory): Maximum number of digits to be processed in the current operation. Only the number of numDigits is captured and any additional digits entered are ignored.
* validDigits (mandatory): Set of digits which the user is allowed enter.
* timeout (optional): Time in seconds to wait to receive the first digit. If the user fails to provide an input within the timeout period, the next element in the response is processed. Default value 10
* retries (optional): Indicates the number of retries the user is allowed to input the digits, if digits are not received within the time specified by timeout. Default value 5


Example
```
<Response>
	<GetDigits numDigits="2" validDigits="0123456789" method="GET" timeout="3" retries="10" action="http://your_domain/menu_response.xml">
		<Play>http://your_domain/menu.mp3</Play>
	</GetDigits>
</Response>
```

### Play
The Play element is used to play an audio file to the caller/callee. The audio file is obtained from a remote URL. API supports mp3 and wav files formats.

Examples

```
<Response>
    <Play>http:/your_domain/test.mp3</Play>
</Response>
```

### Say
The Say element is used to read a text to the caller/callee.

Attributes

* lang (mandatory): The language of the text. Default en_UK

Supported Languages

* English UK : en_UK
* English US : en_US
* Greek : el_GR

Example

```
<Response>
    <Say lang="en_UK">Hello World</Say>
</Response>
```

### Redirect

The Redirect element is used to transfer the control of a call at a different URL, which then starts processing the new XML response. Any elements after <Redirect> will not be processed.

Attributes

* method : Used to specify the HTTP request mode to obtain the Redirect URL. Default GET


