<div style="text-align: right"><a href="../../en/latest/installation.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/installation.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/installation.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/installation.html">🇯🇵 日本語</a></div>

# インストール

quardCRT は Windows、macOS、Linux 向けのパッケージを提供しています。公式アプリストアに登録されているプラットフォームでは、そこからのインストールが最も簡単です。アプリストアが利用できない場合は、GitHub、Gitee、SourceForge からリリースパッケージを取得してください。

## ダウンロード前の目安

- quardCRT をそのまま使いたいだけなら、OS と CPU アーキテクチャに合ったパッケージを選びます。
- Windows でネイティブプラグインをビルドまたは利用する予定がある場合は、一般的な MSVC ツールチェーンとランタイムを合わせやすい `MSVC` 版を推奨します。
- Apple Silicon を使っている場合は、macOS の `arm64` パッケージを選びます。
- Linux では、単一ファイルで持ち運びやすい `AppImage` と、Debian 系ディストリビューション向けの `deb` パッケージを選べます。

## アプリストア

quardCRT は現在、以下のアプリストアで利用できます。

- [![Microsoft Store](https://get.microsoft.com/images/ja%20dark.svg)](https://apps.microsoft.com/detail/quardCRT/9p6102k9qb3t?mode=direct)
- [Spark Store](https://www.spark-app.store/store/application/quardcrt)
- Deepin Store

ここに掲載されていないプラットフォームや配布元では、以下のリリースパッケージを利用してください。

## ダウンロード

### すべてのプラットフォーム

最新版のダウンロードには、次のリリースページを利用できます。

- [GitHub Releases](https://github.com/QQxiaoming/quardCRT/releases)
- [Gitee Releases](https://gitee.com/QQxiaoming/quardCRT/releases)
- [SourceForge](https://sourceforge.net/projects/quardcrt/files/)

リリースアセットでは次の形式を提供しています。

- Windows:
    - `quardCRT_windows_Vxxx_x86_64_setup.exe`
    - `quardCRT_windows_Vxxx_x86_64_msvc_setup.exe`
- macOS:
    - `quardCRT_macos_Vxxx_x86_64.dmg`
    - `quardCRT_macos_Vxxx_arm64.dmg`
- Linux:
    - `quardCRT_Linux_Vxxx_x86_64.AppImage`
    - `quardCRT_Linux_Vxxx_x86_64.deb`
- ソースコード:
    - `quardCRT_Vxxx_source.tar.gz`
    - `quardCRT_Vxxx_source.zip`

### Windows

Windows では `quardCRT_windows_Vxxx_x86_64_setup.exe` または `quardCRT_windows_Vxxx_x86_64_msvc_setup.exe` を選びます。

- `setup.exe`: MinGW ビルド。通常利用向けで互換性が高い構成です。
- `msvc_setup.exe`: MSVC ビルド。MSVC でビルドしたプラグインやネイティブコンポーネントとのランタイム整合性が必要な場合に向いています。

#### インストール

インストーラを起動し、セットアップウィザードに従って進めます。

1. 言語を選択して `OK` をクリックします。

![Windowsインストール例](./img/installation_4.png)

2. `次へ` をクリックします。

![Windowsインストール例](./img/installation_5.png)

3. インストール先を選択して `次へ` をクリックします。

![Windowsインストール例](./img/installation_6.png)

4. デスクトップショートカットを作成するか選び、`次へ` をクリックします。

![Windowsインストール例](./img/installation_7.png)

5. `インストール` をクリックします。

![Windowsインストール例](./img/installation_8.png)

6. `完了` をクリックします。

![Windowsインストール例](./img/installation_9.png)

インストール後は、スタートメニューまたは作成したデスクトップショートカットから quardCRT を起動できます。

### macOS

Intel Mac では `quardCRT_macos_Vxxx_x86_64.dmg`、Apple Silicon Mac では `quardCRT_macos_Vxxx_arm64.dmg` を選んでください。

#### インストール

DMG を開き、通常の macOS アプリと同じ手順でインストールします。

1. `quardCRT` アイコンをダブルクリックします。
2. `quardCRT` アイコンを `Applications` フォルダへドラッグします。

![macOSインストール例](./img/installation_3.png)

> 注: 現在配布している macOS 向けプリビルドパッケージは Apple 署名されていません。初回起動時に未確認の開発元として警告される場合があります。配布物を信頼できる場合は、`xattr -cr /Applications/quardCRT.app` を実行して quarantine 属性を削除できます。信頼できない場合は警告を回避せず、代わりにソースからビルドしてください。

### Linux

Linux では次のいずれかを選べます。

- `quardCRT_Linux_Vxxx_x86_64.AppImage`: 単一実行ファイルとして持ち運べるポータブル形式
- `quardCRT_Linux_Vxxx_x86_64.deb`: Debian、Ubuntu、Deepin など Debian 系ディストリビューション向け

#### インストール

- AppImage

AppImage はインストール不要です。実行権限を付与してそのまま起動できます。

```bash
chmod +x quardCRT_Linux_Vxxx_x86_64.AppImage
./quardCRT_Linux_Vxxx_x86_64.AppImage
```

- deb

Debian パッケージは GUI パッケージマネージャでもコマンドラインでも導入できます。

GUI でインストールする場合:

1. パッケージをダブルクリックします。
2. `インストール` をクリックします。

![deb パッケージインストール例 1](./img/installation_1.png)

3. パスワードを入力して `認証` をクリックします。
4. `閉じる` をクリックします。

![deb パッケージインストール例 2](./img/installation_2.png)

コマンドラインでインストールする場合:

```bash
sudo dpkg -i quardCRT_Linux_Vxxx_x86_64.deb
```

依存関係の不足が報告される場合は、パッケージマネージャ経由で解決できます。たとえば:

```bash
sudo apt install ./quardCRT_Linux_Vxxx_x86_64.deb
```

## 初回起動

インストール後の基本手順は次のとおりです。

1. quardCRT を起動します。
2. パッケージ側で言語選択が促された場合は、利用したい言語を選びます。
3. セッションマネージャまたはクイック接続から接続を作成します。
4. テーマ、フォント、転送先、詳細設定を変えたい場合は `オプション > グローバルオプション` を開きます。

続きは [使い方ガイド](./usage.md) を参照してください。
