# E-mail Regex Tutorial

Welcome to my tutorial of regular expressions (REGEX). REGEX is defined as a sequence of characters that is used to designate a specific search pattern. REGEX is used to make searching, replacing, validating, and other common analysis patterns, easier and faster to use.

## Summary

In this tutorial, the focus will be geared towards the different characters/expressions used with examples that will give better insight on its' functionality. The tutorial will also give real life use cases through examples focused on matching an email.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors are used to search for matching positions in an expression. They can be used before or after characters. Commonly used symbols are:

`^` - carat, hat, exponent

`$` - dollar

The carat symbol is used for matching a start position. Example:

`^Apple` - Having the carat symbol in front of apple, the expression will look for any matching string that begins with Apple.

The dollar symbol is used for matching an end position. Example:

`air$` - Placing the dollar symbol at the end of air, the expression will look for any matching string that ends with air.

An example where using both the carat and dollar symbols:

`^Apple Air$` - Here the expression will look for any matching string that starts with apple and ends with air. A matching string example would be `Apple MacBook Air`

### Quantifiers

Quantifiers are used to look for matches with a specific quantity of characters. Quantifier symbols are placed immediately after the character in question. If a quantifier symbol is intented to look for 2 or more sequencial characters, then curly brackets or paranthesis are used followed immediately by a quantifier symbol. Common symbols are:

`+` - plus

`*` - asterisk

`?` - question mark

`()` - parernthesis

`{}` - curly braces

The plus symbol is used to look for one or more instances of a matching character. Consider the following:

`123+` - The regex will look for string matches where "12" is followed by at least one or more instances of "3". 

The asterisk symbol is used to look for zero or more instances of a matching character. Consider the following:

`abc*` - The regex will look for string matches where "ab" is followed by zero instances of "c" AND where "ab" is followed by one or more instances of "c". 

The question mark symbol is used to look for zero or one instances of a matching character. Consider the following:

`goodbye?` - The regex will look for string matches where "goodby" is followed by zero or one instances of "e".  

The parenthesis symbols are used to group sequencial characters for a quanitier. Consider the following:

`(abc)` - The regex would now consider "abc" as the set of characters to look for matches of depending on the quantifier that would immediately follow the closing parenthesis symbol.

The curly brackets/braces are used to look for specific quantities of character(s) instances. Consider the following:

`abc{5}` - The regex would search for matching instances where "ab" is followed by exactly five instances of "c".

`abc{5,}` - The regex would search for matching instances where "ab" is followed by five instances or more of "c".

`abc{1-5}` -  The regex would search for matching instances where "ab" is followed by one instance of "c" or more, but not containing more than five instances of "c".

### OR Operator

The OR operator is used to look for matches with one or another character. Commonly used symbols:

`( | )` - parenthesis vertical pipe parenthesis

`[]` - square brackets

The parenthesis vertical pipe parenthesis symbols look for matches of a character that directly preceeds the pipe OR a character that directly follows the pipe.

`a(b|c)` - The regex would search for matching instances where "a" immeidately followed by either "b" or "c".

The square brackets look for matches of one or the other characters inside the brackets.

`a[bc]` - The regex would search for matching instances of "a" immediately followed by either "b" or "c" but the "b" or "c" would not be captured.

### Character Classes

Character classes are used for searching specific types  of characters or categories. Commonly used symbols:

`/d` - digit character

`/w` - word character

`/s` - whitespace character

`.` - period character

The digit character will search for matches of a single character that is a digit. Example:

`abc\d` - The regex will search for any instance of a single digit that immediately follows "abc".

The word character will search for matches of an alphanumeric character (which includes the underscore symbol). Example:

`abc\w` - The regex will search for any instance of an alphanumeric character the immediately follows "abc".

The whitespace character will search for matches of any whitespace (which includes tabs and line breaks). Consider the following:

`abc\s` - The regex will search for any instance of whitespace that immediately follows "abc".

The period symbol will search for matches of any character. Example:

`sh.rt` - The regex matches shirt, short, and any other character between sh and rt.

### Flags

Flags are used for changing the default search pattern. Common symbols:

`i` - ignore casing

`g` - search all occurances

`m` - multiple line

The ignore casing removes case sensitvity.

The search all occurances will change to search for all possible matches.

The multiple line allows anchors to match at the beginning and end of each line.

### Grouping and Capturing

Grouping and capturing is used for treating multiple characters as a single unit. Common symbols/syntax:

