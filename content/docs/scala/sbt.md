---
weight: 2
title: sbt
---

# sbt

# 概要
- Scala の標準的なビルドツール．
- GitHub: [sbt/sbt](https://github.com/sbt/sbt)
- WebSite: https://www.scala-sbt.org/
- Docs-en: https://www.scala-sbt.org/1.x/docs/
- Docs-ja: https://www.scala-sbt.org/release/docs/ja/index.html

# Docker で使う
- GitHub: [hseeberger/scala-sbt](https://github.com/hseeberger/scala-sbt)
- GitHub: [mozilla/docker-sbt](https://github.com/mozilla/docker-sbt)

## image を build する
```bash
docker build \
  --build-arg BASE_IMAGE_TAG="8u212-b04-jdk-stretch" \
  --build-arg SBT_VERSION="1.3.8" \
  --build-arg SCALA_VERSION="2.13.1" \
  --build-arg USER_ID=1001 \
  --build-arg GROUP_ID=1001 \
  -t solareenlo/scala-sbt \
  github.com/hseeberger/scala-sbt.git#:debian
```

## docker run
```bash
# コンテナを走らせる
sudo docker run -it --rm -v $(pwd):/root solareenlo/scala-sbt:latest bash
sudo docker run -it --rm -v $(pwd):/root solareenlo/scala-sbt:latest scala
sudo docker run -it --rm -v $(pwd):/root solareenlo/scala-sbt:latest sbt
```

# 使い方
```bash
sbt
runMain TestStudy
```
or
```bash
sbt run
```
or
```bash
sbt console
```

# 設定ファイル
```bash
touch build.sbt

# build.sbt
scalaVersion := "2.13.1"

scalacOptions ++= Seq("-deprecation", "-feature", "-unchecked", "-Xlint")
```
上記のオプションを付けることで以下の警告の情報を出してくれるようになる．
- `-deprecation`: 今後廃止の予定のAPIを利用している
- `-feature`: 明示的に使用を宣言しないといけない実験的な機能や注意しなければならない機能を利用している
- `-unchecked`: 型消去などでパターンマッチが有効に機能しない場合
- `-Xlint`: その他，望ましい書き方や落とし穴についての情報
