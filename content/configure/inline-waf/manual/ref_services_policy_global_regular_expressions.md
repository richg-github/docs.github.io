# Regular Expressions

The Alert Logic Managed Web Application Firewall (WAF) Regular Expressions page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF), see [Web Applications](ref_services_policy_web_applications.md). To go to  the documentation for next section in the WAF section, see [Deny and Error Handling](ref_services_deny_and_error_handling.md).

**To access the Regular expressions section in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**, and then scroll down to the Regular expression section.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

WAF has full support for standard PCRE (Perl Compatible Regular Expressions).

Following below is a brief regular expression "survival guide". For a more thorough explanation of the subject some links and books are recommended at the end of the section.

## What are regular expressions                     

A regular expression is a formula for matching strings that follow some pattern.

Regular expressions are made up of normal characters and special characters. Normal characters include upper and lower case letters and digits. The characters with special meanings and are described in detail below.

In the simplest case, a regular expression looks like a standard text string. For example, the regular expression "john" contains no special characters. It will match "john" and "john doe" but it will not match "John".

In an input validation context we always want the expression to match the whole string. The expression above would now be expressed as ^john$, where the characters ^ and $ means starting of line and end of line. Now john will only match "john" but not "john doe". To obtain match of "john doe" as well as "john smith" etc. we employ a few more simple special characters. In its simplest form "john *lastname*" could be expressed as "^john.*$" meaning: A string starting with the characters "john" followed by zero or more (the "*") occurrences of any character (the "."). For those familiar with the simple wild-card character "*" in (a.o.) DOS and Unix, ".*" equals "*" - that is: *anything*.

Specifying *anything* is not very useful in an input validation context. With regular expressions much more fine grained input validation masks can be defined with the rich set of meta characters, character classes, repetition quantifiers, etc.

A brief explanation with some examples follows below.

#### Metacharacters                     