`()` - parenthesis

`?:` - disable capture group

`?<>` - name group

The parenthesis create a capture group. Consider the following:

`a(bc)` - the regex will look for all instances of "a" that are followed by "bc".

The disable capture group removes the capture group from being included in the match results. Consider the following:

`1(?:23)*` - the regex will look for all instances of "1" that preceed "23" but the "23" is not included in the result. 

The name group provides a name for the character(s) that is between the less than greater than symbols. Consider the following:

`a(?<foo>bc)` - the regex will look for all instances of "a" that is followed by "bc" and the resulting match(s) is a value and the key is foo.

### Bracket Expressions

Bracket Expressions are used for matching a sepcific set of single characters or it may match a set of characters. 

See the following commonly used symbol:

`[]` - square brackets

The square brackets match string values based on the characters inside the brackets. Consider the following:

`[abc]` - the regex will search for string matches that contain "a" or "a b" or "a c".

`[0-9]` - the regex will search for string matches that contains a character from 0-9.

### Greedy and Lazy Match

Greedy and Lazy are terms used to describe the size of a matched result. Quantifiers * and {} are considered greedy because matches can be expanded upon as far as possible. For lazy matched, greedy quantifiers are refined to render more specific results. Adding a `?` symbol can be used to refine the match results.

`<h1> Hello World </h1>` - if a regex such as <.+> was used, the match would render the entire string value because it includes all characters between the very first less than symbol and the very last greater than symbol.

HOWEVER

if a regex such as `<.+?>` was used, the match would render only the `<h1>` and `</h1>` from the string because the ? is refining the search to only include all characters but from within a given set of greater than less than symbols.

### Boundaries

Boundaries are used for refining the match results to look for characters that have a specific type of character before it or after it. Commonly usded symbols:

`\B` - non-word border

`\b` - word border

The non-word border refines match results to include results with characters that are not a word, i.e. special characters $=(@-%++). The word border, on the other hand, includes letters, digits, and/or underscore characters.

`\b123\b` - the regex will search for all instances of "123" but only if a non-word character preceeds the beginning of the string AND another follows the end of the string.

`\B123\B` - the regex will search for all instances of "123" but only if a word character preceeds the beginning of the string AND another follows the end of the string.

### Back-references

Back-references are used for reusing previous capturing groups by referencing them again later in the regex.


See the following for commonly used symbol:

`\1` - back slash number


Back slash number symbol would become the indicator reference for a previously captured group. Consider the following:

`([xyz])\1` - the regex would indentify "xyz" as the captured group and the "\1" would actually be considered "xyz" again when being used for searching matches.

### Look-ahead and Look-behind

Look-ahead and Look-behind are used for modifying results to consider if specified characters are directly following or preceding a matching character.
Commonly used symbols:

`(?=)` - look ahead

`(?<=)` - look behind

The look-ahead will search for matches and then verify the following characters, while the look-behind will search for matches and then verify the preceding characters. Example:

`a(?=b)` - this regex will search for instances of "a", but only if the following character is "b".

`(?<=a>)b` - this regex will search for instances of "a", but only if the preceding character is "a".

## Final Example

This final example will encompass everything above. See if you are able to determine what is being used.

Matching an E-mail:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`




List of symbols used for email matching.

```
/ - denotes the boundary of the regex
^ - meta escape that asserts the starting position of the string
( - begins first capturing group
[ -begins character class
a-z - matches any single character "a" through "z"
0-9 - matches any single digit "0" through "9"
_ - matches an underscore
\. - matches a . symbol
- - matches a - symbol
] - end character class
+ - greedy quantifier to include any number of preceding character class matches
) - end first capturing group
@ - matches a @ symbol
( - begin second capturing group
[ - begin character class
\d - any single digit
a-z - matches any single character "a" through "z"
\. - matches a . symbol
- - matches a - symbol
] - end character class
+ - greedy quantifier to include an number of preciding character class matches
) - end second capture group
\. - matches a . symbol
( - begin third capture group
[ - begin character class
a-z - matches any single character "a" through "z"
\. - matches a . symbol
] - end character class
{2,6} - matches previous character class between 2-6 times
) - end third capture group
$ - meta escape that asserts the ending position of the string
/ - denotes the boundary of the regex
```

## Author

Mihir Patel
[GitHub User Mpz45:](https://github.com/Mpz45/gistTut)
