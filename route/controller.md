# 控制器

控制器是 MVC 架構裡面 Controller 的部份。

重申一下：將邏輯都塞入控制器很方便，但是不建議這麼設計。  
比較好的方式是將控制器當作一個交通警察，由模型（model）處理邏輯，視圖（view）處理外觀

動物書建議使用 artisan 工具來生成控制器

```bash
php artisan make::controller TaskController
```

上述命令會得到一個新檔案 app/Http/Controllers/TasksController.php，內容為：

```php
<?php

namespace App\Http\Controllers

use Illuminate\Http\Request;

use App/Http/Requests

class TaskController extends controller{

}
```

然後，我們加入一個public method，功能類似 Yii2 的 action：

```php
<?php

namespace App\Http\Controllers

use Illuminate\Http\Request;

use App/Http/Requests

class TaskController extends controller{

    public function home(){
        return "Hello, world!";
    }
}
```

然後搭配一個簡單的路由

```php
Route::get('/', 'TasksController@home');
```

這樣就行了！之後訪問 / 時，就會看到 Hello, world!

## 控制器方法

```php
class TaskController extends controller{

    public function index(){
        return view('task.index')
            ->with('tasks', Task::all());
    }
}
```

這樣會載入` tasks/index.blade.php `或者 `tasks/index.php` 的 view，並傳入tasks變數。

## 取得用戶輸入

這裡先假設我們用 POST 方式取得Task的資料。資料有兩部份：標題（title）和說明（description）。

先簡單的綁定 POST 動作

```php
// routes/web.php
Route::post('tasks', 'TasksController@store');
```

從 POST 取得輸入的方法有兩種。其中一種，是下面使用的Input 介面

```php
// TasksController.php
//use Illuminate\Support\facades\Input
...
public function store(){
    $task = new Task;
    
    $task->title = Input::get('title');
    $task->description = Input::get('description');
    $task->save();

    return redirect('tasks');
}
```



