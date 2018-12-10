# Alfresco Gradle SDK Examples [![Build Status](https://travis-ci.org/xenit-eu/alfresco-gradle-sdk-example.svg?branch=master)](https://travis-ci.org/xenit-eu/alfresco-gradle-sdk-example)

Gradle-based project with examples using Xenit's Alfresco Gradle SDK to bootstrap Alfresco development

### Plugins

For Alfresco development, you need to apply 2 plugins. This will
configure your project with an amp task that includes the jar built
in this project.

```
plugins {
    id 'eu.xenit.alfresco' version "0.1.3" // Have a look at https://plugins.gradle.org/plugin/eu.xenit.alfresco for the latest version
    id 'eu.xenit.amp' version "0.1.3"
}
```

The ```eu.xenit.alfresco``` plugin introduces the ```alfrescoProvided```
configuration that makes it possible to define Alfresco dependencies
that are already provided in the Alfresco war, and should not be
included in the amp file. These dependencies are available when running
unit tests.

### Amp configuration

An amp has some typical files and folders. The module.properties file is required.
You can override their locations in the ```ampConfig``` extension:

| property         | description                                                  | default                                              | required |
| ---------------- | ------------------------------------------------------------ | ---------------------------------------------------- | -------- |
| moduleProperties | The file that describes your extension.                      | ```project.file('src/main/amp/module.properties')``` | false    |
| configDir        | This folder will be put on the classpath of the war.         | ```project.file('src/main/amp/config')```            | false    |
| web              | This folder will end up in the "web" directory of the amp file. | ```project.file('src/main/amp/web')```               | false    |
| dynamicExtension | Jar and dependencies are treated as Dynamic Extensions.      | false                                                | false    |

More information about Dynamic Extensions for Alfresco can be found
[here](https://github.com/xenit-eu/dynamic-extensions-for-alfresco).
This plugin can bundle Dynamic Extensions in an ```amp``` file. This means
that the jar and dependencies should be put in the correct location in
the ```amp``` file.

### Usage

To build an amp, run the amp task. In case you have the gradlew wrapper in your project, run.

```
./gradlew amp
```

In case you have gradle installed on your system, run.

```
gradle amp
```
The built amp should be visible in build/dist/


## Alfresco Gradle SDK

For more information, please visit https://github.com/xenit-eu/alfresco-gradle-sdk/