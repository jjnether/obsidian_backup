Papyrus supports five kinds of literal values: boolean, integer, float, string, and None.

## Boolean Literals

```
<boolean> ::= 'true' | 'false'

```

```
 if myBoolean == true
    ;do something
 endif
```

Boolean literals are simple, they are just true or false values.

## Integer Literals

```
<integer> ::= (['-'] <digit>+) | ('0x' (<digit>|<hex digit>)+)

```

```
 if count < 5
    ;do something
    count +=1
 endif
```

Integer literals are sequences of digits (0 though 9) optionally prefixed by a minus sign. If you want a hex number, prefix it with "0x". Valid hex digits are A through F (case-insensitive). Integers are 32-bits in size, signed, which means their valid range is −2,147,483,648 to 2,147,483,647.

### Examples

## Float Literals

```
<float> ::= ['-'] <digit>+ '.' <digit>+

```

```
 if myValue ==  5.123
    ;do something
 endif
```

  
Float literals are sequences of digits (0 through 9) optionally prefixed by a minus sign, and followed by a dot and another sequence of digits. Floats are 32-bits in size, and have a range of 1.175494351 E – 38 to 3.402823466 E + 38 with 7 significant digits. They match the [IEEE standard single type](http://en.wikipedia.org/wiki/IEEE_floating_point#Basic_formats) (23+1 significant bits and 8 exponent bits).

### Examples

## String Literals

```
<string> ::= '"' <anything but another ", \, newline, or linefeed> '"'

```

```
 string myText = "Hello World."
```

String literals are simply text surrounded by double quotes. Newlines, line feeds, quotes, and back slashes are not allowed in the string. If you want one of these special characters, or a tab, then you can use the following escape codes:

<table><tbody><tr><td>\n</td><td>Newline</td></tr><tr><td>\t</td><td>Tab</td></tr><tr><td>\\</td><td>Backslash</td></tr><tr><td>\"</td><td>Double quote</td></tr></tbody></table>

### Examples

```
"Hello, World!"
"" ; Empty string
"\\\n" ; a string with a backslash followed by a new line
```

### Case Insensitivity

Papyrus strings are always case-insensitive. Baked into every save file is a "string cache" that stores the first case-insensitive version of any string created in Papyrus. This means that the first time a string is created in memory, the casing of that string is the only case variant Papyrus will use in that save. This cache is shared between all scripts (and can even be seen in action in the Creation Kit! Try writing the string "true" or "jewelry" into a string property!). Also see the comment included at the top of the [StringUtil Script](https://ck.uesp.net/wiki/StringUtil_Script "StringUtil Script").

```
Debug.trace("wow") ; prints "wow"
Debug.trace("WoW") ; prints "wow", despite the different casing
Debug.trace("WOW") ; prints "wow", despite the different casing
Debug.trace("oh WOW") ; prints "oh WOW" because it's a new string

Debug.trace("trUE") ; prints "TRUE" because "TRUE" is (always?) the first version of 'true' encountered by the engine
```

## None Literal

```
None

```

The None literal simply represents 'nothing' for object types. (Similar to NULL in C) If you want to know if an object variable contains a valid object, just compare it to None.