# paper2html

[![pypi](https://img.shields.io/pypi/v/paper2html.svg)](https://pypi.python.org/pypi/paper2html)
[![License: GPL](https://img.shields.io/badge/License-GPL-yellow.svg)](https://opensource.org/licenses/GPL)
[![Python Version](https://img.shields.io/pypi/pyversions/Django.svg)](https://github.com/ktaaaki/paper2html)
[![TravisCI](https://travis-ci.org/masa-su/paper2html.svg?branch=master)](https://github.com/ktaaaki/paper2html)
[![Downloads](https://pepy.tech/badge/paper2html)](https://pepy.tech/project/paper2html)

It will convert paper pdf to html.
２段組の論文をhtml表示するツールです．

# 導入
## paper2htmlのインストール
依存ライブラリとpaper2htmlのインストール
```
> git clone <url>
> brew install mupdf-tools
> conda install -c conda-forge poppler
> pip install -e .
```

## 使用方法
ipythonから
```
>>> import paper2html
>>> paper2html.open_paper_htmls("path-to-paper-file.pdf")
```
右クリックメニューまたは自動化から

- 翻訳したいpdfを選択して，テキストファイルとして開く，を選択（右クリック＞クイックアクション，からもいける）
- `~/paper2html/downloads`にブラウザからpdfを保存する（自動的に翻訳が起動）

## ショートカットと右クリックメニューの作成（mac用）
クローンしたソースフォルダから`paper2html/open_downloaded_cache.workflow`と
`open pdf as html.workflow`をダブルクリックする．
`.zshrc`で自動的に有効になるconda環境でない場合は，
automatorからインストールされたworkflow内部のシェルスクリプトを変更してください．

ワークフローをインストールしたら，`~/paper2html/downloads`を右クリック＞サービス＞フォルダアクションを設定..を選択し，
サービスを確認
"Finder"が制限されたサービス"フォルダアクションを設定..."を使おうとしています．と出るのでサービスの実行を押し，
＋でスクリプトを追加，`open_downloaded_cache.workflow`を選択し，関連付ける，を選択する．

MacOSがCatalina以上であれば，設定＞セキュリティとプライバシー＞フルディスクアクセス　にFinder.appの追加が必要．
ワークフロー内のシェルスクリプトで(システムのpythonではなく)依存関係をインストールしたpythonを利用するため．
設定しないと`Operation is not permitted`のエラーが出るので注意．

※ `~/paper2html/downloads`のファイルは容量制限を超えると自動削除されるので注意．
容量はautomatorから変更可能（clean_downloadsの2番めの引数，デフォルトで1GB）