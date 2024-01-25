### 1. 基本的なGETルート

```php
use Illuminate\Support\Facades\Route;

Route::get('/example', function () {
    return 'Hello World';
});
```

### 2. コントローラアクションの使用

※{id}はURLパラメータ

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

RESTfull APIエンドポイントを自動で生成
以下のエンドポイントが有効になる

- GET /photos: リソースの一覧を取得（indexメソッド）
- POST /photos: 新しいリソースを作成（storeメソッド）
- GET /photos/{id}: 特定のリソースを表示（showメソッド）
- PUT/PATCH /photos/{id}: 既存のリソースを更新（updateメソッド）
- DELETE /photos/{id}: リソースを削除（destroyメソッド）
