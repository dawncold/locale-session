Programs that work with characters and strings often need to classify a character—is it alphabetic, is it a digit, is it whitespace, and so on—and perform case conversion operations on characters. The functions in the header file ctype.h are provided for this purpose.

Since the choice of locale and character set can alter the classifications of particular character codes, all of these functions are affected by the current locale. (More precisely, they are affected by the locale currently selected for character classification—the LC_CTYPE category

处理字符的程序要对一个字符进行分类，是数字、字母、空格、大写、小写转换等。根据locale选择不同，对一个字符的判断可能不一样，具体的，由LC_CTYPE的值决定。

***
Refs:

https://www.gnu.org/software/libc/manual/html_node/Character-Handling.html#Character-Handling