### 1. 基本的なGETルート

```php
use Illuminate\Support\Facades\Route;

Route::get('/example', function () {
    return 'Hello World';
});
```

### 2. コントローラアクションの使用

```php
use App\Http\Controllers\UserController;
use Illuminate\Support\Facades\Route;

Route::get('/user/{id}', [UserController::class, 'show']);
```

### 3. 名前付きルート

```php
Route::get('/user/profile', [UserProfileController::class, 'show'])->name('profile');
```

### 4. ミドルウェアを使用したルート

```php
Route::middleware(['auth'])->group(function () {
    Route::get('/dashboard', function () {
        // 認証済みユーザーのみアクセス可能
    });
});
```

### 5. リソースコントローラ

```php
use App\Http\Controllers\PhotoController;
use Illuminate\Support\Facades\Route;

Route::resource('photos', PhotoController::class);
```

これらの例は、Laravel 9でのルーティングの基本的な構文を示しています。Laravelのバージョンによっては、特定の機能や構文が異なる場合があるので、公式ドキュメントを参照して、使用しているバージョンに合った正確な情報を確認することが重要です。
