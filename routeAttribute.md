# 路由參數

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

## 選用

如果參數後面加上問號，會變成選用。  
這時候對應變數必須要加上一個預設值，不然邏輯會有錯誤。

```php
Route::get('/user/{id?}/', function ($id= 'default'){
    //前面沒有預設值的話，這裡面的$id就不知道是多少了
});
```

## 正規表示

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

