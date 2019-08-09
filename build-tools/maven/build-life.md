# Build Life

### **Build Life Cycles, Phases and Goals**

The build process in Maven is split up into build life cycles, phases and goals. A build life cycle consists of a sequence of build phases, and each build phase consists of a sequence of goals. When you run Maven you pass a command to Maven. This command is the name of a build life cycle, phase or goal. If a life cycle is requested executed, all build phases in that life cycle are executed. If a build phase is requested executed, all build phases before it in the pre-defined sequence of build phases are executed too.

The syntax for running Maven is as follows:

```text
mvn [options] [<goal(s)>] [<phase(s)>]
```

## **Build Life Cycles** 

Maven has 3 built-in build life cycles**:**

1. default:  The `default` life cycle handles everything related to compiling and packaging your project. 
2. clean:  The `clean` life cycle handles everything related to removing temporary files from the output directory, including generated source files, compiled classes, previous JAR files etc. 
3. site:  The `site` life cycle handles everything related to generating documentation for your project. In fact, `site` can generate a complete website with documentation for your project.

## **Build Phases**

Each build life cycle is divided into a sequence of build phases, and the build phases are again subdivided into goals. Thus, the total build process is a sequence of build life cycle\(s\), build phases and goals.

 When you execute a build phase, all build phases before that build phase in this standard phase sequence are executed. Thus, executing the `install` build phase really means executing all build phases before the `install` phase, and then execute the `install` phase after that.

 The `default` life cycle is of most interest since that is what builds the code. Since you cannot execute the `default` life cycle directly, you need to execute a build phase or goal from the `default` life cycle.

The most commonly used build phases are**:**

| Build Phase | Description |
| :--- | :--- |
| `validate` | Validates that the project is correct and all necessary information is available. This also makes sure the dependencies are downloaded. |
| `compile` | Compiles the source code of the project. |
| `test` | Runs the tests against the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed. |
| `package` | Packs the compiled code in its distributable format, such as a JAR. |
| `install` | Install the package into the local repository, for use as a dependency in other projects locally. |
| `deploy` | Copies the final package to the remote repository for sharing with other developers and projects. |

 If the standard Maven build phases and goals are not enough to build your project, you can create [Maven plugins](http://tutorials.jenkov.com/maven/maven-tutorial.html#maven-plugins) to add the extra build functionality you need.

##  **Build Goals**

 Build goals are the finest steps in the Maven build process. A goal can be bound to one or more build phases, or to none at all. If a goal is not bound to any build phase, you can only execute it by passing the goals name to the `mvn` command. If a goal is bound to multiple build phases, that goal will get executed during each of the build phases it is bound to.

## Lifecycles Reference

Maven defines 3 lifecycles in META-INF/plexus/components.xml:

* [default Lifecycle](https://maven.apache.org/ref/3.5.0/maven-core/lifecycles.html#default_Lifecycle)
* [clean Lifecycle](https://maven.apache.org/ref/3.5.0/maven-core/lifecycles.html#clean_Lifecycle)
* [site Lifecycle](https://maven.apache.org/ref/3.5.0/maven-core/lifecycles.html#site_Lifecycle)

#### default Lifecycle

default lifecycle is defined **without** any associated plugin. Plugin bindings for this lifecycle are [defined separately for every packaging](https://maven.apache.org/ref/3.5.0/maven-core/default-bindings.html):

```text
<phases>
  <phase>validate</phase>
  <phase>initialize</phase>
  <phase>generate-sources</phase>
  <phase>process-sources</phase>
  <phase>generate-resources</phase>
  <phase>process-resources</phase>
  <phase>compile</phase>
  <phase>process-classes</phase>
  <phase>generate-test-sources</phase>
  <phase>process-test-sources</phase>
  <phase>generate-test-resources</phase>
  <phase>process-test-resources</phase>
  <phase>test-compile</phase>
  <phase>process-test-classes</phase>
  <phase>test</phase>
  <phase>prepare-package</phase>
  <phase>package</phase>
  <phase>pre-integration-test</phase>
  <phase>integration-test</phase>
  <phase>post-integration-test</phase>
  <phase>verify</phase>
  <phase>install</phase>
  <phase>deploy</phase>
</phases>
```

#### clean Lifecycle

clean lifecycle is defined directly with its plugin bindings.

```text
<phases>
  <phase>pre-clean</phase>
  <phase>clean</phase>
  <phase>post-clean</phase>
</phases>
<default-phases>
  <clean>
    org.apache.maven.plugins:maven-clean-plugin:2.5:clean
  </clean>
</default-phases>
```

#### site Lifecycle

site lifecycle is defined directly with its plugin bindings.

```text
<phases>
  <phase>pre-site</phase>
  <phase>site</phase>
  <phase>post-site</phase>
  <phase>site-deploy</phase>
</phases>
<default-phases>
  <site>
    org.apache.maven.plugins:maven-site-plugin:3.3:site
  </site>
  <site-deploy>
    org.apache.maven.plugins:maven-site-plugin:3.3:deploy
  </site-deploy>
</default-phases>
```

