In general C is for computer, en_US is for people in US who speak English (and other people who want the same behaviour).

The for computer means that the strings are sometime more standardized (but still in English), so an output of a program could be read from an other program. With en_US, strings could be improved, alphabetic order could be improved (maybe by new rules of Chicago rules of style, etc.). So more user-friendly, but possibly less stable. Note: locales are not just for translation of strings, but also for collation (alphabetic order, numbers (e.g. thousand separator), currency (I think it is safe to predict that $ and 2 decimal digits will remain), months, day of weeks, etc.

In your case, it is just the UTF-8 version of both locales.

In general it should not matter. I usually prefer en_US.UTF-8, but usually it doesn't matter, and in your case (server app), it should only change log and error messages (if you use locale.setlocale(). You should handle client locales inside your app. Programs that read from other programs should set C before opening the pipe, so it should not really matter.

As you see, probably it doesn't matter. You may also use POSIX locale, also define in Debian. You get the list of installed locales with locale -a.

Note: Micro-optimization will prescribe C/C.UTF-8 locale: no translation of files (gettext), and simple rules on collation and number formatting, but this should visible only on server side.

A number of commands have output of a guaranteed form (e.g. ps or df headers, date format) in the C or POSIX locale.

***
Refs

https://stackoverflow.com/questions/55673886/what-is-the-difference-between-c-utf-8-and-en-us-utf-8-locales