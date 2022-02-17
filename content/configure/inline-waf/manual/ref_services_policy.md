# Policy

The Policy page is part of the Alert Logic Managed Web Application Firewall (WAF) section in the web based management interface. To learn about all of the features in the WAF section, see [WAF](ch_waf.md).

This page contains information for the following features found under the Policy section on the WAF page :

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF), see [WAF](ch_waf.md). To go to  the documentation for next subsection in the WAF section, see [Protocol Restrictions ](ref_services_policy_proto_restrictions.md).

**To access the Policy page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## Validation order and scope

The Policy page is defined a list of allowed requests and parameters to a given web system. WAF filters access of the allowed requests and parameters.

The policy is defined by a collection of *proxy global policies* and application specific policies. This combination provides the ability to specify short yet fine grained access control policies, global and web application.

###       Global policy    

Global policies are general rules which specify criteria that allow requests on a proxy global basis. Rules are specified by extension and by specifying a grammar (using regular expressions) for valid URLs and parameters.

Global patterns include Static content policies, Global URL policies, and Global parameters policies.

###       Web applications    

In access policy terms, a web application is defined as an URL path which takes one or more parameters as input.

The web application policy list consists of one or more URL paths each with a specific policy, a web application policy entry.

The web application policy entry is defined by its URL path. The valid input for one or more of the URLs parameters are defined using either a list of allowed values, grammar (a regular expression) or a class which is a predefined regular expression.

Web application policy entries always take precedence over global rules. It is possible though to use a combination of global and specific rules, even for a single application.

Incoming requests are validated in the following order:

1. **Static content policy**        : If the extension and path of the requested filename matches the policy defined in static content policy and the request has no parameters, the request is allowed.
2. **Global URL path policy**        : If the request has no parameters and one of the global URL policy patterns matches, it is allowed. If the URI matches one of the `Denied paths` policy rules, the request is denied.
3. **Web applications policy**        : If the request (including possible parameters) matches an entry in the detailed web application policy, it is allowed.
4. **Web applications policy + global parameters policy**        :                    If a request matches an entry in the web applications policy but one or more parameters are offending, these parameters are checked against the global parameters policy.                    If there is a combined match, the request is allowed.
5. **Global URL policy + global parameters policy:**        If a requested URL with parameters matches a global URL policy pattern and all supplied parameters match global parameter patterns the request is allowed.
6. **No match:**        : The request is denied.

### Regular Expressions guide

WAF has full support for standard PCRE (Perl Compatible Regular Expressions). Click the drop-down to follow a brief regular expression guide. For a more thorough explanation of the subject some links and books are recommended at the end of the section.

    What are regular expressions    #### What are regular expressions                     

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

