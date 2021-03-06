Maven Zookeeper Plugin
======================

Forked from sfines/maven-zookeeper-plugin

**Version 2.0-SNAPSHOT**

This plugin can be used to run Apache Zookeeper 3.4.3 from Maven in order to run integration tests.
At the moment version 2.0-SNAPSHOT has not been published to any public repository.
In order to use it download the code and build it: mvn clean install

#### Note:
Some people can have problems with Zookeeper and ConnectionLoss Exception.
It turned out that Java 7 (Oracle version) with OSX has a problem (https://issues.apache.org/jira/browse/ZOOKEEPER-1477)

to solve it add the following argument:
**-Djava.nio.channels.spi.SelectorProvider=sun.nio.ch.KQueueSelectorProvider**

### Goals
* start
* stop

### Configuration
* dataDirectory (default: ${project.build.directory}/zookeeperData/ )
* port (default: 3000)
* tickTime
* maxConnections

### How to use the plugin

        <build>
                <plugins>
                    <plugin>
                        <groupId>com.objectdriven.maven</groupId>
                        <artifactId>maven-zookeeper-plugin</artifactId>
                        <version>2.0-SNAPSHOT</version>
                        <configuration>
                            <dataDirectory></dataDirectory>
                            <port>2181</port>
                            <tickTime></tickTime>
                            <maxConnections></maxConnections>
                        </configuration>
                        <executions>
                            <execution>
                                <id>startZookeeper</id>
                                <phase>pre-integration-test</phase>
                                <goals>
                                    <goal>start</goal>
                                </goals>
                            </execution>
                            <execution>
                                <id>stopZookeeper</id>
                                <phase>post-integration-test</phase>
                                <goals>
                                    <goal>stop</goal>
                                </goals>
                            </execution>
                        </executions>
        
                    </plugin>
                 </plugins>
        </build>