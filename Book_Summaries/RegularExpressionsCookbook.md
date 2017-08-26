# Regular Expressions CookBook

---------
[Amazon Link](https://www.amazon.co.uk/Regular-Expressions-Cookbook-Jan-Goyvaerts-ebook/dp/B008Y4OP1O/ref=sr_1_1?ie=UTF8&qid=1494148633&sr=8-1&keywords=regular+expressions+cookbook)

-----

## Regular Expressions Defined

* A regular expression is a specific kind of text pattern
* Used by comparing a input to a pattern/expression

-----

## Tools for writing regular expressions

* RegexBuddy
* RegexPal
* RegexMagic
* RegexPlanet
* regex.larsolavtorvik.com
* Nregex
* Rubular
* myregexp.com
* Expresso
* The Regularor
* SDL Regex Fuzzer
* grep
* powerGREP
* RegexRenamer

--------

## Basic Regular Expression Skills

* Matching a string can be met with normal characters
* `\Q ....  \E` is called a block escape/ This supresses all the meta characters including blackslash from `\Q` until `\E`
* Regexes are case sensitive by default
* `(?i)` is used to turn off case sensitivity. Place this before the regex you want to be case insensitive. The brackets are manditory

## Matching Nonprintable Characters

* `\a` matches bell
* `\e` matches escape
* `\f` matches form feed
* `\n` matches line feed / new line
* `\r` matches carriage return
* `\t` matches horizontal tab
* `\v` matches vertical tab
* You can also use the 7-bit character set to match all possible control characters. Please see tables online

## Match One Of Many Characters

* `[xyz]` Allows you to match either x or y. This is known as a character class
* There is no limit to the number of characters you can have in a character class
* `\`,`^`,`-`and `]` are the only special characters in the character class
* `\` escapes the character that follows it, which can be a single characte or the start/end of a range
* Alphanumeric characters cannot be escaped with a `\`
* `^` negates the character class if you place it immediately after the opening bracket. This makes the character class match any character that is **NOT** in the list
* `-` creates a range between two characters, such as `a-z`. This matches all the characters in the range, including the start and end characters

## Short Hand Character Classes

* `\d` or `\D` matches a single digit, however `\D` matches any character that is not a digit
* `\w` matches a single word character. This is when a character is part of a word, including letters, digits and the underscore
* `\W` matches any character that is not part of such a word
* `\s` matches any white space character, including spaces, tabs and line breaks
* `\S` matches any character not matched by `\s`

## Match Any Character

* `.` matches any character including line breaks
* The dot is often overused. It should rarely be used.

## Match Something at the Start and/or End of a Line

* `^` followed by the regex will match at the start of the line
* `\A` does the same as `^`
* `$` matches the end of the line, this should be placed after the regex, eg hello$
* `\Z` does the same as `$`, it should also be put at the end of the line

## Anchors and Lines

* `^`,`$`,`/A`,`/Z` and `/z` are known as anchors
* They dont match characters, the match certain positions in a string
* `/A` mathes the very start of the text, before the first character, `A` must also be uppercase
* `/Z` and `/z` match after the last character. Use this to check that something ends when you want it to
* To test for blank lines for missing imput, `/A/Z` matches empty string, and strings that consist of a single new line, `/A/z` matches only a empty string

## Match Whole Words

* Eg, matching cat, but not bobcat or category
* Use `\b` around the word, eg `\bcat\b`
* `\b` is known as a word boundary. It matches the start or end of the word. This is also a anchor.
* Technically, `/b` matches the following:
	* Before the first character in the subject, if the first character is a word character
	* After the last character in the word, if the last character is a word character
	* Between two characters in the subject, where one is a word character and the other is not a word character
* `\B` is a nonboundary. This matches every position in the text where `\b` does not match.
* `\B` matches the following positions:
	* Before the first character in the subject, if the first character is not a word character
	* After the last character in the subject, if the last character is not a word character
	* Between two word characters
	* Between two non word characters
	* The empty String

## Word Characters

* A word character is a character that can occur as port of a word.
* These are ascii letters

## Unicode Code Points, Categories, Blocks and Scripts

### Unicode code points

* Unicode code points can be used to find special characters
* The syntax is `\uUniCodeHere`. eg, `\u2122`

### Unicode Categories

* Unicode categories syntax is : `p{category}`
* Each unicode code point fits into a unicode category

### Unicode Blocks

* Unicode blocks can be used where unicode categories can be used. the syntax is the same, just needs to be passed a block rather than a category



### Unicode Scripts

* Same as unicode blocks, but some languages do not accept it

## Match One of Several Alternatives

* Done using `x | y`
* Can chain as far as you like.
* This is treated as an **OR**, not **XOR**

## Group and Capture Parts of the Match

* To match the whole word, use the ord statement with `\b` wrapping the statement
* Eg: `\b(Mary|John|Bob)\b`
* To match a pattern, do the same:
* Eg a date: `\b(\d\d)-(\d\d)-(\d\d\d\d)\b`

## Match Previously Matched Text Again

* When wanting to match previously matched text, you have to recapture it.
* This is done by a capturing group as shown above (The bracketed group

## Capture and Name Parts of the Match (PG88)

*
