## osx symfony docker
==================

Mac OSX上でvirtualbox+dockerな環境でsymfony(LAMP)を動かすための設定

ディレクトリ構造はsymfony2のバージョン3.0を想定

### セットアップ方法

symfonyのキャッシュディレクトリを削除する

```
% rm -rf var/cache var/logs
```

virtualbox内でマウントされる共有用のOSX上のファイル(/Users配下)は全てdockerユーザ権限となってしまい、コンテナ内のapacheが書き込めないためこれらのディレクトリはホスト上から削除して、コンテナ内で用意する仕組みになっている

mysqlのデータ永続化のためディレクトリ。コンテナ内の/var/lib/mysqlにマウントされる

```
% mkdir var/db
```

### 実行方法

```
% eval "$(docker-machine env default)"
% docker-compse build
% docker-compse up
```

defaultは自分のvirtualboxマシン名に変更