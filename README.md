mkdocsをGitHub Pageで公開するサンプル
=====================================

mkdocsの出力結果をGitHub Pageで閲覧できるようにできたら便利そうなのでお試し。

## Start

```sh
# プロジェクト作成
mkdocs new test-docs
cd test-docs
# ビルド&サーバ起動
mkdocs serve
```

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
