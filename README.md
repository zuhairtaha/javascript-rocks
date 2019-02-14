# JavaScript rocks!

Welcome to the Wizkids JavaScript test!
The test is inspired by one of our products (AppWriter) which helps people with read/writing troubles by enabling them to read text out load and get word suggestions (predictions) while typing.

Predictions are word completions based on the input text, for example:
If the input text is `I like ca` the predictions could be `cars`, `cats` and `cake`.

The test requires you to write a small web page and JavaScript that implements a small subset of AppWriter functionality. You are free to choose any library to help you or write vanilla JavaScript/HTML/CSS if that's your thing!

If you have any issues getting the word prediction web service to work, don't hesitate in contacting us.

## Tasks

#### 1.  Write a function that performs a web request to fetch word predictions.
See the "Word predictions web service description" section below for more info on how to use the web service.

#### 2. Display the first 10 word predictions in HTML.
 
#### 3. Add a `<textarea>` in your HTML and use the text value for the function you wrote in step #1.
The text should be based on the position of the caret inside the textarea, for example:
```
Hello, my name is J⌶ohn Doe and I like pie! 
```
The extracted text should be from the start of the `<textarea>` up to the caret, which in this example would be `Hello, my name is J`.
The list of word predictions should be updated on either `keyup` or  `keypress` (whichever you think is more appropriate).

#### 4. Make your word predictions result clickable and insert the clicked prediction into the `<textarea>` on click.
The word prediction should be inserted into the `<textarea>` at the location of the caret.

#### 5. (OPTIONAL) Emphasize the part of each word prediction that is already written in the `<textarea>` preceding the caret.
For example, using the text from step #3 `Hello, my name is J` the letter `J` should be emphasized in the predictions `John`, `James` and `June`.

#### 6. Add your code in a Git project on GitHub and share the link with your Wizkids contact.
 
## Word predictions web service description

#### URL
`https://services.lingapps.dk/misc/getPredictions`

#### Authorization
Header (provided by Wizkids): `Authorization: Bearer [TOKEN]`

#### Parameters
  - `locale`: String, the langauge in which the predictions should be computed. Valid values are `da-DK` and `en-GB`.
  - `text`: String, the text from which to compute the predictions.

#### Response
JSON encoded array of strings ordered by prediction probability (descending), for example:
`["cars", "cats", "cake"]`

#### Example

**Request**
```
GET /misc/getPredictions?locale=en-GB&text=I%20like%20ca HTTP/1.1
Host: services.lingapps.titan.wizkids.dk
Authorization: Bearer MjAxOS0wMi0wMQ==.dGVzdEBleGFtcGxlLmNvbQ==.MjExMWMyYjdjZGY3YTU3MmU4MTA5OWY0MDgyMmM0OTk=
Connection: Close

```
**Response**
```
HTTP/1.1 200 OK
Content-Length: 34
Connection: close
Content-Type: application/json

[
    "cars",
    "cats",
    "cake"
]
```
