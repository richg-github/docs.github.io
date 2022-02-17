# Web Applications

The Alert Logic Managed Web Application Firewall (WAF) Web Applications page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF) , see [Website Global Policy](ref_services_policy_policy_global.md). To go to  the documentation for next subsection in the WAF section, see [Output Filter](ref_services_policy_output_filter.md).

**To access the Web application section in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**, and then scroll down to the Web application section.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The *Web applications section* allows for defining a sub scope with different policy rules for select policy components based on regular expressions.

Web applications are either added manually or they are automatically created created by the Learner.

## Scope definition

The scope of the web application is defined by regular expression. Full match is implied (^regular expression$) and caret (^) and dollar ($) do not have to be included in the regular expression.

<colgroup></colgroup>| **              Scope regular expression            ** Input field | Regular expression specifying the scope of the web application section.<dl><dt>                Valid input              </dt><dd>A regular expression
For performance reasons the regular expression has to be re2 compliant so zero-length lookaround assertions are not allowed.
All meta characters except slash (/) must be escaped if used as literals.</dd><dt>                Input example              </dt><dd>`/differentrules/.+\.php` - All php applications in directory /differentrules/ and below
`.+\.aspx` - Any application with extension .aspx
`/ecommerce/cart\.php` - The specific application /ecommerce/cart.php</dd><dt>                Default value              </dt><dd>None</dd></dl> |
| **              Overlapping scopes and validation order            ** | Web application scopes are listed in validation order and if scopes are overlapping validation order can be changed in the policy section "Web application validation order" immediately above the "web applications" group in the policy. If web application scopes overlap - as in the case of `.+\.aspx` vs `/morespecific/.+\.aspx` first match wins so to make the more specific option be evaluated first it should be moved to a position above the more general option. |

## Web application settings

<colgroup></colgroup>| **              Requests            ** Drop-down list | Configure URL request status. When set to deny all requests for the web application will be denied.<dl><dt>                Valid input              </dt><dd>Options from the drop-down list
`allow` or `deny`</dd><dt>                Default value              </dt><dd>`allow`</dd></dl> |
| **              Update            ** Drop-down list | Configure URL update setting.<dl><dt>                Valid input              </dt><dd>Options from the drop-down list
`auto` or `manual`
When update is set to `manual` the ACL entry will not be maintained and updated by the Learner.
When set to `auto` the entry will be maintained by the Learner.</dd><dt>                Default value              </dt><dd>`auto` - `manual` when URL added manually</dd></dl> |
| **              Violation action            ** Drop-down list | Action to take when a request for the web application is denied. When set to block or detect this setting will override the global setting for the violation at hand.<dl><dt>                Valid input              </dt><dd>Options from the drop-down list<dl><dt>                    Use global                  </dt><dd>Global settings will be used.</dd><dt>                    Protect                  </dt><dd>Block settings (as defined in global violation action) will be used no matter if the website is running in Protect or Detect.</dd><dt>                    Detect                  </dt><dd>Detect settings (as defined in global violation action) will be used no matter if the website is running in Protect or Detect.</dd><dt>                    Pass                  </dt><dd>Bypass violations for this specific application. Violations will neither be blocked nor logged.</dd></dl></dd><dt>                Default value              </dt><dd>`Use global`</dd></dl> |

## Global violation action override

Global violation action override allows for an even more fine grained violation action exception handling than simply specifying violation action for the web application. This override feature allows for specifying exceptions from the global violation action on a per violation type basis.

If, for instance, you have an application that generates "Malformed XML" because of some custom built client application sending XML requests that does not conform to standards it is possible to specify a policy exception for that specific violation for that specific application. This way you do not have to bypass XML validation globally or put the entire application in Pass or Detect mode.

To add a violation exception:

1. Select the violation type from the drop-down list **`Global violation action override`**
2. The selected violation type is listed above the drop-down list with two action types: One for global Protect mode and one for global Detect mode.
3. For each mode select the desired action which can be either of Protect, Detect or Pass.

## Methods allowed

Restrict which HTTP methods are allowed.

Corresponding violation: `Method illegal`

<colgroup></colgroup>| **              HEAD            ** Check box | Allow / disallow HTTP method HEAD. Default: `<allow>` |
| **              GET            ** Check box | Allow / disallow HTTP method GET. Default: `<allow>` |
| **              POST            ** Check box | Allow / disallow HTTP method POST. Default: `<allow>` |
| **              OPTIONS            ** Check box | Allow / disallow HTTP method OPTIONS. Default: `<disallow>` |
| **              PUT            ** Check box | Allow / disallow HTTP method PUT. Default: `<disallow>` |
| **              DELETE            ** Check box | Allow / disallow HTTP method DELETE. Default: `<disallow>` |
| **              MKCOL            ** Check box | Allow / disallow HTTP method MKCOL. Default: `<disallow>` |
| **              COPY            ** Check box | Allow / disallow HTTP method COPY. Default: `<disallow>` |
| **              MOVE            ** Check box | Allow / disallow HTTP method MOVE. Default: `<disallow>` |
| **              PROPFIND            ** Check box | Allow / disallow HTTP method PROPFIND. Default: `<disallow>` |
| **              PROPPATCH            ** Check box | Allow / disallow HTTP method PROPPATCH. Default: `<disallow>` |
| **              LOCK            ** Check box | Allow / disallow HTTP method LOCK. Default: `<disallow>` |
| **              UNLOCK            ** Check box | Allow / disallow HTTP method UNLOCK. Default: `<disallow>` |
| **              PATCH            ** Check box | Allow / disallow HTTP method PATCH. Default: `<disallow>` |

