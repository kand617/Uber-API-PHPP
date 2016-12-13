#Getting started

## How to Build

The generated code has dependencies over external libraries like UniRest. These dependencies are defined in the ```composer.json``` file that comes with the SDK. 
To resolve these dependencies, we use the Composer package manager which requires PHP greater than 5.3.2 installed in your system. 
Visit [https://getcomposer.org/download/](https://getcomposer.org/download/) to download the installer file for Composer and run it in your system. 
Open command prompt and type ```composer --version```. This should display the current version of the Composer installed if the installation was successful.

* Using command line, navigate to the directory containing the generated files (including ```composer.json```) for the SDK. 
* Run the command ```composer install```. This should install all the required dependencies and create the ```vendor``` directory in your project directory.

![Building SDK - Step 1](http://apidocs.io/illustration/php?step=installDependencies&workspaceFolder=Uber%20API-PHP)

### [For Windows Users Only] Configuring CURL Certificate Path in php.ini

CURL used to include a list of accepted CAs, but no longer bundles ANY CA certs. So by default it will reject all SSL certificates as unverifiable. You will have to get your CA's cert and point curl at it. The steps are as follows:

1. Download the certificate bundle (.pem file) from [https://curl.haxx.se/docs/caextract.html](https://curl.haxx.se/docs/caextract.html) on to your system.
2. Add curl.cainfo = "PATH_TO/cacert.pem" to your php.ini file located in your php installation. “PATH_TO” must be an absolute path containing the .pem file.

```ini
[curl]
; A default value for the CURLOPT_CAINFO option. This is required to be an
; absolute path.
;curl.cainfo =
```

## How to Use

The following section explains how to use the UberAPI library in a new project.

### 1. Open Project in an IDE

Open an IDE for PHP like PhpStorm. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

![Open project in PHPStorm - Step 1](http://apidocs.io/illustration/php?step=openIDE&workspaceFolder=Uber%20API-PHP)

Click on ```Open``` in PhpStorm to browse to your generated SDK directory and then click ```OK```.

![Open project in PHPStorm - Step 2](http://apidocs.io/illustration/php?step=openProject0&workspaceFolder=Uber%20API-PHP)     

### 2. Add a new Test Project

Create a new directory by right clicking on the solution name as shown below:

![Add a new project in PHPStorm - Step 1](http://apidocs.io/illustration/php?step=createDirectory&workspaceFolder=Uber%20API-PHP)

Name the directory as "test"

![Add a new project in PHPStorm - Step 2](http://apidocs.io/illustration/php?step=nameDirectory&workspaceFolder=Uber%20API-PHP)
   
Add a PHP file to this project

![Add a new project in PHPStorm - Step 3](http://apidocs.io/illustration/php?step=createFile&workspaceFolder=Uber%20API-PHP)

Name it "testSDK"

![Add a new project in PHPStorm - Step 4](http://apidocs.io/illustration/php?step=nameFile&workspaceFolder=Uber%20API-PHP)

Depending on your project setup, you might need to include composer's autoloader in your PHP code to enable auto loading of classes.

```PHP
require_once "../vendor/autoload.php";
```

It is important that the path inside require_once correctly points to the file ```autoload.php``` inside the vendor directory created during dependency installations.

![Add a new project in PHPStorm - Step 4](http://apidocs.io/illustration/php?step=projectFiles&workspaceFolder=Uber%20API-PHP)

After this you can add code to initialize the client library and acquire the instance of a Controller class. Sample code to initialize the client library and using controller methods is given in the subsequent sections.

### 3. Run the Test Project

To run your project you must set the Interpreter for your project. Interpreter is the PHP engine installed on your computer.

Open ```Settings``` from ```File``` menu.

![Run Test Project - Step 1](http://apidocs.io/illustration/php?step=openSettings&workspaceFolder=Uber%20API-PHP)

Select ```PHP``` from within ```Languages & Frameworks```

![Run Test Project - Step 2](http://apidocs.io/illustration/php?step=setInterpreter0&workspaceFolder=Uber%20API-PHP)

Browse for Interpreters near the ```Interpreter``` option and choose your interpreter.

![Run Test Project - Step 3](http://apidocs.io/illustration/php?step=setInterpreter1&workspaceFolder=Uber%20API-PHP)

Once the interpreter is selected, click ```OK```

![Run Test Project - Step 4](http://apidocs.io/illustration/php?step=setInterpreter2&workspaceFolder=Uber%20API-PHP)

To run your project, right click on your PHP file inside your Test project and click on ```Run```

![Run Test Project - Step 5](http://apidocs.io/illustration/php?step=runProject&workspaceFolder=Uber%20API-PHP)

## How to Test

Unit tests in this SDK can be run using PHPUnit. 

1. First install the dependencies using composer including the `require-dev` dependencies.
2. Run `vendor\bin\phpunit --verbose` from commandline to execute tests. If you have 
   installed PHPUnit globally, run tests using `phpunit --verbose` instead.

You can change the PHPUnit test configuration in the `phpunit.xml` file.

## Initialization

### Authentication and 
In order to setup authentication and initialization of the API client, you need the following information.

| Parameter | Description |
|-----------|-------------|
| basicAuthUserName | The username to use with basic authentication |
| basicAuthPassword | The password to use with basic authentication |



API client can be initialized as following.

```php
// Configuration parameters and credentials
$basicAuthUserName = "basicAuthUserName"; // The username to use with basic authentication
$basicAuthPassword = "basicAuthPassword"; // The password to use with basic authentication

$client = new UberAPIClient($basicAuthUserName, $basicAuthPassword);
```

## Class Reference

### <a name="list_of_controllers"></a>List of Controllers

* [APIController](#api_controller)

### <a name="api_controller"></a>![Class: ](http://apidocs.io/img/class.png ".APIController") APIController

#### Get singleton instance

The singleton instance of the ``` APIController ``` class can be accessed from the API Client.

```php
$client = $client->getClient();
```

#### <a name="get_request_map"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getRequestMap") getRequestMap

> Get a map with a visual representation of a Request.


```php
function getRequestMap($requestId)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| requestId |  ``` Required ```  | Unique identifier representing a Request. |



#### Example Usage

```php
$requestId = 'request_id';

$result = $client->getRequestMap($requestId);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues |
| 404 | Not found |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types, such as ?Unacceptable content type. Request resource as: application/json. |
| 409 | A conflict needs to be resolved before the request can be made. |
| 422 | Invalid request. The request body is parse-able however with invalid content or there are issues with a rider's user account. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="delete_request_cancel"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.deleteRequestCancel") deleteRequestCancel

> Cancel an ongoing Request on behalf of a rider.


```php
function deleteRequestCancel($requestId)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| requestId |  ``` Required ```  | Unique identifier representing a Request. |



#### Example Usage

```php
$requestId = 'request_id';

$client->deleteRequestCancel($requestId);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types, such as ?Unacceptable content type. Request resource as: application/json. |
| 409 | A conflict needs to be resolved before the request can be made |
| 422 | Invalid request. The request body is parse-able however with invalid content or there are issues with a rider's user account. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error |



#### <a name="get_request_details"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getRequestDetails") getRequestDetails

> Get the real time status of an ongoing trip that was created using the Ride Request endpoint.


```php
function getRequestDetails($requestId)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| requestId |  ``` Required ```  | TODO: Add a parameter description |



#### Example Usage

```php
$requestId = 'request_id';

$result = $client->getRequestDetails($requestId);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types, such as ?Unacceptable content type. Request resource as: application/json. |
| 409 | A conflict needs to be resolved before the request can be made. |
| 422 | Invalid request. The request body is parse-able however with invalid content or there are issues with a rider's user account. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error |



#### <a name="get_user_profile"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getUserProfile") getUserProfile

> The User Profile endpoint returns information about the Uber user that has authorized with the application.


```php
function getUserProfile()
```

#### Example Usage

```php

$result = $client->getUserProfile();

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types: ?Unacceptable content type. Request resource as: application/json, etc. |
| 422 | Invalid request. The request body is parse-able however with invalid content. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="get_products_types"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getProductsTypes") getProductsTypes

> The Products endpoint returns information about the Uber products offered at a given location. The response includes the display name and other details about each product, and lists the products in the proper display order.


```php
function getProductsTypes($options)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| latitude |  ``` Required ```  | Latitude component of location. |
| longitude |  ``` Required ```  | Longitude component of location. |



#### Example Usage

```php
$latitude = 130.44934206896;
$collect['latitude'] = $latitude;

$longitude = 130.44934206896;
$collect['longitude'] = $longitude;


$result = $client->getProductsTypes($collect);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types: ?Unacceptable content type. Request resource as: application/json, etc. |
| 422 | Invalid request. The request body is parse-able however with invalid content. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="get_price_estimates"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getPriceEstimates") getPriceEstimates

> The Price Estimates endpoint returns an estimated price range for each product offered at a given location. The price estimate is provided as a formatted string with the full price range and the localized currency symbol.


```php
function getPriceEstimates($options)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| endLatitude |  ``` Required ```  | Latitude component of end location. |
| endLongitude |  ``` Required ```  | Longitude component of end location. |
| startLatitude |  ``` Required ```  | Latitude component of start location. |
| startLongitude |  ``` Required ```  | Longitude component of start location. |



#### Example Usage

```php
$endLatitude = 130.44934206896;
$collect['endLatitude'] = $endLatitude;

$endLongitude = 130.44934206896;
$collect['endLongitude'] = $endLongitude;

$startLatitude = 130.44934206896;
$collect['startLatitude'] = $startLatitude;

$startLongitude = 130.44934206896;
$collect['startLongitude'] = $startLongitude;


$result = $client->getPriceEstimates($collect);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types: ?Unacceptable content type. Request resource as: application/json, etc. |
| 422 | Invalid request. The request body is parse-able however with invalid content. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="get_time_estimates"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getTimeEstimates") getTimeEstimates

> The Time Estimates endpoint returns ETAs for all products offered at a given location, with the responses expressed as integers in seconds. We recommend that this endpoint be called every minute to provide the most accurate, up-to-date ETAs.


```php
function getTimeEstimates($options)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| startLatitude |  ``` Required ```  | Latitude component of the start location |
| startLongitude |  ``` Required ```  | Longitude component of the start location |
| customerUuid |  ``` Optional ```  | The customer id interested in estimate |
| productId |  ``` Optional ```  | Id of the requested product |



#### Example Usage

```php
$startLatitude = 130.44934206896;
$collect['startLatitude'] = $startLatitude;

$startLongitude = 130.44934206896;
$collect['startLongitude'] = $startLongitude;

$customerUuid = 'customer_uuid';
$collect['customerUuid'] = $customerUuid;

$productId = 'product_id';
$collect['productId'] = $productId;


$result = $client->getTimeEstimates($collect);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types: ?Unacceptable content type. Request resource as: application/json, etc. |
| 422 | Invalid request. The request body is parse-able however with invalid content. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="get_user_activity_v11"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getUserActivityV11") getUserActivityV11

> The User Activity endpoint returns data about a user's lifetime activity with Uber. The response will include pickup locations and times, dropoff locations and times, the distance of past requests, and information about which products were requested.


```php
function getUserActivityV11($options)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| limit |  ``` Required ```  | Number of items to return for pagging |
| offset |  ``` Required ```  | Page offset for pagging |



#### Example Usage

```php
$limit = 130;
$collect['limit'] = $limit;

$offset = 130;
$collect['offset'] = $offset;


$result = $client->getUserActivityV11($collect);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types: ?Unacceptable content type. Request resource as: application/json, etc. |
| 422 | Invalid request. The request body is parse-able however with invalid content. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="get_promotions"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getPromotions") getPromotions

> The Promotions endpoint returns information about the promotion that will be available to a new user based on their activity's location. These promotions do not apply for existing users.


```php
function getPromotions($options)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| endLatitude |  ``` Required ```  | Latitude component of end location. |
| endLongitude |  ``` Required ```  | Longitude component of end location. |
| startLatitude |  ``` Required ```  | Latitude component of start location. |
| startLongitude |  ``` Required ```  | Longitude component of start location |



#### Example Usage

```php
$endLatitude = 130.44934206896;
$collect['endLatitude'] = $endLatitude;

$endLongitude = 130.44934206896;
$collect['endLongitude'] = $endLongitude;

$startLatitude = 130.44934206896;
$collect['startLatitude'] = $startLatitude;

$startLongitude = 130.44934206896;
$collect['startLongitude'] = $startLongitude;


$result = $client->getPromotions($collect);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request. |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found. |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types, such as ?Unacceptable content type. Request resource as: application/json. |
| 409 | A conflict needs to be resolved before the request can be made. |
| 422 | Invalid request. The request body is parse-able however with invalid content or there are issues with a rider's user account. |
| 429 | Too Many Requests. Rate limited |
| 500 | Internal Server Error. |
| 222 | bac |



#### <a name="create_request"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.createRequest") createRequest

> The Request endpoint allows a ride to be requested on behalf of an Uber user given their desired product, start, and end locations. Please review the Sandbox documentation on how to develop and test against these endpoints without making real-world Requests and being charged.


```php
function createRequest($body)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| body |  ``` Required ```  | TODO: Add a parameter description |



#### Example Usage

```php
$body = new RequestBody();

$result = $client->createRequest($body);

```

#### Errors

| Error Code | Error Description |
|------------|-------------------|
| 400 | Malformed request |
| 401 | Unauthorized the request requires user authentication (not logged in). |
| 403 | Forbidden. Also used for unauthorized requests such as improper OAuth 2.0 scopes or permissions issues. |
| 404 | Not found |
| 406 | Unacceptable content type. Client sent an accepts header for a content type which does not exist on the server. Body includes a list of acceptable content types, such as ?Unacceptable content type. Request resource as: application/json |
| 409 | A conflict needs to be resolved before the request can be made. |
| 422 | Invalid request. The request body is parse-able however with invalid content or there are issues with a rider's user account. |
| 429 | Too Many Requests. Rate limited. |
| 500 | Internal Server Error. |



#### <a name="get_product_detail_by_id"></a>![Method: ](http://apidocs.io/img/method.png ".APIController.getProductDetailByID") getProductDetailByID

> Get product details w.r.t id


```php
function getProductDetailByID($productId)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| productId |  ``` Required ```  | Unique identifier representing a specific product for a given latitude & longitude. For example, uberX in San Francisco will have a different product_id than uberX in Los Angeles. |



#### Example Usage

```php
$productId = 'product_id';

$result = $client->getProductDetailByID($productId);

```


[Back to List of Controllers](#list_of_controllers)



