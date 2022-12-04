# Shell Scripting

To make Command-line entries will be preceded by the Dollar sign ($).

```
PS1="$ " ; export PS1
```

For more info about PS1, PS2, PS3, PS4 and prompt\_command examples, see [here](https://www.thegeekstuff.com/2008/09/bash-shell-take-control-of-ps1-ps2-ps3-ps4-and-prompt\_command/)

Do you know when you write

```
$ echo hello world
```

echo consider this as two parameters, or arguments - first is "Hello", and second is "World".

so even you write

```
$ echo hello           world
```

it will still print "hello world"

```
$ ls
$ mkdir Dir_{0,1,2,3,4,5}
$ ls
Dir_0    Dir_1    Dir_2    Dir_3    Dir_4    Dir_5
$
```

Sample shell script,

```
#!/bin/sh             ----# First Line, A special directive (start with #!), standard location of shell
# This is a comment!  ----# comment start with #
VAR1="Hello World"    ----# shouldn't be any space between variable name and value
echo $VAR1
```

Commands

```
$ read VAR2
----# reads a line from standard input into the variable VAR2
```

for -> loops iterate through a set of values until the list is exhausted:

file1.sh

```
#!/bin/sh
for i in hello 1 * 2 world 
do
  echo "Print :: $i"
done
```

Output as below:

```
Print :: hello
Print :: 1
Print :: <<first directory name>>
Print :: <<line by line directory name>>
Print :: <<last directory name>>
Print :: 2
Print :: world
```

While

file2.sh

```
#!/bin/sh
INPUT_STRING=hello
while [ "$INPUT_STRING" != "bye" ]
do
  echo "Please type something in (bye to quit)"
  read INPUT_STRING
  echo "Input String : $INPUT_STRING"
done
```

```
colon (:) always evaluates to true
so, "while : " will always be true and need to ^C to quit
```

file3.sh

```
$ vi file3.sh

#!/bin/sh
while read f
do
  case $f in
        hello)          echo English    ;;
        howdy)          echo American   ;;
        gday)           echo Australian ;;
        bonjour)        echo French     ;;
        "guten tag")    echo German     ;;
        *)              echo Unknown Language: $f;;
   esac
done < myfile.txt
```

```
$ vi myfile.txt
bonjour
hello
```

```
$ ./file3.sh
French
English
```

Test => \[ ]

In bash you can do **help test** to see test options.

Need to put spaces around all your operators.

```
Few examples:

[ "$X" -lt "0" ]              -> "X is less than zero"
[ "$X" -gt "0" ]              -> "X is more than zero"
[ "$X" -le "0" ]              -> "X is less than or equal to  zero"
[ "$X" -ge "0" ]              -> "X is more than or equal to zero"
[ "$X" = "0" ]                -> "X is the string or number \"0\""
[ "$X" = "hello" ]            -> "X matches the string \"hello\""
[ "$X" != "hello" ]           -> "X is not the string \"hello\""
[ -n "$X" ]                   -> "X is of nonzero length"
[ -f "$X" ]                   -> "No such file: $X"
[ -x "$X" ]                   -> "X is the path of an executable file"
[ "$X" -nt "/etc/passwd" ]    -> "X is a file which is newer than /etc/passwd"
[ -e $name ]                  -> -e returns true if the target exists
```

```
exit - when we want to exist the script completely
break - break the loop
return - returns control to the caller.
```

```
${} acts as a kind of quoting for variables.
$() acts as a kind of quoting for commands but they're run in their own context.
```

**$0 .. $9 , $@ , $\*, $# , $? , \$$** and **$!**

The variable **$0** is the basename of the program as it was called.

**$1 .. $9** are the first 9 additional parameters the script was called with.

The variable **$@** is all parameters **$1** .. whatever.

The variable **$\***, is similar, but does not preserve any whitespace, and quoting, so "File with spaces" becomes "File" "with" "spaces".

As a general rule, use **$@** and avoid **$\***.

**$#** is the number of parameters the script was called with.

**$?** contains the exit value of the last run command.

**\$$** variable is the PID (Process IDentifier) of the currently running shell.

**$!** variable is the PID of the last run background process.

**$IFS** This is the _Internal Field Separator_. The default value is SPACE TAB NEWLINE

For more Info : [http://www.gnu.org/software/bash/manual/html\_node/Special-Parameters.html#Special-Parameters](http://www.gnu.org/software/bash/manual/html\_node/Special-Parameters.html#Special-Parameters)

Always use with double quotes, like **old\_IFS="$IFS"** instead of old\_IFS=$IFS.

```
${parameter:-word} Use Default Values. If parameter is unset or null, the expansion of word is substituted. Otherwise, the value of parameter is substituted.

${parameter:=word} Assign Default Values. If parameter is unset or null, the expansion of word is assigned to parameter. The value of parameter is then substituted. Positional parameters and special parameters may not be assigned to in this way.

${parameter:?word} Display Error if Null or Unset. If parameter is null or unset, the expansion of word (or a message to that effect if word is not present) is written to the standard error and the shell, if it is not interactive, exits. Otherwise, the value of parameter is substituted.

${parameter:+word} Use Alternate Value. If parameter is null or unset, nothing is substituted, otherwise the expansion of word is substituted.
```

```
```

By using curly braces and the special **":-"** usage, you can specify a default value to use if the variable is unset.

**":="** which sets the variable to the default if it is undefined.

backtick (\`)is often associated with external commands. The backtick is used to indicate that the enclosed text is to be executed as a command.

**\` (backtick)** runs in a subshell

shell function cannot change its parameters, though it can change global parameters.

**tr** translated the spaces into octal character 012 (NEWLINE).

```
$ i="Hi How Are You"

$ echo $i
Hi How Are You

$ echo $i | tr ' ' '\012'
Hi
How
Are
You
```

```
AND and OR lists are sequences of one or more pipelines separated by the control operators ‘&&’ and ‘||’, 
respectively. AND and OR lists are executed with left associativity.

An AND list has the form

command1 && command2
command2 is executed if, and only if, command1 returns an exit status of zero.

An OR list has the form

command1 || command2
command2 is executed if, and only if, command1 returns a non-zero exit status.

The return status of AND and OR lists is the exit status of the last command executed in the list.
```

SCRIPT\_DIR="$( cd "$( dirname "${BASH\_SOURCE\[0]}" )" && pwd )"

```
Bash maintains a number of variables including BASH_SOURCE which is an array of source file pathnames.
${} acts as a kind of quoting for variables.
$() acts as a kind of quoting for commands but they're run in their own context.
dirname gives you the path portion of the provided argument.
cd changes the current directory.
pwd gives the current path.
&& is a logical and but is used in this instance for its side effect of running commands one after another.
In summary, that command gets the script's source file pathname, strips it to just the path portion, 
cds to that path, then uses pwd to return the (effectively) full path of the script. This is assigned to SCRIPT_DIR. 
After all of that, the context is unwound so you end up back in the directory you started at but with an environment variable SCRIPT_DIR containing the script's path.
```
