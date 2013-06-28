php-mint-api
============

A simple PHP class for interacting with Mint.com

This class provides methods for connecting to Mint.com as a specific user and downloading that user's transactions in CSV format.

Basic usage:
```php
require_once('php-mint-api/PhpMintApi.php');

$filePath = dirname(__FILE__);
$cookieFile = $filePath . '/cookie.txt';
$transactionsFile = $filePath . '/transactions.csv';

$mint = new PhpMintApi('[Mint.com user email]', '[Mint.com user password]', $cookieFile);

try {
	$mint->connect();
} catch(Exception $e) {
	echo 'Caught exception: ' .  $e->getMessage() . "\n";
	exit;
}

$fp = fopen($transactionsFile, 'w');
$mint->getTransactions($fp);
fclose($fp);
```

Originally inspired by https://github.com/mrooney/mintapi