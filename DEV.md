https://github.com/langgenius/dify からForkしたリポジトリ

## オリジナルから最新を取得し、自身のリポジトリに反映する手順
```
git checkout main
git pull upstream main
git push origin main
```

## ローカルでの起動方法
基本的には[README](./README.md)を参照
Dockerを起動してコマンド実行してコンテナを起動させたら、http://localhost/apps にアクセス


## 別リポジトリから参照したい場合
1. 追加したいリポジトリ先で以下のコマンドを実行
  ```
  git submodule add https://github.com/Cloud-Xero/dify path/to/dify
  ```
  `path/to/dify`は、サブモジュールを配置したいフォルダ名を指定する

  Commit & Push
  ```
  git commit -m "Add dify as a submodule"
  git push origin main
  ```
2. cloneや更新の方法（コラボレーター向け）
   - 初回clone時
    ```
    git clone <参照元リポジトリのURL>
    git submodule update --init --recursive
    ```
   - サブモジュールの更新時
    ```
    cd path/to/dify
    git checkout main
    git pull origin main
    # 必要に応じて 参照元リポジトリに戻って更新のコミット（親リポジトリ側にも「サブモジュールが指し示すコミットが変わった」ことを反映するためのコミットが必要）
    cd ../..
    git add path/to/dify
    git commit -m "Update dify submodule"
    git push origin main
    ```

## DSLについて
- DSL（Dify.AIが定めるAIアプリケーション開発のための標準ファイルフォーマット(YML)）は、現状GUI上からでしかインポートできない
- 追加先のリポジトリ内で`dsl`フォルダを作成してそこにファイルを格納して管理する
- [公式ドキュメント](https://docs.dify.ai/ja-jp/guides/application-orchestrate/creating-an-application#dslfairukara)
