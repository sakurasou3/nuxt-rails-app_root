# docker 関連

1. rails アプリ作成コマンド

```
docker-compose run --rm api rails new . -f -B -d postgresql --api
```

- docker-compose run --rm api
  - run
    - コンテナ内で任意のコマンドを実行する際に利用する
  - --rm
    - rails 以降のコマンド実行後にコンテナを削除する
- rails new . -f -B -d postgresql --api
  - rails アプリ作成コマンド。
  - .
    - docker-compose.yml に定義した api サービスの context のディレクトリを指す
  - -f
    - 既存ファイルに上書きする（Gemfile などが上書きされる）
  - -B
    - bundle install は行わない。
  - -d postgresql
    - rails のデフォルト DB の MySQL ではなく、postgresql を利用する
  - --api
    - api 専用 Rails アプリとして作成する

1-2. nuxt アプリ作成コマンド

```
docker-compose run --rm front yarn create nuxt-app app
```

- app
  - すでに front ディレクトリ直下に Dockerfile がいるため、一度 app ディレクトリ内にアプリを作成する必要がある。

2. image を再ビルド

```
docker-compose build
```

- Docker イメージを作成。以下のようなタイミングで実行する
  - Dockerfile を書き換えたとき
  - Gemfile が書き換わった時

3. api サービスを起動

```
docker-compose up api
```

- up
  - コンテナの生成、起動
  - api をつけることで、サービス指定でコンテナを立ち上げられる。

4. コンテナの停止

```
docker-compose stop
```

5. コンテナの削除

```
docker-compose rm -f
```

6. コンテナの停止・削除を一度に行う

```
docker-compose down
```

7. コンテナ一覧を表示

```
docker-compose ps -a
```

- a
  - 未起動のものも合わせて一覧表示
