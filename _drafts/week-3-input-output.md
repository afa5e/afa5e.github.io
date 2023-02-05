---
layout: post
title: Week 3 - Input/Outputs
categories: 23T1
expires: 2023-09-09 23:59:59 +1100
---

* TOC
{:toc}

## Input/Output
This week's lesson will cover input and output (IO) from both the terminal and 
the filesystem. This will include: `input()`, `open()`, and associated file 
functions.

## Special Characters
In Python, strings are stored as a list of individual characters, and each character is stored as an integer. Not only do we have alphanumeric symbolas and punctuation, but we also have some special characters. When we are printing text to the terminal, we sometimes need to print some characters that we cannot type with our keyboard. 

### ASCII
This mainly includes newlines, but as the terminal, and by extension Python, was designed to be backwards compatible with historic computing devices, there are some special characters that serve some outdated functions such as the `bell` character. These are represented by the ASCII (American Standard Code for Information Interchange) table:

[Skip table](#unicode)

| Symbol | Decimal |     Hex     | Description |
| ------ | ------- | ----------- | ----------- |
| `NUL`  | 0       | 0x00        | Null character |
| `SOH`  | 1       | 0x01        | Start of header |
| `STX`  | 2       | 0x02        | Start of text |
| `ETX`  | 3       | 0x03        | End of text |
| `EOT`  | 4       | 0x04        | End of transmission |
| `ENQ`  | 5       | 0x05        | Enquiry character |
| `ACK`  | 6       | 0x06        | Acknowledge |
| `BEL`  | 7       | 0x07        | Bell |
| `BS`   | 8       | 0x08        | Backspace |
| `HT`   | 9       | 0x09        | Horizontal tab |
| `LF`   | 10      | 0x0A        | Line feed |
| `VT`   | 11      | 0x0B        | Vertical tab |
| `FF`   | 12      | 0x0C        | Form feed |
| `CR`   | 13      | 0x0D        | Carriage return |
| `SO`   | 14      | 0x0E        | Shift out |
| `SI`   | 15      | 0x0F        | Shift in |
| `DLE`  | 16      | 0x10        | Data link escape |
| `DC1`  | 17      | 0x11        | Device control 1 |
| `DC2`  | 18      | 0x12        | Device control 2 |
| `DC3`  | 19      | 0x13        | Device control 3 |
| `DC4`  | 20      | 0x14        | Device control 4 |
| `NAK`  | 21      | 0x15        | Negative acknowledge |
| `SYN`  | 22      | 0x16        | Synchronous idle |
| `ETB`  | 23      | 0x17        | End of transmission block |
| `CAN`  | 24      | 0x18        | Cancel |
| `EM`   | 25      | 0x19        | End of medium |
| `SUB`  | 26      | 0x1A        | Substitute |
| `ESC`  | 27      | 0x1B        | Escape |
| `FS`   | 28      | 0x1C        | File separator |
| `GS`   | 29      | 0x1D        | Group separator |
| `RS`   | 30      | 0x1E        | Record separator |
| `US`   | 31      | 0x1F        | Unit separator |
| `SP`   | 32      | 0x20        | Space |
| `!`    | 33      | 0x21        | Exclamation mark |
| `"`    | 34      | 0x22        | Double quotes |
| `#`    | 35      | 0x23        | Hash symbol |
| `$`    | 36      | 0x24        | Dollar symbol |
| `%`    | 37      | 0x25        | Percent symbol |
| `&`    | 38      | 0x26        | Ampersand symbol |
| `'`    | 39      | 0x27        | Single quotes |
| `(`    | 40      | 0x28        | Left parenthesis |
| `)`    | 41      | 0x29        | Right parenthesis |
| `*`    | 42      | 0x2A        | Asterisk symbol |
| `+`    | 43      | 0x2B        | Plus symbol |
| `,`    | 44      | 0x2C        | Comma |
| `-`    | 45      | 0x2D        | Hyphen |
| `.`    | 46      | 0x2E        | Period |
| `/`    | 47      | 0x2F        | Slash |
| `0`    | 48      | 0x30        | Zero |
| `1`    | 49      | 0x31        | One |
| `2`    | 50      | 0x32        | Two |
| `3`    | 51      | 0x33        | Three |
| `4`    | 52      | 0x34        | Four |
| `5`    | 53      | 0x35        | Five |
| `6`    | 54      | 0x36        | Six |
| `7`    | 55      | 0x37        | Seven |
| `8`    | 56      | 0x38        | Eight |
| `9`    | 57      | 0x39        | Nine |
| `:`    | 58      | 0x3A        | Colon |
| `;`    | 59      | 0x3B        | Semicolon |
| `<`    | 60      | 0x3C        | Less than symbol |
| `=`    | 61      | 0x3D        | Equal symbol |
| `>`    | 62      | 0x3E        | Greater than symbol |
| `?`    | 63      | 0x3F        | Question mark |
| `@`    | 64      | 0x40        | At symbol |
| `A`    | 65      | 0x41        | Capital letter A |
| `B`    | 66      | 0x42        | Capital letter B |
| `C`    | 67      | 0x43        | Capital letter C |
| `D`    | 68      | 0x44        | Capital letter D |
| `E`    | 69      | 0x45        | Capital letter E |
| `F`    | 70      | 0x46        | Capital letter F |
| `G`    | 71      | 0x47        | Capital letter G |
| `H`    | 72      | 0x48        | Capital letter H |
| `I`    | 73      | 0x49        | Capital letter I |
| `J`    | 74      | 0x4A        | Capital letter J |
| `K`    | 75      | 0x4B        | Capital letter K |
| `L`    | 76      | 0x4C        | Capital letter L |
| `M`    | 77      | 0x4D        | Capital letter M |
| `N`    | 78      | 0x4E        | Capital letter N |
| `O`    | 79      | 0x4F        | Capital letter O |
| `P`    | 80      | 0x50        | Capital letter P |
| `Q`    | 81      | 0x51        | Capital letter Q |
| `R`    | 82      | 0x52        | Capital letter R |
| `S`    | 83      | 0x53        | Capital letter S |
| `T`    | 84      | 0x54        | Capital letter T |
| `U`    | 85      | 0x55        | Capital letter U |
| `V`    | 86      | 0x56        | Capital letter V |
| `W`    | 87      | 0x57        | Capital letter W |
| `X`    | 88      | 0x58        | Capital letter X |
| `Y`    | 89      | 0x59        | Capital letter Y |
| `Z`    | 90      | 0x5A        | Capital letter Z |
| `[`    | 91      | 0x5B        | Left bracket |
| `\`    | 92      | 0x5C        | Backslash |
| `]`    | 93      | 0x5D        | Right bracket |
| `^`    | 94      | 0x5E        | Caret symbol |
| `_`    | 95      | 0x5F        | Underscore |
| <code>`</code> | 96 | 0x60     | Backquote |
| `a`    | 97      | 0x61        | Lowercase letter a |
| `b`    | 98      | 0x62        | Lowercase letter b |
| `c`    | 99      | 0x63        | Lowercase letter c |
| `d`    | 100     | 0x64        | Lowercase letter d |
| `e`    | 101     | 0x65        | Lowercase letter e |
| `f`    | 102     | 0x66        | Lowercase letter f |
| `g`    | 103     | 0x67        | Lowercase letter g |
| `h`    | 104     | 0x68        | Lowercase letter h |
| `i`    | 105     | 0x69        | Lowercase letter i |
| `j`    | 106     | 0x6A        | Lowercase letter j |
| `k`    | 107     | 0x6B        | Lowercase letter k |
| `l`    | 108     | 0x6C        | Lowercase letter l |
| `m`    | 109     | 0x6D        | Lowercase letter m |
| `n`    | 110     | 0x6E        | Lowercase letter n |
| `o`    | 111     | 0x6F        | Lowercase letter o |
| `p`    | 112     | 0x70        | Lowercase letter p |
| `q`    | 113     | 0x71        | Lowercase letter q |
| `r`    | 114     | 0x72        | Lowercase letter r |
| `s`    | 115     | 0x73        | Lowercase letter s |
| `t`    | 116     | 0x74        | Lowercase letter t |
| `u`    | 117     | 0x75        | Lowercase letter u |
| `v`    | 118     | 0x76        | Lowercase letter v |
| `w`    | 119     | 0x77        | Lowercase letter w |
| `x`    | 120     | 0x78        | Lowercase letter x |
| `y`    | 121     | 0x79        | Lowercase letter y |
| `z`    | 122     | 0x7A        | Lowercase letter z |
| `{`    | 123     | 0x7B        | Left brace |
| `|`    | 124     | 0x7C        | Vertical bar |
| `}`    | 125     | 0x7D        | Right brace |
| `~`    | 126     | 0x7E        | Tilde |
| `DEL`  | 127     | 0x7F        | Delete character |

