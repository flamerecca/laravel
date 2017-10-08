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



