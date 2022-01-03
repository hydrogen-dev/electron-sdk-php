# Hydrogen Electron API

For more information, please visit [https://www.hydrogenplatform.com/apis](https://www.hydrogenplatform.com/apis)

## Documentation

https://www.hydrogenplatform.com/docs/electron/v1

## Requirements

1. PHP 5.5 and later

## Installation

### Install via Composer

Please run `composer require hydrogenplatform/hydrogen-electron-api`

## Getting Started

Please first follow the [installation](#installation) instructions. Then make sure you use the proper base URL:

### Base URL

Create an authentication object(**AuthApiClient**) and pass the **getDefaultConfiguration** method
 with environment parameter.
 
**Sandbox URL**

\com\hydrogen\nucleus\AuthApiClient::
        getDefaultConfiguration(\com\hydrogen\nucleus\Environment::SANDBOX)
        
**Production URL**

\com\hydrogen\nucleus\AuthApiClient::
        getDefaultConfiguration(\com\hydrogen\nucleus\Environment::PRODUCTION)

### Sample Code
Now you are ready to execute the following PHP code:

```php
<?php
require_once('../vendor/autoload.php');
try {
// Use one of the below method to generate oauth token
// 1) Generate Token for client credentials
$config =
        \com\hydrogen\electron\AuthApiClient::getDefaultConfiguration(\com\hydrogen\electron\Environment::PRODUCTION)
            ->createClientCredential("MYCLIENTID",
             "MYCLIENTSECRET");
// 2) Generate Token for password credentials
$config =
        \com\hydrogen\electron\AuthApiClient::
        getDefaultConfiguration(\com\hydrogen\electron\Environment::PRODUCTION)->createPasswordCredential("MYCLIENTID","MYCLIENTSECRET"
                      ,"MYUSERNAME", "MYPASSWORD");
// 3) Generate Token for client_token
$config = \com\hydrogen\nucleus\AuthApiClient::getDefaultConfiguration(\com\hydrogen\electron\Environment::PRODUCTION)
                ->createClientTokenCredential("MYCLIENTID","MYCLIENTSECRET", "CLIENT_TOKEN");
} catch (\com\hydrogen\electron\ApiException $e) {
    print_r($e);
}
$apiInstance = new com\hydrogen\nucleus\Api\AccountApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$alloc_request = new \com\hydrogen\nucleus\Model\AccountAllocationMapping(); // \com\hydrogen\nucleus\Model\AccountAllocationMapping | allocRequest

try {
    $result = $apiInstance->createAccountAllocationMappingUsingPost($alloc_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AccountApi->createAccountAllocationMappingUsingPost: ', $e->getMessage(), PHP_EOL;
}

?>
```

## Author
The Hydrogen Technology Corporation

https://www.hydrogenplatform.com

*Generated using [Swagger Codegen](https://github.com/swagger-api/swagger-codegen)*
