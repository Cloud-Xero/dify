https://github.com/langgenius/dify からForkしたリポジトリ

## オリジナルから最新を取得し、自身のリポジトリに反映する手順
```
git checkout main
git pull upstream main
git push origin main
```

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
