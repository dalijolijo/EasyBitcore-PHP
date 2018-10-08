EasyBitcore-PHP
===============

A simple class for making calls to Bitcore's API using PHP.

Getting Started
---------------
1. Include easybitcore.php into your PHP script:

    ```php
    require_once('easybitcore.php');
    ```
2. Initialize Bitcore connection/object:

    ```php
    $bitcore = new Bitcore('username','password');
    ```

    Optionally, you can specify a host, port. Default is HTTP on localhost port 8332.

    ```php
    $bitcore = new Bitcore('username','password','localhost','8332');
    ```

    If you wish to make an SSL connection you can set an optional CA certificate or leave blank
    ```php
    $bitcore->setSSL('/full/path/to/mycertificate.cert');
    ````

3. Make calls to bitcored as methods for your object. Examples:

    ```php
    $bitcore->getinfo();
    
    $bitcore->getrawtransaction('0e3e2357e806b6cdb1f70b54c3a3a17b6714ee1f0e68bebb44a74b1efd512098',1);
    
    $bitcore->getblock('000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f');
    ```

Additional Info
---------------
* When a call fails for any reason, it will return false and put the error message in `$bitcore->error`

* The HTTP status code can be found in $bitcore->status and will either be a valid HTTP status code or will be 0 if cURL was unable to connect.

* The full response (not usually needed) is stored in `$bitcore->response` while the raw JSON is stored in `$bitcore->raw_response`

*Forked from https://github.com/aceat64/EasyBitcoin-PHP*

Example
-------
*getnetworkinfo.php*
```php
<?php
require('easybitcore.php');
$bitcore = new Bitcore("<rpcuser>","<rpcpasswd>");
$getnetworkinfo = bitcore->getnetworkinfo();
print_r($getnetworkinfo);
?>
```
    
Ressources
----------
* [Bitcoin Wiki](https://en.bitcoin.it/wiki/API_reference_%28JSON-RPC%29) API reference (JSON-RPC)
* [Bitcoin Wiki](https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_calls_list) Original Bitcoin client/API calls list
* [YouTube Tutorial 5](https://www.youtube.com/watch?v=ARL_PvDEBtU&index=5&list=PLhWIQKZKupCawKJQBAEJc-Y4I30HQ6KBH) Bitcoin JSON-RPC Tutorial 5 - Your First Calls
* [YouTube Tutorial 6](https://www.youtube.com/watch?v=FyLCKMqkWIA&index=6&list=PLhWIQKZKupCawKJQBAEJc-Y4I30HQ6KBH) Bitcoin JSON-RPC Tutorial 6 - JSON Parameters and Errors
* [YouTube Tutorial 7](https://www.youtube.com/watch?v=o4BPt4RXOm4&index=7&list=PLhWIQKZKupCawKJQBAEJc-Y4I30HQ6KBH) Bitcoin JSON-RPC Tutorial 7 - Wallet Notify
