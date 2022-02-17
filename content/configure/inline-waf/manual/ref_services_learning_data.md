# Learning Data

The Alert Logic Managed Web Application Firewall (WAF) Learning Data page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Learning, see [Learning](ref_services_learning.md). To go to  the documentation for next subsection in the Learning section, see [Learning Settings](ref_services_learning_settings.md).

**To access the Learning page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under Learning, click **Learning Data**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

#### Applications learned

Applications learned is shown as a 3-level expandable table.

<colgroup></colgroup>| **              Applications learned            ** Expandable: Click **+** to expand. Expands 2 levels. | Group, URL path and details.<dl><dt>                Application group (level 1)              </dt><dd>Applications are divided into groups based on path characteristics. The group name reflects the characteristics of the group. The most common grouping criteria is the file extension. But also the appearance of special characters like '$' or '.' in the path is used as grouping criteria.<dl><dt>                    Applications URL paths (level 2)                  </dt><dd>When a group is expanded the URL paths in that group is listed. Each URL path is an application learned. Note that this list also contains "simple" applications, applications that only takes global parameters as input, and therefore potentially can be very long.<dl><dt>                        Application details (level 3)                      </dt><dd>When an application URL path is expanded the details learned about that specific application is shown.</dd></dl></dd></dl></dd></dl> |
| **              Param            ** | Number of parameters the application takes as input. If a blue number in parentheses is shown at the left of the number this number indicates how many of the parameters learned that are approved based on the Learner thresholds which are configurable. Parameters that does not exceed one or more threshold values are colored blue while trusted parameters name are black. Applies to: URL path level (2). |
| **              Class            ** | Name of input validation class mapped to a parameter. If the parameter is not trusted yet, the class name is blue. Applies to: Detail level (3). |
| **              Paths            ** | Number of unique URL Paths in the group. Applies to: Group level (1). |
| **              Source            ** | Number of unique IP-addresses requesting the resource. Applies to: Group (1), URL path (2) and Detail level (3). |
| **              Time            ** | Number of unique timestamps in requests for the resource. Applies to: Group (1), URL path (2) and Detail level (3). |
| **              ΔTime (delta time)            ** | Time difference between the first and last observed request for the resource. Applies to: Group (1), URL path (2) and Detail level (3). |

##### Deleting applications or corresponding parameters

To delete a learned application or a corresponding parameter expand to the level desired and click the red X.

#### Global parameters learned

The Global parameters learned section shows all parameters observed on a number of paths that exceeds the Learner setting Global parameters *Path duplication threshold*.

Note that the list also includes observed parameter names which are still pending approval based on the Learner threshold settings. The number of approved, or trusted, observations is indicated with black number while a blue number shows the number of non-approved observations.

<colgroup></colgroup>| **              Global parameters            ** Expandable: Click **+** to expand. Expands 1 level. | Group, URL path and details.<dl><dt>                Parameter name (level 1)              </dt><dd>Name of the parameter<dl><dt>                    Applications URL paths (level 2)                  </dt><dd>When Global parameter is expanded a list of URL paths which are observed taking the parameter as input is shown.</dd></dl></dd></dl> |
| **              Class            ** | Name of input validation class mapped to a parameter. Applies to: Parameter name level (1). |
| **              Paths            ** | Number of unique URL Paths observed using the parameter. Applies to: Parameter name level (1). |
| **              Pending            ** | Number of unique URl Paths using the parameter but where the parameter name is not approved yet - where threshold values is not reached yet. Applies to: Parameter name level (1). |
| **              Trusted            ** | Number of unique URl Paths using the parameter where the parameter name *is approved* - where threshold values is reached. Applies to: Parameter name level (1). |

#### Cookies learned

<colgroup></colgroup>| **              Cookies learned            ** Expandable: Click **+** to expand. Expands 1 level. |  |
| **              Class            ** | Name of input validation class mapped to a parameter. Applies to: Parameter name level (1). |
| **              Pending            ** | Number of unique URl Paths using the parameter but where the parameter name is not approved yet - where threshold values is not reached yet. Applies to: Parameter name level (1). |
| **              Trusted            ** | Number of unique URl Paths using the parameter where the parameter name *is approved* - where threshold values is reached. Applies to: Parameter name level (1). |

#### Static content learned

This section shows all URL Paths to static resources learned. URL Paths are grouped by their extension.

<colgroup></colgroup>| **              Static content learned            ** Expandable: Click **+** to expand. Expands 1 level. | Extension and URL Paths learned.<dl><dt>                Extension (level 1)              </dt><dd>The static content policy is based on allowing extension and URL Path based on characters in the URl path.
To be included in the static content policy, static resources must therefore have a file extension. A case where natural URLs are pointing to static content is handled by the Learner by building Global URL policies.<dl><dt>                    Static content URL paths (level 2)                  </dt><dd>When an extension is expanded the URL paths in that extension group is listed.</dd></dl></dd></dl> |
| **              Paths            ** | Number of unique URL Paths in the extension group. Applies to: Extension level (1). |
| **              Source            ** | Number of unique IP-addresses requesting the resource. Applies to: Extension (1) and URL path level (2). |
| **              Time            ** | Number of unique timestamps in requests for the resource. Applies to: Extension (1) and URL path level (2). |
| **              ΔTime (delta time)            ** | Time difference between the first and last observed request for the resource. Applies to: Extension (1) and URL path level (2). |

##### Deleting static content extensions

To delete a static content extension (a group) click the red X in the list.

#### Tools

This contains tools for tidying the learning data set.

<colgroup></colgroup>| **              Delete querys by name wildcard            ** Input field | Delete learned parameter names using simple wildcard matching.<dl><dt>                Valid input              </dt><dd>A string or a simple wildcard.
Use the following characters to specify wildcards:
`* =` any string any length.
`? =` one ocurrence of any character.</dd><dt>                Input example              </dt><dd>`http://*` - matches all querys (parameter names) beginning with http://</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> **                Preview              ** displays parameter names matching the wildcard below the input field. **                Delete              ** performs deletion of parameters matching wildcard. |
| **              Delete querys by data            ** Input field | Delete learned parameter names using matching occurrence data. **                Source              ** Number of IP addresses requesting the resource.<dl><dt>                Valid input              </dt><dd>`number` in range 0 -</dd><dt>                Input example              </dt><dd>`10` - Querys requested by 10 or less IP addresses.</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> **                Time              ** Number of unique timestamps in requests for the resource.<dl><dt>                Valid input              </dt><dd>`number` in range 0 -</dd><dt>                Input example              </dt><dd>`10` - Querys requested in a maximum of 10 intervals of 1 second.</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> **                ΔTime (delta time)              ** Time difference between the first and last recorded request for the resource.<dl><dt>                Valid input              </dt><dd>Time interval specified in seconds.
`number` in range 0 -</dd><dt>                Input example              </dt><dd>`86400` - Querys with a recorded difference between first and last request of maximum 24 hours (24 * 60 * 60).</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;none&amp;amp;gt;`</dd></dl> **                Preview              ** displays parameter names matching search criteria below the input fields. **                Delete              ** performs deletion of parameters matching search criteria. |

#### Lower button bar

The lower button bar contains the following buttons.

<colgroup></colgroup>| **              Re-analyze data            ** Button | To see the effect of deleting selected learning data in the resulting policy section click this button. Wait a few seconds and reload the page. |
| **              Reset learn data            ** Button | Use with caution! When clicking this button and accepting the confirm pop-up window. *All learning data for that proxy will be deleted!* If learning is enabled the learning and data sampling process will start from scratch. |
