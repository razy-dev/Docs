# Laravel Authenticate

## Authenticate Prodess
### Create AuthManager
* set userResoler
  + set guard
    - resolve guard
      - create session guard, if set session driver
      ```php
      AuthManager::createSessionDriver( $name, $config )
      {
        // Create Provider
        $provider = $this->createUserProvider( $config['provider'] ?? null );

        // Create Guard
        $guard = new SessionGuard( $name, $provider, $this->app['session.store'] );

        ...

        return $guard;
      }
      ```
      - create token guard, if set token driver
      ```php
      AuthManager::createTokenDriver( $name, $config )
      {
        $guard = new TokenGuard(
            $this->createUserProvider( $config['provider'] ?? null ),
            $this->app['request']
        );
        ...
        return $guard;
      }
      ```
      - create custom guard
      ```php
      AuthServiceProvider::boot() {
        ...
        // AuthManager::callCustomCreator( $name, array $config )
        // call closer for guard creation, defined at \app\Providers\AuthServiceProvider.php
        Auth::extend( 'ci_session', function ( $app, $name, $config ) {
          $guard = new CUSTOM_GUARD(
            Auth::createUserProvider( $config['provider'] ),
            $app->make( 'request' )
          )
          ...
          return $guard;
        } )
      }
      ```
    - create provider
      - createDatabaseProvider
        - with TABLE_NAME at config/auth.php
      - createEloquentProvider
        - with MODEL_NAME at config/auth.php
      - customProviderCreators
      ```php
      AuthServiceProvider::boot() {
        // add custom guard provider
        Auth::provider('mongo', function ($app, array $config) {
          return new MongoUserProvider($app->make('App\Models\Auth\User'));
        });
      }
      ```

### AuthManager Prodess
* Auth::user();
  + AUTH_GUARD->user();
  ```php
  AUTH_GUARD::user()
  {
    $id = ...;
    $user = $this->provider->retrieveById($id)
    ...
    return $user;
  }
  ```

---
## Custom Authenticate
### Auth Config
* /config/auth.php
```php
'defaults'  => [
  'guard'     => 'custom', // set default guard
  'passwords' => 'users',
],

'guards'    => [
  'web'    => [
    'driver'   => 'session',
    'provider' => 'users',
  ],

  'api'    => [
    'driver'   => 'token',
    'provider' => 'users',
  ],

  // define custom guard confg
  'custom' => [
    'driver'   => 'ci_session',
    'provider' => 'members',
  ],
],

'providers' => [
  'users'   => [
      'driver' => 'eloquent',
      'model'  => App\User::class,
  ],

  // 'users' => [
  //     'driver' => 'database',
  //     'table' => 'users',
  // ],

  // define custom guard provider
  'members' => [
      'driver' => 'eloquent',
      'model'  => App\Models\Member::class,
  ],
],
```
### Register Custom guard to AuthManager
* \app\Providers\AuthServiceProvider.php
```php
  public function boot()
  {
    $this->registerPolicies();

    /**
     * Register Custom guard to AuthManager
     *  Auth::extend( CUSTOM_DRIVER, function ( $app, $name, array $config ) {
     *      return new CUSTIM_GUARD( Auth::createUserProvider( $config['provider'] ), $app->make( 'request' ) );
     *  } );
     */
    Auth::extend( 'ci_session', function ( $app, $name, array $config ) {
        return new CISessionGuard( Auth::createUserProvider( $config['provider'] ), $app->make( 'request' ) );
    } );
  }
```

### CUSTOM_GUARD
```php
use Illuminate\Contracts\Auth\Guard;
use Illuminate\Contracts\Auth\StatefulGuard;

class CUSTOM_GUARD implements Guard | StatefulGuard {

  public function __construct($name,
                                UserProvider $provider,
                                Session $session,
                                Request $request = null)
  {
      $this->name = $name;
      $this->session = $session;
      $this->request = $request;
      $this->provider = $provider;
  }

  // Guard Interface
  public function check():bool;
  public function guest():bool;
  public function user():Authenticatable;
  public function id():int;
  public function validate(array $credentials = []):bool;
  public function setUser(Authenticatable $user):void;

  // StatefulGuard Interface
  public function attempt(array $credentials = [], $remember = false):bool;
  public function once(array $credentials = []):bool;
  public function login(Authenticatable $user, $remember = false):void;
  public function loginUsingId($id, $remember = false):Authenticatable;
  public function onceUsingId($id):bool;
  public function viaRemember():bool;
  public function logout():void;
}
```

### CUSTOM_PROVIDER
```php
use Illuminate\Contracts\Auth\UserProvider;

class CUSTOM_PROVIDER implements UserProvider {

  public function __construct( HasherContract $hasher, $model )
  {
      $this->model  = $model;
      $this->hasher = $hasher;
      \Log::debug( 'EloquentUserProvider::__construct', [$model] );
  }

  public function retrieveById($identifier):Authenticatable;
  public function retrieveByToken($identifier, $token):Authenticatable;
  public function updateRememberToken(Authenticatable $user, $token):void;
  public function retrieveByCredentials(array $credentials):Authenticatable;
  public function validateCredentials(Authenticatable $user, array $credentials):bool;
}
```

### CUSTOM_MODEL
```php
use Illuminate\Contracts\Auth\Authenticatable;

class CUSTOM_MODEL implements Authenticatable {
  public function getAuthIdentifierName():string;
  public function getAuthIdentifier():mixed;
  public function getAuthPassword():string;
  public function getRememberToken():string;
  public function setRememberToken($value):void;
  public function getRememberTokenName():string;
}
```
