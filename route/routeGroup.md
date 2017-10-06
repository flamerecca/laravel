# 路由群組

定義方式：

```php
Route::group([], function(){
    Route::get('hello', function(){//...});
    Route::get('world', function(){//...});
});
```

上面的定義基本上只是分類，沒做什麼事情

## 引入中介層

路由群組其中一個應用方式，是引入中介層。

```php
Route::group(['middleware' => 'auth'], function(){
    Route::get('dashboard', function(){//...});
    Route::get('account', function(){//...});
});
```

中介層的詳細應用後面會聊到。

### 控制器中引入中介層

比較建議的另一種方式，是在控制器裡面引入。這樣比起前面介紹的方式更清楚一點。

```php
class DashboardController extends Controller{
    public function __construct(){
        $this->middleware('auth');

        $this->middleware('admin-auth')->only('admin');

        $this->middleware('team-member')->except('admin');
    }
}
```

## 路徑前置詞

```php
Route::group(['prefix' => 'api'], function(){
    Route::get('/', function(){ //處理 /api });
    Route::get('users', function(){ //處理 /api/users });
});
```

## 子網域路由

```php
Route::group(['domain'=>'api.myapp.com'], function(){
    Route::get('/', function(){
        //...
    });
});
```

加入參數的方法

```php
Route::group(['domain'=>'{account}.myapp.com'], function(){
    Route::get('/', function($account){
        //...
    });
    Route::get('users/{id}', function($account, $id){
        //...
    });
});
```

## 命名空間前置詞

```php
Route::get('/', 'controllerA@index');
// APP\Http\Controllers\controllerA

Route::group(['namespace'=>'API'], function(){
    Route::get('api/', 'controllerB@index');
    // APP\Http\Controllers\API\controllerB
});
```

## 名稱前置詞

使用 as - prefix 來處理路徑名稱

```php
Route::group(['as'=>'users.', 'prefix'=>'users'], function(){
    Route::group(['as'=>'comments.', 'prefix'=>'comments'], function(){
        Route::get('{id}', function(){
            //...
        })->name('show');
    });
});
```

讓 `users/comments/5` 對應路由 `users.comments.show`



