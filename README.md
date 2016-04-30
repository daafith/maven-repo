#Plugin Repository
Hope to put some more stuff here as time advances.

##Credentials Plugin##
A simple plugin that creates a `.properties` file with a random username and a less than random password. For instance:
```
password=Welkom01@
username=ynvllf
```

###POM configuration###
Add the following to the `pom.xml` of your project.

```xml
<pluginRepositories>
 	<pluginRepository>
    	<id>git-daafith</id>
    	<name>daafith's Git based repo</name>
    	<url>https://github.com/daafith/maven-repo/raw/master/</url>
  	</pluginRepository>
</pluginRepositories>
```

```xml
<build>
	<pluginManagement>
		<plugins>
			<plugin>
				<groupId>credentials.plugin</groupId>
				<artifactId>credentials-maven-plugin</artifactId>
				<version>1.0-SNAPSHOT</version>
			</plugin>
		</plugins>
	</pluginManagement>
</build>
```

###Run It###
`mvn credentials:credentials`

###Customize It###
By default the plugin creates the following data:
* random username --> 6 characters long 
* password --> Welkom01@
* propertiesDirectory --> project root folder
* propertiesFileName -->  credentials

You can customize the output in your configuration:
```xml
<properties>
	<nameLength>16</nameLength>
	<password>qwerty@01</password>
	<propertiesDirectory>src/test/resources/</propertiesDirectory>
	<propertiesFileName>foobar</propertiesFileName>
</properties>
```

```xml
<plugin>
	<groupId>credentials.plugin</groupId>
	<artifactId>credentials-maven-plugin</artifactId>
	<version>1.0-SNAPSHOT</version>
	<configuration>
		<nameLength>${nameLength}</nameLength>
		<password>${password}</password>
		<propertiesDirectory>${propertiesDirectory}</propertiesDirectory>
		<propertiesFileName>${propertiesFileName}</propertiesFileName>
	</configuration>
</plugin>
```
You can then override properties in the command line as well `mvn credentials:credentials -DnameLength="12"`.
