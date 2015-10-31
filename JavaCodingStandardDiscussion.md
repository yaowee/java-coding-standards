

# Code Organisation #

One of the first things we need to think about when starting to write our software is how we organise the source files for development. The way we organise our code is extremely important and will ultimately affect **our goals of attaining code reuse and maintainability**.

Typically the use of software changes over time. It needs to be able to respond to changing specifications. This means that a code base needs to be able to evolve and most likely needs to be able to cope with many different developers reading and changing code over the course of its life time.

To support the evolving code base we discuss:
  * The **concept of a Module** and
  * Java's **package** feature.

## Module ##

A **Module** is a conceptual term in Java. It is a collection of specific **packages** that colloborate together to fufill the responsibility(s) of a given module. Ideally our module(s) will have a source code structure that mirrors the conceptual structure of the module. This creates a natural package naming system and makes navigation easier.

### How do we choose modules? ###

In practise modules can be driven by deployment considerations but in essence a module should allow for individual usage or a distinct role within a system.

### Module Characteristics ###

A Module should:

  * Be Highly Cohesion
  * Have Low Coupling with other modules
  * Support Re-Use
    * The Release Reuse Equivalency Principle (REP)

### Module Principles ###

When considering how to organise our project struture we take into account the following principles outlined in http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf.

  * The Release Reuse Equivalency Principle (REP): The granule of reuse is the granule of release.
  * The Common Closure Principle (CCP): Classes that change together, belong together.
  * The Common Reuse Principle (CRP):  Classes that aren’t reused together should not be grouped together.

### Module Structure ###

Sun provide <a href='http://java.sun.com/blueprints/code/projectconventions.html'>guidelines</a> for the project layout when building end-to-end java applications.

Maven advocates a <a href='http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html'>project directory structure</a>

```
+[ProjectName]
|
----+ src
     |
     ----+ main 
     |   |
     |   ----+ java 
     |
     |----+ test
         |
         ----+ java
----+ lib
----+ target
```

  * All source code goes under src/main. The Java source specifically goes under src/main/java
  * All test code goes under src/test. The Java test code specifically goes under src/test/java
  * All dependencies jars goes under the lib folder.
  * All compiled files go under the target folders (with a split between test and production code as above).

### Module Naming ###

The name of a 'project' or module should reveal what the source code contained within it is responsible for.

If you structure your source underneath one project, you may choose the name of the application/system it is.

We prefer to name our projects/modules with camel case and with capital letters for each word e.g Domain, or ExampleProjectName

At times we append on War or Ear to signify that this module is responsible for specifically storing WAR or EAR source code e.g ExampleApplicationWar, ExampleApplicationEar

### Module Standards ###

Modules that exhibit the desirable characteristics listed will help improve maintainability. Changes to code should not ripple throughout the code base and instead should be confined to the conceptual boundary of the module. As such we add the following to our java coding standards document

  1. No cyclic dependencies between modules
  1. High cohesion within each module
  1. Low coupling with other modules

## Packages ##

A package provides a unique namespace for the types (Classes, Interfaces, Enums, Annotations) it contains.

Packages are used to identify sub-systems of a software application. Types that are used together and change together that serve to implement a practicular behaviour are packaged together.

### How do we choose a package? ###

We use a package to organise our Java types within a praticular namespace. We typically organise the Java types that change together and are used together within their own packages.

### Package Characteristics ###

A Package should:

  * Be Highly Cohesion
  * Have Low Coupling with other packages

### Package Principles ###

When considering how to organise our project struture we take into account the following principles outlined in http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf.

  * The Common Closure Principle (CCP): Classes that change together, are packaged together.
  * The Common Reuse Principle (CRP):  Classes that aren’t reused together should not be packaged together.

### Package Naming ###

By convention we use a hierarchical naming pattern to ensure our packages have unique names. A package name typcially starts with the top-level domain reverse e.g.

```
com.javacrafting.x
```

Packages that appear further down the naming hierarchy are often called **sub-packages** but there is no actual hierarchy enforced via the packaging language feature.

The package name is singular and lowercase by industry convention.

### Package Standards ###

  1. No cyclic dependencies between packages
  1. package has high cohesion
  1. package has low coupling
  1. package name is unique, lowercase and singular starting with reverse top-level domain
  1. package should be documented with javadoc explaing rationale for package.
  1. (package stability? depended on package stability?)

## Files ##

Files with the suffix **.java** hold the source code of our Java types. When these are compiled they are transformed into files that hold bytecode with the suffix **.class**. Typically these files are then archived in a **.jar** file.

While smaller source files are easier to manage and view, we dont set any standard around file size like is mentioned in **Suns Java coding convention**, instead we should get this as a result of our standards around the way we create our classes, interfaces, enums and annotations.

We do agree with what is documented in Doug Leas coding standards that each type should exist in a seperate file and that files name should be named the same as the type that is described by the source code.

### File Standards ###

  1. Each type should exist in a seperate file.
  1. File names should match that of the type they hold
  1. Source files end in **.java**
  1. Class files end in **.class**
  1. Archive files end in **.jar**, **.war** or **.ear**
