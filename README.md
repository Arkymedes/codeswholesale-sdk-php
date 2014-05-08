# CodesWholesale PHP SDK
CodesWholesale is the first easy, secure API of game keys wholesaler. This is the PHP SDK to ease integration of its features with any PHP language based application.

## Installation
You can install **codeswholesale-sdk-php** via Composer or by downloading the source.

### Via Composer:

**codeswholesale-sdk-php** is available on Packagist as the [codeswholesale/sdk](https://packagist.org/packages/codeswholesale/sdk) package.

On your project root, install Composer

    curl -sS https://getcomposer.org/installer | php
	
Or download it from official page: https://getcomposer.org/download/

Configure the **codeswholesale/sdk** dependency in your 'composer.json' file:

    "require": {
        "codeswholesale/sdk": "1.0.*@beta"
    }

On your project root, install the the SDK with its dependencies:

    php composer.phar install
    
## Create your CodesWholesale account

If you have not already done so, register at
[CodesWolesale](https://app.codeswholesale.com) and set up your API credentials:

1. Create a [CodesWholesale](https://app.codeswholesale.com) account and
   create your API keys in WEB API tab, under your profile name link. Save your keys in safe place. Your API password is visible only once.

## Getting Started

1.  **Require the CodesWholesale PHP SDK** via the composer auto loader

    ```php
    require 'vendor/autoload.php';
    ```

2.  **Configure the client** using the API keys

    ```php
    
    $params = array(
       /**
        * API Keys
        * These are common api keys, you can use it to test integration.
        */
        'cw.client_id' => 'ff72ce315d1259e822f47d87d02d261e',
        'cw.client_secret' => '$2a$10$E2jVWDADFA5gh6zlRVcrlOOX01Q/HJoT6hXuDMJxek.YEo.lkO2T6',
        /**
         * CodesWholesale ENDPOINT
         */
        'cw.endpoint_uri' => \CodesWholesale\CodesWholesale::SANDBOX_ENDPOINT,
        /**
        * Due to security reasons you should use SessionStorage only while testing.
        * In order to go live you should change it do database storage.
        */
        'cw.token_storage' => new \fkooman\OAuth\Client\SessionStorage()
    );
     
     
    $clientBuilder = new \CodesWholesale\ClientBuilder($params);
    $client = $clientBuilder->build();
    
    ```
For production release please remember to change endpoint from SANDBOX to LIVE.


3.  **List all products from price list**

    ```php
    $products = $client->getProducts();
    ```
    
4.  **Single product details**

    ```php
    $product = \CodesWholesale\Resource\Product::get($productHref);
    ```
    

5.  **Retrive account details, balance value and available credit**

    ```php
    $account = $client->getAccount();
    ```
    
6.  **Create single code order**

    ```php
    $code = \CodesWholesale\Resource\Order::createOrder($product);
    ```
    
7.  **Create order for multiple codes**

    ```php
    $codes = \CodesWholesale\Resource\Order::createBatchOrder($product, array('quantity' => 10));
    ```
    
You can check "examples" directory for more samples and details.

## Copyright & Licensing

Copyright &copy; 2014 Codeswholesale

This project is licensed under the [Apache 2.0 Open Source License](http://www.apache.org/licenses/LICENSE-2.0).

For additional information, please see:

  1.  fkooman OAuth2 client: https://github.com/fkooman/php-oauth-client
