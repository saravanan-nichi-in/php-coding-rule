# Coding Rule
Coding rule for Laravel Framework
Last updated at 19 Jul 2021

# Table of Contents

1. [Validation](https://github.com/saravanan-nichi-in/laravel-coding-rule#validation)
2. [Utility](https://github.com/saravanan-nichi-in/laravel-coding-rule#utility)
3. [Tools](https://github.com/saravanan-nichi-in/laravel-coding-rule#tools)
4. [Documentation](https://github.com/saravanan-nichi-in/laravel-coding-rule#documentation)
5. [Naming](https://github.com/saravanan-nichi-in/laravel-coding-rule#naming)
6. [Rules](https://github.com/saravanan-nichi-in/laravel-coding-rule#rules)
7. [Helper](https://github.com/saravanan-nichi-in/laravel-coding-rule#helper)
8. [Routing](https://github.com/saravanan-nichi-in/laravel-coding-rule#routing)
9. [Middleware](https://github.com/saravanan-nichi-in/laravel-coding-rule#middleware)
10. [Request](https://github.com/saravanan-nichi-in/laravel-coding-rule#request-1)
11. [Views](https://github.com/saravanan-nichi-in/laravel-coding-rule#views)
12. [Model](https://github.com/saravanan-nichi-in/laravel-coding-rule#model)


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

## Documentation

All code must be documented with inline comments. 

### Class

Classes have their own documentation block describing the classes purpose. 

#### Example :

```php
	/**
	 * First sentence is short description. Then you can write more, just as you like
	 *
	 * Here may follow some detailed description about what the class is for.
	 *
	 * Paragraphs are separated by an empty line.
	 *
	 */
	class SomeClass
	{
	 ...
	}
```

### Properties

Properties of class such as variables, constants, includes should be documented as well.

#### Example :

```php
	/**
	 * A short description, very much recommended
	 *
	 * @var string
	 */
	protected $title = 'Untitled';
```

### Method

Parameters and the return value should only be documented 

#### Example :

```php
	/**
	 * A description for this method
	 *
	 * Paragraphs are separated by an empty line.
	 *
	 * @param Post $post Some description for the $post parameter
	 * @param string $someString Some description for the $someString parameter
	 * @return void
	 *
	 */
	public function addStringToPost(Post $post, string $someString): void
	{
	 ...
	}
```

### Testcase

Testcases need to be marked as being a test and can have some more annotations.

#### Example :

```php
	/**
	 * This method is part of the public API.
	 *
	 * @return void
	 * @api
	 */
	public function fooBar(): void
	{
	 ...
	}
```

## Naming

It is very much mandatory to maintain the consistency across the application

### Class

A class name should follow PascalCase. 

#### Bad :

```php
	class logincontroller extends Controller { }
	class loginController extends Controller { }
	class Logincontroller extends Controller { }	
```

#### Good :

```php
	class LoginController extends Controller
	{

	}
```

### Others

A list of naming conventions provided below table.

| Type | Data | Good |
|:------|:------|:------|
| Class | Singular | UserController |
| Model | Singular | User |
| Trait | adjective | Notifiable |
| Method in test class | camelCase | testGuestCannotSeeArticle |
| Route | plural | articles/1 |
| Named route | snake_case with dot notation | users.show_active |
| hasOne or belongsTo relationship | singular | articleComment |
| All other relationships | plural | articleComments |
| table | plural | article_comments |
| Pivot table | singular model names in alphabetical order | article_user |
| Table column | snake_case without model name | meta_title |
| Foreign key | singular model name with _id suffix | article_id |
| Primary key | - | id |

### Method

A method name should follow camelCase. Only the characters a-z, A-Z and 0-9 are allowed for method names.

#### Bad :

```php
	public function userregistration(){}
	public function Userregistration(){}
	public function user-registration(){}
```

#### Good :

```php
        public function userRegistration()
	{

	}
```

### Function

A function name should follow snake_case.

#### Bad :

```php
	public function abortIf(){}
	public function abortif(){}
	public function abort-If(){}
```

#### Good :

```php
        public function abort_if()
	{

	}
```

### Variable

A variable name should follow camelCase.

#### Bad :

```php
	$myfirstvariable = null;
	$Myfirstvariable = null;
	$my-first-variable = null;
```

#### Good :

```php
        $myFirstVariable = null;
```

### Model

A model property name should follow snake_case.

#### Bad :

```php
	$model->modelProperty;
	$model->model-property;
	$model->ModelProperty;
```

#### Good :

```php
        $model->model_property
```

### Constant

A constant name should follow UPPERCASE. Words can be separated by underscore ( _ ).

#### Bad :

```php
	myconstant = null;
	MyConstant = null;
	My-Constant = null;
	my-constant = null;	
```

#### Good :

```php
        MY_CONSTANT = null;
```

### Filename

A filename name should follow UpperCamelCase.

#### Bad :

```php
	app/Http/Controllers/Auth/myLoginController.php
	app/Http/Controllers/Auth/mylogincontroller.php	
	app/Http/Controllers/Auth/my-login-controller.php	
```

#### Good :

```php
	app/Http/Controllers/Auth/MyLoginController.php
```

### Others

A list of filenaming conventions provided below table.

| Type | Data | Good |
|:------|:------|:------|
| Class | PascalCase | UserController.php, User.php |
| View | kebab-case | show-filtered.blade.php |
| Config | kebab-case | google-calendar.php |
| Migration | snake_case | 2017_01_01_000000_create_articles_table.php |


## Rules

Rules defined here to follow

### Single Responsibility

A class and a method should have only one responsibility.

#### Bad :

```php
   public function getFullNameAttribute()
    {
        if (auth()->user() && auth()->user()->hasRole('client') && auth()->user()->isVerified()) {
            return 'Mr. ' . $this->first_name . ' ' . $this->middle_name . ' ' . $this->last_name;
        } else {
            return $this->first_name[0] . '. ' . $this->last_name;
        }
    }
```

#### Good :

```php
    public function getFullNameAttribute()
    {
        return $this->isVerifiedClient() ? $this->getFullNameLong() : $this->getFullNameShort();
    }

    public function isVerifiedClient()
    {
        return auth()->user() && auth()->user()->hasRole('client') && auth()->user()->isVerified();
    }

    public function getFullNameLong()
    {
        return 'Mr. ' . $this->first_name . ' ' . $this->middle_name . ' ' . $this->last_name;
    }

    public function getFullNameShort()
    {
        return $this->first_name[0] . '. ' . $this->last_name;
    }
```

### Business logic should be in service class

A controller must have only one responsibility, so move business logic from controllers to service classes.

#### Bad :

```php
   public function store(Request $request)
    {
        if ($request->hasFile('image')) {
            $request->file('image')->move(public_path('images') . 'temp');
        }

        ....
    }
```

#### Good :

```php
    public function store(Request $request)
    {
        $this->articleService->handleUploadedImage($request->file('image'));

        ....
    }

    class ArticleService
    {
        public function handleUploadedImage($image)
        {
            if (!is_null($image)) {
                $image->move(public_path('images') . 'temp');
            }
        }
    }
    
```

### Don’t repeat yourself (DRY)

Reuse code when you can. SRP is helping you to avoid duplication. Also, reuse Blade templates, use Eloquent scopes etc.

#### Bad :

```php
   public function getActive()
    {
        return $this->where('verified', 1)->whereNotNull('deleted_at')->get();
    }

    public function getArticles()
    {
        return $this->whereHas('user', function ($q) {
                $q->where('verified', 1)->whereNotNull('deleted_at');
            })->get();
    }
```

#### Good :

```php
    public function scopeActive($q)
    {
        return $q->where('verified', 1)->whereNotNull('deleted_at');
    }

    public function getActive()
    {
        return $this->active()->get();
    }

    public function getArticles()
    {
        return $this->whereHas('user', function ($q) {
                $q->active();
            })->get();
    }
```

### Fat models, skinny controllers

Put all DB related logic into Eloquent models or into Repository classes if you’re using Query Builder or raw SQL queries.

#### Bad :

```php
   public function index()
    {
        $clients = Client::verified()
            ->with(['orders' => function ($q) {
                $q->where('created_at', '>', today()->subWeek());
            }])
            ->get();

        return view('index', ['clients' => $clients]);
    }
```

#### Good :

```php
    public function index()
    {
        return view('index', ['clients' => $this->client->getWithNewOrders()]);
    }

    class Client extends Model
    {
        public function getWithNewOrders()
        {
            return $this->verified()
                ->with(['orders' => function ($q) {
                    $q->where('created_at', '>', today()->subWeek());
                }])
                ->get();
        }
    }
```

### Comment your code, but prefer descriptive method and variable names over comments

Put all DB related logic into Eloquent models or into Repository classes if you’re using Query Builder or raw SQL queries.

#### Bad :

```php
  if (count((array) $builder->getQuery()->joins) > 0)
```

#### Good :

```php
    if ($this->hasJoins())
```

### Prefer to use Eloquent over using Query Builder and raw SQL queries. Prefer collections over arrays

Eloquent allows you to write readable and maintainable code. Also, Eloquent has great built-in tools like soft deletes, events, scopes etc.

#### Bad :

```php
   SELECT *
    FROM `articles`
    WHERE EXISTS (SELECT *
                  FROM `users`
                  WHERE `articles`.`user_id` = `users`.`id`
                  AND EXISTS (SELECT *
                              FROM `profiles`
                              WHERE `profiles`.`user_id` = `users`.`id`)
                  AND `users`.`deleted_at` IS NULL)
    AND `verified` = '1'
    AND `active` = '1'
    ORDER BY `created_at` DESC
```

#### Good :

```php
    Article::has('user.profile')->verified()->latest()->get();
```

### Mass assignment

Eloquent allows you to write readable and maintainable code. Also, Eloquent has great built-in tools like soft deletes, events, scopes etc.

#### Bad :

```php
   $article = new Article;
    $article->title = $request->title;
    $article->content = $request->content;
    $article->verified = $request->verified;
    // Add category to article
    $article->category_id = $category->id;
    $article->save();
```


#### Good :

```php
    $category->article()->create($request->all());
```

### Use config and language files, constants instead of text in the code

Put all DB related logic into Eloquent models or into Repository classes if you’re using Query Builder or raw SQL queries.

#### Bad :

```php
    public function isNormal()
    {
        return $article->type === 'normal';
    }

    return back()->with('message', 'Your article has been added!');
```

#### Good :

```php
    public function isNormal()
    {
        return $article->type === Article::TYPE_NORMAL;
    }

    return back()->with('message', __('app.article_added'));
```

### Use IoC container or facades instead of new Class

new Class syntax creates tight coupling between classes and complicates testing. Use IoC container or facades instead.

#### Bad :

```php
    $user = new User;
    $user->create($request->all());
```

#### Good :

```php
    public function __construct(User $user)
    {
        $this->user = $user;
    }

    $this->user->create($request->all());
```

### Do not get data from the ".env"-file directly

Pass the data to config files instead and then use the config() helper function to use the data in an application.

#### Bad :

```php
    $apiKey = env('API_KEY');
```

#### Good :

```php
    // config/api.php
    'key' => env('API_KEY'),

    // Use the data
    $apiKey = config('api.key');
```



## Helper

Try to consume helper function as possible.

### Session

#### Bad :

```php
$request->session()->get('cart');
Session::get('cart')
$request->session()->get('cart')

Session::put('cart', $data)
```

#### Good :

```php
session('cart');

session(['cart' => $data])
```

### Request

#### Bad :

```php
$request->input('name');
Request::get('name')
$request->has('value') ? $request->value : 'default';
```

#### Good :

```php
$request->name;
request('name')
$request->get('value', 'default')
```

### Redirect

#### Bad :

```php
return Redirect::back()
```

#### Good :

```php
return back()
```

### View

#### Bad :

```php
return view('index')->with('title', $title)->with('client', $client)
```

#### Good :

```php
return view('index', compact('title', 'client'))
```

### Carbon

#### Bad :

```php
Carbon::now()
Carbon::today()
```

#### Good :

```php
now()
today()
```


### Eloquent

#### Bad :

```php
->where('column', '=', 1)
->orderBy('created_at', 'desc')
->orderBy('age', 'desc')
->orderBy('created_at', 'asc')
->select('id', 'name')->get()
->first()->name
```

#### Good :

```php
->where('column', 1)
->latest()
->latest('age')
->oldest()
->get(['id', 'name'])
->value('name')
```


## Routing

### Prefix grouping

#### Bad :

```php
Route::get('/api/user', 'UserController@index');
Route::get('/api/post', 'PostController@index');
```

#### Good :

```php
Route::prefix('api')->group(function(){

	Route::get('/user', 'UserController@index');
	Route::get('/post', 'PostController@index');

});
```

## Middleware

### Middleware Grouping

#### Bad :

```php
Route::get('/user', 'UserController@index')->middleware('auth');
Route::get('/post', 'PostController@index')->middleware('auth');
```

#### Good :

```php
Route::middleware(['auth'])->group(function(){

	Route::get('/user', 'UserController@index');
	Route::get('/post', 'PostController@index');

});
```

### Nested Middleware Grouping

#### Bad :

```php
Route::get('/dashboard', 'DashboardController@index')->middleware(['auth','admin']);
Route::get('/user', 'UserController@index')->middleware(['auth','user']);
Route::get('/post', 'PostController@index')->middleware(['auth','user']);
```

#### Good :

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

## Request

### Validation

Move validation from controllers to Request classes.

#### Bad :

```php
   public function store(Request $request)
    {
        $request->validate([
            'title' => 'required|unique:posts|max:255',
            'body' => 'required',
            'publish_at' => 'nullable|date',
        ]);

        ....
    }
```

#### Good :

```php
    public function store(PostRequest $request)
    {
        ....
    }

    class PostRequest extends Request
    {
        public function rules()
        {
            return [
                'title' => 'required|unique:posts|max:255',
                'body' => 'required',
                'publish_at' => 'nullable|date',
            ];
        }
    }
```

### Fillable and Guarded

Try to implement guarded instead of Fillable.

#### Bad :

```php
   protected $fillable=[
        'id', 'quotation_id', 'order_loss_date', 'scheduled_delivery_date','expected_return_date',
        'created_operator_id', 'payment_type', 'billing_start', 'billing_end', 'unbilled_confirmation',
        'remarks', 'created_at', 'updated_operator_id', 'updated_at'
    ];
```

#### Good :

```php
    protected $guarded = ['project_id'];
```

## Views

### Blade

Do not execute queries in Blade templates and use eager loading (N + 1 problem). For 100 users, 101 DB queries will be executed.

#### Bad :

```php
   @foreach (User::all() as $user)
	
    @endforeach
```

#### Good :

```php
    $users = User::with('profile')->get();

    ...

    @foreach ($users as $user)

    @endforeach
```

## Model

### Query Scopes

Query scopes are useful to make code more elegant.

#### without Query Scope :

```php

   $active_administrators = User::where('active', '=', 1)->where('is_admin', '=', 1)->get();
   
```

#### with Query Scope :

```php
	public function scopeActive($query)
	{
	    return $query->where('active', '=', 1);
	}

	public function scopeAdmin($query)
	{
	    return $query->where('is_admin', '=', 1);
	}
	
	$active_administrators = User::active()->admin()->get();
```
