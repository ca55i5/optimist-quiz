# Optimistディンギー クイズ

Optimistディンギーの帆走ルール・旗・ホイッスル・セッティングなどを楽しく学べるクイズアプリです。

## アクセス

GitHub Pagesで公開中：https://[ユーザー名].github.io/optimist-quiz/

## 内容

全70問、10カテゴリ：

- ⚖️ ルール（RRS） 8問
- 🚩 旗（テキスト） 13問
- 👀 旗を見る（ビジュアル） 12問
- 📣 ホイッスル 6問
- 🔧 セッティング基本 8問
- 📐 セッティング詳細 10問
- ⛵ 艤装・パーツ 6問
- 💨 風・操船 6問
- 🦺 安全 4問
- 📚 クラス知識 5問

## 特徴

- 漢字すべてにふりがな付き（子どもでも読める）
- URLパラメータで日本語 / 英語を切替可能（`?lang=ja` / `?lang=en`）
- カテゴリ別練習・全問シャッフル・ランダム10問の3モード
- 旗の絵をSVGで表示（実物を覚えられる）
- 解答ごとに解説付き

## ランキングを他端末で共有する設定（Firebase）

このアプリは Firebase Realtime Database 未設定時のみ、ブラウザの localStorage に保存します。
Firebase を設定すると、ランキングはクラウドに保存されて他端末共有されます。

1. Firebase プロジェクトを作成
2. Build -> Realtime Database を開いて Database を作成
3. ルールを設定（公開ランキング用途の最小構成）

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

4. Realtime Database URL を確認

例: `https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com`

5. `config.js` に Firebase 情報を設定

```js
window.OPTIMIST_QUIZ_CONFIG = {
  firebaseDatabaseUrl: 'https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com',
  cloudOnlyRanking: true
};
```

`cloudOnlyRanking: true`（デフォルト）では、Firebase 設定後に通信失敗しても localStorage へは保存しません。
つまり「ローカルではなく、共有ランキングのみ」で運用できます。

Firebase 未設定時は localStorage 保存になります。

既存の localStorage ランキングがある場合は、クラウド設定が有効になった初回アクセス時に自動で Firebase へ移行します。
全件の移行成功後に localStorage 側のランキングは自動削除されます（失敗時は削除されません）。

補足: 既存の Supabase 設定（`supabaseUrl` / `supabaseAnonKey`）も互換のため利用可能です。

## ライセンス

個人学習用。
