---
layout: post
title: Regex Key Concepts...
---

### Introduction

What are Regular Expressions(abbreviated regex) ?. Here's a definition from Wikipedia.

>In theoretical computer science and formal language theory, a regular expression (sometimes called a rational expression)is a sequence of characters that define a search pattern,  mainly for use in pattern matching with strings, or string matching, i.e. "find and replace"-like operations.

  The key idea is that a regular expression is a pattern which matches a set of target strings.

    Example

    \w+@\w+\.(com|org|net|in) is a regex that matches most email addresses
    that end with a .com, .net, .org or a .in.

Most regex expressions consist of the following.

1. Literals: They are the simplest things to match. When they are there, we just match them. It could be like an a or a 1.
 
2. Meta-characters: They do not mean what they look like. They usually refer to something else. For example, \d could refer to any digit.

3. Vertical Bar: The &#124; is a symbol or boolean OR. It gives an option to match any of the things it delimits.

4. Quantifiers: They specify how many of the concerned pattern needs to be matched.

5. Grouping and Capturing: Parentheses could be used to group parts of the regex or capturing parts for later use.

### Syntax

Let's look at Meta-characters in a little more detail.

| Meta-character |	Description |
--- | ---: |
^	|   Start of a string
$	| End of a string
\t |	Tab
\n | Newline
\r | Carriage Return
\s |	Any whitespace character
\S | Any non-whitespace character
\d | Any Digit
\D | Any non-digit
\w | Any word-character
\W | Any non-word character
\b | Any word boundary
\B | Any non-word-boundary
. | Any single character, usually barring a newline

And if you want to match a Meta-character literally you need to use \ to escape it. For example, '\\.' would just match the . character.

Expression |	Meaning
--- | --- | ---
[ ] | Matches a single character that is contained within the brackets.
[^ ] | Matches a single character that is not contained within the brackets.
[a-d] | Matches any of the characters in the range a-d.
* |	Matches the preceding element zero or more times. 
? |	Matches the preceding element zero or one time.
+ |	Matches the preceding element one or more times.
&#124;|The choice operator matches either the expression before or the expression after the operator.
{m,n} |	Matches the preceding element at least m and not more than n times.
( ) |	Captures everything inside the bracket.

### Examples

Let's look at a few pattern matches to see how they go together.

Regular Expression |	Meaning
--- | --- | ---
/a.c/	| the letter a followed by any character then c
 /a+c/	| one or more a's followed by c
 /a*c/	| zero or more a's followed by c, so even "c" matches.
 /a?c/	| zero or one a followed by c: "ac" or "c"
 /a.+c/	| a followed by one or more characters, then c
 /a.\*c/	| a followed by zero or more characters, then c, so even "ac" matches.
/a&#124;bc/ | "a" or "bc"
 /(a&#124;b)c/	| "ac" or "bc"
 /(a&#124;b)+c/	| one or more a's or b's, followed by c: ac, bc, aac, abc, aaac, abbabababbac.
 /(a&#124;A)\ssample\smatch/	|   "A" or "a" followed by one whitespace character, then "sample", then one whitespace character, then "match".
/\d\d\d-\d\d\d-\d\d\d\d/	| Any phone number like this: 250-123-1234
/\(\d\d\d\)\s\d\d\d\-\d\d\d\d/	| Any North American phone number like this: (250) 123-1234
 /\(\d{3}\)\s\d{3}-\d{4}/	| As above, but using the count specifier
 /^\t+\S+\s*/ | Any line of text starting with one or more tabs, containing at least one nonwhitespace characer, followed by no or some whitespace
 /^b[aeiouy]+t/ | Any line of text starting with b followed by any combination of 1 or more vowels and then the letter t/


