# Visual Studio Code Java Development Container 

https://code.visualstudio.com/docs/remote/create-dev-container


## 环境


```bash

$ java -version

openjdk version "16.0.2" 2021-07-20
OpenJDK Runtime Environment (build 16.0.2+7-67)
OpenJDK 64-Bit Server VM (build 16.0.2+7-67, mixed mode, sharing)

```

```bash

$ /usr/local/openjdk-16/bin/java -version

openjdk version "16.0.2" 2021-07-20
OpenJDK Runtime Environment (build 16.0.2+7-67)
OpenJDK 64-Bit Server VM (build 16.0.2+7-67, mixed mode, sharing)


```

```bash

$ /usr/local/openjdk-8/bin/java -version
openjdk version "1.8.0_302"
OpenJDK Runtime Environment (build 1.8.0_302-b08)
OpenJDK 64-Bit Server VM (build 25.302-b08, mixed mode)

```


```bash

$ mvn --version

Apache Maven 3.6.2 (40f52333136460af0dc0d7232c0dc0bcf0d9e117; 2019-08-27T15:06:16Z)
Maven home: /usr/local/sdkman/candidates/maven/current
Java version: 16.0.2, vendor: Oracle Corporation, runtime: /usr/local/openjdk-16
Default locale: en, platform encoding: UTF-8
OS name: "linux", version: "5.10.25-linuxkit", arch: "amd64", family: "unix"

```

## 例子

```bash

$ docker build ./docker/build -t tomhjx/java:openjdk-16-mvn-3.6.2-gradle-5.4.1-vscode



```

![](./examples/vscode23.43.42.gif)