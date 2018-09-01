# rg-maven-code-quality

> A maven dependency for providing code quality presets to projects

## How To Use

This dependency is usually not used as a direct dependency to a project but rather by plugin configurations such as findbugs and checkstyle.

### Checkstyle Usage Example

Maven usage

`mvn checkstyle:checkstyle`

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <dependencies>
          <dependency>
            <groupId>com.ragedunicorn.tools.maven</groupId>
            <artifactId>maven-code-quality</artifactId>
            <version>[version]</version>
          </dependency>
          <dependency>
            <groupId>com.puppycrawl.tools</groupId>
            <artifactId>checkstyle</artifactId>
            <version>8.12</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

Additionally the config and header location properties have to be set in the project pom. 

```xml
<properties>
  <checkstyle.config.location>checkstyle.xml</checkstyle.config.location>
  <checkstyle.header.location>LICENSE.txt</checkstyle.header.location>
</properties>
```

### PMD Usage Example

Maven usage

`mvn pmd:pmd`

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-pmd-plugin</artifactId>
        <version>3.10.0</version>
        <configuration>
          <rulesets>
            <ruleset>pmd-ruleset.xml</ruleset>
          </rulesets>
          <printFailingErrors>true</printFailingErrors>
        </configuration>
        <dependencies>
          <dependency>
           <groupId>com.ragedunicorn.tools.maven</groupId>
           <artifactId>maven-code-quality</artifactId>
           <version>[version]</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
  
  <reporting>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-jxr-plugin</artifactId>
      </plugin>
    </plugins>
  </reporting>
  ...
</project>
```

### FindBugs Usage Example

Maven usage

`mvn findbugs:findbugs`

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>findbugs-maven-plugin</artifactId>
        <version>3.0.5</version>
        <dependencies>
          <dependency>
            <groupId>com.ragedunicorn.tools.maven</groupId>
            <artifactId>maven-code-quality</artifactId>
            <version>[version]</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

**Note**: FindBugs requires that the project was previously built and classes are available in the target folder.

## Development

#### Build Project

`mvn clean install`

#### IntelliJ Run Configurations

The project contains IntelliJ run configurations that can be used for most tasks. Create a folder `runConfigurations` inside the `.idea` folder and copy over all run configurations.

## License

Copyright (c) 2018 Michael Wiesendanger

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
