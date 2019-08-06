# Affitto Certificato Client API Library


Simple and fast implementation for services of Affitto Certificato API

[![Latest Stable Version](https://poser.pugx.org/affittocertificato/clientapi/version)](https://packagist.org/packages/affittocertificato/clientapi)
[![License](https://poser.pugx.org/affittocertificato/clientapi/license)](https://packagist.org/packages/affittocertificato/clientapi)

## Basic example

```php

$client = new \AffittoCertificato\Api\Client();

if (!$client->login('username','password')){
  throw new Exception ("Unable to login");
}

// get ratings using user's email address
if (!$client->userRatingByEmail('test@mail.com')){
  throw new Exception ("Unable to get ratings");
}

// to get api results use method getResponse() which return an object as described later in ## responses section
$result = $client->getResponse();
if (!$result->success){
  throw new Exception ("Request failed");
}



```


## Response structure

API calls always return a structured response, as in the exampled below:
```json
{
    "success": true,
    "requestID": "4e7b02eb-c17e-4046-9449-caca246d5bb8",
    "errorType": null,
    "errorMessage": null,
    "response": {
        "registered": false,
        "referenced": false,
        "probed": false
    }
}
```

where field "success" (boolean) means if the call has been succesfully processed, this not means "success" of the operations itself, but only mean "succesfully" of the api call.

"requestID" is an universal id that identify the request for future logging and debugging operations

"errorType" is a unique string that identify the type of error. This field is useful, to the client, to discriminate the type of error and adopt the appropriate measures (display an error message, rollback on the database, and more)

"errorMessage" is a descriptive text of error (if any)

"response" is the "real" response produced by API method, and the structure depend on it. In the example above is shown the response for "userRatingByEmail" call.


## Requirements

- PHP >= 7.0

## Installation

The recommended way is to install the lib [through Composer](http://getcomposer.org/).

Simply run `composer require affittocertificato/clientapi` for it to be automatically installed and included in your `composer.json`.

Now you can use the autoloader, and you will have access to the library:

```php
require 'vendor/autoload.php';
```

## Documentation

A swagger testing page can be found [here](https://api.affittocertificato-services.cloud/api-doc/index.html).
You can use this page to test the API calls.


## License

This library is released under the GPL-3.0 license