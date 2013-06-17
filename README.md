Ant for Dummies
===============

Apache Ant is a build tool, like make.

Differences:
* Make uses a Makefile; Ant uses a build.xml file.
* Ant is extended using Java classes, rendering it less platform-dependent.

## Installation
To install, see _Installing Apache Ant_ at http://ant.apache.org/manual/index.html

## Writing a BuildFile
A buildFile contains one project and at least one target for the project.
Targets are sets of tasks to execute. A project might have a target for compiling and a target for making a redistributable. Targets may depend on other targets.
Tasks are referenced by their unique ID attributes. A Task is code that can be executed.
The basic structure for tasks is:
	<name attribute1="value1" attribute2="value2" .../>
Ant includes a set of [built-in tasks](http://ant.apache.org/manual/tasklist.html). 

A project has three attributes:
* name: (optional)
* default: the default target to use when none is supplied (optional)
* basedir: the base directory from which all paths are constructed (optional)



