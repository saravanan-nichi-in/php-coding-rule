# Coding Rule
Coding rule for Laravel Framework
Last updated at 21 Jun 2021

# Table of Contents

1. [Routing](https://github.com/saravanan-nichi-in/laravel-coding-rule#routing)
2. [Middleware](https://github.com/saravanan-nichi-in/laravel-coding-rule#middleware)


## Routing

### Grouping Routes

#### Do's

```
Route::prefix(‘api’)->group(function(){

	Route::get(‘/user’, UserController@index);
	Route::get(‘/post’, PostController@index);

});
```


#### Don't

```
Route::get(‘/api/user’, UserController@index);
Route::get(‘/api/post’, PostController@index);
```
