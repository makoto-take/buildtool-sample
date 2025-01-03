build tool の整理

## 参考

https://qiita.com/MahoTakara/items/ff73338e218b656bedfa

## WSLで色々インストール

```sh
$ uname -a
Linux altium 5.15.167.4-microsoft-standard-WSL2 #1 SMP Tue Nov 5 00:21:55 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
$ sudo apt-get install make
$ sudo apt-get install openjdk-21-jdk
$ sudo apt-get install ant
$ sudo apt-get install maven
$ sudo apt-get install gradle
```

gradle は古すぎて init でエラーになったので削除
```
$ gradle --version

------------------------------------------------------------
Gradle 4.4.1
------------------------------------------------------------

Build time:   2012-12-21 00:00:00 UTC
Revision:     none

Groovy:       2.4.17
Ant:          Apache Ant(TM) version 1.10.7 compiled on October 24 2019
JVM:          21.0.5 (Ubuntu 21.0.5+11-Ubuntu-1ubuntu120.04)
OS:           Linux 5.15.167.4-microsoft-standard-WSL2 amd64

$ sudo apt-get remove gradle
$ sudo add-apt-repository ppa:cwchien/gradle
$ sudo apt-get install gradle
$ gradle --version

Welcome to Gradle 8.3!

Here are the highlights of this release:
 - Faster Java compilation
 - Reduced memory usage
 - Support for running on Java 20

For more details see https://docs.gradle.org/8.3/release-notes.html


------------------------------------------------------------
Gradle 8.3
------------------------------------------------------------

Build time:   2023-08-17 07:06:47 UTC
Revision:     8afbf24b469158b714b36e84c6f4d4976c86fcd5

Kotlin:       1.9.0
Groovy:       3.0.17
Ant:          Apache Ant(TM) version 1.10.13 compiled on January 4 2023
JVM:          21.0.5 (Ubuntu 21.0.5+11-Ubuntu-1ubuntu120.04)
OS:           Linux 5.15.167.4-microsoft-standard-WSL2 amd64
```

## ant

ビルド
```
$ ant compile
```

クリーンナップ
```
$ ant clean
```

## maven

以下のコマンドで自動生成される
```
mvn archetype:generate -DgroupId=org.tkr.app -DartifactId=hello-world -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

パッケージ化
```
mvn package
```

クリーンナップ
```
mvn clean
```

実行
```
java -cp target/hello-world-1.0-SNAPSHOT.jar org.tkr.app.App
```

## gradle

プロジェクトの初期化
```
$ gradle init
```

task の確認
```
$ ./gradlew tasks
```

実行
```
$ ./gradlew run
```

クリーンナップ
```
$ ./gradlew clean
```
