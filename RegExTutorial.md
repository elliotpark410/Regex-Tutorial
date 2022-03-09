# Regular Expressions Tutorial

As you probably know, there are many ways to validate a string to verify that it contains the characters required. In fact, JavaScript has many useful methods that can check if a string contains a certain letter or phrase. You can use methods like `.includes()`, `.startsWith()`, or `.endsWith()`, but the downside with these methods is that they are limited to direct matches. A more flexible way to validate strings is with regular expressions. Regular expressions (aka RegEx) allows us to check for patterns in text strings, and it is particularly useful for search operations like searching for phone numbers written multiple different ways, e.g. (123)456-7890 or 123.456.7890 or 123-456-7890. 

## Summary

In this tutorial, I will explain how you can use RegEx for validating an email address. The code to verify that a user entered a valid email address will look something like this:

“Matching an Email”
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
These characters are actually a search pattern which translates to:

* The string begins with any lowercase letter between a–z

* The string can contain any number between 0–9

* The string can contain an underscore `_`, slash `/`, period`.`, or hyphen`-`

* The string contains an at `@` symbol

* The string can contain digits, any lowercase letter between a-z, period`.`, or hyphen`-`

* The string contains a perod `.` symbol

* The string ends with any lowercase letter between a-z and is 2-6 characters long


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)

## Regex Components

Before diving into RegEx components, it's important to note that RegEx is case-sensitive and it is considered a literal, so the pattern must be wrapped in slash characters `/`.

### Anchors

The characters `^` and `$` are considered anchors. The `^` anchor signifies a string that begins with the characters that follow it. For example, `^The` will match with `"The"` or `"The code"`, but it won't match with `"the"`. The `$` anchor signifies a string that ends with the characters that precede it. For example, `ing$` will match with `"testing"` or `"thing"`.

### Quantifiers

In the code shown in the summary section, you will see `{2,6}` which is a quantifier that requires the string to be between 2-6 characters long. A quantifier sets the limits of the string that your RegEx matches. They usually include the minimum and maximum number of characters that your RegEx is looking for.

### Grouping Constructs

One of the cool things about RegEx is that you can check multiple parts of a string to determine whether different sections fulfill different requirements. You achieve this with grouping constructs.

The primary way you group a section is by using parentheses `()`. Each section within parentheses is known as a subexpression. For example `(abc):(xyz)` has one subexpression that is looking for a part of the string that matches the string `"abc"`. The second subexpression is looking for `"xyz"`. In between the subexpressions, we have a colon `:`, therefore, the string `"abc:xyz"` would match, but the string `"acb:xyz"` would not. 

### Bracket Expressions

Bracket Expressions are anything inside square brackets `[]` and it is used to represent a range of characters. For example, `[abc]` will look for a string that includes `a` or `b` or `c`, regardless of the length of the string. So all of the following examples would match: `"aaa"`, `"bin"`, `"court"`, `"abracadabra"`, or `"bca"`.

Additionally, you can use a hyphen `-` between alphanumeric characters to represent a range of possible characters. For example, `[a-d]` and `[abcd]` will do the same thing. The same applies for numbers. For example, `[0-2]` and `[012]` will do the same thing.

The code under “Matching an Email” includes `[a-z0-9_\.-]` which means there will be a match for any string that includes any combination of lowercase letters between a and z, any number between 0 and 9, and the special characters of an underscore, slash, period, or hyphen. The characters can be in any order and this pattern does not require the string to meet all of these requirements, it can meet any of them.

### Character Classes

A character class in RegEx defines a set of characters, any one of which can occur in an input string to fulfill a match. Here are some common character classes: 

* `.` - Matches any character except the newline character `\n`

* `\d` - Matches any Arabic numeral digit. This class is equivalent to the bracket expression `[0-9]`

* `\w` - Matches any alphanumeric character from the basic Latin alphabet, including the underscore `_`. This class is equivalent to the bracket expression `[A-Za-z0-9_]`

* `\s` - Matches a single whitespace character, including tabs and line breaks

### Character Escapes

The backslash `\` in RegEx escapes a character that otherwise would be interpreted literally. For example, let's say that I want to `console.log("This is an "escape" character")` the code won't work as intended becaause as soon as the browser encounters quote `"` before `escape`, then it will think that the string has finished. The code `console.log("This is an \"escape"\ character")` will work as intended because it knows the backslash tells the browser not to interpret the characters between it. 

## Author

Written by Elliot Park
<br>
[Github Profile](https://github.com/elliotpark410)
<br>
[Github Repo](https://github.com/elliotpark410/Regex-Tutorial)
