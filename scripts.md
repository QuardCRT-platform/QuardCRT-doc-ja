<div style="text-align: right"><a href="../../en/latest/scripts.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/scripts.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/scripts.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/scripts.html">🇯🇵 日本語</a></div>

# スクリプト

quardCRT は V0.5.0 からスクリプト機能に対応しています。スクリプトは Python で記述し、quardCRT の組み込み API を呼び出すことで、端末操作、ダイアログ、画面マッチング、ファイル転送ワークフローを自動化できます。

このページでは、まず日常利用向けの使い方を説明し、その後に API の概要を示します。

## スクリプトでできること

典型的な用途は次のとおりです。

- 機器やサーバーへのログイン手順を自動化する
- 特定のプロンプトが出るまで待ってから次のコマンドを送る
- テスト手順や初期化手順を自動化する
- quardCRT 内から転送や小さな補助ワークフローを起動する
- 手動操作を録画して、たたき台となるスクリプトを生成する

## 利用可否

スクリプト機能は Python サポートを含むビルドで利用できます。Python ランタイム統合が含まれていないビルドでは、スクリプト関連メニューが無効になる場合があります。

## スクリプトを実行する

UI から Python スクリプトを実行する手順は次のとおりです。

1. `Script` メニューを開きます。
2. `Run...` を選択します。
3. Python スクリプトファイルを選びます。
4. quardCRT がスクリプトを開始し、現在のスクリプトが終了またはキャンセルされるまで `Run...` は無効になります。

ファイルピッカー経由で正常に実行したスクリプトは、同じメニューからすぐ再実行できるよう最近使ったスクリプト一覧に追加されます。

## 実行中のスクリプトをキャンセルする

スクリプトが動作中の場合は、`Script` メニューのキャンセル操作で停止できます。

次のような場合に役立ちます。

- 接続先が想定どおり応答しなくなった
- 別のスクリプトを誤って起動した
- 待機時間が長すぎる

## スクリプトを記録する

quardCRT は対話的な端末操作を記録し、たたき台となる Python スクリプトを生成できます。

`Script` メニューから次を行います。

1. `Start Recording Script` を選択します。
2. 現在のターミナルセッションで操作します。
3. `Stop Recording Script...` を選択して生成された `.py` を保存します。

記録を破棄したい場合は `Cancel Recording Script` を使います。

### 記録スクリプトの生成内容

生成される Python ファイルには、通常次のようなコードが含まれます。

- `crt.Screen.Synchronous = True`
- `crt.Screen.Send(...)` による入力送信
- `crt.Screen.WaitForString(...)` または `crt.Screen.WaitForStrings(...)` によるプロンプト待ち

便利なたたき台にはなりますが、そのままで本番運用に向くとは限りません。実際には、待機条件の見直しや不要な手順の削除が必要になることがあります。

## 最近使ったスクリプト

ファイルピッカーからスクリプトを実行すると、quardCRT はそれを `Script` メニュー内の最近使ったスクリプト一覧に保存します。

この一覧を消したい場合は `Clean all recent script` を使います。

## このリポジトリに含まれるサンプルスクリプト

このリポジトリには、実行して改造できる小さなサンプルスクリプトが `test/scriptengine/` 配下に含まれています。

最初の参考として有用なのは次のスクリプトです。

- `test/scriptengine/session/prompted_ssh2.py`: ホスト、ポート、ユーザー名、パスワードの入力を促し、SSH2 で接続します
- `test/scriptengine/session/prompted_telnet_login.py`: Telnet で接続し、login、password、shell の各プロンプトを待ちながらログインシーケンスを完了します
- `test/scriptengine/screen/send_command_and_capture.py`: アクティブなセッションにコマンドを送り、プロンプトに一致するまで出力を読み取ります
- `test/scriptengine/screen/save_screen_to_file.py`: 現在表示されている画面テキストをローカルファイルに保存します
- `test/scriptengine/misc/repeat_command_logger.py`: 同じコマンドを複数回実行し、各回の出力をログファイルへ保存します
- `test/scriptengine/tab/send_to_all_sessions.py`: アクティブなタブグループ内のすべてのセッションへ同じコマンドを送信します
- `test/scriptengine/filetransfer/zmodem_upload_dialog.py`: ローカルファイルを選択して Zmodem アップロードを開始します

## 最初の例

以下は、メッセージボックスに quardCRT のバージョンを表示する最小構成のスクリプトです。

```python
import sys
from quardCRT import crt

def main():
	# Display quardCRT's version
	crt.Dialog.MessageBox("quardCRT version is: " + crt.Version)

if __name__ == '__main__':
	main()
```

これは通常の Python ファイルです。違いは、quardCRT が `quardCRT` モジュールと自動化用オブジェクトを実行時に提供する点です。

この例で行っていることは次のとおりです。

- `import sys`: コマンドライン引数取得のために `sys` を読み込みます。
- `from quardCRT import crt`: quardCRT の API を読み込みます。
- `def main():`: メイン処理を定義します。
- `# Display quardCRT's version`: 次の行の意図を示すコメントです。
- `crt.Dialog.MessageBox("quardCRT version is: " + crt.Version)`: quardCRT のバージョン情報をメッセージボックスで表示します。
- `if __name__ == '__main__':`: スクリプトがメインとして実行されたか判定します。
- `main()`: メイン処理を呼び出します。

## 実用的な自動化パターン

端末自動化では、次の流れがよく使われます。

1. アクティブな画面またはセッションを取得する。
2. `crt.Screen.Send(...)` でコマンドを送る。
3. `crt.Screen.WaitForString(...)` または `crt.Screen.WaitForStrings(...)` で次の想定プロンプトを待つ。
4. 作業完了まで繰り返す。

固定時間のスリープだけに頼るより、この方法の方が一般に安定します。

## API 概要

quardCRT の API には次の主要オブジェクトがあります。

- `crt`: quardCRT の主要 API。
- `crt.Dialog`: ダイアログ操作。
- `crt.Session`: 現在のアクティブセッション操作。
- `crt.Screen`: 現在のアクティブ画面操作。
- `crt.Window`: quardCRT ウィンドウ操作。
- `crt.Arguments`: コマンドライン引数取得。
- `crt.Clipboard`: クリップボード操作。
- `crt.FileTransfer`: ファイル転送操作。
- `crt.CommandWindow`: コマンドウィンドウ操作。
- `crt.Tab`: タブグループ管理。
