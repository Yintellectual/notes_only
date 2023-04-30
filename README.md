# notes_only
== Json Format==
 1. By default, spring requires Json with double quotes, for example: {"name":"Peter Smith"}. 
 2. curl in windows can be used to POST Json, but there's two things to remember:
   2.1 curl consumes double quotes in the command line input, for example, -d '{"name":"Peter"}' is received as {name:Peter}  
   2.2 curl requires double quotes to mark a string containning spaces. for example, -d "Peter Smith" is valid but -d 'Peter Smith' is invalid. 
 In conclusion, use curl in this manner: -d "{\"name\":\"Peter Smith\"}"
 
 
== bundle.js created by ReactJS is not up-to-date ==
1. Typically, ReactJS constantly update static/built/bundle.js
2. tomcat won't reload static/built/bundle.js everytime, which is unacceptable in developing.
3. the solution is found in stackflow: https://stackoverflow.com/a/24764196
4. generally speaking, this solution requires ReactJS to place built/bundle.js under src/main/webapp
5. the problem is that everything in webapp is not exposed by default, so we need maven-resource-plugin to always copy files in src/main/webapp to src/main/resources/static
6. Here is the code for pom.xml:
```
<plugin>
    <artifactId>maven-resources-plugin</artifactId>
    <version>2.6</version>
    <executions>
        <execution>
            <id>copy-resources</id>
            <phase>validate</phase>
            <goals>
                <goal>copy-resources</goal>
            </goals>
            <configuration>
                <outputDirectory>${basedir}/target/classes/static</outputDirectory>
                <resources>
                    <resource>
                        <directory>src/main/webapp</directory>
                        <filtering>true</filtering>
                    </resource>
                </resources>
            </configuration>
        </execution>
    </executions>
</plugin>
```
