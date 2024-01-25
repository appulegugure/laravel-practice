'''php
namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Models\User;

class UserController extends Controller
{
    /**
     * ユーザーの一覧を表示します。
     */
    public function index(Request $request)
    {
        $users = User::all();
        return view('users.index', ['users' => $users]);
    }

    /**
     * 新しいユーザーを保存します。
     */
    public function store(Request $request)
    {
        // リクエストデータのバリデーション
        $validatedData = $request->validate([
            'name' => 'required|max:255',
            'email' => 'required|email',
            // その他のバリデーションルール...
        ]);

        // ユーザーモデルの作成
        $user = new User();
        $user->name = $request->name;
        $user->email = $request->email;
        // その他の属性の設定...
        $user->save();

        // リダイレクトまたはビューの表示
        return redirect()->route('users.index');
    }

    // その他のアクション...
}
'''
