<div style="text-align: right"><a href="../../en/latest/plugins.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/plugins.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/plugins.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/plugins.html">🇯🇵 日本語</a></div>

# プラグイン

quardCRT は V0.4.0 からプラグインに対応しています。プラグインは Qt プラグインとして実装され、動的ライブラリとして読み込まれます。

このページでは、プラグインを利用するユーザー向けの説明と、プラグインを開発する方向けの説明の両方を扱います。

## ユーザー向け

プラグインは、その実装内容に応じて quardCRT を次のように拡張できます。

- メイン画面にアクションやメニューを追加する
- ターミナルのコンテキストメニューに項目を追加する
- サイドバー領域に独自のプラグインウィジェットを追加する
- SSH、シリアル、Raw Socket、VNC などの接続関連アクションを起動する

quardCRT には、プラグインの状態、互換性情報、初期化エラーを確認できるプラグイン情報ウィンドウも用意されています。

### プラグインの読み込み動作

起動時に quardCRT はプラグインディレクトリ内の同梱プラグインを読み込みます。アプリ設定で任意のプラグインディレクトリを指定している場合は、その場所からも追加で読み込めます。

プラグインを読み込めない場合、quardCRT はそれを黙って成功扱いにせず、プラグイン情報ダイアログに失敗理由を記録します。

よくある失敗理由は次のとおりです。

- プラグインのメタデータ不足
- 未対応のプラグイン API バージョン
- 初期化失敗
- quardCRT が期待するメニューまたはウィジェットのエントリポイント不足

### プラグインの有効化と無効化

プラグインの有効状態はアプリ設定に保存されます。対応プラグインはプラグイン情報ダイアログから有効化または無効化できます。

これは次のような場面で便利です。

- ファイルを削除せずに一時的にプラグインを無効化したい
- 新しいプラグインを試し、簡単に元へ戻したい
- マシンごとに異なるプラグイン構成を使い分けたい

## 開発者向け

## プラグイン開発

### API

プラグイン API 仕様は [plugininterface](https://github.com/QuardCRT-platform/plugininterface) リポジトリで管理されています。

カスタムプラグインの一般的な開発手順は次のとおりです。

- plugininterface.h ヘッダをインクルードする
- プラグインクラスを定義し、PluginInterface を継承する
- PluginInterface が要求するメソッドを実装する
- 対象プラットフォーム向けに `dll`、`so`、`dylib` などのネイティブプラグインライブラリをビルドする
- quardCRT が読み込める場所にビルド済みプラグインを配置する

実用的なプラグインは、たとえば次のような機能を持つことが多いです。

- メインメニューのアクションまたはメニュー
- サイドバーのウィジェット
- ターミナルコンテキストメニュー項目
- プラグイン用設定の読み書きフック
- `setLanguage()` や `retranslateUi()` による多言語対応

以下は最小構成の例です。

```c++
#include "plugininterface.h"

#include <QMap>
#include <QMessageBox>
#include <QDebug>

#define PLUGIN_NAME    "Hello World"
#define PLUGIN_VERSION "0.0.1"

class HelloWorld : public PluginInterface
{
	Q_OBJECT
	Q_PLUGIN_METADATA(IID "org.quardCRT.PluginInterface" FILE "../plugininterface.json")
	Q_INTERFACES(PluginInterface)

public:
	HelloWorld() : m_action(nullptr) {}
	virtual ~HelloWorld() {}

	int init(QMap<QString, QString> params, QWidget *parent) {
		foreach (QString key, params.keys()) {
			qDebug() << key << " : " << params[key];
		}
		qDebug() << "Hello World init";
		m_action = new QAction("Hello World", parent);
		connect(m_action, &QAction::triggered, [parent](){
			QMessageBox::information(parent, "Hello World", "Hello World");
		});

		return 0;
	}

	void setLanguage(const QLocale &language,QApplication *app) {Q_UNUSED(language);Q_UNUSED(app);}
	void retranslateUi() {}
	QString name() { return PLUGIN_NAME; }
	QString version() { return PLUGIN_VERSION; }

	QMap<QString,void *> metaObject() {
		QMap<QString,void *> ret;
		ret.insert("QAction", (void *)m_action);
		return ret;
	}

	QMenu *terminalContextMenu(QString selectedText, QString workingDirectory, QMenu *parentMenu) {Q_UNUSED(selectedText);Q_UNUSED(workingDirectory);Q_UNUSED(parentMenu); return nullptr;}
	QList<QAction *> terminalContextAction(QString selectedText, QString workingDirectory, QMenu *parentMenu) {Q_UNUSED(selectedText);Q_UNUSED(workingDirectory);Q_UNUSED(parentMenu); return QList<QAction *>();}

private:
	QAction *m_action;
};
```

### テンプレートプロジェクト

新しいプラグイン開発には、GitHub テンプレートプロジェクト [plugin-template](https://github.com/QuardCRT-platform/plugin-template) を推奨します。

このテンプレートには次のものが含まれています。

- プラグイン開発向けの基本プロジェクト構成
- ビルドスクリプトとプロジェクト設定
- GitHub Actions を使った CI 設定

そのため、土台作りよりもプラグインの実装に集中できます。

### 互換性に関する注意

プラグインをビルドするときは次の点に注意してください。

- 実行中の quardCRT が期待するプラグイン API バージョンに合わせる必要があります。
- プラグインはネイティブバイナリなので、コンパイラ、Qt バージョン、アーキテクチャ、プラットフォームの互換性が重要です。
- 追加の共有ライブラリに依存する場合、それらも実行時に利用可能である必要があります。

見た目は正しくても読み込めない場合、まずプラグイン情報ウィンドウを確認してください。

## 例

quardCRT には、参考になるオープンソースプラグインがいくつかあります。

- [plugin-SearchOnWeb](https://github.com/QuardCRT-platform/plugin-SearchOnWeb)

選択したテキストを Google、Bing、Baidu、GitHub などで検索するコンテキストメニューを追加します。

- [plugin-quickcomplete](https://github.com/QuardCRT-platform/plugin-quickcomplete)

ユーザー定義コマンドを現在のセッションへ素早く送信できます。

- [plugin-onestep](https://github.com/QuardCRT-platform/plugin-onestep)

SSH 接続情報の事前入力やホスト選択を効率化し、組み込み開発や機器初期化の作業を助けます。

## さらに詳しく

関連リポジトリ、テンプレート、追加情報は quardCRT プラグインプラットフォームを参照してください。

- [https://github.com/QuardCRT-platform](https://github.com/QuardCRT-platform)

プラグイン機構は今後も拡張予定です。API や拡張ポイント、開発者向けツールに関するアイデアがあれば、GitHub または Gitee で issue や discussion を作成してください。
