# stormHelloworld

## 安装storm开发环境

```
brew install storm
```


----------


## 相关程序
```
<dependency>
    <groupId>org.apache.storm</groupId>
    <artifactId>storm-core</artifactId>
    <version>0.9.6</version>
    <scope>provided</scope>
</dependency>

<!-- 通过maven-shade-plugin将一个项目打包成一个可执行的jar包。包括所依赖的jar -->
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-shade-plugin</artifactId>
            <version>2.2</version>
            <configuration>
                <createDependencyReducedPom>true</createDependencyReducedPom>
            </configuration>
            <executions>
                <execution>
                    <phase>package</phase>
                    <goals>
                        <goal>shade</goal>
                    </goals>
                    <configuration>
                        <transformers>
                            <transformer
                                    implementation="org.apache.maven.plugins.shade.resource.ServicesResourceTransformer"/>
                            <transformer
                                    implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                <mainClass></mainClass>
                            </transformer>
                        </transformers>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```


----------


## 运行方式

```
mvn package
```

运行

```
storm jar /Users/momo/Desktop/helloworld/storm/stormHelloworld/target/stormHelloworld-1.0-SNAPSHOT.jar com.tutorial.stormHelloworld.WordCountTopology
```

格式

```
storm jar jar包的名称 main方法的名称
```

output

```
--- FINAL COUNTS ---
a : 1
ate : 1
beverages : 1
cold : 1
cow : 1
dog : 2
don't : 1
fleas : 1
has : 1
have : 1
homework : 1
i : 1
like : 1
man : 1
my : 2
the : 1
```

----------

from PacktPub——Storm Blueprints: Patterns for Distributed Real-time Computation
https://www.packtpub.com/packtlib/book/Big%20Data%20&%20Business%20Intelligence/9781782168294/1