#### Session protection

<colgroup></colgroup>| **              Require a valid session to access this resource            ** Check box | Enable / disable authorization of access to this resource based on session validity. If enabled, whenever this resource is requested, WAF will only allow the request if it originates from a valid user session. Note that session protection and request authorization have to be enabled for resource request authorization to be effective. See [Session and CSRF protection](ref_services_policy_policy_global.md#global_session) Default: `<disabled>` |
| **              Enable request origin validation for this application            ** Check box | Enable/disable validation of requests resulting from forms with this application as action. If enabled, whenever a request for this application contains a specific parameter (see below) it is verified that the request origins from a form on a web page/application belonging to the web system and that the form has been issued on a page belonging to the current users session. Note that for the validation token to be generated Generate request form validation tokens (CSRF protection) has to be enabled. See [Session and CSRF protection](ref_services_policy_policy_global.md#global_session). Default: `<disabled>` |
| **               Validate parameter name            ** Input field | String specifying the name of a specific parameter to be present for WAF to perform request origin validation.<dl><dt>                Valid input              </dt><dd>A string definining a parameter name.</dd><dt>                Input example              </dt><dd>`amount`
Suppose for instance that you want to validate a money transfer request from a logged in user. With request CSRF protection configured (Session protection / generation of request form validation tokens / origin validation) enabled should a legitimate logged in user be tricked into issuing a forged request= then the origin of the request does not validate. In this case because the validation parameter (__pffv__) is not present.</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> |

## Parameters

This section contains a list of current defined parameters with corresponding input validation type and value and other settings.

To update a parameter simply change the values and click on the **Save** button.

<colgroup></colgroup>| **              Select parameter            ** Check box | Select or clear check box to mark for deletion. Default: <<kbd>not selected</kbd>> To mark an entry for deletion, check the box. When the parameter list is saved the parameter will be deleted. |
| **              Name            ** Input field | String specifying the parameters name.<dl><dt>                Valid input              </dt><dd>A string defining a name. No regular expressions.</dd><dt>                Input example              </dt><dd>`print` - the parameter print</dd><dt>                Default value              </dt><dd>The parameter name</dd></dl> |
| **              Type            ** Drop-down list | Input validation type.<dl><dt>                Valid input              </dt><dd>Options from the drop-down list<dl><dt>                    Class                  </dt><dd>A predeclared regular expression used by WAF for input request validation. Classes are defined on a proxy global basis. When a class is modified all parameters using that class is affected.</dd><dt>                    Static                  </dt><dd>Legitimate values for the parameter can only have fixed values defined. Values are separated by a newline.</dd><dt>                    Regexp                  </dt><dd>Legitimate input values for the parameter are based on the regular expression defined. Only one regular expression is allowed.</dd></dl></dd><dt>                Default value              </dt><dd>Class</dd></dl> |
| **              Value(s)            ** Depends on `type` | Value for input validation.<dl><dt>                Valid input              </dt><dd><dl><dt>                    Class name                  </dt><dd>When type `Class` is selected a drop-down menu is available in the **values** field. Input validation for the parameter is based on the regular expression corresponding to the selected class name.</dd><dt>                    Static values                  </dt><dd>Input values are validated against the static list of legitimate values for the parameter. If they match, the request is allowed by WAF. otherwise, the entire request is blocked.</dd><dt>                    Regular expression                  </dt><dd>input values are validated against the defined regular expression. if they match, the request is allowed by WAF. otherwise, the entire request is blocked.
For examples of using regular expressions for input validation refer to [Examples of regular expressions for input validation](ref_services_policy_global_regular_expressions.md#ap_validating_input_parameters).
Full match is implied for each regular expression, meaning that each will match from the start to the end of the request (a caret ^ and dollar $ will be appended if not present)</dd></dl></dd><dt>                Default value              </dt><dd>Class `Numeric`</dd></dl> |
| **              Negative Check            ** Drop-down options | Use negative checking if validation class is above configured threshold. If set to Auto the policy configured in classes negative signatures policy will be applied when validating input.<dl><dt>                Valid input              </dt><dd>Drop-down options</dd><dt>                Default value              </dt><dd>`Auto`</dd></dl> |
| **              Update            ** Drop-down options | Configure how the parameter should be handled by the Learner. If set to `Upgrade only` the Learner will only change the parameter if the class needs to set to a higher rank (relaxed). When set to `Auto` the Learner will make all changes to the parameter, including removing it if it later is learned to be a global parameter.<dl><dt>                Valid input              </dt><dd>Drop-down options</dd><dt>                Default value              </dt><dd>`Upgrade only`</dd></dl> |
