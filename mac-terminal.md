# Mac Terminal

set bash\_profile

```
alias mr='ssh User_Name@xxxx-xxx.xxx.xxxx.com'
export SPARK_HOME=/Users/myUser/sparkDownload/spark-2.3.0-bin-hadoop2.7
PATH=$PATH:$SPARK_HOME/bin

To load the bash_profile
$ source ~/.bash_profile
```

To find any process

```
# Trying to find kafka 
$ ps ax | grep -i 'kafka'
```

```
$ tar -xzf tarFile.tgz
$ tar -zxf git-2.0.0.tar.g
you may v for verbose mode
$ tar -zxvf spark-2.3.0-bin-hadoop2.7.tgz -C sparkDownload/
```

grep command (**g**lobally search a **r**egular **e**xpression and **p**rint))

```
$ grep 'text' /folder/                  # search for lines containing 'text' in /folder/

$ grep "text" file.txt                  # in a file.txt
or $ grep 'text' file.txt
or $ grep text file.txt                 # quotes is optional, if not using regex patterns

$ grep -i text file.txt                 # case-insensitive (text, tExt, TEXT) 

$ grep -B5 -A5 "text" file.txt          # fetch 5 lines before and 5 lines after

$ grep -v "text" file.txt               # find any line NOT containing "text"
$ grep -vi fred /folder/                # adding case-insensitive 

$ grep '^text' /folder/                 # find 'test', but only at the start of a line
$ grep '[ABC]xyz' *                     # find Axyz or Bxyz or Cxyz
$ grep '[0-9][0-9][0-9]' *              # find three numbers in a row

$ find /folder/ -type f -exec grep -l 'text' {} \;     # get filenames under /folder/ containing 'text'
```

find command (this is a very powerful command)

```
$ find /folder/ -type f -exec grep -l 'text' {} \;     # get filenames under /folder/ containing 'text'
```

To find open port and close the port (e.g. 5307) from the terminal on Mac

```
$ sudo lsof -i :5307
$ sudo kill -9 PID
```

```
# give execute permission to sh file
$ chmod +x someScriot.sh
# to give read and execute permission to user
$ chmod u+rx someScriot.sh
```
