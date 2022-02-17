# Learning Settings

The Alert Logic Managed Web Application Firewall (WAF) Learning Settings page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Learning, see [Learning Data](ref_services_learning_data.md). To go to  the documentation for next section, see [Reports](ref_services_reports.md).

**To access the Learning page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under Learning, click **Learning Data**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

#### Policy generation options

<colgroup></colgroup>| **              Application profiling (Learning)            ** Drop-down list | Enable/disable learning |
| **              Develop static extensions list            ** Check box | Enable / disable static extensions learning. If enabled, WAF will treat static content separately and develop a static content policy (from learned static content. Default: `<enabled>` See [Validate static requests separately](ref_services_policy_policy_global.md#ref_services_policy_policy_global.md#global_static) for more information. |
| **Enable global parameters generation            ** Check box | Enable / disable global parameters generation If enabled, WAF will identify parameters which many or all learned applications have in common. If a (configurable) number of applications takes a specific parameter as input the parameter will be learned as a global parameter and added to the [Query and Cookie validation](ref_services_policy_policy_global.md#ref_services_policy_policy_global.md#global_parm) section. Default: `<enabled>` |
| **Enable global parameters name grouping            ** Check box | Enable / disable global parameters name grouping. If enabled, WAF will analyze the global parameter names to identify name similarities and build parameter groups based on common characteristics. If the number of parameter names in a group exceeds a configurable threshold a parameter name pattern will be built matching all parameter names in the group. Grouped parameter names with corresponding input validation classes are inserted in [Query and Cookie validation](ref_services_policy_policy_global.md#ref_services_policy_policy_global.md#global_parm). Default: `<enabled>` |
| **Enable autostart of policy generation            ** Check box | Enable / disable auto start of policy generation. If enabled, when a (configurable) number of sample data chunks has been processed without resulting in a number of policy changes exceeding thresholds a policy will be generated, the operating mode will automatically be changed to `Detect` and the Learner will stop collecting data samples. Default: `<enabled>` |
| **Learn applications only            ** Check box | Only learn applications. If enabled, WAF will only learn from requests with parameters. This will keep WAF from constantly adding new URL paths to the learning database for sites that use natural URL versions of for instance blog entries. Default: `<disabled>` |
| **Avoid learning from broken bots            ** Check box | Enable / disable checks for broken robots. If enabled, WAF will try to identify requests originating from robots not behaving correctly. An example is robots that maps the URL /index.asp?page=8&amp;print=1 but for some reason translates the print parameter to &amp;amp;print=1 when requesting it. Because the parameter &amp;amp;print is not requested in general from many different sources, it will never exceed threshold values and consequently will not be included in the policy. Default: `<enabled>` |
| Include empty parameters in learn data Check box |  |
| **Learn from hostile sources (IPs)            ** Check box | Enable / disable exclusion of sample data from hostile sources. If disabled, requests from sources from which entries in the deny log classified as attacks also originates will not be included in the sample population used for generating the policy. As all learning samples are validated against negative policy rules obvious attacks will not be included no matter what the setting of this option is. But as attackers often "sneak around" trying different probes to detect vulnerability against for instance SQL injection (entering `O'Neill` instead of `'or 1=1`) chances are that the classes mapped for input validation becomes looser than they have to. Disabling learning from hostile sources reduces the likelihood that this will happen. Default: `<disabled>` |
| **Auto enable request origin validation (CSRF protection)            ** Check box | Enable / disable automatic activation of request origin validation. If Session protection and generation of request form validation tokens (CSRF protection) is enabled (see [Session and CSRF protection                     ](ref_services_policy_policy_global.md#global_session)) the Learner will map applications taking input from forms generated by the web system by detecting the validation token parameter (___pffv___) inserted by WAF and correlating other input parameters to the presense of the validation token. If parameters are detected that are only present in requests where the validation token is also present (like "amount" or "submit") then the application is created in the web applications policy with one of these parameters as "validation parameter" - that is: a parameter which when present in requests will trigger a validation of the request form origin based on the validation token which is tied to the current user session.If Auto enable request origin validation (CSRF protection) is enabled the Learner will map the validation parameter and enable origin validation (CSRF protection) for that application. If disabled the Learner will only map the validation parameter.                            Default: `<disabled>` |
| **Keep validation settings for enabled applications            ** Check box | Enable / disable automatic overwriting of request origin validation activation settings. This input is only active when Auto enable request origin validation (CSRF protection) is disabled. Suppose you want the Learner to map validation parameters for request origin validation but that you only wan to activate it for certain applications. In order to avoid the Learner overwriting the activation settings for the activated applications next time it develops a policy activate this control. Default: `<disabled>` |

#### Global parameters

<colgroup></colgroup>| **              Path duplication threshold            ** Input field | Define how many unique paths (applications) are required to take the parameter as for the parameter to be regarded global.<dl><dt>                Valid input              </dt><dd>Number of paths</dd><dt>                Input example              </dt><dd>`5`</dd><dt>                Default value              </dt><dd>`3`</dd></dl> |
| **              Name grouping threshold            ** Input field | Define how many occurrences of a global parameter with similar patterns in name it requires for the generation of a name pattern.<dl><dt>                Valid input              </dt><dd>Number of parameters</dd><dt>                Input example              </dt><dd>`5`</dd><dt>                Default value              </dt><dd>`3`</dd></dl> |

#### Policy verification

Policy verification thresholds allow for granular control of when the Learner will generate a policy or notify by email that thresholds are reached.

<colgroup></colgroup>| **              Web application policy changes threshold            ** Input field | Define the upper threshold of web application policy changes.<dl><dt>                Valid input              </dt><dd>Number of changes to the web application policy.</dd><dt>                Input example              </dt><dd>`0`</dd><dt>                Default value              </dt><dd>`0`</dd></dl> |
| **              Static content policy changes threshold            ** Input field | Define the upper threshold of static content policy changes.<dl><dt>                Valid input              </dt><dd>Number of changes to the static content policy.</dd><dt>                Input example              </dt><dd>`0`</dd><dt>                Default value              </dt><dd>`0`</dd></dl> |
| **              Global parameters policy changes threshold            ** Input field | Define the upper threshold of global parameters policy changes.<dl><dt>                Valid input              </dt><dd>Number of changes to the global parameters policy.</dd><dt>                Input example              </dt><dd>`0`</dd><dt>                Default value              </dt><dd>`0`</dd></dl> |
| **              Global URL patterns policy changes threshold            ** Input field | Define the upper threshold of global URL patterns policy changes.<dl><dt>                Valid input              </dt><dd>Number of changes to the global URL patterns policy.</dd><dt>                Input example              </dt><dd>`0`</dd><dt>                Default value              </dt><dd>`0`</dd></dl> |
| **              Verification runs            ** Input field | The Verification runs threshold controls how many trial policies without changes exceeding the threshold values below are required before a learned policy is considered verified and ready to be committed to WAF. The process of verifying the policy before committing to WAF is important because it reduces the risk of false positives.<dl><dt>                Valid input              </dt><dd>Number of trial policies built in a row without changes.</dd><dt>                Input example              </dt><dd>`30`</dd><dt>                Default value              </dt><dd>`20`</dd></dl> |

#### Learning thresholds

To avoid learning from worms, attacks and other unauthorized access the Learner employs a combination of heuristic attack classification, statistics and server responses.

The statistic analysis is based on aggregates, delta, min values etc.

The statistics based approving of request samples is divided into approving:

1. URL Paths based on the URL Paths group membership. This approval only affects the URL Path, not parameters and associated input values.
2. Parameters

##### Path groups

The approval of URL paths, applications as well as static resources, is based on the URL Path group membership.

The threshold values below control the statistics based approval of groups.

<colgroup></colgroup>| **                IP addresses              ** Input field | The minimum number of unique IP addresses observed requesting URL paths belonging to a group.<dl><dt>                  Valid input                </dt><dd>Number</dd><dt>                  Input example                </dt><dd>`500`</dd><dt>                  Default value                </dt><dd>`100`</dd></dl> |
| **                Timestamps              ** Input field | The minimum number of unique timestamps observed on requests for URL paths belonging to a group. The timestamp granularity is in seconds.<dl><dt>                  Valid input                </dt><dd>A number in the interval `0 - 9999999999`.</dd><dt>                  Input example                </dt><dd>`300`</dd><dt>                  Default value                </dt><dd>`100`</dd></dl> |
| **                Time spread              ** Input field | The minimum difference in seconds between the first and the last request for URL Paths belonging to the group.<dl><dt>                  Valid input                </dt><dd>A number in the interval `0 - 9999999999`.</dd><dt>                  Input example                </dt><dd>`259200 (3 days)`</dd><dt>                  Default value                </dt><dd>`36000 (ten hours)`</dd></dl> |

##### Query names

The threshold values below control the statistics based approval of query names.

Note that the threshold values applies to unique URL Path/Query combinations.

The term Query name refers to a request parameter name (ie. *name*=value).

<colgroup></colgroup>| **                IP addresses              ** Input field | The minimum number of unique IP addresses observed requesting the URL Path/Query combination.<dl><dt>                  Valid input                </dt><dd>Number</dd><dt>                  Input example                </dt><dd>`100`</dd><dt>                  Default value                </dt><dd>`100`</dd></dl> |
| **                Timestamps              ** Input field | The minimum number of unique timestamps observed requesting the URL Path/Query combination. The timestamp granularity is in seconds.<dl><dt>                  Valid input                </dt><dd>A number in the interval `0 - 9999999999`.</dd><dt>                  Input example                </dt><dd>`100`</dd><dt>                  Default value                </dt><dd>`100`</dd></dl> |
| **                Time spread              ** Input field | The minimum difference in seconds between the first and the last request for the URL Path/Query combination.<dl><dt>                  Valid input                </dt><dd>A number in the interval `0 - 9999999999`.</dd><dt>                  Input example                </dt><dd>`36000 (ten hours)`</dd><dt>                  Default value                </dt><dd>`36000 (ten hours)`</dd></dl> |

##### Input validation class selection for query values

The threshold values below control the statistics based selection of input validation class selection for approved Querys (above).

The term Query value refers to a request parameter value (ie. name=*value*).

The methods available depend on the license type.

<colgroup></colgroup>| **                Determine valid input class using value frequency analysis              ** Check box + Input fields | If enabled input validation class selection will be based on value the relative frequency of class samples. This method utilizes that in most cases valid samples will vastly outnumber invalid samples (like for instance attack probes not matching signatures - searching for o'neill for instance to test for proper input handling in forms). Input validation classes are ranked according to possible complexity in input with simple classes having the lowest rank. When input values to a parameter are learned the values are mapped to input validation classes. The higher the rank of the class the more general input is accepted. When the policy is built the class with the highest rank is chosen provided enough samples of the class has been recorded with respect to its relative weight in the sample population in terms of hits, unique IP sources and unique timestamps. Input fields for relative thresholds: **                  Source frequency threshold                **<dl><dt>                  Valid input                </dt><dd>A value in the interval `0.0 - 99.9`</dd><dt>                  Input example                </dt><dd>`1.5`</dd><dt>                  Default value                </dt><dd>`1.0`</dd></dl> **                  Timestamp frequency threshold                **<dl><dt>                  Valid input                </dt><dd>A value in the interval `0.0 - 99.9`</dd><dt>                  Input example                </dt><dd>`1.5`</dd><dt>                  Default value                </dt><dd>`1.0`</dd></dl> **                  Hits frequency threshold                **<dl><dt>                  Valid input                </dt><dd>A value in the interval `0.0 - 99.9`</dd><dt>                  Input example                </dt><dd>`1.5`</dd><dt>                  Default value                </dt><dd>`1.0`</dd></dl> |
| **                Determine valid input class using value counting              ** Check box + Input field | If enabled input validation class selection will be based on value counting. **                  Class samples required for query value                ** Input validation classes are ranked according to possible complexity in input with simple classes having the lowest rank. When input values to a parameter are learned the values are mapped to input validation classes. The higher the rank of the class the more general input is accepted. When the policy is built the class with the highest rank is chosen provided enough samples of the class has been recorded. This threshold is defined by **                  Class samples required for query value                **.<dl><dt>                  Valid input                </dt><dd>A number in the interval `0 - 9999999999`.</dd><dt>                  Input example                </dt><dd>`10`</dd><dt>                  Default value                </dt><dd>`1`</dd></dl> The lower threshold selected the higher is the risk that a few invalid samples will affect the class selection resulting in a policy that is too lose. |

#### Learn data sampling

Learn data sampling settings allow for limiting learn data sampling to specific source IP addresses or specific URL Paths. Similarly it is possible to exclude learning from IP addresses and URL Paths.

<colgroup></colgroup>| **Parameters** Check box |  |
| **Regular expression** Input field |  |
| **Comment** Input field |  |
| **              Path - Only learn from the paths below            ** Check box + Input field | If enabled the Learner will *only record* sample data from the URL Paths specified in the input area. In combination with very general global policies it is possible to learn and filter specific applications only.<dl><dt>                Valid input              </dt><dd>One or more URL path regular expresions separated by new-line.</dd><dt>                Input example              </dt><dd>`/cgi-bin/.*`</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **              Path - Do not learn from the paths below            ** Check box + Input field | If enabled the Learner will *not record* sample data from the URL Paths specified in the input area.<dl><dt>                Valid input              </dt><dd>One or more URL path regular expressions separated by new-line.</dd><dt>                Input example              </dt><dd>`/admin/.*`</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **              IP - Only learn from the IP addresses below            ** Check box + Input field | If enabled the Learner will *only record* sample data from the IP addresses specified in the input area.<dl><dt>                Valid input              </dt><dd>IP address with net mask (IP/mask) in CIDR notation</dd><dt>                Input example              </dt><dd>`192.168.0.8/32` - the IP address 192.168.0.8
`192.168.0.0/24` - IP addresses 192.168.0.0 - 255
`192.168.0.8/29` - IP addresses 192.168.0.8-15</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |
| **              IP - Do not learn from the IP addresses below            ** Check box + Input field | If enabled the Learner will *not record* sample data from the IP addresses specified in the input area.<dl><dt>                Valid input              </dt><dd>IP address with net mask (IP/mask) in CIDR notation</dd><dt>                Input example              </dt><dd>`192.168.0.8/32` - the IP address 192.168.0.8
`192.168.0.0/24` - IP addresses 192.168.0.0 - 255
`192.168.0.8/29` - IP addresses 192.168.0.8-15</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |

#### Learning expiration

<colgroup></colgroup>| **              Number of paths plus parameters that will trigger expiration            ** Input field |  |
| **Maximum number of paths plus parameters to keep** |  |

#### Lower button bar

<colgroup></colgroup>| **              Build policy            ** Button | Builds a policy which is accessible and editable in the Global Patterns and Web applications windows. When clicked a confirm dialog is shown with the question: "Disable data sampling and switch to detect mode when a policy is generated?" Select *cancel* if the Learner should continue the data sampling and learning process and *OK* if you want the Learner to switch to *detect mode*. If *cancel* is selected the built policy will have no effect but the editing and reporting tools will be available. |
| **              Reset learn data            ** Button | Use with caution! When clicking this button and accepting the confirm pop-up window. *All learning data for that proxy will be deleted!* If learning is enabled the learning and data sampling process will start from scratch. |
| **              Default values            ** | Revert to default values. |
| **              Save settings            ** | Click **Save settings** to save settings. |
