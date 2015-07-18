Google reCAPTCHA widget for Yii2
================================
Based on reCaptcha API 2.0.

Installation
------------
Cara untuk menginstall yang paling mudah adalah menggunakan composer [composer](http://getcomposer.org/download/).

* Either run

```
php composer.phar require --prefer-dist "himiklab/yii2-recaptcha-widget" "*"
```

or add

```json
"himiklab/yii2-recaptcha-widget" : "*"
```

to the `require` section of your application's `composer.json` file.

* [Daftar dulu reCAPTCHA API keys](https://www.google.com/recaptcha/admin#createsite).

* Tambahkan ke file config/web.php

```php
'components' => [
    'reCaptcha' => [
        'name' => 'reCaptcha',
        'class' => 'himiklab\yii2\recaptcha\ReCaptcha',
        'siteKey' => 'siteKey setelah mendaftar',
        'secret' => 'secret key setelah mendaftar',
    ],
    ...
```

* Tambahkan `ReCaptchaValidator` pada model yang digunakan untuk formnya, contoh:

```php
public $reCaptcha;

public function rules()
{
  return [
      // ...
      [['reCaptcha'], \himiklab\yii2\recaptcha\ReCaptchaValidator::className()]
  ];
}
```

Pemakaian
-----
Tambahkan kode berikut ke form yang akan ditambahkan captcha

```php
<?= $form->field($model, 'reCaptcha')->widget(
    \himiklab\yii2\recaptcha\ReCaptcha::className()
) ?>
```

atau

```php
<?= \himiklab\yii2\recaptcha\ReCaptcha::widget([
    'name' => 'reCaptcha',
    'widgetOptions' => ['class' => 'col-sm-offset-3']
]) ?>
```
Resources
---------
* [Google reCAPTCHA](https://developers.google.com/recaptcha)
