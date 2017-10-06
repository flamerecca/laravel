# 視圖

視圖就是 MVC 架構裡面 View 的部份。

Laravel 裡面區分成兩種：一般 php 以及 Blade 模板。  
像是 about.php 這種名稱的檔案會使用 PHP 引擎處理，about.blade.php 則使用 Blade 引擎處理。

簡單用法

```php
return view('home');
```

或者使用 `View::make()` ，或者注入 `Illuminate\View\ViewFactory`

## 傳遞變數

```php
return view('task.index')->with('tasks', Task::all());
```

這會傳遞一個名為`tasks`的變數，內容為`Task::all()`的回傳。



