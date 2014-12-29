Yii2 component for Yandex Money integration in your web appications
===================================================================

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist grigorieff/yii2-yandex-money "*"
```

or add

```json
"grigorieff/yii2-yandex-money": "*"
```

to the require section of your composer.json.

Configuration
------------

Add to your app config:

```php
    'components' => [

        .........

        'ym' => [
            'class' => grigorieff\ym\YMComponent,
            'client_id' => '......',
            'code' => '......',
            'redirect_uri' => '......',
            'client_secret' => '......'
        ],

        .........

    ];
```

Usage
-----

```php
$ym = Yii::$app->ym;

// get account info

$accountInfo = $ym->accountInfo();

.......

// get operation history with last 3 records
$operationHistory = $ym->->operationHistory(array("records"=>3));

......

// make request payment
$requestPayment = $ym->requestPayment([
    "pattern_id" => "p2p",
    "to" => $money_wallet,
    "amount_due" => $amount_due,
    "comment" => $comment,
    "message" => $message,
    "label" => $label,
]);

......

// call process payment to finish payment
$processPayment = $ym->processPayment(array(
    "request_id" => $request_payment->request_id,
));

......

```

License
-------

MIT

Requirements
------------
This Yii2 component require [Yandex Money SDK][1]


[1]:https://github.com/yandex-money/yandex-money-sdk-php