<colgroup></colgroup>| `^` | Beginning of string (implied in WAF) |
| `$` | End of string (implied in WAF) |
| `.` | Any character except newline |
| `*` | Match 0 or more times |
| `+` | Match 1 or more times |
| `?` | Match 0 or 1 times; or: shortest match quantifier (i.e. *?) |
| `|` | Alternative (like logical OR) |
| `()` | Grouping |
| `[]` | Set of characters (a list of characters) |
| `{}` | Repetition modifier |
| `\` | Quote or special |

**Metacharacters in regular expressions**

To present a metacharacter as a data character standing for itself, precede it with \ (e.g. \. matches the full stop character "." only).

In WAF all regular expressions are forced to match the entire string (URL path or parameter value) by automatically prefixing an expression with "^" and suffixing it with "$".

#### Repetition                     

<colgroup></colgroup>| `a*` | Zero or more a's |
| `a+` | One or more a's |
| `a?` | Zero or one a's (i.e., optional a) |
| `a{m}` | Exactly m a's |
| `a{m,}` | At least m a's |
| `a{m,n}` | At least m but at most n a's |
| `repetition?` | Same as repetition but the shortest match is taken |

**Repetition in regular expressions**

Read "a's" as "occurrences of strings, each of which matches the pattern a".

Read *repetition* as any of the repetition expressions listed above it.

Shortest match means that the shortest string matching the pattern is taken. The default is "greedy matching", which finds the longest match.

#### Special notations with \                     

<colgroup></colgroup>| `\t` | tab |
| `\n` | newline |
| `\r` | return (CR) |
| `\xhh` | character with hex. code hh |
| `\b` | "word" boundary (zero space assertion) |
| `\B` | not a "word" boundary |
| `\w` | matches any single international character classified as a "word" character (alphanumeric or _). Examples: A, z, 1, 9, Æ, â |
| `\W` | matches any non-"word" character |
| `\s` | matches any whitespace character (space, tab, newline) |
| `\S` | matches any non-whitespace character |
| `\d` | matches any digit character, equiv. to [0-9] |
| `\D` | matches any non-digit character |
| `\pN` | Matches any UNICODE character classified as numeric |

**Notations with \ in WAF regular expressions**

#### Character sets [...]                     

A character set is denoted by [...]. Different meanings apply inside a character set ("character class") so that, instead of the normal rules given here, the following apply:

<colgroup></colgroup>| `[characters]` | matches any of the characters in the list (c,h,a,r,a,c,t,e,r,s) |
| `[x-y]` | matches any of the characters from x to y (inclusively) in the ASCII code |
| `[\-]` | matches the hyphen character - |
| `[\n]` | matches the newline; other single character denotations with \ apply normally, too |
| `[^something]` | Negation. Matches any character except those that [something] denotes; that is, immediately after the leading [ the circumflex ^ means "not" applied to all of the rest |

**Character sets in regular expressions**

#### Lookaround                     

The lookaround construct allows for the creation of regular expressions matching *something* but only when it is followed/preceded or *not* followed/preceded by *something else*. Note that the lookaround construct is a zero-width assertion. It is testing for a match of something else but it will not actually match it - that is why it is called an assertion. The lookaround constructs allows for the creation of otherwise impossible or too complex expressions.

In an input validation context look ahead could be used for specifying an expression allowing angle brackets <> but only when they are not closed.

<colgroup></colgroup>| a(?!*expression*) | Negative lookahead. Matches "a" when not followed by *expression*, where expression is any regular expression. |
| a(?=*expression*) | Positive lookahead. Matches "a", when followed by *expression*. |
| (?<!*fixed-expression*)a | Negative lookbehind. Matches "a" when not preceded by *fixed-expression*, where fixed-expression is any regular expression specifying a fixed number of characters. That is "aaa" wil work but a+ will not work. |
| (?<=*fixed-expression*)a | Positive lookbehind. Matches "a" when preceded by *fixed-expression*. |

**Lookaround in regular expressions**

#### Examples                     

##### Global URL regular expressions                        

The URL regular expressions filter matches URLs without parameters on a proxy global basis. If a request matches any of the defined regular expressions, it will be marked as valid by WAF and forwarded to the back-end server.

<colgroup></colgroup>| Expression | Matches |
|---|---|
| `(/[\w\-]+)+\.html` | URL with the extension html containing any international word characters, digits, _ and -. (\w matches upper and lower case alphanumeric characters plus _). |
| `/abc(?:/[\w\-]+)*\.html` | Same URL starting with `/abc`, including the URL `/abc.html`. |
| `(/[\w\-]+)+\.html?` | Same URL matching extensions `html` and `htm` |
| `(/[\w\-]+)+\.(html|pdf)` | Same URL matching extensions `html` and pdf. |
| `(/[abcdefgh]+)+\.html` | URL with the extension `html` containing any of the lower case letters `abcdefgh`. |
| `/index\.html` | Exact match of `/index.html` |
| `(/[\w\-]+)+/?` | "Natural" URL containing international alphanumeric characters, digits, `_` and `-`. |
| `/sw[0-9]{0,12}\.asp` | URL with the extension `asp` starting with `/sw` followed by 0-12 digits. |
| `/(login|logout)` | Only URLs `/login` or `/logout` |
| `(/[\w\-]+)+\.(htm|html|shtml|pdf) ` | Any international characters URL with one of the extensions htm, html shtml or pdf. |

**Examples of global URL regular expressions**

##### Validating input parameters                        

<colgroup></colgroup>| regular expression | matches |
|---|---|
| `^[\w \.@()\-]+$` | International alphanumeric characters, underscore, a space, dot, @, parentheses and a dash. |
| `^[0-9a-za-z. ]+$` | digits, ASCII characters a-z, a dot and a space. |
| `^[0-9]+$` | only digits. `[0-9]` can also be expressed as `\d` |
| `^[\d]{1,5}$` | one to five digits. |
| `^[a-z]+$` | only lower case ASCII characters from a-z. |
| `^[a-z]{0,32}$` | matches only lower case ASCII characters from a-z and limits the total length to maximum 32 characters. |

**Examples of regular expressions for input validation**

##### Global parameters                        

When specifying global parameters both the name and the value are defined using regular expressions.

<colgroup></colgroup>| Name | Value | Matches |
|---|---|---|
| `usepf` | `true` | The specific parameter `usepf` with the static value `true` |
| `parm\d{3}` | `[a-zA-Z\d]{3,32}` | All parameters with name starting with `parm` followed by three digits with the value any combination of letters `a-Z` (upper and lowercase) or digits with a minimum length of 3 and a maximum length of 32 characters. |
| `\w{1,25}` | `[\w\s_,/:()@$*\.\-]*` | Any parameter with name consisting of international word characters and with values containing zero or more"friendly characters". |

**Examples of global parameters regular expressions**

##### Predefined standard classes in WAF

The following classes are predefined in WAF. The classes are presented in the order the `Automatic Policy Generator` evaluates them when automatically mapping classes to input parameters.

<colgroup></colgroup>| Class | Regular expression | Description |
|---|---|---|
| empty |  | No values allowed |
| num | `\d{1,32}` | Digits - a maximum of 32 digits |
| payment_card | `(?:\d{4}[\-\x20]?){2}\d{4,5}[\-\x20]?(?:\d{2,4})?` | Payment card numbers, allows for spaces and hyphens between number groups. |
| ms_ident | `{?[A-Za-z0-9]{8}-[A-Za-z0-9]{4}-[A-Za-z0-9]{4}-[A-Za-z0-9]{4}-[A-Za-z0-9]{12}}?` | Microsoft identifier with optional preceding and trailing curly brackets. |
| alphanum | `\w{1,256}` | International alphanumeric characters. No spaces. max. 256 chars. |
| text | `(?!.*(\.\.|//).*)[\w\x20+.,\-:@=/]+` | Simple international text. |
| url | `(?:https?://)?(?!.*(\.\.|//).*)[\w\x20@,.(){}/\-=?&amp;]+` | Simple international URL match. With parameters. Consecutive "/" or "." not allowed (negative look ahead) |
| standard | `[\w\s@,.(){}/\-=?&amp;_:]+` | Text input, international, several special characters allowed including newline. |
| printable | `[^\x00-\x08\x0b\x0c\x0e-\x1f\x7f]+` | Any number of printable characters. Defined by negating character class containing non-printable characters. |
| anything | `.+` | Anything but newline. |
| Anything_multiline | `(?:.|\n)*` | Anything including newline. |

**Predefined standard classes in WAF**

#### Further reading                     

A number of web sites and books are describing regular expressions in more detail.

##### Web sites                        

<dl><dt>        Wikipedia      </dt><dd>A general description
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)</dd><dt>        The 30 Minute Regex Tutorial      </dt><dd>The code project
.NET specific tutorial, includes a software tool for testing.
[http://www.codeproject.com/dotnet/RegexTutorial.asp](http://www.codeproject.com/dotnet/RegexTutorial.asp)</dd><dt>        Regular-Expressions.info      </dt><dd>Excellent web site dealing extensively with the subject.
[http://www.regular-expressions.info](http://www.codeproject.com/dotnet/RegexTutorial.asp)</dd></dl>##### 1.8.8.2. Books                        

There are many good books covering regular expressions. Here we mention a few.

<dl><dt>        Regular Expression Pocket Reference      </dt><dd>Introduction and quick reference from O'Reilly.
[http://www.oreilly.com/catalog/regexppr/index.html](http://www.oreilly.com/catalog/regexppr/index.html)</dd><dt>        Regular Expression Pocket Reference      </dt><dd>Introduction and quick reference from O'Reilly.
[http://www.oreilly.com/catalog/regexppr/index.html](http://www.oreilly.com/catalog/regexppr/index.html)</dd><dt>        Mastering Regular Expressions, Second Edition      </dt><dd>Learning to use regular expressions efficiently. Does not pretend to be introductory in any way. Also from O'Reilly.
[http://www.oreilly.com/catalog/regex2/index.html](http://www.oreilly.com/catalog/regex2/index.html)</dd><dt>        Sams Teach Yourself Regular Expressions in 10 Minutes      </dt><dd>Sounds appealing. If you are new to regular expressions this is probably a good place to start. From Sams Publishing.
[http://www.samspublishing.com/title/0672325667](http://www.samspublishing.com/title/0672325667)</dd></dl>
