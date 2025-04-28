A statement is an arrangement of [expressions](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference") used to perform work (and may just be a simple expression). There are also some more complicated statements like "if" and "while".

## Define Statement

```
<define statement> ::= <type> <identifier> ['=' <expression>]

```

A define statement defines a single [variable](https://ck.uesp.net/wiki/Variable_Reference "Variable Reference") and, optionally, initializes it to a value. If a value is not given to it, it starts with the standard [default value](https://ck.uesp.net/wiki/Default_Value_Reference "Default Value Reference"). A variable defined inside a function does not conflict with a variable defined in another function. A variable defined in an if or while block will not conflict with a variable defined in another if or while block that is not a child or a parent of the block that defined it.

### Examples

```
; Create an integer variable named var that starts with the default value of 0
int var
```

```
; Create a float variable named seconds that starts with a default value
float seconds = CurrentTimeInMinutes() * 60.0f
```

## Assign Statement

```
<assign statement> ::= (<l-value> '=' <expression>) |
                       (<l-value> '+=' <expression>) |
                       (<l-value> '-=' <expression>) |
                       (<l-value> '*=' <expression>) |
                       (<l-value> '/=' <expression>) |
                       (<l-value> '%=' <expression>)
<l-value>          ::= ([<expression> '.'] <identifier>)
                       (<expression> '[' <expression> ']')

```

An assignment statement calculates the results of the expression to the left of the assignment operator, and variable referred to by the l-value, and either assigns the result to the l-value, or modifies the l-value by the result.

### Examples

```
; Assign 5 to x
x = 5

;This assignment is equivalent to x = x + 5 
x += 5

;This assignment is equivalent to x = x * (5 + 5)
x *= 5 + 5
```

```
; Increment the property by the calculated value
MyObject.MyProperty += CoolFunction() * 10
```

## Return Statement

```
'Return' [<expression>]

```

The return statement immediately stops running the function, calculates the result of the expression (if it exists), and returns it to the caller. The type the expression resolves to must match the return type of the function. If the function has no return type, then just use a return statement with no expression. If a function with a return type exits without a return statement, then None will be return (and a warning printed by the game if None is not allowed to be assigned to the return type)

### Examples

```
; Assuming the return type is int, return the value to the caller
Return 5
```

```
; Return immediately, returning nothing
Return
x = 5 ; This never runs, because execution has exited this function
```

## If Statement

```
<if statement> ::= 'if' <expression>
                     <statement>*
                   ['elseif' <expression>
                     <statement>*]*
                   ['else'
                     <statement>*]
                   'endIf'

```

The if statement calculates its expression and, if the result is true, runs the statements underneath it until it runs into an "elseif", "else", or "endif". If the expression's result is false, then it jumps down the if, checking each "elseif" as well until it hits an "else" (which then runs its statements) or an "endif". At each "elseif" encountered, it will check the expression and, if true, run the statements under it and if false, will jump to the next "elseif", "else", or "endIf".

### Examples

```
; If value is true, will set x to 1, otherwise it will do nothing
if (value)
  x = 1
endIf
```

```
; If myCoolValue is 20, will set x to 5, otherwise it will set it to 10
if (myCoolValue == 20)
  x = 5
else
  x = 10
endIf
```

```
; If the value is above 10 it will set x to 1, if it is below 10 it will set x to -1, otherwise it will set x to 0
if (value > 10)
  x = 1
elseif (value < 10)
  x = -1
else
  x = 0
endIf
```

```
; if the sum of x and y is less than 10, set z to 1, otherwise set z to -1.
if ((x + y) < 10)
    z = 1
else
    z = -1
endif
```

## While Statement

```
'while' <expression>
  <statement>*
'endWhile'

```

The while statement is a loop and will repeatedly execute the statements inside it until the expression is false.

### Examples

```
; Loop until x is 10
x = 0
while (x < 10)
  DoCoolStuff()
  x += 1
endWhile
```

### While and Variable Lifetime

Variables defined inside While loops have a lifetime of as many times as the loop runs, not a lifetime of each iteration of the loop as one might expect. This means that it is very important to always assign a value to variables defined inside a While loop, or avoid defining variables inside While loops altogether.

Here is an example to illustrate this potential pitfall.

```
int i = 0
while i < 5
    int j
    j += 1
    debug.trace("j = " + j)
endWhile
```

Here, j is defined inside the loop. Since we are calling "int j" each iteration, and since the default value of an integer is 0, we might expect output that resembles:

```
[06/04/2016 - 01:24:38PM] j = 1
[06/04/2016 - 01:24:38PM] j = 1
[06/04/2016 - 01:24:38PM] j = 1
[06/04/2016 - 01:24:38PM] j = 1
[06/04/2016 - 01:24:38PM] j = 1
```

However, since j's value is maintained across iterations of the loop, we instead get:

```
[06/04/2016 - 01:49:52PM] j = 1
[06/04/2016 - 01:49:52PM] j = 2
[06/04/2016 - 01:49:52PM] j = 3
[06/04/2016 - 01:49:52PM] j = 4
[06/04/2016 - 01:49:52PM] j = 5
```