<dl><dt>                                Wikipedia                              </dt><dd>A general description
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)</dd><dt>                                The 30 Minute Regex Tutorial                              </dt><dd>The code project
.NET specific tutorial, includes a software tool for testing.
[http://www.codeproject.com/dotnet/RegexTutorial.asp](http://www.codeproject.com/dotnet/RegexTutorial.asp)</dd><dt>                                Regular-Expressions.info                              </dt><dd>Excellent web site dealing extensively with the subject.
[http://www.regular-expressions.info](http://www.codeproject.com/dotnet/RegexTutorial.asp)</dd></dl>##### 1.8.8.2. Books                        

There are many good books covering regular expressions. Here we mention a few.

<dl><dt>                                Regular Expression Pocket Reference                              </dt><dd>Introduction and quick reference from O'Reilly.
[http://www.oreilly.com/catalog/regexppr/index.html](http://www.oreilly.com/catalog/regexppr/index.html)</dd><dt>                                Regular Expression Pocket Reference                              </dt><dd>Introduction and quick reference from O'Reilly.
[http://www.oreilly.com/catalog/regexppr/index.html](http://www.oreilly.com/catalog/regexppr/index.html)</dd><dt>                                Mastering Regular Expressions, Second Edition                              </dt><dd>Learning to use regular expressions efficiently. Does not pretend to be introductory in any way. Also from O'Reilly.
[http://www.oreilly.com/catalog/regex2/index.html](http://www.oreilly.com/catalog/regex2/index.html)</dd><dt>                                Sams Teach Yourself Regular Expressions in 10 Minutes                              </dt><dd>Sounds appealing. If you are new to regular expressions this is probably a good place to start. From Sams Publishing.
[http://www.samspublishing.com/title/0672325667](http://www.samspublishing.com/title/0672325667)</dd></dl>

## Basic operation

### WAF operating mode definitions

Operating modes are sets of configurations defining what violations to block and what violations to just log. Two configurable and one non-configurable presets are available.

<dl><dt>        Protect: The protect mode preset by default blocks and logs all violations according to the access policy.</dt><dt>        Detect: In the default detect mode preset, only logging occurs and no blocking protection is activated. Blocking protection that may occur in protect mode is logged and available for review in the deny log. Operating in the default detect mode is comparable to an intrusion detection system; it detects and logs activities but does not protect or prevent policy violations.                     </dt><dt>        Pass: In pass mode, all requests are passed through the website proxy. No requests are blocked and no logging is performed. As no filters are active in pass mode, it is not configurable.                     </dt></dl>
For each violation, WAF can be configured to either block and log or just log.

#### Violations

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

#### Content violations

<colgroup></colgroup>| **Path unknown** | No policy rules allow the path segment of the URL, either because it does not match a positive policy rule or because it matches a negative policy rule - a signature. |
| **Path denied** | The path is explicitly denied by an URL blocking policy rule. |
| **Query unknown** | No positive policy rules match the name of the request parameter. |
| **Query illegal** | No policy rules allow the value of the request parameter, either because it does not match a positive policy rule or because it matches a negative policy rule - a signature. |
| **Session validation failed** | The request session ID is not valid, either because the session token has been tampered with or hijacked. |
| **Form validation failed** | The form submitted cannot be verified as having been issued by the web application in a response to a request from the current user session. This is an indication of a CSRF attack. |
| **Session expired** | The request session has exceeded the idle expiration threshold configured in WAF for the web application. |
| **Malformed XML** | Submitted XML request is malformed and hence cannot be parsed and validated. |
| **Multiple encoded request** | The request contains elements that are encoded more than twice or it contains elements that are encoded using %u-encoding. |
| Illegal or malformed Unicode |  |
| Illegal or malformed %u encoding |  |
| **Authorization failed** | User is not authorized to access requested resource. |
| **Header unknown** | Request header not RFC 2616 compliant. |
| **Header illegal** | Header value failed strict validation. |
| **Header validation failed** | Header value failed pragmatic validation. |
| **Output illegal** | Server response contains illegal string. |

#### Protocol violations                           

<colgroup></colgroup>| **HTTP Protocol version** | HTTP protocol version not allowed. |
| **Method illegal** | HTTP method not allowed. |
| **Missing hostname** | Request does not specify host name. |
| **Invalid hostname** | Not website proxy is configured for the requested host name. |
| **Request line maximum length** | Entire request line (URI?query) exceeds allowed maximum length. |
| **Request path maximum length** | Request path exceeds allowed maximum length. |
| **Query string maximum length** | Request query exceeds allowed maximum length. |
| **Content type not enabled** | Request content type is supported but not enabled. |
| **Header name length** | Header name exceeds allowed maximum length. |
| **Header value length** | Header value exceeds allowed maximum length. |
| **Maximum number of headers** | Header number exceeds allowed maximum. |
| **Upload attempt** | Upload attempted but upload not allowed. |
| **Payload length exceeded** | POST payload exceeds allowed maximum size. |
| **Maximum number of upload files** | Number of files to upload in a request exceeds allowed maximum. |
| **Total upload size** | Total size of upload files in request exceeds allowed maximum. |
| **Maximum file size** | Size of a single upload file exceeds allowed maximum. |
| **Cookie version not allowed** | Request cookie version not allowed. |
| **Maximum number of cookies** | Number of cookies in request exceeds allowed maximum. |
| **Cookie name length** | Name of a cookie exceeds allowed maximum length. |
| **Cookie value length** | Value of a cookie exceeds allowed maximum length. |
| **Maximum number of GET parameters** | GET parameter number exceeds allowed maximum. |
| **GET parameter name length** | GET parameter name exceeds allowed maximum length. |
| **GET parameter value length** | GET parameter value exceeds allowed maximum length. |
| **GET parameter combined length** | Combined length of GET parameter name and value exceeds allowed maximum length. |
| **Maximum number of POST parameters** | POST parameter number exceeds allowed maximum. |
| **POST parameter name length** | POST parameter name exceeds allowed maximum length. |
| **POST parameter value length** | POST parameter value exceeds allowed maximum length. |
| **POST parameter combined length** | Combined length of POST parameter name and value exceeds allowed maximum length. |
| **Generic protocol violation** | Protocol violations like missing content length or content type headers for POST requests. |
| **General request violation** | Other generic violations. |

### Request parsing

For WAF to parse requests as close as possible to the way the target application/web server technology does, it is important to configure web application behavior.

#### Delimiters                        

According to the official RFC, query part of a URL is delimited by ? and parameter part by &amp;. Some web applications do not honor this delimiter and use different delimiters. Possible delimiters are: ";?:@&amp;+$,". Several delimiters are separated by a space.

You cannot reuse a delimiter characters across the three delimiter categories.

<colgroup></colgroup>| **Query delimiter(s)** Input field | Characters used for delimiting query part of the URL.<dl><dt>                    Valid input                  </dt><dd>Characters: `;?:@&amp;amp;amp;+$,`
Several delimiters are separated by a space.</dd><dt>                    Input example                  </dt><dd>`?` - /somepage.jsp**?**par1=val1&amp;amp;amp;par2=val2</dd><dt>                    Default value                  </dt><dd>`?`</dd></dl> |
| **Parameter delimiter(s)** Input field | Characters used for delimiting parameters in the URL.<dl><dt>                    Valid input                  </dt><dd>Characters: `;?:@&amp;amp;amp;+$,`
Several delimiters are separated by a space.</dd><dt>                    Input example                  </dt><dd>`&amp;amp;amp;` - /somepage.jsp?par1=val1**&amp;amp;amp;**par2=val2</dd><dt>                    Default value                  </dt><dd>`&amp;amp;amp;`</dd></dl> |
| **URL session id delimiter(s)** Input field | Characters used for delimiting URL based session identfiiers from the rest of the query.<dl><dt>                    Valid input                  </dt><dd>Characters: `;?:@&amp;amp;amp;+$,`
Several delimiters are separated by a space.</dd><dt>                    Input example                  </dt><dd>`;` - /somepage.jsp**;**jsessionid=longidstring?par1=val1&amp;amp;amp;par2=val2</dd><dt>                    Default value                  </dt><dd>`;`</dd></dl> |

Do not change these delimiters unless you are absolutely certain that you know the consequences.

#### Response encoding                        

When output rewriting or CSRF protection is enabled, WAF must know the character set for the pages served by the web application/server to rewrite pages correctly. WAF tries to read the character set in use from the Content-Type header in the web server response. However, if the header does not specify a character set WAF defaults to the configured charset.

<colgroup></colgroup>| **Response charset default** Input field | Default character set used for encoding served pages if none specified by backend server.<dl><dt>                    Valid input                  </dt><dd>Character set as defined in the response server header Content-Type or in the META tag content-type in the response body of pages served by the backend web server.
Examples:
Meta tag: &amp;amp;lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&amp;amp;gt; - UTF-8
Header: Content-Type: text/html; charset=iso-8859-1 - iso-8859-1</dd><dt>                    Input example                  </dt><dd>`utf8`
`iso-8859-1`
`shift_jis`</dd><dt>                    Default value                  </dt><dd>`utf8`</dd></dl> |

#### Content type - POST requests                        

These options are all related to parsing and validation of POST requests.

<colgroup></colgroup>| **Guess Content-Type** Check box | Inspect payload of POST requests to guess content type if Content-Type header not present. Default: `<disabled>` |
| **Validate multipart/form-data request format** Check box | When parsing, multipart form data requires that the payload is formatted correctly. If enabled, requests that does not validate correctly will be denied. Default: `<disabled>` |
| **Block on multipart/form-data request parsing errors** Check box | When parsing, multipart form data blocks recoverable request parsing errors like missing data caused by content-length being too small. If enabled, requests that that does not parse correctly are blocked. It is highly recommended that this setting is enabled as disabling it introduces the risk of attacks bypassing the WAF filter. Default: `<enabled>` |

#### Case sensitivity                        

Some web systems match requests case sensitive and some do not. When web systems are not case sensitive it is not uncommon that samples of requests are presented in different case combinations.

To avoid requests to resources with different case being learned as different requests, case sensitivity can be disabled.

<colgroup></colgroup>| **Enable case sensitivity** Check box | Enable / disable case sensitivity matching. Some web systems match requests case sensitive and some do not. When web systems are not case sensitive it is not uncommon that samples of requests are presented in different case combinations. If enabled, WAF will match case sensitive. Default: `<disabled>` |

#### Request header re-writing                        

WAF allows for re-writing arbitrary request header values using regular expressions for matching the value to re-write.

<colgroup></colgroup>| **Enable header re-writing** | Select or clear the check box **Enable request header re-writing** to enable this feature. |
| **Rewriting rules** | In the input area enter one or more rules for header rewriting.<dl><dt>                    Valid input                  </dt><dd>A triplet in the format: `Header_field::match_regular_expression::subst_value`.
`match_regular_expression` is a regular expression matching the substring in the header value to replace with `subst_value`.
Escape meta characters (`.*+?()[]-|^$\`) with `\` to match literally.</dd><dt>                    Input examples                  </dt><dd><dl><dt>                        Rewriting Referer field value                      </dt><dd>substitute https with http
Referer::^https::http</dd><dt>                        Rewriting X-Forwarded-For ip address                      </dt><dd>X-Forwarded-For::10\.10\.10\.10::192.168.0.11</dd></dl></dd><dt>                    Default value                  </dt><dd>`none`</dd></dl> |

### Attack class criticality

For each attack class in the list define the criticality level.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>Attack class</b>
        <ul>
          <li>Drop-down lists: SQL injection</li>
          <li> XPath injection</li>
          <li>SSI injection </li>
          <li>OS commanding</li>
          <li> XSSPath traversal </li>
          <li>Enumeration</li>
          <li> Format string</li>
          <li> Buffer overflow</li>
          <li>DoS attempt</li>
          <li> Worm probe, and more<![CDATA[                           ]]></li>
        </ul>
      </td>
      <td>
        <p>Select a criticality level for the attack class.</p>
        <dl>
          <dt>                  Valid input                </dt>
          <dd>
            <p>Options from the drop-down list:</p>
            <ul>
              <li>
                <p>
                  <code>Critical</code>
                </p>
              </li>
              <li>
                <p>
                  <code>High</code>
                </p>
              </li>
              <li>
                <p>
                  <code>Medium</code>
                </p>
              </li>
              <li>
                <p>
                  <code>Low</code>
                </p>
              </li>
              <li>
                <p>
                  <code>None</code>
                </p>
              </li>
            </ul>
          </dd>
          <dt>                  Default value                </dt>
          <dd>
            <p>Attack class dependent.</p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>### Source IP tracking and blocking

Source IP tracking and blocking adds IP sources exceeding a certain risk level to summary database. This allows for tracking attacker activity across the websites configured in WAF. The [Dashboard Deny Log Interactive List](ch_dashboards.md#ref_dashboards_deny_log.md) and the global [Attack Source Auto Blocking](ref_services_network.md#ref_services_network_attack_source_auto_blocking.md) are both based on the information collected when this feature is enabled.

##### Track violating IPs across websites                        

<colgroup></colgroup>| **Enable IP source tracking** Check box | Enable / disable IP source tracking. Tracked IPs will feed into the blacklisting controls and, if enabled, IPs exceeding limits will be blocked. Default: `<enabled>` |
| **Risk level** Drop-down list | Sets the risk level above which the source IP is tracked and added to the global database.<dl><dt>                  Valid input                </dt><dd>Options from the drop-down list
`Critical`, `High`, `Medium`, `Low`, `None`</dd><dt>                  Default value                </dt><dd>`&amp;amp;lt;High&amp;amp;gt;`</dd></dl> |

#### Immediate blacklisting

When a request is denied at the application level, instead of just stopping the request the source IP can be blacklisted forcing the attacker to change IP address or to find another target.

<colgroup></colgroup>| ** Enable IP source immediate blocking** Check box | Enable / disable IP source immediate blocking. Default: `<disabled>` |
| **Risk level** Drop-down list | Sets the risk level above which the source IP is immediately blocked. When the IP is blocked, the attacker will not be able to access the website from that source IP for a duration configured in                                 [Attack source auto blocking](ref_services_network.md#ref_services_network_attack_source_auto_blocking.md).<dl><dt>                    Valid input                  </dt><dd>Options from the drop-down list
`Critical`, `High`, `Medium`, `Low`, `None`</dd><dt>                    Default value                  </dt><dd>`&amp;amp;lt;High&amp;amp;gt;`</dd></dl> |

#### Layer 7 source IP blocking

If application layer source IP blocking is enabled, when running behind a layer 7 proxy that otherwise would hide the client source IP, client source IPs are extracted from the X-Forwarded-For header and source IP based blocking controls are enforced at layer 7 instead of at the network layer.

<colgroup></colgroup>| **Layer 7 source IP blocking** Check box | Enable / disable Layer 7 source IP blocking. Note that this feature has to be enabled at the global level. If this is not the case, this will be indicated in the field label. Default: `<disabled>` |

#### Geolocation IP access control

Geo IP blocking restricts access to your website from certain regions based on the geographic location of the incoming request. The Alert Logic Managed Web Application Firewall (WAF) product checks incoming IP addresses against a blacklist or whitelist account, and determines whether to approve or deny access to the request. You can configure which countries you want WAF to block.

<colgroup></colgroup>| **Enable GeoIP access control** Check box | 1. Select the country you want to either blacklist or whitelist. You can also select more than one country.
 Default: `<disabled>` |
| Select **Whitelist** or **Blacklist** | Whitelist or Blacklist the countries you added. |

Single-clicking  will deselect all other countries if you previously had other countries selected. You must select the countries you previously had selected again, and any new ones you want to add. To select more than one country, click and hold the control key on your keyboard as you click to select countries.

### External notification

#### Alerts and summary                        

#### Syslog alerts                           

Enable sending of alerts to syslog server. Only alerts with priority above or equal to the configured threshold are sent. Alerts are sent to `Local3` facility.

To have attack alerts sent to an external syslog server configure threshold level and server address in **System**->**Configuration**.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>Enable alerts to syslog</b>
        <p>Check box + Drop-down list</p>
      </td>
      <td>
        <p>Enable or disable sending of alerts to syslog server.</p>
        <p>When enabled, the drop-down menu <b>Syslog criticality threshold</b> specifies the lowest informational level (priority) for which alerts will be sent to the syslog server.                                 </p>
        <dl>
          <dt>                        Valid input                      </dt>
          <dd>
            <p>Options from the drop-down list:</p>
            <ul>
              <li>
                <p>
                  <code>LOG_CRIT</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_ERR</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_WARNING</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_NOTICE</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_INFO</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_DEBUG</code>
                </p>
              </li>
            </ul>
          </dd>
          <dt>                        Default value                      </dt>
          <dd>
            <p>
              <code>Disabled - LOG_WARNING</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>#### Email alerts                           

Enable sending of alerts by email. Only alerts with priority above or equal to the configured threshold are sent.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>Enable email alerts</b>
        <p>Check box + Drop-down list</p>
      </td>
      <td>
        <p>Enable or disable sending of email alerts.</p>
        <p>When enabled, the drop-down menu <b>Instant email criticality threshold</b> specifies the lowest informational level (priority) for which alerts will be sent.                                 </p>
        <dl>
          <dt>                        Valid input                      </dt>
          <dd>
            <p>Options from the drop-down list:</p>
            <ul>
              <li>
                <p>
                  <code>LOG_CRIT</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_ERR</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_WARNING</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_NOTICE</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_INFO</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_DEBUG</code>
                </p>
              </li>
            </ul>
          </dd>
          <dt>                        Default value                      </dt>
          <dd>
            <p>
              <code>Enabled - LOG_ERR</code>
            </p>
          </dd>
        </dl>
        <p>The email address is the contact email specified in <b>System</b>-&amp;gt;<b>Configuration</b>.                                 </p>
      </td>
    </tr>
  </tbody>
</table>#### Attack class criticality to log priority mapping                        

For each criticality level set the corresponding log priority (informational level).

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>Criticality level</b>
        <p>Drop-down lists (Critical, High, Medium, Low, None)</p>
      </td>
      <td>
        <p>Select a log priority level for each criticality level.</p>
        <dl>
          <dt>                      Valid input                    </dt>
          <dd>
            <p>Options from the drop-down list:</p>
            <ul>
              <li>
                <p>
                  <code>LOG_ALERT</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_CRIT</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_ERR</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_WARNING</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_NOTICE</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_INFO</code>
                </p>
              </li>
              <li>
                <p>
                  <code>LOG_DEBUG</code>
                </p>
              </li>
            </ul>
          </dd>
          <dt>                      Default value                    </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>Critical -&amp;gt; LOG_CRIT</code>
                </p>
              </li>
              <li>
                <p>
                  <code>High -&amp;gt; LOG_ERROR</code>
                </p>
              </li>
              <li>
                <p>
                  <code>Medium -&amp;gt; LOG_WARNING</code>
                </p>
              </li>
              <li>
                <p>
                  <code>Low -&amp;gt; LOG_NOTICE</code>
                </p>
              </li>
              <li>
                <p>
                  <code>None -&amp;gt; LOG_INFO</code>
                </p>
              </li>
            </ul>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>### Deny log settings

#### Policy violations                        

Enable/disabled support for logging of blocked requests.

When a request fails the defined access policy for a given proxy, WAF will block the request.

<colgroup></colgroup>| **Enable logging for normal/filtered requests** Check box | Enable / disable logging for normal/filtered requests. If enabled, WAF will log blocked requests for normal/filtered end-user traffic. Default: `<enabled>` |
| **Enable logging for pass-through requests (IP whitelisted)** Check box | Enable / disable logging for pass-through requests (Pass through mode) If enabled, WAF will log blocked requests from client matching the pass-through white-list. Default: `<disabled>` |
| **Do not log bypassed requests from trusted clients** Check box | Disable logging of bypassed requests (that would have been blocked) from trusted clients. If selected, WAF will not log requests that are violating the policy but are bypassed because the source IP is in the trusted clients list of the website proxy and HTTP blocking bypass is enabled for trusted clients. Default: `<disabled>` |
| **Do not log blocked requests from trusted clients** Check box | Disable logging of blocked requests from trusted clients. If checked, WAF will not log requests that get blocked if the source IP is in the trusted clients list of the website proxy. It is not recommended to disable logging of blocked requests unless there is a good reason for it. If for example some kind of monitoring software is used to regularly verify that specific requests are being blocked it could be desirable not to have these requests logged in order to prevent the log from being filled with these (known) requests. Default: `<disabled>` |
| **Do not log GeoIP violations** Check box | Supported optional silencing of GeoIP access violations If checked, WAF will  silence GeoIP access violations and not log them Default: `<disabled>` |

#### Broken requests                        

Enable/disable logging of broken requests.

Broken requests are either requests resulting from broken internal or external links. Broken bot requests are requests originating from bots not adhering to standards.

<colgroup></colgroup>| **Enable logging of broken links** Check box | Enable / disable logging of referred requests (requests with a referrer header) allowed by the policy but resulting in a `404 not found` error from the web server. Default: `<disabled>` |
| **Enable logging of webserver 404 not found** Check box | Enable / disable logging of requests allowed by the policy but resulting in a `404 not found` error from the web server. Default: `<disabled>` |
| **Enable logging of broken bot requests** Check box | Enable / disable logging of requests classified as broken bot requests. Default: `<disabled>` |

#### Log data masking                        

In order to avoid compromising confidential data like for instance payment card numbers (along with other payment card data like control code and expiration date) ending up in the deny log it is possible to configure log data masking policies based on regular expressions.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>Enable rewriting of logged querys</b>
      </td>
      <td>
        <p>Select or clear the check box <b>Enable rewriting of logged querys</b> to enable this feature.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>Name</b>
      </td>
      <td>
        <p>This is an informal field allowing for assigning a human readable name to the rewrite policy rule.</p>
        <dl>
          <dt>                      Valid input                    </dt>
          <dd>
            <p>Any text string</p>
          </dd>
          <dt>                      Input example                    </dt>
          <dd>
            <ul>
              <li>
                <p>Payment Card</p>
              </li>
              <li>
                <p>SSN</p>
              </li>
            </ul>
          </dd>
          <dt>                      Default value                    </dt>
          <dd>
            <p>
              <code>Payment card</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>Search for</b>
      </td>
      <td>
        <p>A regular expression matching the string to replace.</p>
        <dl>
          <dt>                      Valid input                    </dt>
          <dd>
            <p>A regular expression.</p>
          </dd>
          <dt>                      Input example                    </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>
                    <code>(?:\d{4}[\-\x20]?){2}\d{4,5}[\-\x20]?(?:\d{2,4})?</code>
                  </code> - matches most payment card numbers                                                </p>
              </li>
              <li>
                <p>
                  <code>
                    <code>\d{3}-\d{2}-\d{4}</code>
                  </code> - matches US Social Security Number strings, no validation of the value.                                                </p>
              </li>
            </ul>
          </dd>
          <dt>                      Default value                    </dt>
          <dd>
            <p>
              <code>(?:\d{4}[\-\x20]?){2}\d{4,5}[\-\x20]?(?:\d{2,4})?</code>
            </p>
          </dd>
        </dl>
        <p>Notice the use of backslash ("\") in the examples above to escape the metacharacter ".". Without escaping the "." it will be interpreted as a metacharacter matching any character resulting in the regular expression also matching strings like xxxyhost2xxx4tld and xxxhost_xxx_tld (a.o.).                              </p>
        <p>The regular expressions matches case insensitive in a repetitive fashion meaning that if more than one instance of the search pattern is present in the string they will all be replaced.                              </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>Replace with</b>
      </td>
      <td>
        <p>A string to replace with</p>
        <dl>
          <dt>                      Valid input                    </dt>
          <dd>
            <p>Any text string gramatically equal to the data being matched but with no semantic meaning (in order to mask the information in the string being matched).                                       </p>
          </dd>
          <dt>                      Input example                    </dt>
          <dd>
            <ul>
              <li>
                <p>
                  <code>
                    <code>9999-9999-9999-9999</code>
                  </code>
                </p>
              </li>
              <li>
                <p>
                  <code>999-99-9999</code>
                </p>
              </li>
            </ul>
          </dd>
          <dt>                      Default value                    </dt>
          <dd>
            <p>
              <code>9999-9999-9999-9999</code>
            </p>
            <p>The log data input policy rules rewrites all data being handled by the website proxy log subsystem. This includes data for the Learner. Therefore <strong>do not</strong> rewrite a payment card number to something like MASKED_PAN as this will result in the Learner wrongfully selecting the class alphanum for payment card input which will not match payment card numbers with "-" (dash) or " " (space) in. Instead rewrite to something similar like in the examples above.</p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>
The default rule that matches most standard credit card numbers is always on in order to reduce the risk of payment card from inadvertently being transmitted to the Alert Logic backend with deny log information.

### Access log settings                     

When *access logging* is enabled all requests to the website is logged.

The access log is generated on a per day basis and closed logs are made available for download.

<colgroup></colgroup>| **Enable access logging** Check box | Enable / disable access logging. If enabled, WAF will log all proxied requests to the web site. Default: `<disabled>` |
| **Access log format** Drop-down list | Select the format for the access log.<dl><dt>                  Valid input                </dt><dd>Options from the drop-down list
`Web Application Firewall Common`, `Common Log Format`, `Common Log Format with Virtual Host`, `NCSA extended/combined`, `Custom`</dd><dt>                  Default value                </dt><dd>`&amp;amp;lt;Web Security Manager Common&amp;amp;gt;`</dd></dl> When the `Custom` is selected, the input field below the drop-down becomes active and allows for specifying a custom log format. |
| **Custom format** Input field | Define a custom log format.<dl><dt>                  Valid input                </dt><dd>A sequence of the input fields below separated by space.</dd><dt>                  Input example                </dt><dd>`remote_addr time_local request status body_bytes_sent referer`</dd><dt>                  Default value                </dt><dd>`remote_addr remote_logname remote_user time_local request status body_bytes_sent referer user_agent cookie roundtrip`</dd></dl> |
| **Add roundtrip time and cache info to access log format** Check box | Enable / disable additional proxy specific log fields. If enabled, WAF will add roundtrip time and "served from cache flag" to the selected log format. Default: `<disabled>` |

#### Getting/viewing the access log files                        

When log files are available for download, the file name is an active link. To download an access log file click on the file name.

When remote backup is enabled, the latest access log file made available for download will be compressed (using gzip) and copied to the remote backup destination along with the backup of the system configuration.

#### Access log formats                        

WAF supports a number of standard access log formats suitable for importing into log-analysis tools. For plain access logging the WAF format is the most condensed.

#### Alert Logic Managed Web Application Firewall (WAF) Common                           

The WAF Common log format is a condensed version of the Common log format (below). It contains only basic HTTP access information and the time field is kept in Unix epoch format to save time and space.

<colgroup></colgroup>| **Source IP** | The client source IP address. |
| **Time** | Time the request was received (UNIX timestamp) |
| **Request** | First line of request |
| **Server response code** | Web server server response code - i.e. `200` |
| **Response size** | Size of response in bytes, excluding HTTP headers |
| **Response time** | The time taken to serve the request, in microseconds |
| **Cached response** | Is response served from cache or not (1=yes, 0=no) |

####  Common Log Format                           

The Common log format contains only basic HTTP access information.

<colgroup></colgroup>| **Source IP** | The client source IP address. |
| **Remote logname** | N/A - will contain a dash, included for compatibility. |
| **Remote user** | N/A - will contain a dash, included for compatibility. |
| **Time** | Time the request was received (standard english format) |
| **Request** | First line of request |
| **Server response code** | Web server server response code - i.e. `200` |
| **Response size** | Size of response in bytes, excluding HTTP headers. In CLF format, i.e. a '-' rather than a 0 when no bytes are sent. |

#### Common Log Format with Virtual Host                           

The Common log format contains only basic HTTP access information with the addition of canonical name of the Virtual Host serving the request.

<colgroup></colgroup>| **Virtual Host** | The canonical ServerName of the server serving the request. |
| **Source IP** | The client source IP address. |
| **Remote logname** | N/A - will contain a dash, included for compatibility. |
| **Remote user** | N/A - will contain a dash, included for compatibility. |
| **Time** | Time the request was received (standard english format) |
| **Request** | First line of request |
| **Server response code** | Web server server response code - i.e. `200` |
| **Response size** | Size of response in bytes, excluding HTTP headers. In CLF format, i.e. a '-' rather than a 0 when no bytes are sent. |

####  NCSA extended/combined                           

The NCSA extended/combined format contains the same information as the Common log format plus two additional fields: the referral field and the user_agent field. This log format is also called Apache Combined log format.

<colgroup></colgroup>| **Source IP** | The client source IP address. |
| **Remote logname** | N/A - will contain a dash, included for compatibility. |
| **Remote user** | N/A - will contain a dash, included for compatibility. |
| **Time** | Time the request was received (standard english format) |
| **Request** | First line of request |
| **Server response code** | Web server server response code - i.e. `200` |
| **Response size** | Size of response in bytes, excluding HTTP headers. In CLF format, i.e. a '-' rather than a 0 when no bytes are sent. |
| **Referrer** | The content of the request header "Referer". |
| **User-Agent** | The content of the request header "User-Agent". |

####  Custom format                           

The custom log format allows for specifying custom log formats by entering log format field names separated by space. The field names below are available.

<colgroup></colgroup>| **Source IP** | remote_addr | The client source IP address. |
| **Remote logname** | remote_logname | N/A - will contain a dash, included for compatibility. |
| **Remote user** | remote_user | N/A - will contain a dash, included for compatibility. |
| **Time** | time_local | Time the request was received (standard english format) |
| **Request** | request | First line of request |
| **Server response code** | status | Web server server response code - i.e. `200` |
| **Response size** | body_bytes_sent | Size of response in bytes, excluding HTTP headers. In CLF format, i.e. a '-' rather than a 0 when no bytes are sent. |
| **Referrer** | referer | The content of the request header "Referer". |
| **User-Agent** | user_agent | The content of the request header "User-Agent". |
| **Cookie** | cookie | The content of the request header "Cookie". |
| **Response time** | roundtrip | The time taken to serve the request, in microseconds. |
| **UNIX timestamp** | timestamp | Time the request was received (UNIX timestamp). |
| **Cached response** | cache | Is response served from cache or not (1=yes, 0=no). |

#### Additional fields                           

If "Add roundtrip time and cache info to access log format" is enabled, the fields below will be added to the selected log format.

<colgroup></colgroup>| **Response time** | The time taken to serve the request, in microseconds |
| **Cached response** | Is response served from cache or not (1=yes, 0=no) |

### Response inspection

#### Response logging

#### Response inspection

### Mirror proxy policy from master                     

This feature allows for configuring the proxy to dynamically mirror the policy of another website proxy.

To mirror a proxy, select it in the drop-down list and enable the Mirror proxy policy from master module.

When mirroring is enabled, it will be indicated in the top of the page with the text (MIRROR OF PROXY xx). Also in the websites overview the information in the Virtual Web server column will contain the text (M:X) where X is the website proxy ID.

Note that the selected mode is not mirrored. This means that if the mirrored proxy (the master) is running in Protect mode and the mirror (the proxy for which mirroring is enabled) is running in Detect mode, it will log/block according to the Detect mode preset while the mirrored proxy will use the Protect mode preset.
