# session讲locale

* operation system
* programming language
* database

## operation system

**locale** is a set of parameters that defines the user's language, region and any special variant preferences that the user wants to see in their user interface.

### What's inside

* Number format
* Currency
* Date format
* String collation
* Paper size
* ...

Notice: close terminal sets locale variables automatically

```console
$ locale

# macOS
LANG=
LC_COLLATE="C"
LC_CTYPE="UTF-8"
LC_MESSAGES="C"
LC_MONETARY="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_ALL=

# Ubuntu (terminal set locale variables)
LANG=C.UTF-8
LANGUAGE=
LC_CTYPE=C.UTF-8
LC_NUMERIC="C.UTF-8"
LC_TIME="C.UTF-8"
LC_COLLATE="C.UTF-8"
LC_MONETARY="C.UTF-8"
LC_MESSAGES="C.UTF-8"
LC_PAPER="C.UTF-8"
LC_NAME="C.UTF-8"
LC_ADDRESS="C.UTF-8"
LC_TELEPHONE="C.UTF-8"
LC_MEASUREMENT="C.UTF-8"
LC_IDENTIFICATION="C.UTF-8"
LC_ALL=

# Ubuntu (not set locale)
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

program references `LANG` to display error msg, instructions, collating sequences, date formats, and so forth

`LC_ALL` override all other `LC_*`

`LC_COLLATE` It determines collation information for regular expressions and sorting, including equivalence classes and multi-character collating elements

### examples for LANG

```console
# LANG=C.UTF-8
$ date
Wed Jun 17 15:42:22 UTC 2020

$ sudo locale-gen zh_CN.UTF-8
Generating locales (this might take a while)...
  zh_CN.UTF-8... done
Generation complete.

$ LANG=zh_CN.UTF-8 date
2020年 06月 17日 星期三 15:43:09 UTC

$ LANG=C.UTF-8 sort <<< $'a\nb\nA\nB'
A
B
a
b

$ LANG=zh_CN.UTF-8 sort <<< $'a\nb\nA\nB'
a
A
b
B
```

### locale identifier

<LANG>_<COUNTRY>

e.g. `zh_CN`, `en_US`

### POSIX locale identifier
included character set, e.g. `zh_CN.UTF-8`

### POSIX
APIs between OS.

Not to be confused with Unix, Unix-like, or Linux.

***
Refs

https://www.cnblogs.com/xlmeng1988/archive/2013/01/16/locale.html
http://blog.remibergsma.com/2012/07/10/setting-locales-correctly-on-mac-osx-terminal-application/
