.. raw:: html

   <div style="text-align: right"><a href="../../en/latest/index.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/index.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/index.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/index.html">🇯🇵 日本語</a></div>

quardCRT
----------------------------------

.. image:: https://img.shields.io/github/actions/workflow/status/qqxiaoming/quardCRT/windows.yml?branch=main&logo=data:image/svg+xml;base64,PHN2ZyByb2xlPSJpbWciIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48dGl0bGU+V2luZG93czwvdGl0bGU+PHBhdGggZD0iTTAsMEgxMS4zNzdWMTEuMzcySDBaTTEyLjYyMywwSDI0VjExLjM3MkgxMi42MjNaTTAsMTIuNjIzSDExLjM3N1YyNEgwWm0xMi42MjMsMEgyNFYyNEgxMi42MjMiIGZpbGw9IiNmZmZmZmYiLz48L3N2Zz4=
   :target: https://github.com/QQxiaoming/quardCRT/actions/workflows/windows.yml
   :alt: Windows ci
.. image:: https://img.shields.io/github/actions/workflow/status/qqxiaoming/quardCRT/linux.yml?branch=main&logo=linux&logoColor=white
   :target: https://github.com/QQxiaoming/quardCRT/actions/workflows/linux.yml
   :alt: Linux ci
.. image:: https://img.shields.io/github/actions/workflow/status/qqxiaoming/quardCRT/macos_arm64.yml?branch=main&logo=apple
   :target: https://github.com/QQxiaoming/quardCRT/actions/workflows/macos_arm64.yml
   :alt: Macos ci
.. image:: https://img.shields.io/codefactor/grade/github/qqxiaoming/quardCRT.svg?logo=codefactor
   :target: https://www.codefactor.io/repository/github/qqxiaoming/quardCRT
   :alt: CodeFactor
.. image:: https://img.shields.io/readthedocs/quardcrt.svg?logo=readthedocs
   :target: https://quardcrt.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status
.. image:: https://img.shields.io/github/license/qqxiaoming/quardCRT.svg?colorB=f48041&logo=gnu
   :target: https://github.com/QQxiaoming/quardCRT
   :alt: License
.. image:: https://img.shields.io/github/v/tag/QQxiaoming/quardCRT?filter=V*&logo=git
   :target: https://github.com/QQxiaoming/quardCRT/releases
   :alt: GitHub tag (latest SemVer)
.. image:: https://img.shields.io/github/downloads/QQxiaoming/quardCRT/total.svg?logo=pinboard
   :target: https://github.com/QQxiaoming/quardCRT/releases
   :alt: GitHub All Releases
.. image:: https://img.shields.io/github/stars/QQxiaoming/quardCRT.svg?logo=github
   :target: https://github.com/QQxiaoming/quardCRT
   :alt: GitHub stars
.. image:: https://img.shields.io/github/forks/QQxiaoming/quardCRT.svg?logo=github
   :target: https://github.com/QQxiaoming/quardCRT
   :alt: GitHub forks
.. image:: https://gitee.com/QQxiaoming/quardCRT/badge/star.svg?theme=dark
   :target: https://gitee.com/QQxiaoming/quardCRT
   :alt: Gitee stars
.. image:: https://gitee.com/QQxiaoming/quardCRT/badge/fork.svg?theme=dark
   :target: https://gitee.com/QQxiaoming/quardCRT
   :alt: Gitee forks

.. image:: ./img/social_preview.jpg
   :align: center
   :alt: quardCRT

quardCRT は、Windows、Linux、macOS 向けのクロスプラットフォームなターミナルエミュレータ兼リモートデスクトップクライアントです。プラットフォーム間で一貫した操作体験を重視しつつ、日常利用に必要な機能をまとめて提供します。たとえば、マルチタブ、セッション管理、ファイル転送、テーマ切り替え、多言語 UI、拡張可能なプラグイン機構などに対応しています。

quardCRT は、すぐに使い始められる分かりやすさを持ちながら、日常的な開発、組み込み機器のデバッグ、サーバーメンテナンス、軽量なリモートデスクトップ作業にも十分対応できることを目指して設計されています。

----------------------------------
クイックスタート
----------------------------------

1. :doc:`インストールガイド <installation>` を読み、自分のプラットフォームに合ったパッケージを選びます。
2. :doc:`使い方ガイド <usage>` でメインウィンドウの構成、クイック接続、基本操作を確認します。
3. :doc:`設定ガイド <configuration>` で外観、ターミナル挙動、転送ディレクトリ、詳細設定を調整します。

----------------------------------
quardCRT が提供するもの
----------------------------------

- Windows、Linux、macOS でほぼ同じワークフローを実現するクロスプラットフォームデスクトップクライアント
- 一般的なターミナル接続とリモートアクセスのプロトコルを 1 つのアプリに統合
- 保存済みセッション、タブ操作、分割レイアウト、フローティングウィンドウ
- SFTP、Xmodem、Ymodem、Zmodem、Kermit に対応したファイル転送
- フォント、配色、カーソル、スクロールバック、背景メディアなどのユーザー向けカスタマイズ
- 多言語 UI とプラグインによる拡張性

