# Laravel Process

## 1. /public/index.php
### 1.1. Register The Auto Loader
```php
require __DIR__.'/../vendor/autoload.php';
```
### 1.2 Turn On The Lights
```php
$app = require_once __DIR__.'/../bootstrap/app.php';
```
> @see 2.1 /bootstrap/app.php

### 1.3 Run The Application
```php
$kernel = $app->make(Illuminate\Contracts\Http\Kernel::class);

$response = $kernel->handle(
    $request = Illuminate\Http\Request::capture()
);

$response->send();

$kernel->terminate($request, $response);
```

---
## 2. /bootstrap/app.php
### 2.1 Create The Application
```php
$app = new Illuminate\Foundation\Application(
    $_ENV['APP_BASE_PATH'] ?? dirname(__DIR__)
);
```
> ```php
> class Application extends Container implements ApplicationContract, HttpKernelInterface
> ```
> * bind()
> * make()

### 2.2 Bind Important Interfaces
```php
$app->singleton(
    Illuminate\Contracts\Http\Kernel::class,
    App\Http\Kernel::class
);
```
> ```php
> class Kernel extends HttpKernel
> {
>   //
>   protected $middleware = [
>     \App\Http\Middleware\CheckForMaintenanceMode::class,
>     \Illuminate\Foundation\Http\Middleware\ValidatePostSize::class,
>     \App\Http\Middleware\TrimStrings::class,
>     \Illuminate\Foundation\Http\Middleware\ConvertEmptyStringsToNull::class,
>     \App\Http\Middleware\TrustProxies::class,
>   ];
> }
> ```

```php
$app->singleton(
    Illuminate\Contracts\Console\Kernel::class,
    App\Console\Kernel::class
);
```

```php
app->singleton(
    Illuminate\Contracts\Debug\ExceptionHandler::class,
    App\Exceptions\Handler::class
);
```

### 2.3 Return The Application
```php
return $app;
```