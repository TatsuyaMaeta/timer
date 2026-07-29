# Timer App

シンプルなリアルタイムタイマー UI と管理画面です。

- `admin.html` で Supabase へ接続し、タイマーの開始・停止・カウントモード・カウントダウン時間・ベル送信を操作できます。
- `user.html` は `timer-room` チャンネルの `timer-state` イベントを受信し、タイマー表示をリアルタイム更新します。

## 特長

- Supabase Realtime で管理者側からタイマー状態を受信
- カウントアップとカウントダウンに対応
- 残り時間 60 秒以下で注意表示
- タイムアップ時に `TIME UP` 表示とベルアニメーション
- 接続状態表示
- 画面サイズに応じた自動フォントサイズ調整

## ファイル構成

- `user.html` - パブリック表示用タイマー画面
- `admin.html` - 管理者用タイマー操作画面

## セットアップ

1. `user.html` をエディターで開く
2. ファイル先頭付近の `SUPABASE_URL` と `SUPABASE_ANON_KEY` を Supabase 管理画面の値に置き換える

```html
<script>
  var SUPABASE_URL  = 'YOUR_SUPABASE_URL';
  var SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';
</script>
```

3. ブラウザで `user.html` を開く

### `admin.html` の使い方

1. ブラウザで `admin.html` を開く
2. Supabase Project URL と Anon Key を入力して接続する
3. `カウントアップ` / `カウントダウン` を切り替え
4. カウントダウンの場合は開始時間・ベルタイミングを設定
5. `スタート` / `一時停止` / `リセット` を操作して状態を送信する

## 使い方

- `user.html` は `timer-room` チャンネルの `timer-state` イベントを受信します
- 受信したペイロード例:
  - `mode`: `up` または `down`
  - `startSec`: カウントダウン開始秒数
  - `elapsed`: 経過秒数
  - `running`: タイマー実行中フラグ
  - `bell`: ベル演出を鳴らすフラグ

## 注意点

- この HTML は Supabase のクライアントライブラリを CDN から読み込みます
- `SUPABASE_URL` / `SUPABASE_ANON_KEY` を正しく設定しないと動作しません
- 管理者側のタイマー送信ロジックは含まれていません

## ライセンス

作成者の自由にご利用ください。