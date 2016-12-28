![](https://raw.githubusercontent.com/JacobBennett/StripeTestToken/master/stripetesttoken-01.jpg)

# Stripe Test Tokens

Use this to quickly create Stripe test tokens for successful and exceptional responses from Stripe.

## Install
```bash
composer require jacobbennett/stripe-test-token
```

## Usage
```php
<?php

use JacobBennett\StripeTestToken;
use Stripe\Charge;

StripeTestToken::setApiKey('your_stripe_secret_test_key');

// Fake a Successful Charge

Charge::create([
	'amount' => 500,
	'curreny' => 'usd',
	'source' => StripeTestToken::validVisa(),
]);


// Fake a Failing Charge

try {

	Charge::create([
		'amount' => 500,
		'curreny' => 'usd',
		'source' => StripeTestToken::cvcFail(),
	]);

} catch (\Stripe\Error\Card $e) {
	// handle errors
}

```

### ToDo

- scrutinizer
- packagist images
- badges
- update readme

### License

This project is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)

