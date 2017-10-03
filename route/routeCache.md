# 路由快取

執行 `php artisan route::cache` 可以將 route 解析的結果儲存起來，大概可以節省解析的零點幾秒時間。

要快取路由檔案，不能使用 closure 的路由方式，僅僅能使用控制器函式（字串）或者資源的路由。

刪除快取的命令為 `php artisan route::clear` 。

動物書作者建議僅在正式伺服器上面使用路由快取。每次佈署新的主機時呼叫 route::cache 命令。

