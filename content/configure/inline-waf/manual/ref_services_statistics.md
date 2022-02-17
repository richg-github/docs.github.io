# Statistics

The Alert Logic Managed Web Application Firewall (WAF) Statistics page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of the Reports subsection, see [Reports](ref_services_reports.md). To go to  the documentation for next subsection in the Reports subsection, see [System](ch_system.md).

**To access the Reports page in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under Reports, click **Statistics**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The *Statistics section* contains various proxy specific statistics information.

### Interval selection

This section is used for selection of the interval used for generating the statistics. The interval is always calculated from the current time.

<dl><dt>        Show last      </dt><dd>Shows the statistics from current date and time and back the selected interval. Eg. 8 hours.</dd><dt>        Show stats      </dt><dd>Refresh the statistics based on the current selection.</dd></dl>### Summary section

This section shows the statistics for the currently selected proxy.

<colgroup></colgroup>| **              Requests total            ** | Total number of requests. |
| **              Requests/sec (avg.)            ** | Average number of requests for the selected period. |
| **              Compression ratio            ** | Compression ratio for the selected period. Eg. 60% means that the original data was compressed to the 60% of it's original size. |
| **              Cache hits            ** | Percentage of responses served from the cache |
| **              Original data            ** | Amount of original data before compression (in megabytes). |
| **              Data transferred            ** | Amount of data transferred. |
| **              Data received            ** | Amount of data received. |
| **              Response codes            ** | Click **Show details** link to toggle display of web server response codes:<dl><dt>                    Normal                  </dt><dd>Response code: ``200``
Number of requests processed normally.</dd><dt>                    Redirect                  </dt><dd>Response codes: `300-399`
Number of requests redirected.</dd><dt>                    Access denied                  </dt><dd>Response codes `400-499` except `404`
Number of requests that was denied for some reason.</dd><dt>                    Not found                  </dt><dd>Response code: `404`
Number of requests for unavailable content or resources.</dd><dt>                    Internal error                  </dt><dd>Response codes: `500-599` except `502`
Number of requests resulting in an internal server error.</dd><dt>                    Bad gateway                  </dt><dd>Response code: `502`
Number of requests resulting in the `bad gateway` error.</dd><dt>                    Other                  </dt><dd>Number of requests generating other error codes.</dd></dl> |
| **              Interval            ** Drop-down options | Selection of the interval used for generating the statistics. The interval is always calculated from the current time.<dl><dt>                    8 hours                  </dt><dd>Displays an interval of 8 hours counting backwards from the current time.</dd><dt>                    24 hours                  </dt><dd>Displays an interval of 24 hours counting backwards from the current time.</dd><dt>                    Week                  </dt><dd>Displays an interval of one week counting backwards from the current time.</dd><dt>                    Month                  </dt><dd>Displays an interval of one month counting backwards from the current time.</dd></dl> |
| **              Period start            ** | Starting date and time for the generated statistics. |
| **              Period end            ** | Ending date and time for the generated statistics. |

### Compression and served from cache graph

This graph shows the compression ratio and served from cache ratio for the selected proxy and interval.

<colgroup></colgroup>| **              Compression ratio            ** | Compression ratio spanning the selected interval. |
| **              Requests/sec (avg.)            ** | Shows the served from cache ratio spanning the selected interval. |

### Requests total and served from cache graph

This graph shows the total number of requests and served from cache number for the selected proxy and interval.

<colgroup></colgroup>| **              Requests total            ** | Shows the total requests spanning the selected interval. |
| **              Requests served from cache            ** | Shows the served from cache requests spanning the selected interval. |

### Lower button bar

<colgroup></colgroup>| **              Clear stats            ** | Clear all stat data and start from scratch. |
