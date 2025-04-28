The following are valid operators in the Papyrus language:

```
() [] ,  =  +  -
*  /  %  .  "" !
== != >  <  >= <=
|| && += -= *= /=
%= as

```

## Parenthesis

```
()

```

Parenthesis, when surrounding an [expression](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference"), will cause that expression to be evaluated before any operators outside of the parenthesis. When following a [function](https://ck.uesp.net/wiki/Function_Reference "Function Reference") name, they denote the parameter list for the function.

Examples:

```
; i will get the value of 9
i = (1 + 2) * 3
```

```
; call the function MyFunction with a parameter of 10
MyFunction(10)
```

## Square Brackets

```
[]

```

Square brackets are used for [arrays](https://ck.uesp.net/wiki/Array_Reference "Array Reference"). Either for accessing a specific array element, denoting the size of an array for a new one, or for denoting that a type is an array type.

Examples:

```
; i whatever is in element 0 of the array
i = myArray[0]
```

```
; define an array of size 10
int[] myArray = new int[10]
```

## Comma

```
,

```

The comma operator separates parameters in a [function](https://ck.uesp.net/wiki/Function_Reference "Function Reference") definition, or a function call.

Examples:

```
; call the function MyFunction with a parameter of 10 and 20
MyFunction(10, 20)
```

## Math Operators

```
+ - * / %

```

Math operators perform some sort of operation on the two [expressions](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference") it sits between. Papyrus supports assignment, addition, subtraction, multiplication, division, and integer modulus. The minus sign is also used for negation (also known as unary minus). The addition operator can also be used to concatenate ('paste together') strings. If you try to divide by zero or find the remainder of a divide by zero through modulus the result is undefined and the game will spit an error to the log. Integer division will return an integer value and discard any remainders.

Examples:

```
; i will get the value of 7
i = 1 + 2 * 3
```

```
; i will get the value of 1
i = 9 % 4

; i will get the value of -3
i = -7 % 4
```

```
; i will get the value of 4
i = 29 / 6
```

```
; i will get the string "Hello World"
i = "Hello " + "World"
```

  
The next example _will not compile_ as perhaps expected because the minus sign is also used for negation

```
int x
int y
x = 22
y = x-1 ; compiler: no viable alternative at input 'x'
```

## Dot

```
.

```

The dot operator goes after a variable name to let you call [functions](https://ck.uesp.net/wiki/Function_Reference "Function Reference") on it, or to access [properties](https://ck.uesp.net/wiki/Property_Reference "Property Reference").

Examples:

```
; Call the function on the variable
myVariable.MyFunction()
```

```
; Set the property to 10
myVariable.MyProperty = 10
```

## Double Quotes

```
""

```

Double quotes surround a [string literal](https://ck.uesp.net/wiki/Literals_Reference#String_Literals "Literals Reference").

Examples:

```
; A basic hello world string
hello = "Hello World!"
```

## Logical Operators

```
! || &&

```

Logical operators evaluate to true or false values, based on their [expressions](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference").

-   The NOT operator (!) will be true if its single expression (to the right of the operator) is false, and false if it is true.
-   The OR operator (||) will be true if one of the expressions to its left and right are true, and will short-circuit if the left expression is true (it will not evaluate the right expression at all).
-   Note that If A == (B || C || D) is a common mistake, it should be If A == B || A == C || A == D, read more [here](http://forums.bethsoft.com/topic/1460024-operator-or-question/)
-   The AND operator (&&) will be true if both of the expressions to its left and right are true, and will short-circuit if the left expression is false (it will not evaluate the right expression at all).

Examples:

```
; i gets true if both a and b are true
i = a && b
```

```
; i gets true if a is false
i = !a
```

```
; short-circuit can make sure a reference exists before doing something with it
if ref && ref.HasKeyword(VendorItemClutter)
```

## Comparison Operators

```
== != < > <= >=

```

The comparison operators compare both [expressions](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference") to their left and right, and return a boolean value based on the operator used. If floating-point values are being compared, a tiny epsilon value is accounted for to conteract floating-point error.

-   Equality (==) returns true if both expressions have equal values.
-   Inequality (!=) returns true if both expressions have inequal values.
-   Less-than (<) returns true if the left expression's value is smaller then the right expression's value.
-   Greater-than (>) returns true if the left expression's value is larger then the right expression's value.
-   Less-than or equal to (<=) returns true if the left expression's value is smaller than or equal to the right expression's value.
-   Greater-than or equal to (>=) returns true if the left expression's value is larger than or equal to the right expression's value.

Examples:

```
; i will get true if a is greater then b
i = a > b
```

```
; i will get true if a is equal to b
i = a == b
```

## Assignment Operators

```
= += -= *= /= %=

```

Assignment operators assign the value from the right [expression](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference") to the [variable](https://ck.uesp.net/wiki/Variable_Reference "Variable Reference") (or [property](https://ck.uesp.net/wiki/Property_Reference "Property Reference")) from the left expression. If the equal sign starts with one of the math operators, then the right expression's value will be added to the current value of the left expression, and then assigned to the left expression. Note that if the left expression is a property, then both the property's get and set functions will be called.

Examples:

```
; add 1 to the current value of i, and assign it to i
i += 1
```

Only the = operator can be used to assign values to an [array](https://ck.uesp.net/wiki/Arrays_(Papyrus) "Arrays (Papyrus)") element:

```
 ; Will not compile, as the compiler doesn't know how to handle it.
 myArray[3] += 5
```

## Cast

```
as

```

The [cast](https://ck.uesp.net/wiki/Cast_Reference "Cast Reference") operator attempts to cast the value from the left [expression](https://ck.uesp.net/wiki/Expression_Reference "Expression Reference") to the type to the right of it, and returns the resulting value.

Examples:

```
; cast a to a float and assign it to i
i = a as float
```

## Operator Precedence

Operator precedence is listed in the following table, from highest to lowest:

<table><tbody><tr><td>()</td><td>Mathematical parenthesis</td></tr><tr><td>.</td><td>Dot operator (for accessing functions and properties)</td></tr><tr><td>as</td><td>Cast operator</td></tr><tr><td>-&nbsp;!</td><td>Unary minus and logical NOT</td></tr><tr><td>* /&nbsp;%</td><td>Multiplication, division, and modulus</td></tr><tr><td>+ -</td><td>Addition and subtraction</td></tr><tr><td>==&nbsp;!= &gt; &lt; &gt;= &lt;=</td><td>Comparison operators</td></tr><tr><td>&amp;&amp;</td><td>Logical AND</td></tr><tr><td>||</td><td>Logical OR</td></tr><tr><td>= += -= *= /=&nbsp;%=</td><td>Assignment</td></tr></tbody></table>