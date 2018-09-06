mkdocsをGitHub Pageで公開するサンプル
=====================================

mkdocsの出力結果をGitHub Pageで閲覧できるようにできたら便利そうなのでお試し。

## Install

まずは`mkdocs`をインストール
```sh
pip install mkdocs
```

## Create Project

```sh
# プロジェクト作成
mkdocs new test-docs
cd test-docs
```

一旦プロジェクトを作成したら、
数式やFontAwesomeなどの色々なパッケージをインストールして便利になるのでpipenvを導入しておくとよさそう。
```sh
pip install pipenv
# 初期ファイルの生成
# (Pipfileなどが生成されてパッケージ管理できるようになる)
pipenv install

pipenv install mkdocs # 一応Pipfileにも入れておく
pipenv install mkdocs-material
```

参考までに、あとGit管理するならここで
```sh
git init
```

## 起動

```sh
# 仮想環境が有効化されたシェルを起動
# (pipenvでインストールしたコマンドが使える環境)
pipenv shell
# ビルド&サーバ起動
mkdocs serve
```
または
```sh
pipenv run mkdocs serve
```
`http://127.0.0.1:8000`にブラウザでアクセスするとページが表示される。

## Hint

mkdocsは`mkdocs COMMAND --help`でもCOMMANDごとのヘルプが表示される。


## デフォルトの出力先フォルダを変更

GitHub Pageで閲覧できると便利だが、gh-pagesブランチはドキュメントが専用ブランチに分離されてしまって使いづらい気がする。(なので`gh-deploy`コマンドは使用しない)  
GitHubの設定で`docs`のみをGitHub Pageとして公開する事もできるのでこちらを活用する。
1. `docs`ディレクトリを`mkdocs`などに名称変更
2. `mkdocs.yml`でインプット用ディレクトリとアウトプット用ディレクトリを指定する。  
   * `docs_dir`: `mkdocs`
   * `site_dir`: `docs`
3. `mkdocs build[serve]`すると`docs`に出力されるので、そのままプッシュする。
4. `https://{username}.github.io/{repository}/`にアクセスするとWebページが表示される。
