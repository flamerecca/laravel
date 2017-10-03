# 路由

基本範例為

```php
//routes/web.php 

Route::get('/', function () {  
    return 'Hello, world!';  
});
```

裡面使用回傳匿名函式（closure）的方式，來讓其他程式碼知道要做什麼事情。

## 路由動詞

對應常見的

* GET
* POST
* PUT
* DELETE

等等需求。可以使用

* Route::get
* Route::post
* Route::put
* Route::delete

特殊一點的用法有

* Route::any：對應所有的 request 形式
* Route::match：選擇部份 request 使用
  像是 `Route::match(['get', 'post'], '/', function(){} );`

## 字串取代 closure

用法為

```php
Route::get('/', 'WelcomeController@index')
```

會呼叫 `WelcomeController` 的 `index()` 函式。

## 路由參數

用法為

```php
Route::get('/user/{id}/', function ($id){} );
```

可以使用多個參數，像是

```php
Route::get('/user/{id}/comments/{commentId}', function (
    $theActualUserId,//對應{id}
    $theActualCommentId//對應{commentId}
){} );
```

其匹配的方式為順序，所以可以使用不同名稱。

但是建議使用相同名稱如下：

```php
Route::get('/user/{id}/comments/{commentId}', function (
    $id,
    $commentId
){
    //...
});
```

### 選用

如果參數後面加上問號，會變成選用。  
這時候對應變數必須要加上一個預設值，不然邏輯會有錯誤。

```php
Route::get('/user/{id?}/', function ($id= 'default'){
    //前面沒有預設值的話，這裡面的$id就不知道是多少了
});
```

### 正規表示

可以使用正規表示來對路由參數進行限制

```php
Route::get('/user/{id}/', function ($id){
})->where('id', '[0-9]+');

Route::get('/user/{username}/', function ($username){
})->where('username', '[A-Za-z]+');

Route::get('/post/{id}/{slug}', function ($username){

})->where(['id'=>'[0-9]+', 'slug'=>'[A-Za-z]+']);//用陣列處理
```

由上往下進行匹配，如果全部條件均不符合，回傳 404 錯誤。





