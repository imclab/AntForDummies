Ant for Dummies
===============

Apache Ant is a build tool, like make.

Differences:
* Make uses a Makefile; Ant uses a build.xml file.
* Ant is extended using Java classes, rendering it less platform-dependent.

## Installation
To install, see _Installing Apache Ant_ at http://ant.apache.org/manual/index.html

## Writing a BuildFile
A buildFile contains one _Project and at least one _Target for the _Project.
_Targets are sets of tasks to execute. A _Project might have a _Target for compiling and a _Target for making a redistributable. _Targets may depend on other _Targets.
A _Task is code that can be executed. Ant includes a set of [built-in _Tasks](http://ant.apache.org/manual/tasklist.html).

### Projects
A _Project has three attributes:
* name: (optional)
* default: the default _Target to use when none is supplied (optional)
* basedir: the base directory from which all paths are constructed (optional)

### Targets
A _Target can have the following attributes:
*

### Tasks
The basic structure for _Tasks is:
	<taskname attribute1="value1" attribute2="value2" .../>

A _Task can have the following attributes:
* name: a name used in log messages
* id: a unique ID for the _Task. References to this _Task should use this ID.

#### Properties
_Properties may be set in a buildFile or outside of Ant. A _Property has a case-sensitive name and a value. 
_Properties may be used as the value of _Task attributes by using `attribute="${property}"`.

#### An Example BuildFile

<project name="MyProject" default="dist" basedir=".">
	<description>
		this is an example buildFile
	</description>
	<!-- set global properties for the build -->
	<property name="src" location="src" />
	<property name="build" location="build" />
	<property name="dist" location="dist" />
	
	<target name="init">
		<!-- create the time stamp -->
		<tstamp/>
		<!-- create the build directory structure used by the compile target -->
		<mkdir dir="${build}"/>
	</target>
	
	<target name="compile" depends="init" description="compile the source">
		<!-- compile the Java code from ${src} intdo ${build} -->
		<javac srcdir="${src}" destdir="${build}"/>
	</target>

	<target name="dist" depends="compile" description="generate the distribution">
		<!-- create the distribution directory -->
		<mkdir dir="${dist}/lib"/>
		
		<!-- put everything in ${build} into the MyProject-${DSTAMP}.jar file -->
		<jar jarfule="${dist}/lib/MyProject-${DSTAMP}.jar" basedir="${build}" />
	</target>

	<target name="clean" description="clean up" >
		<!-- delete the ${build} and ${dist} directory trees -->
		<delete dir="${build}" />
		<delete dir="${dist}" />
	</target>
</project>
