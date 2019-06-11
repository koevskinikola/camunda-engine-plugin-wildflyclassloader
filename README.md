# A WildFly (12+) Classloader Plugin

## How to install it

1. Build the plugin
2. Copy the generated artifact to `$WILDFLY_HOME/modules/org/camunda/bpm/camunda-engine-plugin-wildflyclassloader/main`
3. Create a `module.xml` file in the same directory with the following contents (adjust versions if necessary):

```xml
<module xmlns="urn:jboss:module:1.0" name="org.camunda.bpm.camunda-engine-plugin-wildflyclassloader">
  <resources>
    <resource-root path="camunda-engine-plugin-wildflyclassloader-1.0.jar" />
  </resources>

  <dependencies>
  	<module name="org.camunda.bpm.camunda-engine" />
    <module name="javax.api"/>
    <module name="org.slf4j" />
  </dependencies>
</module>
```

4. Add the following under the `<plugins>` tag of your Camunda Process Engine Configuration in `standalone.xml`:

```xml
<plugin>
    <class>org.camunda.wildfly.plugin.wildflyclassloader.WildflyClassloaderPlugin</class>
</plugin>
```
