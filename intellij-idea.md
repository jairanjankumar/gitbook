# IntelliJ Idea

Useful commands

```
cmd+shift+a
# search the action to perform
```

Open Breakpoints dialog

```
Ctrl + Shift + F8
```

To show the heap memory indicator at bottom right corner.

```
Go to IntelliJ IDEA -> Preferences -> Appearance & Behavior-> Appearance
Check the option 'Show memory indicator'
```

To increase the heap size memory for IntelliJ IDEA

```
Go to Help -> Edit Custom VM Options...

First time, this will ask to create Custom VM Options file (idea.vmoptions).

Physical location of idea.vmoptions file is '~/Library/Preferences/IdeaIC2017.2/idea.vmoptions' 

$ cat ~/Library/Preferences/IdeaIC2017.2/idea.vmoptions 
# custom IntelliJ IDEA VM options

-Xms1024m
-Xmx2048m
-XX:ReservedCodeCacheSize=240m
-XX:+UseCompressedOops
-Dfile.encoding=UTF-8
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-Xverify:none

-XX:ErrorFile=$USER_HOME/java_error_in_idea_%p.log
-XX:HeapDumpPath=$USER_HOME/java_error_in_idea.hprof
-Xbootclasspath/a:../lib/boot.jar
```

Intellij how to zoom in /out

```
Intellij Idea > Preferences > Editor > General -> Change font size (Zoom) with Ctrl+Mouse Wheel
```

Not able to navigate code (when press cmd+b, it says 'cannot find declaration to go to')

```
1) # mark the src folder to Sources Root 
right click in src -> Mark Directory as > Sources Root

2) go to Gradle tab, and click 'Refresh all Gradle projects'
```

IntelliJ doesn't show any folders in my project view on the left

```
File > Project Structure > Modules, 
there's supposed to be project file present. 
If it's empty, do the following:
In File > Project Structure > Modules, click the "+" button, and add the project.
```

Maven package works but Intellij's build fails and does't create compiled files target folder&#x20;

```
mvn idea:idea
```

Scala Worksheet - When executed, nothing comes up or throws Internal Error: null

```
In worksheet -> go to setting -> change 'Run type' from REPL to Plain
```
