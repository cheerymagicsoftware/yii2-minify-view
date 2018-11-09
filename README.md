Yii 2 Minify View Component
===========================

The main feature of this component - concatenate and compress files 
connected through "AssetBundle". 
Optimize for [CMS Luya](https://luya.io). 
Because Luya set  

[![License](https://poser.pugx.org/rmrevin/yii2-minify-view/license.svg)](https://packagist.org/packages/rmrevin/yii2-minify-view)
[![Latest Stable Version](https://poser.pugx.org/rmrevin/yii2-minify-view/v/stable.svg)](https://packagist.org/packages/rmrevin/yii2-minify-view)
[![Latest Unstable Version](https://poser.pugx.org/rmrevin/yii2-minify-view/v/unstable.svg)](https://packagist.org/packages/rmrevin/yii2-minify-view)
[![Total Downloads](https://poser.pugx.org/rmrevin/yii2-minify-view/downloads.svg)](https://packagist.org/packages/rmrevin/yii2-minify-view)

Code Status
-----------
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/rmrevin/yii2-minify-view/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/rmrevin/yii2-minify-view/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/rmrevin/yii2-minify-view/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/rmrevin/yii2-minify-view/?branch=master)
[![Travis CI Build Status](https://travis-ci.org/rmrevin/yii2-minify-view.svg)](https://travis-ci.org/rmrevin/yii2-minify-view)
[![Dependency Status](https://www.versioneye.com/user/projects/54119b4b9e1622a6510000e1/badge.svg)](https://www.versioneye.com/user/projects/54119b4b9e1622a6510000e1)

Support
-------
[GutHub issues](https://github.com/rmrevin/yii2-minify-view/issues) or [public chat](https://gitter.im/rmrevin/support).

Installation
------------

The preferred way to install this extension is through [composer](https://getcomposer.org/).

Either add

```
"repositories": [
    {
        "type":"vcs",
        "url":"https://github.com/cheerymagicsoftware/yii2-minify-view.git"
    }
],

"require": {
    "cheerymagic/yii2-minify-view": "master@dev"
},
```

to the `require` section of your `composer.json` file.

Configure
---------
In config/env.php add follow code: 
```php
<?php

$view = [];
if (php_sapi_name() != 'cli')
{
     $view = [
                'class' => '\cheerymagic\yii\minify\View',
                'enableMinify' => !YII_DEBUG,
                'concatCss' => true, // concatenate css
                'minifyCss' => true, // minificate css
                'concatJs' => true, // concatenate js
                'minifyJs' => true, // minificate js
                'minifyOutput' => true, // minificate result html page
                'webPath' => '@web', // path alias to web base
                'basePath' => '@webroot', // path alias to web base
                'minifyPath' => '@webroot/minify', // path alias to save minify result
                'jsPosition' => [ \yii\web\View::POS_END ], // positions of js files to be minified
                'forceCharset' => 'UTF-8', // charset forcibly assign, otherwise will use all of the files found charset
                'expandImports' => true, // whether to change @import on content
                'compressOptions' => ['extra' => true], // options for compress
                'excludeFiles' => [
                    'jquery.js', // exclude this file from minification
                    'app-[^.].js', // you may use regexp
                 ],
                 'excludeBundles' => [
                    \app\helloworld\AssetBundle::class, // exclude this bundle from minification
                 ],
            ];
}

return [
	// ...
	'components' => [
		// ...
		'view' => $view
	]
];
```
Forked From
---------
[rmrevin/yii2-minify-view](https://github.com/rmrevin/yii2-minify-view)
