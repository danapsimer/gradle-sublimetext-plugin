# sublimeText Plugin for Gradle
The sublimeText plugin allows gradle to create a Sublime Text 2 project file.

##Usage
Put the following into your build script and tweak the settings to your liking:

```groovy

apply plugin: 'sublimeText'

buildscript {
  repositories {
    maven {
      url 'http://phildop.us/m2repo'
    }
    dependencies {
      classpath 'us.phildop:gradle-sublimetext-plugin:0.5'
    }
  }
}

sublimeText {
  // enter relevant (and optional) config stuff here, explained below
}
```


####sublimeProjectName

If set, the generated file will be named &lt;sublimeProjectName&gt;.sublime-project.
Otherwise, it will default to the gradle project's name.

```groovy
sublimeText {
  sublimeProjectName = 'custom-project-name'
}
```


####defaultFileExcludePatterns &amp; defaultFolderExcludePatterns

Exclude unimportant files and folders generated by gradle and eclipse.
These will be copied to each folder entry.

```groovy
sublimeText {
  defaultFileExcludePatterns = ['.project', '.classpath', '.pydevproject']
  defaultFolderExcludePatterns = ['.gradle', 'bin', 'build', '.settings']
}
```


####addDependencyProjects

If set to true, any dependency project folders will be added.

```groovy
sublimeText {
  addDependencyProjects = true
}
```


####SublimeJava

Generate paths for [SublimeJava](https://github.com/quarnster/SublimeJava)

```groovy
sublimeText {
  generateSublimeJavaClasspath = true
  generateSublimeJavaSrcpath = true
}
```


####addGradleCompile

If set to true, generate a Sublime Text build system that calls gradle compileJava on project.

```groovy
sublimeText {
  addGradleCompile = true
}
```


####addSublimeLinterConfig

If set to true, generate configuration for [SublimeLinter](https://github.com/SublimeLinter/SublimeLinter).

```groovy
sublimeText {
  addSublimeLinterConfig = true
}
```


####EclipseJavaFormatter

Options for [EclipseJavaFormatter](https://github.com/phildopus/EclipseJavaFormatter).

```groovy
sublimeText {
  eclipseJavaFormatterConfigFile = "/path/to/config/org.eclipse.jdt.core.prefs"
  eclipseJavaFormatterSortImportsOrder = ["java", "javax", "org", "com"]
  eclipseJavaFormatterRestoreLineEndings = true
}
```


On the command line issue the following command:

```bash
gradle sublimeText
```