### Unicode
While the ASCII table covers all of the alphanumeric symbols and most other 
punctuation that is used, this is only suitable for the English alphabet, there 
is no support for other languages or scripts with other symbols. To solve this, we
can use Unicode, which is backwards compatible with ASCII but uses more memory per
character.

## Terminal IO
As our code is being run in the terminal, we will need to be able to interact with 
it. To do this, we will be using a variety of different functions that not only 
allows us to do basic IO operations, but can also allow complex formatting.

### Input
As we should all be familiar now, the function to get an input from the terminal is 
the `input()` function. This function has no parameters, and returns the input from 
the terminal as a string. This means that we need to assign the returned value to a 
variable to store the input. Another use for the input is to hold a terminal window 
open at the end of a program execution.

```python
# Saving input from the terminal
variable = input()

# Holding the terminal window open does not need us to save the input
# This should be the last line of code in the file.
input()
```

### Output

#### Print()
Terminal output can be accomplished mainly through the `print()` function, 
allowing us to print text to the terminal. When we are using the `print()` 
function, there are some arguments that we need to give it first: what we 
are printing, *seperator*, *ending* and *file*. (Italicised arguments are 
optional)

Not only can we print out a single string, but we can also print out multiple 
objects, such as strings, numbers and variables with one function call. We do 
this by calling the print function with multiple objects separated by commas. 
This will be formatted in the terminal with a space separating them by default. 
We can change with with the `sep` argument.

After each print call, by default a newline will be added, but if we want to 
change this we can use the `end` argument.

```python
# Printing out a single string
# Hello World!
print("Hello World!")

# Printing out a variable
# Python 3.10
text = "Python 3.10"
print(text)

# Printing out multiple objects
# Welcome to Python 3.10
print("Welcome to", text)

# Printing out multiple objects with no separator
# Welcome toPython 3.10
print("Welcome to", text, sep = "")

# Printing out without a newline terminator
print("Hello", end = "")
```

#### Chr()
We can convert each ASCII or Unicode decimal code to the associated character for us to print with the `chr()` function.