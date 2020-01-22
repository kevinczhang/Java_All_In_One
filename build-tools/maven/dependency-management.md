# dependency management

The dependency management section is a mechanism for centralizing dependency information. When you have a set of projects that inherit from a common parent, it's possible to put all information about the dependency in the common POM and have simpler references to the artifacts in the child POMs.

In the parent POM, the main difference between the **`<dependencies>`** and **`<dependencyManagement>`** is this:

Artifacts specified in the **`<dependencies>`** section will ALWAYS be included as a dependency of the child module\(s\).

Artifacts specified in the **`<dependencyManagement>`** section, will only be included in the child module if they were also specified in the **`<dependencies>`** section of the child module itself. Why is it good you ask? because you specify the version and/or scope in the parent, and you can leave them out when specifying the dependencies in the child POM. This can help you use unified versions for dependencies for child modules, without specifying the version in each child module.

