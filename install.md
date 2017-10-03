# 安裝

## 使用 Laravel 安裝工具

動物書建議使用 Laravel 安裝工具。

首先，使用 composer 安裝 Laravel 安裝工具。

```
composer global require "laravel/installer =~ 1.1"
```

安裝完畢之後，只要使用

```
laravel new projectName
```

就可以開啟新專案

## 使用 Create-project 安裝

看起來安裝跟 Yii2 沒有差別，都是使用composer，輸入以下指令：

```
composer create-project laravel/laravel –-prefer-dist
```

然後要認laravel運作起來，輸入：

```
php artisan serve
```

應該要能看到這張圖片

![](/assets/import.png)

看到的話，就代表安裝成功了。

以下不建議使用手動安裝的作法，故不紀錄此教學。