.. list-table:: 
   :widths: 33 33 33
   :header-rows: 0

   * - .. image:: ./img/windows.png
          :align: center
          :height: 160px
     - .. image:: ./img/macos.png
          :align: center
          :height: 160px
     - .. image:: ./img/linux.png
          :align: center
          :height: 160px
   * - Windows
     - MacOS
     - Linux

----------------------------------
特徴
----------------------------------

- **クロスプラットフォーム**: Windows、macOS、Linux
- **プロトコル**: SSH、Telnet、Serial、Local Shell、Raw Socket、Named Pipe、VNC
- **セッションワークフロー**: マルチタブ、マルチウィンドウ、分割表示、フローティングウィンドウ
- **言語**: 英語、簡体字中国語、繁体字中国語、日本語、韓国語、スペイン語、フランス語、ロシア語、ドイツ語、ポルトガル語 (ブラジル)、チェコ語、アラビア語
- **テーマ**: ライト / ダーク
- **セッション履歴**: 履歴保存とクイック検索
- **セッション管理**: セッションの作成、保存、整理、インポート、エクスポート
- **HEX 表示**: ターミナル出力を 16 進数で確認
- **ファイル転送**: SFTP、Xmodem、Ymodem、Zmodem、Kermit
- **端末カスタマイズ**: フォント、配色、カーソル、スクロールバック、背景画像や動画など

----------------------------------
特別機能
----------------------------------

- タブのフローティングプレビュー
- フローティングウィンドウサポート、タブのドラッグアンドドロップでフローティングウィンドウ
- SSH2セッションワンクリックでSFTPファイル転送ウィンドウを開く
- 作業ディレクトリブックマーク
- 自動送信
- ターミナルの背景画像はgifアニメーションとビデオをサポート
- ターミナルキーワードハイライトマッチング
- 選択したテキストの翻訳機能
- パスマッチングとワンクリック直接
- 作業パス直接
- Windowsローカルターミナルの強化（Tabキーで完全なコマンドを選択など）
- セッションのブロードキャスト
- セッション ラベル タグの色
- ブロック選択 (Shift キーを押しながらクリック) と列選択 (Alt キーを押しながら Shift キーを押しながらクリック)

----------------------------------
ドキュメントガイド
----------------------------------

- :doc:`インストール <installation>`: ダウンロード元、パッケージの選び方、プラットフォーム別の導入手順
- :doc:`使い方 <usage>`: 画面構成、最初に試す操作、メニューとツールバーの概要
- :doc:`設定 <configuration>`: グローバル設定、セッション設定、保存場所、詳細オプション
- :doc:`スクリプト <scripts>`: スクリプト機能の使い方と API 概要
- :doc:`プラグイン <plugins>`: プラグイン機構、テンプレートプロジェクト、参考例
- :doc:`よくある質問 <faq>`: ライセンス、プライバシー、よくある疑問

----------------------------------
プラグイン
----------------------------------

quardCRT は V0.4.0 からプラグインに対応しています。プラグインは Qt プラグインとして動的ライブラリの形で読み込まれます。開発用の資料、テンプレート、サンプルはプラグイン `platform <https://github.com/QuardCRT-platform>`_ を参照してください。プラグイン機構についてのアイデアや要望があれば、 `GitHub <https://github.com/QQxiaoming/quardCRT>`_ または `Gitee <https://gitee.com/QQxiaoming/quardCRT>`_ で issue や discussion を作成してください。

----------------------------------
ストアからインストール
----------------------------------

.. image:: https://get.microsoft.com/images/ja%20dark.svg
   :target: https://apps.microsoft.com/detail/quardCRT/9p6102k9qb3t?mode=direct
   :alt: Microsoft Store

- .. image:: https://www.spark-app.store/assets/favicon-96x96-BB0Q9LsV.png
   :target: https://spk-resolv.spark-app.store/?spk=spk://store/development/quardcrt
   :alt: Spark Store

----------------------------------
寄付
----------------------------------

quardCRT が役に立った場合は、寄付によって継続的な開発を支援できます。

.. list-table:: 
   :widths: 33 33 33
   :header-rows: 0

   * - .. image:: ./img/donate/paypal.jpg
          :align: center
     - .. image:: ./img/donate/alipay.jpg
          :align: center
     - .. image:: ./img/donate/wechat.jpg
          :align: center
   * - paypal
     - alipay
     - wechat

.. toctree::
   :maxdepth: 3
   :caption: 目次:

   インストール<installation.md>
   使い方<usage.md>
   設定<configuration.md>
   スクリプト<scripts.md>
   プラグイン<plugins.md>
   よくある質問<faq.md>
   貢献<contributing.md>
   更新履歴<changelog.md>
   ライセンス<license.md>
   ロードマップ<roadmap.md>
   謝辞<acknowledgements.md>
   プライバシー<privacy.md>
