# Coding Rule
Coding rule for Laravel Framework
Last updated at 21 Jun 2021

# Table of Contents

1. [Validation](https://github.com/saravanan-nichi-in/laravel-coding-rule#validation)
2. [Utility](https://github.com/saravanan-nichi-in/laravel-coding-rule#utility)
3. [Tools](https://github.com/saravanan-nichi-in/laravel-coding-rule#tools)
4. [Routing](https://github.com/saravanan-nichi-in/laravel-coding-rule#routing)
5. [Middleware](https://github.com/saravanan-nichi-in/laravel-coding-rule#middleware)


## Validation

Extensions for Visual Studio code


#### PHP import checker

Purpose : This tool will report unwanted import statement to remove.

URL : https://marketplace.visualstudio.com/items?itemName=marabesi.php-import-checker

#### Mess Detector

Purpose : This tool detects method and variable declaration.

URL : https://marketplace.visualstudio.com/items?itemName=ecodes.vscode-phpmd

#### Code Spell Checker

Purpose : This tools detects wrong spelling which used for variables & methods.

URL : https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker

#### PHP CS Fixer

Purpose : This tool beautify php code.

URL : https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer


## Utility

Extensions for Visual Studio code

#### PHP Namespace Resolver

Purpose : This tool supports auto import and expand namespace

URL : https://marketplace.visualstudio.com/items?itemName=MehediDracula.php-namespace-resolver

#### PHP Debug

Purpose : This tool supports code step by step debugging.

URL : https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug

#### PHP Intellisense

Purpose : This tool supports Autocompletion and Refactoring.

URL : https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-intellisense

#### PHP Doc Blocker

Purpose : This tool  create doc block for method instantly.

URL : https://marketplace.visualstudio.com/items?itemName=neilbrayfield.php-docblocker

## Tools

Extensions for Visual Studio code

#### Sonarqube

Setup sonarqube in server to scan dynamically with the help of Jenkins.

#### PHP Code Sniffer

* Add in Composer Dev dependencies => "squizlabs/php_codesniffer": “3.*",
* Sudo rm -rf vendor
* Composer install
* vendor/bin/phpcs --standard=PSR12 path-to-directory ( windows use “\” )

#### PHP Stan

* Add in Composer Dev dependencies => composer require --dev phpstan/phpstan
* vendor/bin/phpstan analyse src tests


## Routing

### Prefix grouping

#### Don't :

```php
Route::get('/api/user', 'UserController@index');
Route::get('/api/post', 'PostController@index');
```

#### Do's :

```php
Route::prefix('api')->group(function(){

	Route::get('/user', 'UserController@index');
	Route::get('/post', 'PostController@index');

});
```

### Middleware Grouping

#### Don't :

```php
Route::get('/user', 'UserController@index')->middleware('auth');
Route::get('/post', 'PostController@index')->middleware('auth');
```

#### Do's :

```php
Route::middleware(['auth'])->group(function(){

	Route::get('/user', 'UserController@index');
	Route::get('/post', 'PostController@index');

});
```

### Nested Middleware Grouping

#### Don't :

```php
Route::get('/dashboard', 'DashboardController@index')->middleware(['auth','admin']);
Route::get('/user', 'UserController@index')->middleware(['auth','user']);
Route::get('/post', 'PostController@index')->middleware(['auth','user']);
```

#### Do's :

```php
Route::middleware(['auth'])->group(function(){
	Route::middleware(['user'])->group(function(){
		Route::get('/user', 'UserController@index');
		Route::get('/post', 'PostController@index');	
	});
	
	Route::middleware(['admin'])->group(function(){
		Route::get('/dashboard', 'DashboardController@index');
	});
});
```
