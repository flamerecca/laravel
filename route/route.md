# 路由基本

基本範例為

```php
//routes/web.php 

Route::get('/', function () {  
    return 'Hello, world!';  
});
```

裡面使用回傳匿名函式（closure）的方式，來讓其他程式碼知道要做什麼事情。

> 這種方式會無法使用快取，請參考 [路由快取](//route/routeCache.md)

## 路由動詞

對應常見的

* GET
* POST
* PUT
* DELETE

> 沒有 header 和 patch

等等需求。可以使用

* Route::get\(\)
* Route::post\(\)
* Route::put\(\)
* Route::delete\(\)

特殊一點的用法有

* Route::any\(\)：對應所有的 request 
* Route::match\(\)：選擇部份 request 使用
  像是 `Route::match(['get', 'post'], '/', function(){} );`

## 字串取代 closure

用法為

```php
Route::get('/', 'WelcomeController@index')
```

會呼叫 `WelcomeController` 的 `index()` 函式。

## 自我複習

* [ ] Route::get\(\) 是什麼意思？
* [ ] Route::match\(\) 用法是？
* [ ] 'WelcomeController@index' 對應什麼函式？



