# Coding Rule
Coding rule for Laravel Framework
Last updated at 21 Jun 2021

# Table of Contents

1. [Routing](https://github.com/saravanan-nichi-in/laravel-coding-rule#routing)
2. [Middleware](https://github.com/saravanan-nichi-in/laravel-coding-rule#middleware)


## Routing

## Prefix grouping

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

## Middleware Grouping

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

## Nested Middleware Grouping

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
