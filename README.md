# Laravel 11 應用程式和資料庫備份

引入 spatie 的 laravel-backup 套件來擴增對應用程式和資料庫進行備份。現實的世界並不完美。當災難發生時，事情可能以多種方式出錯使情況更糟，有時是因為故意而變糟的，但往往並不是故意變糟的。一旦我們知道出錯的原因後，總是會過得很不愉快。

## 使用方式
- 打開 php.ini 檔案，啟用 PHP 擴充模組 zip，並重啟服務器。
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產⽣ Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 執行 __Artisan__ 指令的 __migrate__ 來執行所有未完成的遷移。
```sh
$ php artisan migrate
```
- 執行 __Artisan__ 指令的 __backup__ 來執行對檔案和資料庫進行備份。
```sh
$ php artisan backup:run
```

----

## 畫面截圖
![](https://i.imgur.com/sfNyPEl.png)
> 您必須先完成一次備份或還原要求後，才能進行還原

![](https://i.imgur.com/5vx5f3W.png)
> 使用電子郵件通知備份成功

![](https://i.imgur.com/HntcJDU.png)
> 取得原始資料 ZIP 壓縮檔格式後，將其保存在安全的儲存位置
