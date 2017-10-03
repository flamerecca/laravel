# 路由名稱

使用`url()` ，可以簡化視圖中的連接

```
<a href="<?php echo url('/');?>"> 
//輸出 <a href="http://myapp.com/">
```

對很長的網址，我們可以命名該路徑。

## 定義路由名稱

```php
Route::get('members/{id}', 'MembersController@show')->name('members.show');
```

存取該路由的方式為

```php
echo route('members.show', ['id' => 14]);
```

> Laravel 裡面，一般資源命名法均為\[資源名稱\(複數\)\].\[動作名稱\]，像是上面的 members.show 或者 users.comments.show

這邊建議一律使用 `route()` 來產生網址，避免使用 `url()`。

## 路由參數

傳遞的方法是在 `route()` 裡面使用陣列。

假設我們定義了一個路由`users.comments.show`為`users/{userId}/comments/{commentId}`，方法有以下幾種：

* `route('users.comments.show', [1, 2]);`
  * 回傳網址 http://myapp.com/users/1/commenets/2
* `route('users.comments.show', ['userId' => 1, 'commentId' => 2]);`
  * 回傳網址 http://myapp.com/users/1/commenets/2
* `route('users.comments.show', ['commentId' => 2, 'userId' => 1]);`
  * 回傳網址 http://myapp.com/users/1/commenets/2
* `route('users.comments.show', ['userId' => 1, 'commentId' => 2, 'opt' => 3]);`
  * 回傳網址 http://myapp.com/users/1/commenets/2?opt=3

## 自我複習

* `url()` 的使用方式？
* 定義路由名稱的方式？
* 透過名稱存取的方式？
* 路由參數的傳遞方式？
  * 如果不命名參數會？
  * 如果多傳參數會？









