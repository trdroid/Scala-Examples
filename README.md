### Scala Download

http://www.scala-lang.org/download/

### SBT Download

http://www.scala-sbt.org/download.html

Scala programs can be composed and executed in the following ways:

1. Interactively at an REPL prompt
2. As a single-file script
3. Scala programs can be compiled to class files and packaged into JAR files, just like in Java

### Scala REPL

*Printing Hello World!*

```sh
$ scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_91).
Type in expressions for evaluation. Or try :help.

scala> println("Obligatory Hello World!")
Obligatory Hello World!

scala> :quit
```

*println()* is a wrapper around System.out.println() method.


*Exploring the REPL*

To get a list of commands available, use the *:help* command 

```sh
$ scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_91).
Type in expressions for evaluation. Or try :help.

scala> :help
All commands can be abbreviated, e.g., :he instead of :help.
:edit <id>|<line>        edit history
:help [command]          print this summary or command-specific help
:history [num]           show the history (optional num is commands to show)
:h? <string>             search the history
:imports [name name ...] show import history, identifying sources of names
:implicits [-v]          show the implicits in scope
:javap <path|class>      disassemble a file or class name
:line <id>|<line>        place line(s) at the end of history
:load <path>             interpret lines in a file
:paste [-raw] [path]     enter paste mode or paste a file
:power                   enable power user mode
:quit                    exit the interpreter
:replay [options]        reset the repl and replay all previous commands
:require <path>          add a jar to the classpath
:reset [options]         reset the repl to its initial state, forgetting all session entries
:save <path>             save replayable session to a file
:sh <command line>       run a shell command (result is implicitly => List[String])
:settings <options>      update compiler options, if possible; see reset
:silent                  disable/enable automatic printing of results
:type [-v] <expr>        display the type of an expression without evaluating it
:kind [-v] <expr>        display the kind of expression's type
:warnings                show the suppressed warnings from the most recent line which had any
```

*Exploring numbers*

In the following example, an expression specified at the REPL prompt is evaluated and assigned to a variable 'res0'. Scala also infers type of the value to be of type *Int*. 

'res0' can be used throughout the lifetime of the session. 

Variables created in an REPL session are available for the lifetime of the session. 

```sh
$ scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_91).
Type in expressions for evaluation. Or try :help.

scala> 2 + 5
res0: Int = 7
```

In the same session, an expression composed with 'res0' as shown below results in a value that gets assigned to a new variable 'res1', which can be used in further expressions in the same REPL session.

```sh
scala> res0 * 2
res1: Int = 14
```

*Exploring Strings*

```sh
scala> val str = "Sample string"
str: String = Sample string

scala> var len = str.length
len: Int = 13
```

*Importing a Java library*

```sh
scala> import java.util._
import java.util._

scala> val cal = new GregorianCalendar
cal: java.util.GregorianCalendar = java.util.GregorianCalendar[time=1471487772489,areFieldsSet=true,areAllFieldsSet=true,lenient=true,zone=sun.util.calendar.ZoneInfo[id="America/New_York",offset=-18000000,dstSavings=3600000,useDaylight=true,transitions=235,lastRule=java.util.SimpleTimeZone[id=America/New_York,offset=-18000000,dstSavings=3600000,useDaylight=true,startYear=0,startMode=3,startMonth=2,startDay=8,startDayOfWeek=1,startTime=7200000,startTimeMode=0,endMode=3,endMonth=10,endDay=1,endDayOfWeek=1,endTime=7200000,endTimeMode=0]],firstDayOfWeek=1,minimalDaysInFirstWeek=1,ERA=1,YEAR=2016,MONTH=7,WEEK_OF_YEAR=34,WEEK_OF_MONTH=3,DAY_OF_MONTH=17,DAY_OF_YEAR=230,DAY_OF_WEEK=4,DAY_OF_WEEK_IN_MONTH=3,AM_PM=1,HOUR=10,HOUR_OF_DAY=22,MINUTE=36,SECOND=12,MILLISECOND=489,ZONE_OFFSET=-18000000,...

scala> cal.get(Calendar.DAY_OF_WEEK)
res2: Int = 4

scala> cal.get(Calendar.DAY_OF_WEEK)
res3: Int = 4
```

Notice how the value from an expression is assigned to a new variable in each evaluation.

### Scala Scripts

Scripts are simple programs that can be written in Scala just like in Ruby/Python/Groovy. Scripts in Scala does not require an explicit *main* method. When Scala executes a script, it wraps the script code in a *main* method, compiles the code and calls the *main* method. 

Save the scala code in a file and name it with a .scala extension.

```scala
$ scalac -help
Usage: scalac <options> <source files>
where possible standard options include:
  -Dproperty=value                Pass -Dproperty=value directly to the runtime system.
  -J<flag>                        Pass <flag> directly to the runtime system.
  -P:<plugin>:<opt>               Pass an option to a plugin
  -X                              Print a synopsis of advanced options.
  -bootclasspath <path>           Override location of bootstrap class files.
  -classpath <path>               Specify where to find user class files.
  -d <directory|jar>              destination for generated classfiles.
  -dependencyfile <file>          Set dependency tracking file.
  -deprecation                    Emit warning and location for usages of deprecated APIs.
  -encoding <encoding>            Specify character encoding used by source files.
  -explaintypes                   Explain type errors in more detail.
  -extdirs <path>                 Override location of installed extensions.
  -feature                        Emit warning and location for usages of features that should be imported explicitly.
  -g:<level>                      Set level of generated debugging info. (none,source,line,vars,notailcalls) default:vars
  -help                           Print a synopsis of standard options
  -javabootclasspath <path>       Override java boot classpath.
  -javaextdirs <path>             Override java extdirs classpath.
  -language:<_,feature,-feature>  Enable or disable language features: `_' for all, `-language:help' to list
  -no-specialization              Ignore @specialize annotations.
  -nobootcp                       Do not use the boot classpath for the scala jars.
  -nowarn                         Generate no warnings.
  -optimise                       Generates faster bytecode by applying optimisations to the program
  -print                          Print program with Scala-specific features removed.
  -sourcepath <path>              Specify location(s) of source files.
  -target:<target>                Target platform for object files. All JVM 1.5 targets are deprecated. (jvm-1.5,jvm-1.6,jvm-1.7,jvm-1.8) default:jvm-1.6
  -toolcp <path>                  Add to the runner classpath.
  -unchecked                      Enable additional warnings where generated code depends on assumptions.
  -uniqid                         Uniquely tag all identifiers in debugging output.
  -usejavacp                      Utilize the java.class.path in classpath resolution.
  -usemanifestcp                  Utilize the manifest in classpath resolution.
  -verbose                        Output messages about what the compiler is doing.
  -version                        Print product version and exit.
  @<file>                         A text file containing compiler arguments (options and source files)
```
