# locale on OS

## All parts

* operation system
* programming language
* database

## Introduction

Locales are used by glibc and other locale-aware programs or libraries for rendering text, correctly displaying regional monetary values, time and date formats, alphabetic idiosyncrasies, and other locale-specific standards.

**locale** is a set of parameters that defines the user's language, region and any special variant preferences that the user wants to see in their user interface.

```console
$ locale

LANG=
LC_COLLATE="C"
LC_CTYPE="C"
LC_MESSAGES="C"
LC_MONETARY="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_ALL=
```

## locale values

`<LANG>_<COUNTRY>.<CHARSET>@<MODIFIER>`

e.g. `zh_CN.UTF-8`, `en_GB.ISO-8859-1`, `de_DE.UTF-8@euro`

## locale priority

* LC_ALL
* LC_*
* LANG default value for LC_*

## Locale and environment variables

### All locale variables does not exists in environment variables

```console
$ env

TERM_SESSION_ID=w0t0p0:E0DD8416-4A1F-4693-8602-6F857738E637
SSH_AUTH_SOCK=/private/tmp/com.apple.launchd.KBe8qw1ZNW/Listeners
LC_TERMINAL_VERSION=3.3.11
Apple_PubSub_Socket_Render=/private/tmp/com.apple.launchd.LO62KZ1KMU/Render
COLORFGBG=7;0
ITERM_PROFILE=Default
XPC_FLAGS=0x0
PWD=/Users/zhen.tian
SHELL=/bin/zsh
TERM_PROGRAM_VERSION=3.3.11
TERM_PROGRAM=iTerm.app
PATH=/usr/local/opt/ruby/bin:/Users/zhen.tian/.gem/ruby/2.7.0/bin:/Users/zhen.tian/.cargo/bin:/usr/local/go/bin:/usr/local/sbin:/usr/local/gnupg-2.2/bin:/Library/Frameworks/Python.framework/Versions/3.8/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
LC_TERMINAL=iTerm2
COLORTERM=truecolor
TERM=xterm-256color
HOME=/Users/zhen.tian
TMPDIR=/var/folders/5x/_dsq5j616b167_j2rn7tdbf80000gn/T/
USER=zhen.tian
XPC_SERVICE_NAME=0
LOGNAME=zhen.tian
__CF_USER_TEXT_ENCODING=0x0:0:0
ITERM_SESSION_ID=w0t0p0:E0DD8416-4A1F-4693-8602-6F857738E637
SHLVL=1
OLDPWD=/Users/zhen.tian/Downloads
ZSH=/Users/zhen.tian/.oh-my-zsh
PAGER=less
LESS=-R
LSCOLORS=Gxfxcxdxbxegedabagacad
_=/usr/bin/env
```

## SSH SendEnv / AcceptEnv

...

## Use locale

```console
$ date
Thu Jul  2 00:21:20 CST 2020

$ LC_TIME=zh_CN.UTF-8 date
2020年 7月 2日 星期四 00时21分43秒 CST
```

## C and POSIX

The C locale, also known as the POSIX locale, is the POSIX system default locale for all POSIX-compliant systems.

POSIX stands for Portable Operating System Interface, for maintaining compatibility between operating systems.

POSIX defines the API, along with command line shells and utility interfaces, for software compatibility with variants of Unix and other operating systems.

## LC_COLLATE

### string sorting

on Ubuntu, macOS sort uses same locale!

```console
$ LC_COLLATE=en_US.UTF-8 sort <<< $'a\nb\nA\nB'
a
A
b
B

$ LC_COLLATE=C.UTF-8 sort <<< $'a\nb\nA\nB'
A
B
a
b
```

### regular expression

`[a-z]` is not mean `[abcdefgh...z]`, it could be `[aBbCcDd...Zz]` under some locales

## LC_CTYPE

处理字符的程序要对一个字符进行分类，是数字、字母、空格、大写、小写转换等。根据locale选择不同，对一个字符的判断可能不一样，具体的，由LC_CTYPE的值决定。

...
